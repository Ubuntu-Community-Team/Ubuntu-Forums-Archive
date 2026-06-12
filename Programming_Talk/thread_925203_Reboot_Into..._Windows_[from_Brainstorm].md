---
title: "Reboot Into... Windows [from Brainstorm]"
date: 2008-09-20
forum: Programming Talk
---

### Post by mridkash on 2008-09-20
**UPDATE**
This is the final working script.
[PHP]#!/bin/bash

if [[ "`whoami`" != "root" ]] ; then
  zenity --error --title "You must be root" --text 'Launch this script with sudo in front, like "sudo rebootinto"'
  exit
fi
find_grub_dir ()
{
    for d in $grub_dirs ; do
        if [ -d "$d" ] ; then
            grub_dir="$d"
            break
        fi
    done
    
    if [ -z "$grub_dir" ] ; then
        zenity --error --title "No Grub Directory" --text "No Grub Directory Found"
    fi

    echo $grub_dir
}

grub_dirs="/boot/grub /boot/boot/grub"

grub_dir=$(find_grub_dir)

config_file=$grub_dir/menu.lst


# &#8595; Move to the temp directory, make a folder to contain temporary files

cd /tmp
tempDir='rebootinto'
mkdir $tempDir 2>/dev/null

# &#8595; if succesfully created temp directory, go into it, and make a copy of menu file
 
if cd $tempDir; then 

cp $config_file menu.lst

# &#8595; filter out the options from menu file, also remove recovery options and "Other Operating system" option

grep -e '^title' menu.lst | cut -f3 | grep -n "" | grep -v "recovery" | grep -v "Other" > options.lst 
selected=$(cat options.lst | cut -d':' -f2  | zenity --list --text "Select One to be Default in Boot Menu" 
--title "Reboot Into" --column "Options" --width 400 --height 400);

if [[ $selected == "" ]]; then #if pressed Cancel or none selected then exit
exit 1;
fi

selected=$(grep -e "$selected" options.lst) #find out the selected item from list of options

selectedNum=$(expr `echo $selected | cut -d':' -f1` - 1) 

# modify the menu.lst file and replace the 'default   0' entry with 'saved'
# so that savedefault works properly. Also, store modifications in a file

sed 's/\(^default.*[^0-9]\)[0-9]/\1'"saved"'/w modifications' < menu.lst > newMenu.lst

# actually change the grub menu file only if there is some change in temp. file
# by last command

if [[ `diff -q menu.lst newMenu.lst` != "" ]]; then

if $(cp $config_file $grub_dir/menu.Backup); then

  echo "Automaticaly Made a backup of original menu file"

  sudo cp newMenu.lst $config_file    
  echo "Done"
fi

fi

# &#8595; this section is from grub-reboot script.

default_file=$grub_dir/default

default="$selectedNum" ; shift
grub --batch --config-file=$config_file $@ <<EOT
savedefault --once --default=$default
quit
EOT

echo "
#
#
#
#
#
#
#
#
#
#
# WARNING: If you want to edit this file directly, do not remove any line
# from this file, including this warning. Using \`grub-set-default\' is
# strongly recommended." >> $default_file

# /sbin/shutdown -r now "Rebooting into $selected" #Reboot command  # UNCOMMENT (remove # at front) this line to restart.



fi
exit 0;  [/PHP]

Hello,
 I want [this functionality]("http://brainstorm.ubuntu.com/idea/13354/") in Ubuntu. Though aimed at advanced users, it is real good.

I wanted to see if it can be implemented with a small bash script. And yes it can.

This script modifies the default variable in /boot/grub/menu.lst file so that one can specify the default selection on next boot.

**Use case: **Suppose Joe wants to reboot into windows after this session in ubuntu, but he doesn't like to wait for ubuntu to shutdown and boot screen to come up where he has to select windows and press enter.
He clicks on an icon in panel which runs a script and asks him what option he want to choose next time, he selects and presses ok. The machine reboots and automatically boots into the option he selected, and Joe's eyes get some rest in the meantime.

Here is the script, read it verify it and tell me your thoughts.
[php]#!/bin/bash

#Move to the default directory, usually home folder, make a hidden folder to contain temporary files
cd
mkdir .rebootInto 2>/dev/null

#if succesfully created new directory, go into it
 
if cd .rebootInto; then 

cp /boot/grub/menu.lst menu.lst

# filter out the options from menu.lst file, also remove recovery options or Other Operating system option
grep -e '^title' menu.lst | cut -f3 | grep -n "" | grep -v "recovery" | grep -v "Other" > options.lst 
selected=$(cat options.lst | zenity --list --text "Select One to be Default in Boot Menu" --title "Reboot Into" --column "Options" --width 400 --height 400)
selectedNum=$(expr `echo $selected | cut -d':' -f1` - 1) 

#modify the menu.lst file and replace the 'default   0' entry with selected number and store modifications in a file
sed 's/\(^default.*[^0-9]\)[0-9]/\1'"$selectedNum"'/w modifications' < menu.lst > newMenu.lst

#actually change the file at /boot/grub/menu.lst, first create a backup
 if $(gksudo cp /boot/grub/menu.lst /boot/grub/~menu.lst); then
  echo "Automaticaly Made a backup of original menu file"
  #sudo cp newMenu.lst /boot/grub/menu.lst    #< UNCOMMENT this line after checking that the script works properly 
  echo "Done"
  #sudo /sbin/shutdown -r now "Rebooting into $selected"    #< ALSO UNCOMMENT this line to actually reboot
 fi
  

fi[/php]If you keep the two lines at end commented then this script is harmless, you should dry run this script first and check the modifications file in .rebootInto folder in home directory. The modifications file should contain only 1 line like this 'default      0' or with any number other than 0. If it contains anything else, dont uncomment last lines and run the script, ask for help.

ScreenShot

[IMG]http://farm4.static.flickr.com/3142/2872459181_68643470be.jpg?v=0[/IMG]

[[IMG]http://brainstorm.ubuntu.com/idea/13354/image/1/[/IMG]]("http://brainstorm.ubuntu.com/idea/13354/")

---

### Post by thats_Mr_noob_to_you on 2008-09-21
I have a heavily (IMHO) modified menu.lst, and I have commented out all of my options with the exception of 1 linux OS, 1 windows and an OSX.  Will your script still work without the 'Other' line?

Is there any way to take the '#:' out of the dialog? Can you set the script to make a backup of the original on first use? (or an option to make a backup, and also restore the original).  Could you make an option to either save your modified menu.lst default and exit -or- save and restart?

I haven't tried your script yet, (not on my linux box yet), but awesome work.

/I wish I was good at scripting

---

### Post by MarkieB on 2008-09-22
no longer participating in ubuntuforums.org

---

### Post by Tomosaur on 2008-09-22
Take a look at GrubEd in my sig - uses bash scripting to alter the Grub boot menu. You might be able to use something from there.

BTW: I haven't updated or tested GrubEd on anything past Feisty really, so there may be some things which don't work. There are better and more tightly integrated grub menu editors out there now so really GrubEd is probably only good for messing about with shell scripting really.

---

### Post by mridkash on 2008-09-23
Whoa! Thanks for the comments, I was kinda getting disappointed after getting no comment in these 2 days. 

To tell you, I'm just a kind of "advanced noob" ;) in linux land, and do web programming generally. 

Thanks **MarkieB** for the grub-reboot part. I didn't know that.

and **Mr_noob**, if you leave the last lines commented, you can run the script harmlessly on linux system. And to make sure that it is working fine, go to home folder and open the .rebootinto folder. Look for the modifications file in it and see if it contains something like 'default    0'. You can also look in other file 'options' in that folder and see if it is ok.

Also, I'll test with grub-reboot option and see if it works successfully.

Thanks.

---

### Post by mridkash on 2008-09-23
Ok, as suggested by **MarkieB **I looked at grub-reboot. 
It didn't work at my system at first because, in the menu.lst file the default entry needs to be set to 'saved', then it works.

I found that grub-reboot program is a small script located in /usr/sbin folder and so I merged its code with rebootinto script. Now it should work properly.

Also, you'll see there are no numbers in selection window.

Here is the modified script, NOTE: this is NOT a fully working script that restarts your computer when you run it. You can UNCOMMENT (ie remove preceding # ) the line at end to make it fully functional.

Also, **please verify it** and tell if it works properly on your system.

[php]
#!/bin/bash

if [[ "`whoami`" != "root" ]] ; then
  zenity --error --title "You must be root" --text 'Launch this script with sudo in front, like "sudo rebootinto"'
  exit
fi
find_grub_dir ()
{
    for d in $grub_dirs ; do
        if [ -d "$d" ] ; then
            grub_dir="$d"
            break
        fi
    done
    
    if [ -z "$grub_dir" ] ; then
        zenity --error --title "No Grub Directory" --text "No Grub Directory Found"
    fi

    echo $grub_dir
}

grub_dirs="/boot/grub /boot/boot/grub"

grub_dir=$(find_grub_dir)

config_file=$grub_dir/menu.lst


# &#8595; Move to the temp directory, make a folder to contain temporary files

cd /tmp
tempDir='rebootinto'
mkdir $tempDir 2>/dev/null

# &#8595; if succesfully created temp directory, go into it, and make a copy of menu file
 
if cd $tempDir; then 

cp $config_file menu.lst

# &#8595; filter out the options from menu file, also remove recovery options and "Other Operating system" option

grep -e '^title' menu.lst | cut -f3 | grep -n "" | grep -v "recovery" | grep -v "Other" > options.lst 
selected=$(cat options.lst | cut -d':' -f2  | zenity --list --text "Select One to be Default in Boot Menu" \
--title "Reboot Into" --column "Options" --width 400 --height 400);

if [[ $selected == "" ]]; then #if pressed Cancel or none selected then exit
exit 1;
fi

selected=$(grep -e "$selected" options.lst) #find out the selected item from list of options

selectedNum=$(expr `echo $selected | cut -d':' -f1` - 1) 

# modify the menu.lst file and replace the 'default   0' entry with 'saved'
# so that savedefault works properly. Also, store modifications in a file

sed 's/\(^default.*[^0-9]\)[0-9]/\1'"saved"'/w modifications' < menu.lst > newMenu.lst

# actually change the grub menu file only if there is some change in temp. file
# by last command

if [[ `diff -q menu.lst newMenu.lst` != "" ]]; then

if $(cp $config_file $grub_dir/menu.Backup); then

  echo "Automaticaly Made a backup of original menu file"

  sudo cp newMenu.lst $config_file    
  echo "Done"
fi

fi

# &#8595; this section is from grub-reboot script.

default_file=$grub_dir/default

default="$selectedNum" ; shift
grub --batch --config-file=$config_file $@ <<EOT
savedefault --once --default=$default
quit
EOT

echo "
#
#
#
#
#
#
#
#
#
#
# WARNING: If you want to edit this file directly, do not remove any line
# from this file, including this warning. Using \`grub-set-default\' is
# strongly recommended." >> $default_file

# /sbin/shutdown -r now "Rebooting into $selected" #Reboot command  # UNCOMMENT (remove # at front) this line to restart.



fi
exit 0;
[/php][IMG]http://farm4.static.flickr.com/3101/2881836278_8ba30b2127.jpg?v=0[/IMG]

---

### Post by mridkash on 2008-09-23
> Can you set the script to make a backup of the original on first use? (or an option to make a backup, and also restore the original)

Yes, the script automatically makes a backup of original menu.lst file before overwriting. 
The backup file is named menu.Backup
You can restore the file by renaming it back to menu.lst

Also, the script makes changes to menu.lst file only if it is really required. Otherwise, it just skips the overwriting code.

---

### Post by dwhitney67 on 2008-09-23
I feel like I am an "advanced user" of Linux (Fedora, Ubuntu) and even with certain Unix systems.

I can not fathom why anyone today would set up a dual boot system, when virtualization is available.

I use VMware Server under Fedora and Ubuntu to run windoze, never having to reboot.  For Ubuntu, there is also VirtualBox (sp?), and for Fedora, there is Zen.

One could easily run VMware Server under windoze to run their favorite *nix system.

I think dual-booting is passé.

---

### Post by Tuna-Fish on 2008-09-23
> **dwhitney67 said:**
> I feel like I am an "advanced user" of Linux (Fedora, Ubuntu) and even with certain Unix systems.

I can not fathom why anyone today would set up a dual boot system, when virtualization is available.

I use VMware Server under Fedora and Ubuntu to run windoze, never having to reboot.  For Ubuntu, there is also VirtualBox (sp?), and for Fedora, there is Zen.

One could easily run VMware Server under windoze to run their favorite *nix system.

I think dual-booting is passé.

So, how will you run 3d drivers in windows under virtualization?

That's right, you don't.

---

### Post by dwhitney67 on 2008-09-23
> **Tuna-Fish said:**
> So, how will you run 3d drivers in windows under virtualization?

That's right, you don't.

For those who prefer to run windoze for gaming purposes, then stick to it.  If you want Ubuntu, or other *nix system for additional purposes, then install VMware Server to run it.

Get it??????

---

### Post by mujambee on 2008-09-23
> **dwhitney67 said:**
> I can not fathom why anyone today would set up a dual boot system, when virtualization is available.

Case 1: My Windows takes ages to start and shutdown. I boot into it if I'll play a game, but if I want to google for something I boot Ubuntu which is much faster.

Case 2: I've just compiled my kernel, I want to make a one-off boot to check it running and then come back to the old tested one.

Just a couple of things that come to mind (in fact, Case 1 is real for me).

---

### Post by dwhitney67 on 2008-09-23
Got it.

Btw, I'm using Ubuntu right now... however I am responding via WinXP, which is the guest OS.

---

### Post by MadsRH on 2008-09-24
Great project ;-)
[B]
//MadsRH[/B]

---

### Post by RaptorITA on 2008-11-04
Thx very much, very useful for a dualboot pc

---

### Post by Endolith on 2008-11-07
I think Fedora already has something like this.

[http://www.dcheng.members.sonic.net/friends/jspaar/pub/bootnext/](http://www.dcheng.members.sonic.net/friends/jspaar/pub/bootnext/)

This really needs to be built into the shutdown menu though.

---

### Post by trunkmonkey2008 on 2008-11-29
I need help rebooting my laptop into windows. Windows was pre-installed when I bought the computer. A reinstall disk didn't come with my computer...

---

### Post by Endolith on 2008-12-01
> **trunkmonkey2008 said:**
> I need help rebooting my laptop into windows. Windows was pre-installed when I bought the computer. A reinstall disk didn't come with my computer...

Do you mean re*install*ing Windows? Did you leave Windows on its own partition or delete it entirely?

---

### Post by jimi_hendrix on 2008-12-01
thank you...i always wanted one of these

---

### Post by Endolith on 2008-12-01
> **Endolith said:**
> I think Fedora already has something like this.

[http://www.dcheng.members.sonic.net/friends/jspaar/pub/bootnext/](http://www.dcheng.members.sonic.net/friends/jspaar/pub/bootnext/)

This really needs to be built into the shutdown menu though.

Actually, it looks like Fedora's bootnext is a really simple package.  Just a python script and some meta information.  It wouldn't take much for someone knowledgeable to port it to the Ubuntu repositories and include it in the shutdown menu.  Here's all there is to the code:

[php]#!/usr/bin/python

# bootnext: Tell GRUB what kernel to boot for the next boot only, and reboot
# 
# Allows user to choose which OS to reboot into for next reboot only.
# Useful for folks who dual-boot another OS occasionaly but don't want to
# permanently change the default.
#
# Default menu choice is set to match expression DEFAULT_TITLE_RE.
# If a command line argument is present, that is used instead 
# of DEFAULT_TITLE_RE.  In either case, expressions are Python regexs.
#
# Must be run with superuser privileges.
# The menu is graphical, and requires that X be running and zenity is
# installed.
# 
# For non-Fedora distros,  change GRUB_CONFIG accordingly.
# 
# Written by Jack Spaar <jspaar-at-myrealbox-dot-com>
# Released under the terms of the GNU General Public License.
#
# Changelog:
# Wed Feb 11 20:01:30 PST 2004 -- Created.
# Wed Mar  3 18:05:05 PST 2004 -- added OK/Cancel prompt.
# Sun Mar 14 22:28:07 PST 2004 -- use zenity to choose grub title to boot.
# Fri Jun 11 14:04:33 PDT 2004 -- use --batch with grub.
# Tue Nov 30 20:47:31 PST 2004 -- use --no-floppy to avoid probe hang on FC3.
# Thu Jan 27 22:32:41 PST 2005 -- allow a regex for finding default title
# Wed Feb  2 19:56:11 PST 2005 -- allow default title on command line
# Tue Aug 23 18:42:37 PDT 2005 -- packaged as rpm
# Sat Dec  2 00:00:34 PST 2006 -- use absolute path for zenity, tweak win width
# Fri Jun  1 15:18:47 PDT 2007 -- use /boot/grub/grub.conf instead of /etc/...
#
# v0.12

import re, os, sys

progName = "bootnext"

# Edit the following to set the default menu selection
#     Note: command line argument overrides this default.
DEFAULT_TITLE_RE = "(?!.*Fedora)"    # match first non-Fedora title.

# Non-Fedora distros often use /boot/grub/menu.lst instead
GRUB_CONFIG = "/boot/grub/grub.conf"

GRUB_PATH =  "/sbin/grub --batch --no-floppy"
DIALOG_TEXT = "Select which OS to boot:"

ZENITY_PATH = "/usr/bin/zenity"
ZENITY_WIDTH = 320
ZENITY_HEIGHT = 325

REBOOT_COMMAND = "/sbin/shutdown -r now &"

def grub_title_list():
    f = open(GRUB_CONFIG, 'r')
    lines = f.readlines()
    f.close()

    p = re.compile('^\s*title\s*(.*)')
    tlist = []

    for line in lines:
        m = p.match(line)
        if m : 
            tlist = tlist + [ m.group(1) ]

    return tlist


## MAIN

if (len(sys.argv) > 1) :
    default_title_re = sys.argv[1]
else:
    default_title_re = DEFAULT_TITLE_RE

titles = grub_title_list()

# form a zenity command to allow user to select from the grub title list
zen = '%s --width %d --height %d --list --radiolist --title "%s" --text "%s" --column "Selected" --column  "Boot Title"  ' % (ZENITY_PATH, ZENITY_WIDTH, ZENITY_HEIGHT, progName, DIALOG_TEXT)

p = re.compile(default_title_re)
default_found = 0
for title in titles:
    # Turn on radio button for 1st title matching DEFAULT_TITLE_RE
    if ((not default_found) and (p.match(title))):
        zen += " TRUE "        
        default_found = 1
    else:
        zen += " FALSE "
    zen += "\"%s\"" % (title)

# run zenity and grab the user's choice
pipe = os.popen(zen, 'r')
choice = pipe.read().strip("\n")
okCancel = pipe.close()
if (okCancel != None):
    print "Cancelled."
    sys.exit(okCancel)

# convert the title to a grub index number
num = 0
for title in titles:
    if (title == choice):
        break
    num += 1

# Now tell GRUB we want that other OS for the next boot only
grubCommands ='savedefault --default=%s --once\nquit\n'%(num)

pipe = os.popen(GRUB_PATH, 'w')
pipe.write(grubCommands)
pipe.close()

# Now reboot
os.system(REBOOT_COMMAND)

sys.exit(0)[/php]

---

### Post by mridkash on 2008-12-02
Hello,
The fedora reboot script also utilizes the grub savedefault with -once flag. My script also does this, but it doesn't work that way. It does reboot the correct option chosen, but that option persists. The same option is selected everytime you boot. I think the -once flag is not working.
Can you test if the option is selected only once while booting.

Thanks

---

### Post by Endolith on 2008-12-16
[https://bugs.launchpad.net/ubuntu/+bug/304215](https://bugs.launchpad.net/ubuntu/+bug/304215)

---

