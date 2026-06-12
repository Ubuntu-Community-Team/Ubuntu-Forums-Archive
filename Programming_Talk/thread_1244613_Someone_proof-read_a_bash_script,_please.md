---
title: "Someone proof-read a bash script, please"
date: 2009-08-19
forum: Programming Talk
---

### Post by Clorow on 2009-08-19
I am creating a script that gives Ubuntu GobuLinux-style directories before installing. Tell me of any problems:
```

#!/bin/bash
# This script is made by Clay Smalley and made available under the "New" BSD license.

# Copyright (c) 2009, Clay Smalley
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above copyright
#       notice, this list of conditions and the following disclaimer in the
#       documentation and/or other materials provided with the distribution.
#     * The name of Clay Smalley may not be used to endorse or promote products
#       derived from this software without specific prior written permission.
# 
# THIS SOFTWARE IS PROVIDED BY CLAY SMALLEY ''AS IS'' AND ANY
# EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
# WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
# DISCLAIMED. IN NO EVENT SHALL CLAY SMALLEY BE LIABLE FOR ANY
# DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
# (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
# LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
# ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
# SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


#############################################################################
# This script DOES NOT INCLUDE GOBOHIDE.                                    #
# This script DOES NOT INCLUDE GOBOHIDE.                                    #
# This script DOES NOT INCLUDE GOBOHIDE.                                    #
# This script DOES NOT INCLUDE GOBOHIDE.                                    #
# This script just puts everything where it's supposed to be GoboLinux-wise.#
#############################################################################

###################
#Prepare variables#
###################
directory=
question=

######################
#Beginning user input#
######################
if [ $(id -u) != "0" ]
then
    echo "You must use sudo to run this script. Exiting..." >&2
    exit 1
fi
       
until [ -d newdir ]
do
    echo -n "Type the directory of the mountpoint of your new installation: "
    read newdir
done

until [ "$question" = yes ]
do
    echo "GoboBuntu will be prepared in $newdir. Is this correct?"
    echo -n "You must type \"yes\": "
    read question
done

#############
#Here we go!#
#############
echo "Working..."

#/usr, to make sure things go right
mkdir usr
ln -s usr usr/local

#Home directory
cd $newdir
mkdir Users
ln -s Users home
mkdir Users/root
ln -s Users/root root

#Mountage
mkdir Media
ln -s Media mnt
ln -s Media media

#System
mkdir System
cd System

# Devices
mkdir Devices
ln -s Devices ../dev

# Boot
mkdir Boot
ln -s Boot ../boot

# Settings
mkdir Settings
ln -s Settings ../etc

# Optional install directory
mkdir Extras
ln -s Extras ../opt

# Processes
mkdir Processes
ln -s Processes ../proc

# Servers
mkdir Servers
ln -s Servers ../srv

# Kernel
mkdir Kernel
ln -s Kernel ../sys

# Temporary files
mkdir Temporary
ln -s Temporary ../tmp

# Variable (I'm not gonna deal with this.)
mkdir Variable
ln -s Variable ../var

# Links (Here we go again...)
mkdir Links
cd Links

#  Executables
mkdir Executables
ln -s Executables ../../bin
ln -s Executables ../../sbin
ln -s Executables ../../usr/bin
ln -s Executables ../../usr/sbin

#  Headers
mkdir Headers
ln -s Headers ../../usr/include

#  Source
mkdir Source
ln -s Source ../../usr/src

#  Shared
mkdir Shared
ln -s Shared ../../usr/share

#  Libraries
mkdir Libraries
cd Libraries

#   Main
mkdir main
ln -s main ../../../lib
ln -s main ../../../usr/lib

#   32
mkdir 32
ln -s 32 ../../../lib32
ln -s 32 ../../../usr/lib32

#   64
mkdir 64
ln -s 64 ../../../lib64
ln -s 64 ../../../usr/lib64

cd ../../..


#FIXME Anything else left to do????









echo "Completed! You are ready to install."
exit 0


```

---

### Post by geirha on 2009-08-20
One obvious pitfall is that you never check the return value of cd. If cd fails, it will run the commands in the wrong directory.

```

cd "$newdir" || exit
# At this point you are sure to be in $newdir

```

You forgot the $ on one of the expansions of the newdir variable. And also, quote parameter expansions! Especially if they contain pathnames.

```

mkdir "/tmp/foo bar"
newdir="/tmp/foo bar"

cd $newdir   # Does this do what you expect?
cd "$newdir" # Does this?

```

---

### Post by Clorow on 2009-08-20
Thanks! I found out a few other mistakes by myself also, but this helped a lot. :P

---

### Post by Clorow on 2009-08-20
Also, I sort of made sure the directory was valid with the "if [ -d ....." statement. But there's nothing bad about being too sure.

---

### Post by geirha on 2009-08-20
> **Clorow said:**
> Also, I sort of made sure the directory was valid with the "if [ -d ....." statement. But there's nothing bad about being too sure.

Yes, but [ -d ... ] only tells you if the file exist, and that it is a directory. It doesn't tell you if the directory's permission mode allows you to cd into it. And of course, there's also the slight chance that the dir gets removed or renamed (by some other process) between the [-command and the cd-command.

---

