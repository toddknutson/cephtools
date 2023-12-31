# cephtools installation instructions

## Introduction

There are multiple ways to start using cephtools. 

1. Load a module
1. Clone the repo and checkout any version tag or commit


## Load a module

### Load the default version (i.e. most current)  *highly recommended*

```
MODULEPATH="/home/lmnp/knut0297/software/modulesfiles:$MODULEPATH" module load cephtools
```


### Check available versions or load a specific version

```
MODULEPATH="/home/lmnp/knut0297/software/modulesfiles:$MODULEPATH" module avail cephtools

MODULEPATH="/home/lmnp/knut0297/software/modulesfiles:$MODULEPATH" module load cephtools/2.0.0
```

> Technical note: 
>  
> If you include `MODULEPATH="/home/lmnp/knut0297/software/modulesfiles:$MODULEPATH"` before running the `module` commands (e.g. `avail`, `load`, etc.), the `MODULEPATH` variable will be prepended to include my personal modulefile path, in addition to the default MSI modulefile paths normally included in the `MODULEPATH` variable. Doing this will not export or permanently change your `MODULEPATH` variable -- it only changes your `MODULEPATH` variable for the single `module` command, run on the same line. 

 

## Clone the repo and checkout any version tag or commit

### Download
The repo is located on the UMN GitHub site, but is public to anyone with access to [github.umn.edu](github.umn.edu). However, using `wget` with https does not work because you need to authenticate using your UMN GitHub credentials. 


```
git clone git@github.umn.edu:knut0297org/cephtools.git
cd cephtools

# List available tags
git tag

# List recent commits
git log

git checkout tags/<tag_name>
git checkout <commit>

```



#### Build the tool

The repo contains a makefile that will build the final bash script and manual pages. By default, a "build" dir is created inside the cephtools repo that will contain the program.
 
```
# Move into the repo dir (cephtools) and run make
make

# Update paths
# Add these to your ~/.bashrc if you want cephtools available in every new shell
export PATH="${PWD}/build/bin:${PATH}"
export MANPATH="${PWD}/build/share/man:${MANPATH}"
```



If you want to build the program in a different location, specify an build/install directory by setting a PREFIX variable when running `make`.


```
# Move into the repo dir (cephtools) and run make
make PREFIX=/my/fav/build/dir

# Update paths
# Add these to your ~/.bashrc if you want cephtools available in every new shell
export PATH="${PREFIX}/bin:${PATH}"
export MANPATH="${PREFIX}/share/man:${MANPATH}"
```



