# Documentation for ExtendScript API #

This repo contains the source code for building the documentation system. If you're only interested in viewing the documentation then please look [here](http://yearbook.github.com).

## Prerequisites ##

  - Python3
  - Node.js and npm
  - Adobe InDesign/Illustrator/Photoshop and ExtendScript Toolkit for XML source files

## Generating the documentation ##

Install node packages:

    $ npm install

Build automatically (only works on OSX):

    $ npm run build

The docs will be compiled to `public/`. OMV XML files will automatically be found, if you're building on Windows you will need to locate these yourself.

## Development guide ##

Building the documentation requires the following steps:

  1. Locate the source OMV XML files, copy them to `./xml/source`. The script `./src/findxml` will do this for you on OSX.
  2. Parse the XML files, output as JSON with `./src/xml2json.py`.
  3. Map the output JSON files to the `public` directory with `./src/json2public.py`. The file `./xml/map.json` defines what files to copy.
  4. Build the web interface.

gulp and npm are setup to run these for you.

To build all the documentation from scratch:

    $ npm run build
    
To watch `src/` and compile automatically to `public/`:

    $ npm run watch

To clean the dist files:

    $ npm run clean

The easiest way to view the docs locally is to use [zapp](https://www.github.com/wridgers/zapp).

    $ npm install -g zapp
    $ zapp public/

Now open your browser [here](http://localhost:8080).

### XML file locations ###

The XML source files can be found in the following locations on Mac OS X:

  - `/Library/Application Support/Adobe/Scripting Dictionaries CC/CommonFiles`
  - `/Library/Application Support/Adobe/Scripting Dictionaries CC/Illustrator`
  - `/Library/Application Support/Adobe/Scripting Dictionaries CC/photoshop`
  - `~/Library/Preferences/ExtendScript Toolkit/4.0/`
  
On Windows:

  - `C:\Program Files (x86)\Common Files\Adobe\Scripting Dictionaries CC/CommonFiles`
  - `C:\Program Files (x86)\Common Files\Adobe\Scripting Dictionaries CC/illustrator`
  - `C:\Program Files (x86)\Common Files\Adobe\Scripting Dictionaries CC/photoshop`
  - `C:\Users\<YourUserName>\AppData\Roaming\Adobe\ExtendScript Toolkit\4.0`
  
If you have a 64-Bit version of the Adobe program installed, go to `C:\Program Files\` instead of `C:\Program Files (x86)\`.

# License #

All source code for generating the documentation is under the MIT license. The XML source files (not included) remain property of Adobe.
