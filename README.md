//  
// These files for students analysis raw data  
// There are files for root 5 or root 6 installed, along with instructions for how to convert from root 5 to root 6.


// Get the dependencies listed here: https://root.cern/install/dependencies  
// (One of the downloads listed in the optinal dependencies didn't work for me)  
// Next, follow https://root.cern/install/build_from_source/  
// I started with `git clone --branch v5-34-38 https://github.com/root-project/root.git root_src` for root 5.
// This downloads it to a folder called root_src  

// If you get error 2: This does not look like a tar archive, do: `sudo apt install curl`

// For root 6, you can install one of the pre-built binaries, or build it yourself using the instructions in the above links.

// To add ROOT to your environment variables (allows you to open it by just typing `root`), you need to follow these instructions:  
// https://root.cern.ch/root/htmldoc/guides/users-guide/GettingStarted.html  
// These will only work for the session you're in. To set them permanently, add them to your .bashrc file, a hidden file in your home directory. The ones I added for Ubuntu 20 were:  

`export ROOTSYS=$HOME/root`  
`export PATH=$PATH:$ROOTSYS/bin`  
`export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ROOTSYS/lib`  
`export PROJECT=$HOME/Documents/mu2e/ExampleRootForStudents`  // use your directory path  

//  
// Next, go into the main directory of your ForStudents files, open terminal, type `make clean`, then `make`. This compiles a bunch of necessary files for you.

//  
// You'll need to untar the data .root file.  
// Example untar file 

`$ tar xvjf file.tbz`

// x = extract  
// v = verbose, verbosely list files processed  
// j = use bzip2  
// f = file, take file input

//  
// For us

`$ tar xvjf data/1000evn.tbz`

// Example analysis raw data

`$ cd macros`  
`/macros$ root -l`  
`root[0] .L testShowProf_rawevent.cxx`  
`root[1] testShowProf_rawevent("path/to/rootfile",100)`         //100 is the number of events  
// as of initial commit, the path to the rootfile from the macros folder is "../data/1000evn_v3.root"  

// with root6 in macOS  
`$ cd macros`  
`/macros$ root -l`  
`root [0] .L testShowProf_rawevent_root6.cxx `

```
RooFit v3.60 -- Developed by Wouter Verkerke and David Kirkby 
                Copyright (C) 2000-2013 NIKHEF, University of California & Stanford University
                All rights reserved, please read http://roofit.sourceforge.net/license.txt

Error in <TCling::RegisterModule>: cannot find dictionary module DataCint_rdict.pcm
```  

// it shows error here but it can run the macro file.

`root [1] testShowProf_rawevent("../data/1000evn_v3.root",100)`

