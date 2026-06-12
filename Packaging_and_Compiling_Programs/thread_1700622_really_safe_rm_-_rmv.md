---
title: "really safe rm - rmv"
date: 2011-03-05
forum: Packaging and Compiling Programs
---

### Post by saphil on 2011-03-05
At a linux freedom fest, we discovered a deep-seated fear among beginning users.  This may surprise you but some beginners are very concerned by the idea that rm takes things completely out of the system, with no recovery option.  
The idea of a safe remove command was sugggested.  Just for fun, here is the command we came up with.  
```

#!/bin/sh
# rmv - this does a safe remove, sends stuff to $HOME/Trash2
# wolf@sourcefreedom.com

#  License..
#    Copyright (C) 89, 90, 91, 1995-2003 Free Software Foundation.
#
#   This program is free software; you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation; either version 2, or (at your option)
#   any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program; if not, write to the 
#   Free Software Foundation,Inc.
#   59 Temple Place - Suite 330, 
#   Boston, MA 02111-1307, USA
##################################################################

if [ -z "$1"  ]
    then
    echo "\n        You must specify a file or folder to remove"
    echo "\n        Command syntax:

        rmv [file or folder]

         - This created the Trash2 folder, if it doesn't already exist, 
           and then puts the named file or folder into Trash2.  If you 
           feel the need to double-check your action, just look in the 
           /home/your_profile/Trash2 folder as in the example below:

           ls $HOME/Trash2"
else

    if [ ! -e $HOME/Trash2 ]
        then
        #echo "EEEEEK"
        mkdir $HOME/Trash2
    fi

    echo ' '
    mv -v $1 $HOME/Trash2/
    # $1 is an argument on the command line
    # $HOME is current user's home folder
    echo "The file or directory $1 has been safely removed\n"
fi

```

---

### Post by MadCow108 on 2011-03-05
your tool should be following the freedesktop trash specification:
[http://www.freedesktop.org/wiki/Specifications/trash-spec](http://www.freedesktop.org/wiki/Specifications/trash-spec)

btw. there are already a bunch of command line tools doing this.
e.g. trash-cli
[http://code.google.com/p/trash-cli/](http://code.google.com/p/trash-cli/)

---

### Post by saphil on 2011-03-05
Thanks for the link to the draft trash specification.  
Since this is a mv command with benefits, it could well be a benefit to link to the gui trash directory and send moved files there.

---

