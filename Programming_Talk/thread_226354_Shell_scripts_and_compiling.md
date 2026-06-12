---
title: "Shell scripts and compiling"
date: 2006-07-31
forum: Programming Talk
---

### Post by mnf on 2006-07-31
Hi,

I'm new to Ubuntu Linux (and Linux generally) - and although the install went smoothly (wonderfully) I am having problems using the compiler.

I want to compile using the boost libraries (see boost.org - if you use C++ these are well worth checking out) - and thought to start by compiling bjam (a make replacement)
Unfortunately I cannot get the build script to work
I use
   sudo sh build.sh
This would compile fine under mandriva but here throws up a lot of 'command not found' errors.
So I'd guess it may be a PATH error - but I'm at a loss where to look.
So any suggestions gratefully received.

Martin

---

### Post by adamkane on 2006-07-31
Post the script, and we'll walk you through the Ubuntu jungle.

---

### Post by mnf on 2006-07-31
OK, the whole script is pretty long, but the first part is :


#!/bin/sh



#~ Copyright 2002-2004 Rene Rivera.

#~ Distributed under the Boost Software License, Version 1.0.

#~ (See accompanying file LICENSE_1_0.txt or [http://www.boost.org/LICENSE_1_0.txt](http://www.boost.org/LICENSE_1_0.txt))



# Reset the toolset.

BOOST_JAM_TOOLSET=



# Run a command, and echo before doing so. Also checks the exit

# status and quits if there was an error.

echo_run ()

{

    echo "$@"

    $@

    r=$?

    if test $r -ne 0 ; then

        exit $r

    fi

}



# Print an error message, and exit with a status of 1.

error_exit ()

{

    echo "###"

    echo "###" "$@"

    echo "###"

    echo "### You can specify the toolset as the argument, i.e.:"

    echo "###     ./build.sh gcc"

    echo "###"

    echo "### Toolsets supported by this script are:"

    echo "###     acc, como, darwin, gcc, intel-linux, kcc, kylix, mipspro,"

    echo "###     sunpro, tru64cxx, vacpp"

    echo "###"

    echo "### A special toolset; cc, is available which is used as a fallback"

    echo "### when a more specific toolset is not found and the cc command is"

    echo "### detected. The 'cc' toolset will use the CC, CFLAGS, and LIBS"

    echo "### envrironment variables, if present."

    echo "###"

    exit 1

}



# Check that a command is in the PATH.

test_path ()

{

    if `command -v command 1>/dev/null 2>/dev/null`; then

        command -v $1 1>/dev/null 2>/dev/null

    else

        hash $1 1>/dev/null 2>/dev/null

    fi

}



# Check that the OS name, as returned by "uname", is as given.

test_uname ()

{

    if test_path uname; then

        test `uname` = $*

    fi

}




Using sudo sh ... this fails with (as does the complete script)
: command not found
: command not found
: command not found
'uild.sh.2: line 12: syntax error near unexpected token `
'uild.sh.2: line 12: `echo_run ()

Martin

---

### Post by adamkane on 2006-07-31
I've downloaded Boost. I'll work on this more later tonight.

---

### Post by mlind on 2006-07-31
try executing *sudo bash -x build.sh* to get a clue where it chockes.
If it calls some binaries on the way, using strace helps.

---

### Post by mnf on 2006-07-31
Just tried again with the sh -x option.  It could just be that it is choking on the return '\r' control characters - I notice that when I posted the copy   
of the shell script it was double spaced too?

Martin

---

### Post by mlind on 2006-07-31
> **mnf said:**
> Just tried again with the sh -x option.  It could just be that it is choking on the return '\r' control characters - I notice that when I posted the copy   
of the shell script it was double spaced too?

Martin

It would make script easier to read if you post it inside [code] [/code ] elements.

---

