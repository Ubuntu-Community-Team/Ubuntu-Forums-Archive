---
title: "Bash Script: &quot;Yes/No&quot; User Input."
date: 2007-08-21
forum: Programming Talk
---

### Post by jusmurph on 2007-08-21
I have begun playing with bash scripting and i want to make a very simple script for when i do a fresh reinstall.

Simply it is a list of:

"Sudo apt-get install XXX
Sudo apt-get install YYY...etc"

What i want to do is put in a question before each install so its something like:

"do you want to install XXX?
If yes sudo apt-get install XXX
if no continue onto the next line
do you want to install YYY?
If yes sudo apt-get install YYY
if no continue onto the next line...etc"

---

### Post by Wybiral on 2007-08-21
Look for info on the "read" command.

---

### Post by vanadium on 2007-08-21
i.e. type "info read" at the prompt. Curiously, there is no man page ("man read") available.

---

### Post by Mr. C. on 2007-08-21
This post has some examples of how to use the read command:

[http://ubuntuforums.org/showthread.php?t=530833](http://ubuntuforums.org/showthread.php?t=530833)

MrC

---

### Post by sacherjj on 2007-08-21
How about something like this:

```

read -p "Install XXX (y/n)?"
[ "$REPLY" == "y" ] || sudo apt-get install XXX
read -p "Install YYY (y/n)?"
[ "$REPLY" == "y" ] || sudo apt-get install YYY

```

If the user types "y", it runs the or'ed (||) code.  Otherwise it skips it.

Edit: Might want to force running as root when you start, instead of sudo'ing each statement, like my script that MrC linked to right above.

---

### Post by Siljrath on 2009-08-18
i just tried that out with my adapted script to test that out.

```
#!/bin/bash
echo hey!
read -p "write 'gooba gooba gooba' (y/n)?"
[ "$REPLY" == "y" ] || echo "gooba gooba gooba"
read -p "Install YYY (y/n)?"
[ "$REPLY" == "y" ] || sudo apt-get install YYY
```

and as this screenshot shows, i said yes to gooba and no to install, and it did it the wrong way around![[img]http://omploader.org/tMjZjcw[/img]](http://omploader.org/vMjZjcw)
how'd that come about!?

edit:
ah!
> Last edited by sacherjj; August 21st, 2007 at 07:46 PM.. Reason: changed != "y" to == "y". 
you were right the first time.
glad u did that though, now i know how to make it a "press this" or a "press anything but this"

---

### Post by Mr. C. on 2009-08-18
Use && when you want the second part to run (be evaluated) when the first part is true.

Use || when you want the second part to run (be evaluated) when the first part is false.

---

### Post by Siljrath on 2009-08-18
> **Mr. C. said:**
> Use && when you want the second part to run (be evaluated) when the first part is true.

Use || when you want the second part to run (be evaluated) when the first part is false.

ah, cool. so you can invert the true/false with both &&/|| and !=/==.


edit:
so for example,```
#!/bin/bash
echo hey!
read -p "write 'gooba gooba gooba' (y/n)?"
[ "$REPLY" != "y" ] || echo "gooba gooba gooba"
read -p "Install YYY (y/n)?"
[ "$REPLY" == "y" ] && sudo apt-get install YYY
```
both work.   ... except of course YYY is just a placeholder, not a package.  ;)

---

### Post by geirha on 2009-08-18
You can also combine them to get something similar to an if/else, though if either [[ or aptitude fails, it will jump to the part after ||

```

read -n1 -p "Install foo? (y/n) "
echo
[[ $REPLY = [yY] ]] && echo sudo aptitude install foo || { echo "You didn't answer yes, or installation failed."; exit 1; }

```

---

### Post by lswb on 2009-08-18
> **vanadium said:**
> i.e. type "info read" at the prompt. Curiously, there is no man page ("man read") available.

"read" is part of bash, it is covered in "man bash"

---

### Post by potat on 2010-06-17
If you have a lot of packages...

```

#!/bin/bash
PKGLIST="conky build-essential chromium-browser torcs"
PKGINST=" "
echo "Time to install stuff!"
for PN in $PKGLIST
do
    read -p "Install ${PN} (y/n)?"
    [ $REPLY = "y" ] && PKGINST="${PKGINST} ${PN}"
done
sudo apt-get install $PKGINST


```

---

### Post by geirha on 2010-06-17
> **potat said:**
> If you have a lot of packages...

```

#!/bin/bash
PKGLIST="conky build-essential chromium-browser torcs"
PKGINST = " "
echo "Time to install stuff!"
for PN in $PKGLIST
do
    read -p "Install ${PN} (y/n)?"
    [ $REPLY = [yY] ] && PKGINST="${PKGINST} ${PN}"
done
sudo apt-get install $PKGINST


```

Maybe you should try that code yourself first, because that will not work...

---

### Post by angry_johnnie on 2010-06-17
i've adapted your idea, using zenity:

```
#!/bin/bash

## easy installer
## by angry_johnnie
## send me money! -_-

## gain root power, because we have to

gksudo -k -m "What's the magic word?" /bin/echo "got r00t?"
sudo -v


## add the medibuntu repository, if necessary

if [ ! -e "/etc/apt/sources.list.d/medibuntu.list" ]
	then

(
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
) | zenity --progress --pulsate --auto-close --auto-kill --title="easy installer" --text="adding repository"  --percentage=0 --width 350 --height 25

fi

## create a bash script within the user's home directory

echo "#!/bin/bash" > $HOME/files
echo " " >> $HOME/files

## determine which packages/apps/files are going to be installed

ans=$(zenity  --list  --width 300 --height 50  --text "What do you want to install?" --checklist  --column "Pick" --column "options"  --column "description" FALSE "program" "description"   --separator=" "); echo "sudo apt-get install --yes --force-yes $ans" >> $HOME/files
if $ans
	then
	exit 0
fi

## make the resulting file executable

sudo chmod a+rx $HOME/files

## install files

cd $HOME
(
./files
) | zenity --progress --pulsate --auto-close --auto-kill --title="easy installer" --text="installing packages"  --percentage=0 --width 350 --height 25

## remove resulting file, given it's not necessary any more

rm $HOME/files

## update menu entries

if [ -e "/usr/bin/update-menus" ]
then
sudo update-menus
else
sudo apt-get install menu
sudo update-menus
fi

exit 0

```

i think it should work, although i haven't tried it :p

i know for a fact it does write the file, and it does make it executable, so it should work.   but then again, i haven't tried it.  I might try it, though, next time i re install/install/upgrade or whatever :p




:p  i just realized this thread was originally started about 3 years ago :o

anyway... i still think this script would work :p


it does work

---

### Post by j7%&lt;RmUg on 2010-06-17
i already have a nice install script that adds all the ppas i want, installs everything i want and also spits out all the custom settings i use for various programs.

---

### Post by potat on 2010-06-18
> **geirha said:**
> Maybe you should try that code yourself first, because that will not work...
Thanks, and sorry about that. I fixed the code above (I accidentally added the spaces in the PKGINST assignment and i changed the conditional statement to one that another poster had provided at the last minute). It should work now though!

---

### Post by Krupski on 2010-06-18
> **jusmurph said:**
> I have begun playing with bash scripting and i want to make a very simple script for when i do a fresh reinstall.

Simply it is a list of:

"Sudo apt-get install XXX
Sudo apt-get install YYY...etc"

What i want to do is put in a question before each install so its something like:

"do you want to install XXX?
If yes sudo apt-get install XXX
if no continue onto the next line
do you want to install YYY?
If yes sudo apt-get install YYY
if no continue onto the next line...etc"

Here's a little script that I use to check for and install updates. Mine installs all new ones, asks if I want to reboot if there's a kernel update, etc...

It's not exactly what YOU asked for, but it contains all the "parts" you need to write your own.

```

#!/bin/bash

rebootflag=0
answer="N"

/bin/echo Checking for system updates...
/usr/bin/apt-get -V update
/usr/bin/apt-get -V dist-upgrade

/bin/echo Checking for Linux header updates...
/usr/bin/apt-get -V install linux-headers-`uname -r`

/bin/echo Updating PCI ids file...
/usr/bin/update-pciids

/bin/echo Updating USB ids file...
/usr/sbin/update-usbids

/bin/echo Updating CPU microcode file...
/usr/sbin/update-intel-microcode

/bin/echo Updating mlocate database...
/usr/bin/updatedb
/usr/bin/updatedb.mlocate

/bin/echo SYNC...
/bin/sync

/bin/ls /var/cache/apt/archives/ | /bin/grep -i linux-image* &> /dev/null && rebootflag=1

if [ ${rebootflag} -eq 1 ]; then
{
	/bin/echo
	/bin/echo -n "Reboot required - reboot now? (yes/N) "
	read answer
}
fi

if [ "$answer" == "yes" ]; then
{
	/usr/bin/apt-get -V clean
	/bin/sync
	/bin/sleep 5	
	/sbin/shutdown -rv now
}
else
{
	/bin/echo
	/bin/echo "Update done!"
	/bin/echo
	exit 0
}
fi

```

**[COLOR="Red"]NOTE: I always run my system as root (yeah yeah I know....) -- so if you don't have root access in your normal account, you'll have to do a "sudo su" before running this, of else build a root login into the script.[/COLOR]**

Hope this helps.

-- Roger

---

### Post by gpwil1 on 2010-12-02
> **nisshh said:**
> i already have a nice install script that adds all the ppas i want, installs everything i want and also spits out all the custom settings i use for various programs.

Thats great - but how about posting?!

---

