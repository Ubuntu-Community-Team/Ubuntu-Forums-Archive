---
title: "Simple Shell Script help"
date: 2010-11-02
forum: Programming Talk
---

### Post by Flame_Phoenix on 2010-11-02
Hi guys. I am making a very simple shell script that basically consists of an "if statement" so far. 
I installed Ubuntu yesterday, and now I already want to become a power user and learn the so called "shell magic". I think I am doing quite fine but, as every starter I have some problems I can't yet understand.

```
#!/bin/bash

cMount = "/media/c"

echo "cheking if /media/c exists"
if [ -d $cMount ] then
	echo "/media/c already exists, moving on"
else
	echo "creating /media/c"
	mkdir $cMount
fi

```

And I have these errors:

> 
./test.sh: line 3: cMount: command not found
cheking if /media/c exists
./test.sh: line 9: syntax error near unexpected token `else'
./test.sh: line 9: `else'


I don't understand why I have all these errors, I am following a tutorial here:
[http://www.injunea.demon.co.uk/pages/page205.htm#top](http://www.injunea.demon.co.uk/pages/page205.htm#top)

My main idea is to check if a folder exists or not (I assume -d does that). If it does not exist, I simply create it. I am not sure if I need sudo to create a folder in /media.

After creating this folder, I want to check if a symbolic link exists:
[http://www.tech-recipes.com/rx/172/create_a_symbolic_link_in_unix_solaris_linux/](http://www.tech-recipes.com/rx/172/create_a_symbolic_link_in_unix_solaris_linux/)

and if it does not exist, I simply create one to my windows volume, and voilá! :D

I am also open to ideas on how to improve my programing style. 
Finally, if this is not the right place to post my question, please tell me where I should do so.

Thx in advance, Flame_Phoenix.

---

### Post by meastwood on 2010-11-02
$ cat ./test.sh
#!/bin/bash

cMount="/media/c"                            #  No spaces - else the shell thinks cMount is a command

echo "cheking if /media/c exists"
if  [ -d $cMount ]                           # then goes on new-line  or could also write     if [ -d $cMount ];then
then                                         # instead of putting then on this line 
	echo "/media/c already exists, moving on"
else
	echo "creating /media/c"
	mkdir $cMount
fi

~$ ./test.sh
cheking if /media/c exists
creating /media/c
mkdir: cannot create directory `/media/c': Permission denied

**** the last message is just down to the user I ran the script under - that user does not have permission to create the mount directory.

---

### Post by Flame_Phoenix on 2010-11-02
```
#!/bin/bash

cMount="/media/c"

echo "cheking if /media/c exists"
if [-d $cMount];then
echo "/media/c already exists, moving on"
else
echo "creating /media/c"
mkdir $cMount
fi
```

This is what I have now. However I get the weir output:

> 
$ ./test.sh
cheking if /media/c exists
./test.sh: line 6: [-d: command not found
creating /media/c
mkdir: cannot create directory `/media/c': File exists


Do I need to install something special like a library ??
Btw, thx for the help!

---

### Post by meastwood on 2010-11-02
The joys of coding ... 'spaces' are very important - you missed out the spaces in the [ .. ]
$ mkdir fred

$ if [-d fred]; then  echo "fred exists"; fi
bash: [-d: command not found

$ if [ -d fred ]; then  echo "fred exists"; fi
fred exists

If you are using Ubuntu the default is that only root can create directories (and mount devices for that matter) on root directories.

There are number of ways round this - however which you choose is done to how secure you wish to keep things.

---

### Post by Vox754 on 2010-11-02
> **meastwood said:**
> The joys of coding ... 'spaces' are very important - you missed out the spaces in the [ .. ]
$ mkdir fred

$ if [-d fred]; then  echo "fred exists"; fi
bash: [-d: command not found

$ if [ -d fred ]; then  echo "fred exists"; fi
fred exists

If you are using Ubuntu the default is that only root can create directories (and mount devices for that matter) on root directories.

There are number of ways round this - however which you choose is done to how secure you wish to keep things.

Oh, for the love of God! If you are going to help him, at least be nice and use "code" tags.

Otherwise your explanations lose meaning because the normal font is not a monospaced font, and indentation is not preserved.

```

#!/bin/bash

cMount="/media/c"

echo "cheking if $cMount exists"
if [ -d "$cMount" ]            # Enclose in quotes
then
   echo "$cMount already exists, moving on"
else
   echo "creating $cMount"     # Already enclosed in quotes
   mkdir "$cMount"             
fi

```

Make sure to use quotes around variables, "$cMount" instead of just $cMount. In this example it doesn't matter, but it will when paths contain spaces. So it's a good practice.

Also, to the original poster. Try your shell scripting abilities on files owned by you first. That way you won't have permission problems. Later, when you know how things work, you will use "sudo" to acquire root privileges.

---

### Post by Flame_Phoenix on 2010-11-03
```
#!/bin/bash

cMount="/media/c"

echo "cheking if /media/c exists"
if [ -d "$cMount" ];then
echo "/media/c already exists, moving on"
else
echo "creating /media/c"
mkdir "$cMount"
fi

```
It works, thx!!! (Mwuhahahahaahaha)
Well, I never saw a scripting language that depended this heavily on "spaces and \n". I am surprised, but I am learning fast thx to you guys!

sudo has always been one of my major problems. The main idea is to make this script run when I turn on my computer:
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

At this stage my password is not requested, but when the script ends, the created folders and mounts belong to root, and so I don't have full access to them. 

Is there a way to "ignore" sudo? I am the only user of this computer, so technically I should be root as well (but I read on forums that is a bad thing to do because I get to much power! ... Thing is that now I need that extra evil power!!!!)

> 
There are number of ways round this - however which you choose is done to how secure you wish to keep things. 
What are the other solutions ?? I am willing to learn!

---

### Post by meastwood on 2010-11-03
Safest way is to use sudo to give your self permission.

Use the 'visudo' either
```
$ sudo visudo
```
or as root
```
# visudo
```

On debian systems the default editor used by visudo is 'nano'.  I prefer 'vi' though be warned - 'vi' allows shell escaping which means it is possible to escape 'visudo' to a root shell - but then you are root anyway (or have root permission).

If you just want to give yourself permission to do this single task then add the following line below these lines (assume your username is mary).  The line to add starts with mary:

```
# User privilege specification
root	ALL=(ALL) ALL
mary    ALL=(root) NOPASSWD:/usr/bin/mkdir
```

save and exit.
To use on the cmd-line:
```
mary:~$ sudo mkdir /media/testdir
```

To use in script:
```
sudo mkdir "$cMedia"
```

If you want to give yourself permission to do everything (as root and other users) - be careful if you do as it is easy to make a mistake on the cmd-line use
```
mary    ALL=(ALL) NOPASSWD:ALL 
```

Forgot!! -- if you want to change the editor for visudo (and as the system default editor)
```
root:/etc/alternatives# ls -al editor
lrwxrwxrwx 1 root root 9 2009-10-27 16:03 editor -> /bin/nano
root:/etc/alternatives# which vi
/usr/bin/vi
root:/etc/alternatives# rm editor
root:/etc/alternatives# ln -s /usr/bin/vi editor
roo:/etc/alternatives# ls -al editor
lrwxrwxrwx 1 root root 11 2010-11-03 12:04 editor -> /usr/bin/vi
```

---

### Post by epicoder on 2010-11-03
Assuming your script is running with root powers, you can change the ownership by the way of "chown":
```
chown user "$cMount"
```

---

### Post by Flame_Phoenix on 2010-11-03
Hey guys, I decided to move on with my idea and now I finally hit the "almost" final stage! I still have a few question though.

```
#!/bin/bash

#vars
volMountDir="/media/c"
volMount="/dev/sda2"
symbRealFile="/media/c/Users/Pedro/My Documents/My Dropbox"
symbLink="/home/pedro/"

#Mount directory for the windows volume
echo "cheking if $volMountDir exists"	#how to write a variable's content? I cannot do "$volMountDir" inside quotes here!
if [ -d "$volMountDir" ];then
echo "$volMountDir already exists, moving on"
else
echo "creating $volMountDir"
sudo mkdir "$volMountDir"
sudo chown pedro "$volMountDir"
fi

#Mounting the volume itself
echo "mount $volMount inside $volMountDir"
sudo mount -t ntfs -o nls=utf8 "$volMount" "$volMountDir"	#how to check is a volume is already mounted?

#checking if the symbolic link exists
echo "creating symbolic link to $symbLink"					#how to reuse a pre-existing symblinc
ln -s "$symbRealFile" "$symbLink"
```

And about the sudo thing, is there a way to solve the problem without changing the file? I want to share this when I am done and I would like it to be as versatile as possible so others can use it too :S

---

### Post by meastwood on 2010-11-03
Re.  sudo - a way round seems to be the way you are doing it - have the script owned by root and have it 'chown' when needs be.  Someone else should be able to run it as
# sudo yourscript

(assuming they are on single user system with sudo access as in an Ubuntu default desktop install).  

There are other tools - supermount, submount, autofs and AMD just to mention a few - that can do what I think you want to do.

Below is some scripting that may help with the questions you posed - I've NOT tested the NFS mount command as I do not have access to remote filesystems.

```
#!/bin/bash

volMountDir="/media/c"
volMount="/dev/sda22"
symbRealFile="/home/mark/realfile.txt"
symbLink="/home/mark/testdir/pedro/"
linkname=${symbRealFile##*/}                            # Returns 'realfile.txt'

# Print a variable - just place it outside the ""
var=$(whoami)
echo "I am "$var

# Test if symlink exists - if yes echo message, if no create
[[ -L $symbLink$linkname ]] && echo "link ... "$symbLink$linkname" exists" || ln -s "$symbRealFile" "$symbLink"

# The above is a short hand form of this
#if [[ -L $symbLink$linkname ]]
#then
#   echo "Link ... "$symbLink$linkname"exists"
#else
#   ln -s "$symbRealFile" "$symbLink"
#fi

# See if the dir is mounted - throw the results and any errors away
# Checks /etc/mtab file
mount | grep $volMountDir 2>&1 >/dev/null

# Check the return code of 'grep' from the above command - if 0 then a match ie. dir is mounted.
[[ $? == 0 ]] && echo $volMount" is mounted" || sudo mount -t ntfs -o soft,nolock -o nls=utf8 "$volMount" "$volMountDir" 

# Maybe worth looking at '-o nolock,soft' for the nfs mount

```

---

### Post by Flame_Phoenix on 2010-11-03
@meastwood: Thanks for all the help. There are however some things I don't understand.

```
linkname=${symbRealFile##*/} 
```
What is this line supposed to do?

```
#if [[ -L $symbLink$linkname ]]

```
Why are you using "[[ (...) ]]" instead of "[ (...) ]" ? and what is -L supposed to mean?

As for he mount:
```

# See if the dir is mounted - throw the results and any errors away
# Checks /etc/mtab file
mount | grep $volMountDir 2>&1 >/dev/null

```

I made a more detailed search and I found this:
[http://www.linuxquestions.org/questions/programming-9/bash-check-if-fs-is-already-mounted-on-directory-137282/](http://www.linuxquestions.org/questions/programming-9/bash-check-if-fs-is-already-mounted-on-directory-137282/)

Looks like since 2004 there is a new command we can use to check this:
[http://www.linuxquestions.org/questions/programming-9/bash-check-if-fs-is-already-mounted-on-directory-137282/#post4061678](http://www.linuxquestions.org/questions/programming-9/bash-check-if-fs-is-already-mounted-on-directory-137282/#post4061678)

I tried to use this by making:
```
if [ /bin/mountpoint -q "$volMountDir" -eq 0 ];then
echo "$volMountDir" " is a mountpoint, moving on"
else
echo "mount $volMount inside $volMountDir"
sudo mount -t ntfs -o nls=utf8 "$volMount" "$volMountDir"	#how to check is a volume is already mounted?
fi
```

But it looks like I have too many argument on the first line. What's wrong?

As for your solution:```

# Maybe worth looking at '-o nolock,soft' for the nfs mount
```
Where can I find information about this? I tried to make "man mount" but I didn't find "soft" nor "nolock" when i searched. Google is also overcomplicated in this matter :S

Current state of script:
```

#!/bin/bash

#vars
volMountDir="/media/c"
volMount="/dev/sda2"
symbRealFile="/media/c/Users/Pedro/My Documents/My Dropbox"
symbLink="/home/pedro/"
linkname=${symbRealFile##*/} 	#Returns 'realfile.txt'

#Mount directory for the windows volume
echo "cheking if " "$volMountDir" " exists"
if [ -d "$volMountDir" ];then
echo "$volMountDir" " already exists, moving on"
else
echo "creating " "$volMountDir"
sudo mkdir "$volMountDir"
sudo chown pedro "$volMountDir"
fi

#Mounting the volume itself
echo "cheking if " "$volMount" " is mounted"

# See if the dir is mounted - throw the results and any errors away
# Checks /etc/mtab file
mount | grep $volMountDir 2>&1 >/dev/null

# Check the return code of 'grep' from the above command - if 0 then a match ie. dir is mounted.
[[ $? == 0 ]] && echo $volMount" is mounted" || sudo mount -t ntfs -o nls=utf8 "$volMount" "$volMountDir"

#checking if the symbolic link exists
if [[ -L $symbLink$linkname ]];then
echo "Symbolic link " "$symbLink$linkname" " already exists, moving on"
else
echo "creating symbolic link to $symbLink"	
ln -s "$symbRealFile" "$symbLink"
fi


```

I want to learn as much as I can and I want to perfect it making it easier to read and more user friendly. Any ideas?

Thanks in advance!

---

### Post by meastwood on 2010-11-03
You've asked a lot of questions so this reply is a bit long. Okay - first of all I've been messing around with Unix and Linux for 30 plus years (well since kernel 0.99 for linux) - and there's a lot I don't know along with the stuff I cannot remember!!!

BASH is a massive topic all on it's own - but it's a tool - so for me, I delve into it when the need arises.  I'm sure you have already, but keep going back to .. the man page.
#----------------------------------------
Code style:
Yours will develop over time - there are conventions - but as to style?.  People approach problems in different ways and this will be reflected in style and content.  The more you learn then perhaps the more efficient,  concise  your code becomes (and arguably more difficult for others to read :-)).  

What is important is that you comment and describe what it is you are doing - I'm guilty of not doing that all the time - I've gone back to stuff I've written and have had a hell of a time trying to follow it - it's not just the code, it is how you are thinking at the time of writing it. 

So don't expect to write the perfect bit of code - for me I try and make it robust, maintainable and fairly concise.  There is nearly always some way to improve it.  As for your script, well, I'd just get it working. Once it's working you can than tinker with it to get it in a state/style that you are happy with.  And it can always be improved.

#-----------------------------------------
As for your questions: 
```
linkname=${symbRealFile##*/}
```
This is referred to as 'Parameter Expansion' - in the bash man page.  What the above does - in plain terms - is remove the largest pattern, starting from the left, up to and including a '/' from the variable $symbRealFile
```
$ symbRealFile="/abc/def/hijklmn.txt"            (populate a variable)
$ echo ${symbRealFile##*/}                       (remove the largest part, starting from the LEFT, up to and including a '/')
hijklmn.txt

$ symbRealFile="/abc/def/hijklmn.txt"
$ echo ${symbRealFile#*/}                        (remove the smallest part, starting from the LEFT, up to and including a '/')
abc/def/hijklmn.txt

$ symbRealFile="/abc/def/hijklmn.txt"             
$ echo ${symbRealFile%/*}                        (remove the smallest part, starting from the RIGHT, up to and including a '/'
/abc/def
$ symbRealFile="/abc/def/hijklmn.txt" 
$ echo ${symbRealFile%%/*}                       (remove the largest part, starting from the RIGHT, up to and including a '/')
                                                                                                      (since the string starts with a '/' the whole string is removed)
$
```
#-----------------------------------------
Brackets:
Referred to as 'Compound Commands' - in the bash man page. Use of [ .. ], [[ ..]] and (( .. )) are shorthand forms of the bash built-in command 'test'. 'test' returns 0 (True) or 1 (False) depending on the evaluation of an expression expr. Can examine the return value by displaying $?.  There are various forms:

test expr 
Using the test command.

[ expr ]
Somewhat unwieldy due to its requirement for escaping and the difference between string and arithmetic comparisons

(( expr ))
Evaluates an arithmetic expression, returns 1 if expr = 0, or 0 if expression = non-zero. Do not need to escape operators between (( and ))

[[ expr ]]
Can do arithmetic tests as well however if < and > operators are not in a (( compound )) they will compare the operands as strings
#--------------------------------------------------------------
```
#if [[ -L $symbLink$linkname ]]
```
-L   is an operand for the 'test' command, the same as '-d' that you used earlier but instead of testing whether the file is a directory it tests to see  if the file is a symbolic link ( '-h' also tests for a symbolic link).  There are many such operands ... man pages :-)
```
$ if test -L realfile.txt; then echo "Is a symlink";fi
Is a symlink

$ [[ -L realfile.txt ]] && echo "Is a symlink"
Is a symlink

$ [ -L realfile.txt ] && echo "Is a symlink"
Is a symlink
```
All three are the same - I use [[ .. ]] instead of [..] out of habit and because of the reasons given above - a matter of preference, that's all.
 #--------------------------------
/bin/mountpoint  I've not come across this command before.  It checks to see if a directory is a mount point not if something is mounted so  I do not think it is what you want as the results below demonstrate:
```
$ mountpoint /media
/media is not a mountpoint

$ mountpoint /media/floppy
mountpoint: /media/floppy: not a directory

$ sudo mount -t vfat /dev/fd0 /media/floppy
[sudo] password for mark: 
mount: block device /dev/fd0 is write-protected, mounting read-only

$ mountpoint /media/floppy 
mountpoint: /media/floppy: not a directory         (Does not detect that device is mounted)

$ mountpoint /media
/media is not a mountpoint                         (Does not detect that device is mounted)

$ mount | grep 'floppy' 2>&1 >/dev/null
$ [[ $? == 0 ]] && echo "Floppy is mounted" || echo "Floppy is NOT mounted"
Floppy is mounted
$ sudo umount /dev/fd0
$ mount | grep 'floppy' 2>&1 >/dev/null
$ [[ $? == 0 ]] && echo "Floppy is mounted" || echo "Floppy is NOT mounted"
Floppy is NOT mounted
```
#--------------------------------------------
soft
You are quite right this option is not referenced in the 'mount' command man pages - it is a filesystem specific option and is covered in the NFS man pages. - mounting a NFS filesystem.  I do not have NFS installed.  Basically there are two types of mounts, hard and soft.  The default is hard - this can cause a problem if there is a network problem though there is another NFS specific option that allows a hard mount to be interrupted - it does not time out.  A soft mount will time out and can be interrupted.  Not real sure if this is still an issue with latest versions of NFS.

---

### Post by Flame_Phoenix on 2010-11-04
Thx for all the explanation !!
I ended the comments on my script and now I think it is ready to post it! I searched a section call "Dual Boot" here and although I find a lot of posts related to this I know it is a bad idea to spam everything with this thread. 

I want to share this with the community, this way people who have dropbox (per example) or who want to use their music library on windows can use this script and do the job easily with only a few modification!
What is the best place to shares this for those who might need it?


Here is the final version of the code, enjoy!
```

#!/bin/bash

#==========================================================================================================================================
# Author: Pedro Miguel P. S. Martins, aka Flame_Phoenix
#
# Description: creates a directory to mount a volume, then mounts the volume and creates a symbolic link to connect to it.
#If the mount direcotry, or the volume or the symbLink already exist, then there is no problem and we just move on.
#Requires sudo password in order to run. To configure this script, siply change the setup section as needed. 
#
# Version 1.0:
# - Innitial release to the public
#
# Credits:
# -meastwood, for detailed explanations, suggestions and teachings
# -Vox754, sh228, for suggestions and help 
#
#Original build thread can be consulted here:
# - http://ubuntuforums.org/showthread.php?t=1612116&page=2
#==========================================================================================================================================
#==============================================================SETUP_START=================================================================
#==========================================================================================================================================

#vars
volMountDir="/media/c"											#the direcotry where you will mount the volume
volMount="/dev/sda2"											#the volume you pretend to mount
symbRealFile="/media/c/Users/Pedro/My Documents/My Dropbox"		#the file on the volume that you want to link
symbLink="/home/pedro/"											#where the simbolyc link will be created

#==========================================================================================================================================
#===============================================================SETUP_END==================================================================
#==========================================================================================================================================

linkname=${symbRealFile##*/} 									#Returns 'realfile.txt'

#Mount directory for the windows volume
echo "cheking if " "$volMountDir" " exists"
if [ -d "$volMountDir" ];then
echo "$volMountDir" " already exists, moving on"
else
echo "creating " "$volMountDir"
sudo mkdir "$volMountDir"
sudo chown pedro "$volMountDir"
fi

#Mounting the volume itself
echo "cheking if " "$volMount" " is mounted"

# See if the dir is mounted - throw the results and any errors away
# Checks /etc/mtab file
mount | grep "$volMountDir" 2>&1 >/dev/null

# Check the return code of 'grep' from the above command - if 0 then a match ie. dir is mounted.
#[[ $? == 0 ]] && echo "$volMount" " is mounted" || sudo mount -t ntfs -o nls=utf8 "$volMount" "$volMountDir"
if [[ $? == 0 ]];then 
echo "$volMount" " is mounted, moving on"
else
echo "mounting " "$volMount"	
sudo mount -t ntfs -o nls=utf8 "$volMount" "$volMountDir"
fi


#checking if the symbolic link exists
if [[ -L $symbLink$linkname ]];then
echo "Symbolic link " "$symbLink$linkname" " already exists, moving on"
else
echo "creating symbolic link to $symbLink"	
ln -s "$symbRealFile" "$symbLink"
fi


```

---

### Post by Vox754 on 2010-11-04
> **Flame_Phoenix said:**
> ...
Here is the final version of the code, enjoy!


Ugh...

Personally, I don't trust old Unix users. Some of them are helpful because they know a lot, but others are more concerned with using cryptic constructs which they've learned through millennia.

I prefer a modern approach of being verbose, and using external tools if possible, while old timers typically try to squeeze as much code as possible in a single line.

Couple of practical suggestions.

1. Don't use "sudo" within scripts. That's not what it's there for. Once you call sudo, subsequent calls to it are redundant, because you already have root privileges for the next couple of minutes. The correct way is to call sudo once *outside* the script. The advice on visudo is for advanced users, most people don't need to know about it.

2. Don't use tabs to align your code or comments. The tabs may look okay in your system, but once they are expanded to different spaces, they don't align. In particular, this forum expands tabs to 8 spaces, which was common back in the day, and is still the default for many editors.

3. You may use tabs at the beginning of the line, that is, for "indentation". But using tabs at the end of lines causes bad alignment. If you must, use spaces instead.

4. Your lines should be restricted to 80 characters in length, for clarity purposes.

5. Don't add wordy, obvious comments. Comment blocks of code, not every single line. Actually, because everything is explained in "echos", this script practically doesn't need comments.

6. Don't mix the simple shell commands, such as single brackets [ ], with bash specific constructs, such as the double [[ ]] ones. Be consistent. Decide if you want your script to be "sh" compatible, or use advanced features of "bash".

7. The generally accepted way to abbreviate "symbolic link" is "symlink", not "symblink".

8. Indent your code.
8. Indent your code.
8. Indent your code.

Give it a name, and call it with sudo.
```

sudo ./drop_mount

```

```

#!/bin/bash

# Directories to mount and link
vol_mount_dir="/media/c"
vol_mount="/dev/sda2"

real_file="${vol_mount_dir}/Users/Pedro/My Documents/My Dropbox"
name="${real_file##*/}"
link_name="${HOME}/$name"

echo "cheking if $vol_mount_dir exists"

if [ -d "$vol_mount_dir" ]
then
    echo "$vol_mount_dir already exists, moving on"
else
    echo "creating $vol_mount_dir"
    mkdir "$vol_mount_dir"
    chown pedro "$vol_mount_dir"
fi

# Checks /etc/mtab file
echo "cheking if $vol_mount is mounted"

mount | grep "$vol_mount_dir" 2>&1 >/dev/null

if [ $? -eq 0 ]
then
    echo "$vol_mount is mounted, moving on"
else
    echo "mounting $vol_mount"
    mount -t ntfs -o nls=utf8 "$vol_mount" "$vol_mount_dir"
fi


if [ -L "$link_name" ]
then
    echo "Symbolic link $link_name already exists, moving on"
else
    echo "creating symbolic link to $link_name"
    ln -s "$real_file" "$link_name"
fi

```

Notice the use of braces, ${variable} is the same as $var in most cases. It is used when you want to differentiate the variable name from a path name, specially the underscores.

For instance, "/dir/$var_one_two/file" could be
```

/dir/${var}_one_two/file    # the variable is "var"
/dir/${var_one}_two/file    # the variable is "var_one"
/dir/${var_one_two}/file    # the variable is "var_one_two"

```

---

### Post by Flame_Phoenix on 2010-11-05
Hey, thx for all the help zox!
One question though, is ${HOME} equal to /home/username ? I think it is :P

Final version!

```

#!/bin/bash

#===============================================================================
# Author: Pedro Miguel P. S. Martins, aka Flame_Phoenix
#
# Description: creates a directory to mount a volume, then mounts the volume and
# creates a symbolic link to connect to it.If the mount direcotry, or the volume
# or the symbLink already exist, then there is no problem and we just move on.
#Requires sudo password in order to run. To configure this script, siply change 
#the setup section as needed. 
#
# Version 1.0:
# - Innitial release to the public
#
# Version 1.1:
# - Fixed identation
# - removed sudo from the script, now to run it you have to do "sudo scriptname"
# - removed tabs on the script
# - restricted lines and comments to 80 characters
# - Cleaned and fixed code style
# - Added a variable for the user's name
#
# Credits:
# - meastwood and Vox754 for detailed explanations, suggestions and teachings
# - sh228, for suggestions and help 
#
#Original build thread can be consulted here:
# - http://ubuntuforums.org/showthread.php?t=1612116&page=2
#===============================================================================

#===============================================================================
#===========================SETUP_START=========================================
#===============================================================================
# Directories to mount and link
vol_mount_dir="/media/c"
vol_mount="/dev/sda2"

real_file="${vol_mount_dir}/Users/Pedro/My Documents/My Dropbox"
name="${real_file##*/}"
link_name="${HOME}/$name"
userName="pedro"
#===============================================================================
#=============================SETUP_END=========================================
#===============================================================================
echo "cheking if " "$vol_mount_dir" " exists"

if [ -d "$vol_mount_dir" ]
then
    echo "$vol_mount_dir" " already exists, moving on"
else
    echo "creating " "$vol_mount_dir"
    mkdir "$vol_mount_dir"
    chown "$userName" "$vol_mount_dir"
fi

# Checks /etc/mtab file
echo "cheking if " "$vol_mount" " is mounted"

mount | grep "$vol_mount_dir" 2>&1 >/dev/null

if [ $? -eq 0 ]
then
    echo "$vol_mount" " is mounted, moving on"
else
    echo "mounting " "$vol_mount"
    mount -t ntfs -o nls=utf8 "$vol_mount" "$vol_mount_dir"
fi


if [ -L "$link_name" ]
then
    echo "Symbolic link " "$link_name" " already exists, moving on"
else
    echo "creating symbolic link to " "$link_name"
    ln -s "$real_file" "$link_name"
fi

```

Flagged as solved ! Thx guy!
Where do you think I should post this on the fourm?

---

