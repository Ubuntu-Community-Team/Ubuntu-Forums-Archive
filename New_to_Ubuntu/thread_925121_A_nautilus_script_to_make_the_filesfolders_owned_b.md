---
title: "A nautilus script to make the files/folders owned by you"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by graben3 on 2008-09-20
Hello,

I made my first nautilus script. Its based on another script I found on the ubuntu forums :

[http://ubuntuforums.org/showthread.php?t=683945](http://ubuntuforums.org/showthread.php?t=683945)

But this script did not work at all for me so I changed it and added some extra security features.

Copy the script below, save it as "Own those files"

Put this script in /home/<your user name>/.gnome2/nautilus-scripts
Make it executable

When a folder belongs to root, you can now right click and select Own those files.

Additionnaly, this script checks if you are about to chown a major folder (ie /bin, /sbin, /tmp, etc...) so you have less chances to break your system that way.If you are about to do something stupid, the script will display an error message and exit.

I would like other experienced people to check this script and tell me what I should have done in another way to make this script better and learn more about bash programming at the same time.

Feel free to user this script as you want, or even take it as a part of another script you are making...

```

#!/bin/bash
# Make owned by current user - Makes the selected files owned by the current user with group
# being the user's primary group (the first in the output from the "groups" command)
#
# Installation:
# Put this script into the Nautilus script dir (~/.gnome2/nautilus-scripts) and make it executable.
#
# Usage:
# Right-click on files in Nautilus and choose Scripts -> Make owned by current user
#
# History:
# v20080131 - Fredrik Wollsén (this script is based on this guy's version you can find at : http://ubuntuforums.org/showthread.php?t=683945)
# This version did not work for me I dont know why... 
#
# So i made this version with additionnal functionnalities
# v20080919 - Emmanuel Morin (this script's current version)
#
# License GPL v3

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

#Finds your current username
USER=`whoami`;

#Finds your user group name
GROUP=`groups | sed -r 's/ .*//g'`

#If no group... your group is your username
if [ "$GROUP" == "" ] ; then
GROUP=$USER;
fi

# This part ensure the directories you are trying to chown are not crucial directories
#echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS | zenity --text-info 
array=(/bin /boot /dev /etc /initrd /lib /lib32 /lib64 /lost+found /mnt /opt /proc /root /sbin /srv /sys /tmp /usr /var /initrd.img /tftpboot /vmlinuz)
len=${#array[*]}
i=0
while [ $i -lt $len ]; do
    filelist=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
    dir=${array[$i]}
    found=${filelist#*$dir *}
    if [ "$found" == "$filelist" ]; then 
        found=${filelist##$dir}
    fi
    if [ "$found" != "$filelist" ]; then 
        zenity --error --text="You cannot own the $dir directory. This will most likely break your system."
        exit 1
    fi
	let i++
done

gksudo -u root -k -m "root password is required to change owner/permissions:" /bin/echo "Do you have root access?"
quoted=$(echo -e "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | awk 'BEGIN {FS = "\n"} { printf "\"%s\" ", $1 }' | sed -e s#\"\"##)
eval sudo chown $USER:$GROUP -R -c $quoted
exit 0

```

---

### Post by nkri on 2008-09-20
This looks really useful...when I'm on my Ubuntu laptop later, I'll test it out and post the results:)

---

### Post by nkri on 2008-09-20
Okay, I tried it out and absolutely love it!  It is exactly what I need, especially because this is one of the only things for which I don't like using the Terminal (I'm always afraid I'll do something wrong and screw up my system...it's happened before).  I'm no expert with scripts, but I think a lot of people can benefit from this.

Keep up the good work!
-nkri

---

### Post by graben3 on 2008-09-20
Thank you very much...

If you think of something to improve the script, let me know !
Ill try to improve it in my free time...

---

### Post by mastapat11 on 2008-10-15
w00t!! this script kicks ***.  i just downloaded 125 scripts from:
[http://www.ubuntu-unleashed.com/2007/09/125-nautilus-scripts-to-simplify.html](http://www.ubuntu-unleashed.com/2007/09/125-nautilus-scripts-to-simplify.html)
but none of them did what yours does.

i was wondering if u or anybody, knows how to make a nautilus script to create a folder underneath the one ur right clicking on?  does that make sense?

---

### Post by graben3 on 2008-10-15
You mean basically this :

Right click on "MyCustomFolder" and select "Create folder into this one" as the nautilus script to execute and it pops up a little zenity box (dialogs boxes that are in graphical mode) and asks for the folder name to create in that folder ?

Could it be applied to multiple folders too ? Lets say I want a "files" folder into multiple directories... is that what you want ? Let me know... I can do some basic stuff like that. Im trying to learn shell script programming right now to unleash the full power of linux on my computer ! If I managed to program this one, I can do much more !

***

It makes me think it would really be nice if I programmed another script to auto-magically generate all folders I need for a project (i'm in graphical design... and programming too !).

---

### Post by graben3 on 2008-10-15
I just made this script, let me know if it's what you want...

```

#!/bin/bash
# Make a new folder named after the user input in the folder(s) selected
#
# Installation:
# Put this script into the Nautilus script dir (~/.gnome2/nautilus-scripts) and make it executable.
#
# Usage:
# Right-click on files in Nautilus and choose Scripts -> Create new folder into this
#
# v20081014 - Emmanuel Morin (this script's current version)
#
# License GPL v3
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

#Get the input paths to create a new folder into
len=${#NAUTILUS_SCRIPT_SELECTED_FILE_PATHS[*]}
i=0

#Get the new folder name to be created in this folder
export newfoldername=`zenity --entry --text="Type the name of the new folder to create into the selected folders"`
if ["$newfoldername" == "" || "$newfoldername" == 0]; then
    exit 0
fi

IFS=$'\n'
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    mkdir "$FILE/$newfoldername"
done
exit 0

```

---

### Post by graben3 on 2008-10-15
Here is another script. It creates a new project folder in the folder you right click into (only works in the current working directory). 

It then creates a directory structure you can customize to your needs. I will use this to create my new projects directory so they will all be the same...

```
#!/bin/bash
# Make a new folder named after the user input in the folder(s) selected
# and creates the needed directories in it so all your projects will be organized the same way
#
# Installation:
# Put this script into the Nautilus script dir (~/.gnome2/nautilus-scripts) and make it executable.
#
# Usage:
# Right-click on files in Nautilus and choose Scripts -> Create new project
#
# v20081014 - Emmanuel Morin (this script's current version)
#
# License GPL v3
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

#Get the new folder name to be created in this folder
export newfoldername=`zenity --entry --text="Type the name of the new project folder to create"`
if ["$newfoldername" == "" || "$newfoldername" == 0]; then
    exit 0
fi

#Remove the file:// at the beginning of the $NAUTILUS_SCRIPT_CURRENT_URI variable
basefolder=`echo "$NAUTILUS_SCRIPT_CURRENT_URI" | awk '{ print substr( $0, 8, length($0) ) }'`
zenity --error --text="$basefolder/$newfoldername/Originaux"

#Create the new project folder
mkdir "$basefolder/$newfoldername"

#Modify the lines below to create different directory names for your use of the script
#You should only modify the part after the last '/' caracter
mkdir "$basefolder/$newfoldername/Originaux"
mkdir "$basefolder/$newfoldername/Documents"
mkdir "$basefolder/$newfoldername/Essais"
mkdir "$basefolder/$newfoldername/Finaux"
exit 0

```

---

### Post by mastapat11 on 2008-10-22
> **graben3 said:**
> You mean basically this :

Right click on "MyCustomFolder" and select "Create folder into this one" as the nautilus script to execute and it pops up a little zenity box (dialogs boxes that are in graphical mode) and asks for the folder name to create in that folder ?

yes this is exactly what i wanted. i tried the script & it worked perfectly.  thanks.

> 
Could it be applied to multiple folders too ? Lets say I want a "files" folder into multiple directories... is that what you want ? Let me know... I can do some basic stuff like that. Im trying to learn shell script programming right now to unleash the full power of linux on my computer ! If I managed to program this one, I can do much more !

***

It makes me think it would really be nice if I programmed another script to auto-magically generate all folders I need for a project (i'm in graphical design... and programming too !).

haven't tried this one. not sure what u mean by it. i'm not a programmer, so don't need too much advanced stuff. but thanks anyways.

---

