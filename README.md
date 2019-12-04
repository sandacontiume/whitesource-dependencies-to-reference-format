# whitesource-dependencies-to-reference-format
## Description
Extracts dependencies from the inventory report json artifact of tool Whitesource.

Outputs the following file: 
  - __dependencies.json__ contains the dependencies extracted from the inventory file, in a reference format. This reference format is a JSON file containing arrays of objects with keys _name_ and _version_. It contains unique objects by the combination _name_ and _version_

### Preconditions
The  inventory whitesource report is expected to contain keys _name_ and _version_ for every element in the inventory.

### How is information extracted to reference format?
The version in the output file matches the version in the whitesource inventory report. The dependency name in the output file is derived from the name and version fields in the inventory report, as indicated in the following examples:

| Name in Whitesource                  | Version in Whitesource | Name in output                       |   Version in output   
| -------------------------------------|:----------------------:|  ------------------------------------|--------------------
| json-schema-0.2.3.tgz                | 0.2.3                  | json-schema                          | 0.2.3
| annotations-13.0.jar                 | 13.0                   | annotations                          | 13.0 
| io.js                                | v0.9.2                 | io.js                                | v0.9.2
| webassemblyjs-wasm-parser-1.7.10.tgz |                        | webassemblyjs-wasm-parser-1.7.10.tgz |

# Status
0.0.1, see [CHANGELOG.md](./CHANGELOG.md)

# Limitation
- tested with Whitesource output (version 19.11.1.190) as generated by scanning projects of the following technologies: 
  - Java
  - Javascript

# Prerequisites
- you should have Node installed (this script was tested with node v12.2.0)
- you should have yarn installed (we used version v1.19.0)

# Usage
```
yarn extract [options]
```

### Supported options:

| Flag                 | Alias | Functionality
| ---------------------|:-----:| -------------------------------------
| --input [filename]   |  -i   | (mandatory) Filename of the Whitesource inventory report file to extract dependencies from.
| --output [filename]|  -o   | (optional) Filename to which the list of dependencies (name+version) is written (json format). If the file already exists, it will be overwritten. Default value: dependencies.json
| --verbose          |       | Verbose output of commands and errors
| --help             | -h    | Displays usage information
| --version          | -v    | Displays version number



### Sample usage
```
yarn extract -i ./sampleData/sampleInput.json
```
## Technology stack
- Javascript
- This software is intended to be used standalone, as a command-line tool

## How to build
Get the sources locally; in a command line, go to the root folder of this project and execute:
```
yarn install
```
## How to test
```
yarn test
```
or 
```
yarn coverage
```

## How to do static analysis of code
Automatically enabled: standard
```
yarn lint
```

## Owners
See [CODEOWNERS](./CODEOWNERS)

## Maintainers
See [MAINTAINERS.md](./MAINTAINERS.md)

## Contributing
See [CONTRIBUTING.md](./CONTRIBUTING.md)

## License
See [LICENSE.md](./LICENSE.md)

## Author
Sanda Contiu

## Keywords
  - dependencies
  - sbom
  - software bill of material
  - whitesource
  - extract
  - retrieve