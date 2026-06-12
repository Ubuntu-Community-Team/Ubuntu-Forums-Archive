---
title: "Nautilus Script: Make owned by current user"
date: 2008-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by motin on 2008-01-31
Every now and then, we use sudo or another user to create some files which remain uneditable and unremovable for our normal non-privileged user. Either we have to resort into a terminal and sudo chown our files, or start up a sudo nautilus and remove or change the owner accordingly. 

Especially - I often find files in the Trash bin which I cannot remove without this technique. 

With this Nautilus script you can instead right-click on a file, and select Scripts -> Make owned by current user, enter your sudo password and you are good to go.

Note: This is non-recursive by default, so it will only operate on the specific folder and files that you have selected. If you want recursive behavior - uncomment the "#RECURSIVE=-R;" line. It is left out be default since the risk of messing up ownerships is pretty big when something like this gets so easy. 

```
#!/bin/bash
#Title=Make owned by current user
#Title[se]=Gör nuvarande användare till ägare
 
# Make owned by current user - Makes the selected files owned by the current user with group 
# being the user's primary group (the first in the output from the "groups" command)

# Installation:
# Put this script into the Nautilus script dir (~/.gnome2/nautilus-scripts) and make it executable.
#
# Usage:
# Right-click on files in Nautilus and choose Scripts -> Make owned by current user
#
# Notes:
# This operates non-recursively by default, so it will only operate on the specific folder and files that 
# you have selected. If you want recursive behavior - uncomment the "#RECURSIVE=-R;" line further down.
# It is left out be default since the risk of messing up ownerships is pretty big when something 
# like this gets so easy. 
#
# Acknowledements and version history:
# v20080131 - Fredrik Wollsén
#
# License GPL v3
#
# Feel free to provide feedback on this script here:
# http://ubuntuforums.org/showthread.php?t=683945
#
# Suggestions for improvements:
#  - Show a zenity dialogue box to dynamically decide whether or not the command 
#    should be run recursively or not.
#  - Show a zenity progress bar for the execution of the command.
#
# THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR
# IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
# WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY
# DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE
# GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER
# IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
# OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN
# IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

USER=`whoami`;
GROUP=`groups | sed -r 's/ .*//g'`;
#RECURSIVE=-R; # Uncomment this to make the ownerships be implemented resursively

# default to a group name identical to the username if a group is not found (is this case even possible? this if-statement could be totally useless - but: better safe than sorry...)
if [ "$GROUP" == "" ] ; then
GROUP=$USER;
fi

gksudo -- chown -v $RECURSIVE $USER:$GROUP "$@"| zenity --text-info --height=100 --width=300;

exit 0;
```

---

### Post by Mary.Riley on 2008-02-05
Thanks for this tip. It just made my life a whole lot easier..!

---

### Post by nikkpap on 2010-06-11
I think i LOVE you ... thanks man .... really :guitar::guitar::guitar::guitar:

---

### Post by t.rei on 2010-06-11
Now that is a usefull script! Especially since I play around alot with themes and such, copying them from /usr/share/themes or icons to my home folder for messing with them, this comes in handy quite often.

I hope I managed to remove the textinfo thingy, and hope this still works:
```

gksudo -- chown -v $RECURSIVE $USER:$GROUP "$@";

```

---

### Post by slakkie on 2010-06-11
why such a complicated script?

sudo chown -R $USER $HOME

does the trick.

Anyhows, instead of using sed: 

GROUP=$(groups | awk '{print $1}')

or

_user=$(id -u)
_group=$(id -g)
sudo chown -R $_user:$_group $HOME # and you are done

---

### Post by score100 on 2011-03-11
Thanks man I had to google like an hour to find this. Should be more people aware of it!

---

