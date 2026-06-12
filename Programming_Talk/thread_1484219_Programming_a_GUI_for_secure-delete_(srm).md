---
title: "Programming a GUI for secure-delete (srm)"
date: 2010-05-15
forum: Programming Talk
---

### Post by within on 2010-05-15
Hi there,

I'd like to start (from scratch?) to program a nice GUI for the secure-delete (srm) package.

I have no idea from where to start and how to start, but I'd like to make a nice open-source application, in respecting the GNU GPL.

I do have some skills in C programming under windows, but never tried for a GNU OS until now. I'd like this to be my first step.

Any advice and help is grandly appreciated :)

Cheers,
within

---

### Post by shadylookin on 2010-05-15
You could do it with any language you want really. If you want to do it in C you can use the gtk gui library

---

### Post by soltanis on 2010-05-15
Python is a favorite of this forum and is commonly used when wrapping command line tools with a GUI.

---

### Post by within on 2010-05-15
> **soltanis said:**
> Python (...) is commonly used when wrapping command line tools with a GUI.

I'm open-minded to any way, but as I said, I really start from a "no-****ing-idea-how-to-start-and-with-what-I-need" way :mrgreen:

To be sure to use the basics I did already:
```
$ sudo apt-get install build-essential automake autoconf
```

I guess now I should find a nice GUI maker with a cool IDE (sorry, forgive me I come from windows world and I use VisualStudio) to build the GUI and wrap the different srm commands..

Any software/tool advice?

Cheers,
within 

PS: sorry to be such a n00b, but everyone did start one day...

---

### Post by Seeked on 2010-06-28
I recently wrote these shell scripts.  They are what I use as a front-end (GUI) for srm. I utilized Zenity to generate the windows.  I believe Zenity is included with the Ubuntu installation.

Use this one to securely remove (srm) a file:

```
#!/bin/sh
    cd $HOME/Desktop
    FILE=`zenity --file-selection --title="Select a File to Remove Securely (srm)"`

    case $? in
        0)
            srm "$FILE"
            # echo $FILE
              if [ -f "$FILE" ] ; then

                zenity --error --text "$FILE was NOT able to be removed."
             else
                zenity --info --text "$FILE was removed securely."
            fi ;;
        esac
```This script also utilizes Zenity but it allows you to select a directory instead of a file and uses a -r flag in the srm command to remove a directory recursively.

```
#!/bin/sh
    cd $HOME/Desktop
    DIRECTORY=`zenity --file-selection --directory --title="Select a Directory to Remove Securely (srm -r)"`

    case $? in
        0)
            srm -r "$DIRECTORY"
            if [ -d "$DIRECTORY" ] ; then

                zenity --error --text "$DIRECTORY was NOT able to be removed."
             else
                zenity --info --text "$DIRECTORY was removed securely."
            fi ;;

        esac 
```You can start the GUI from the command prompt "sh SHELL_SCRIPT.sh" or create an application launcher by right clicking on your desktop and select "create launcher".  Make sure the type is "Application" and the command would be  "sh /PATH/TO/YOUR/SCRIPT.sh". 

Hope this helps...

---

### Post by within on 2010-07-31
@ Seeked:

thanks very much for your scripts!

Right now, I just did create a Nautilus action for srm.
I still plan to start something from scratch with srm sources, but the lack of time is really really a problem for me these months.

Thanks,
within

---

