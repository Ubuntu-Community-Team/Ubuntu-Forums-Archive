---
title: "Anyone knowledgable in Doxygen?"
date: 2010-05-04
forum: Programming Talk
---

### Post by Zyrtec on 2010-05-04
I'm doing a project that requires Doxygen documentation of the program. The program itself is compiled from 2 different .c files.

I was wondering how to do Doxygen documentation on one main.c file that includes the functions from the other 2 .c files. Up until now, I've only had to do Doxygen on one file, so I'm not sure of how to go about doing several.

Thanks!

---

### Post by Compyx on 2010-05-04
It's quite simple. ;)

I'm going to assume your source files are in a directory 'src'.

In the root directory of your project, you run:
```

doxygen -g

```
to generate a 'Doxyfile' configuration file.

You then edit that file and alter a few settings:
```

OUTPUT_DIRECTORY = doc
OPTIMIZE_OUTPUT_FOR_C = YES
INPUT = src

```

I also prefer to set 'WARN_NO_PARAMDOC = YES' and enable generation of call/caller graphs by setting 'HAVE_DOT = YES', 'CALL_GRAPH = YES' and 'CALLER_GRAPH = YES' (you'll need to install Graphviz for this to work).

There's a boatload of other options, just read through the Doxyfile to see if you need them.

Once you're done, you simple run 'doxygen' in your project's root directory to have it generate the documentation in ./doc/html and ./doc/latex.


And if you happen to use Vim, you can do a :set syn=c.doxygen to get syntax highlighting of the doxygen tags in your source files.


I also prefer to run doxygen from my Makefile:

```

.PHONY: doc-html-doxygen
doc-html-doxygen:
        $(SH) bin/run_doxygen.sh

```

With the run_doxygen script containing:
```

#!/bin/bash
# vim: set et ts=4 sw=4 sts=4 fdm=marker:
#
# This script simply runs doxygen to generate the html documentation and prints
# any errors or warnings at the end of the output, reducing the amount of
# scrolling through the warnings.

# File to redirect doxygen's stderr to
DOXYLOG=doxygen.errors

# Run doxygen and redirect stderr to file
doxygen Doxyfile 2>$DOXYLOG

# Display file content if the file is not empty
if [ -s $DOXYLOG ]; then
    echo -e "\033[31mErrors/warnings:\033[0m"
    cat $DOXYLOG
else
    echo -e "\033[32mOK - no errors or warnings\033[0m"
fi

```

This outputs all warnings and errors after doxygen has run, separating the warnings/errors from the other output of doxygen.

---

### Post by Zyrtec on 2010-05-04
Thanks for the awesome advice!

---

