---
title: "How to build project? OpenAL"
date: 2011-03-02
forum: Programming Talk
---

### Post by lelandnielsen on 2011-03-02
Hi, noob here.  Hope I'm posting my very basic question in the right place.  

I just jumped into Ubuntu and I'm teaching myself C++.  I want to install the OpenAL audio libraries to use in a project.  The OpenAL instructions read: 

```
To install OpenAL Soft, use your favorite shell to go into the build/
directory, and run:

cmake ..

Assuming configuration went well, you can then build it, typically using GNU
Make (KDevelop, MSVC, and others are possible depending on your system setup
and CMake configuration).
```

cmake runs and I get this:
```
cmake version 2.8.0
Usage

  cmake [options] <path-to-source>
  cmake [options] <path-to-existing-build>

Options
  -C <initial-cache>          = Pre-load a script to populate the cache.
  -D <var>:<type>=<value>     = Create a cmake cache entry.
  -U <globbing_expr>          = Remove matching entries from CMake cache.
  -G <generator-name>         = Specify a makefile generator.
  -Wno-dev                    = Suppress developer warnings.
  -Wdev                       = Enable developer warnings.
  -E                          = CMake command mode.
  -i                          = Run in wizard mode.
  -L[A][H]                    = List non-advanced cached variables.
  --build <dir>               = Build a CMake-generated project binary tree.
  -N                          = View mode only.
  -P <file>                   = Process script mode.
  --graphviz=[file]           = Generate graphviz of dependencies.
  --system-information [file] = Dump information about this system.
  --debug-trycompile          = Do not delete the try compile directories..
  --debug-output              = Put cmake in a debug mode.
  --trace                     = Put cmake in trace mode.
  --help-command cmd [file]   = Print help for a single command and exit.
  --help-command-list [file]  = List available listfile commands and exit.
  --help-commands [file]      = Print help for all commands and exit.
  --help-compatcommands [file]= Print help for compatibility commands.
  --help-module module [file] = Print help for a single module and exit.
  --help-module-list [file]   = List available modules and exit.
  --help-modules [file]       = Print help for all modules and exit.
  --help-custom-modules [file]= Print help for all custom modules and exit.
  --help-policy cmp [file]    = Print help for a single policy and exit.
  --help-policies [file]      = Print help for all policies and exit.
  --help-property prop [file] = Print help for a single property and exit.
  --help-property-list [file] = List available properties and exit.
  --help-properties [file]    = Print help for all properties and exit.
  --help-variable var [file]  = Print help for a single variable and exit.
  --help-variable-list [file] = List documented variables and exit.
  --help-variables [file]     = Print help for all variables and exit.
  --copyright [file]          = Print the CMake copyright and exit.
  --help                      = Print usage information and exit.
  --help-full [file]          = Print full help and exit.
  --help-html [file]          = Print full help in HTML format.
  --help-man [file]           = Print full help as a UNIX man page and exit.
  --version [file]            = Show program name/version banner and exit.

Generators

The following generators are available on this platform:
  Unix Makefiles              = Generates standard UNIX makefiles.
  CodeBlocks - Unix Makefiles = Generates CodeBlocks project files.
  Eclipse CDT4 - Unix Makefiles
                              = Generates Eclipse CDT 4.0 project files.
  KDevelop3                   = Generates KDevelop 3 project files.
  KDevelop3 - Unix Makefiles  = Generates KDevelop 3 project files.

```

Then I am unable to build.  I've done this before with other packages by typing "make".
What am I missing here?  

I've been Googling for the last hour and no dice.  Any help is greatly appreciated.
Thanks!

---

