# node-wot
Web of Things implementation on Node.js

Build:
[![Build Status](https://travis-ci.org/thingweb/node-wot.svg?branch=master)](https://travis-ci.org/thingweb/node-wot)

## License

W3C Software License

## Prerequisites

On Windows, install the build tools
```
npm install --global --production windows-build-tools
```

## How to get ready for coding

```
# Clone the repository
git clone https://github.com/thingweb/node-wot

# Go into the repository
cd node-wot

# install root dependencies (locally installs tools like typescript and lerna)
npm install 

# bootstrap the packages (installs dependencies and links the inter-dependencies)
# Note: This step is automatically done on building or testing
npm run bootstrap

# use tsc to transcompile TS code to JS in dist directory for each package
npm run build

# run test suites of all packets
npm run test 

# (OPTIONAL!) 
# make all packages available on your local machine (as symlinks)
# you can then use each paket in its local version via "npm link" instead of "npm install"
# see also https://docs.npmjs.com/cli/link
sudo npm run link

```

## No time for explanations - I want to start from something running!
Run all the steps above and then run this:

```
cd examples/scripts
wot-servient


# e.g., Windows CMD shell
# node  packages\node-wot-servient-examples\dist\command-line-tool\wot-servient.js  examples\scripts\counter.js
```

* go to http://localhost:8080/counter and you'll find a thing description.
* you can query the count by http://localhost:8080/counter/properties/count
* you can modify the count via POST on http://localhost:8080/counter/actions/increment and http://localhost:8080/counter/actions/decrement
* application logic is in ``examples/scripts/counter.js``

## How to use the library

This library implements the Scripting API defined in the [WoT Current Practices](https://w3c.github.io/wot/current-practices/wot-practices.html#scripting-api) document. 

You can also see _examples/scripts_ to have a feeling of how to script a Thing.

Not everything has been succesfully implemented.

## Logging

We used to have a node-wot-logger package to allow fine-grained logging (by means of Winston). It turned out though that depending on the actual use-case other logging libraries might be better suited. Hence we do not want to prescribe which logging library to use. Having said that, we use console statements which can be easily overriden to use the prefered logging library if needed (see [here](https://gist.github.com/spmason/1670196)).
