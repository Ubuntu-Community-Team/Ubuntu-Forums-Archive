---
title: "Root terminal, hard to find trash of root"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by yogo on 2008-05-03
What happened is a mess but I have about four to five files in root trash that are eating up hard drive space but I can not remove them. My problem is I do not know how to navigate to the correct folder to remove them.

I have tried a gazillian different ways but to no avail.

Anyways here are the files I found, but have no idea what to run to get rid of them

root@steve-desktop:/home/steve# find / -size +300M -exec ls -l {} \;
[COLOR=Red]-rw-r--r-- 1 steve steve 1073739776 2008-05-03 17:25 /root/.Trash/GDG MAGICAL MISSIONS DOM/VIDEO_TS/VTS_03_2.VOB
-rw-r--r-- 1 steve steve 563521536 2008-05-03 17:26 /root/.Trash/GDG MAGICAL MISSIONS DOM/VIDEO_TS/VTS_03_3.VOB
-rw-r--r-- 1 steve steve 1073739776 2008-05-03 17:23 /root/.Trash/GDG MAGICAL MISSIONS DOM/VIDEO_TS/VTS_03_1.VOB
-rw-r--r-- 1 steve steve 1073739776 2008-05-03 17:14 /root/.Trash/FullDisc/qqqMAGICAL MISSIONS DOM/VIDEO_TS/VTS_03_2.VOB
-rw-r--r-- 1 steve steve 1073739776 2008-05-03 17:14 /root/.Trash/FullDisc/qqqMAGICAL MISSIONS DOM/VIDEO_TS/VTS_03_3.VOB
-rw-r--r-- 1 steve steve 1073739776 2008-05-03 17:14 /root/.Trash/FullDisc/qqqMAGICAL MISSIONS DOM/VIDEO_TS/VTS_03_1.VOB[/COLOR]
-r-------- 1 root root 939528192 2008-05-03 22:06 /proc/kcore
find: /proc/16519/task/16519/fd/4: No such file or directory
find: /proc/16519/task/16519/fdinfo/4: No such file or directory
find: /proc/16519/fd/4: No such file or directory
find: /proc/16519/fdinfo/4: No such file or directory


If someone could tell me what the exact file is and where to navigate to issue a rm command.

TIA

---

### Post by Bakon Jarser on 2008-05-03
have you tried running 

sudo nautilus

and seeing if you can find them that way?

---

### Post by tdrusk on 2008-05-03
> **Bakon Jarser said:**
> have you tried running 

sudo nautilus

and seeing if you can find them that way?

to run graphical programs as root use gksu

```
gksu nautilus
```

---

### Post by fluffman86 on 2008-05-03
try navigating to /home and looking in .Trash-0 and .Trash-root

---

### Post by yogo on 2008-05-03
Yes I tried gksu nautilus, it shows my trash is empty, but there are about five gigs these files are taking up.  I believe these files really do not exist but are showing up and eating up my hd.

Possibly because these files had errors and are not the size they supposedly are.

Not sure what is going on but it was a Diego movie for my son I wanted to back up before he scrathed this one any more:)

So I am really clueless right now.

---

### Post by yogo on 2008-05-03
> **fluffman86 said:**
> try navigating to /home and looking in .Trash-0 and .Trash-root

Just gave that a try but do not have .Trash-0 and .Trash-root, I do have a .Trash but that is empty???

Thanks

---

### Post by cubeist on 2008-05-04
try this in terminal, without the quotes of course:
```
locate "whatever the name is"
```

then cd to that location, then rm the files.  Use man cd and man rm if you are not familiar with those commands.

---

### Post by yogo on 2008-05-04
> **cubeist said:**
> try this in terminal, without the quotes of course:
```
locate "whatever the name is"
```then cd to that location, then rm the files.  Use man cd and man rm if you are not familiar with those commands.


I have managed to find all the files but still some are not removing, especially the ones that have a copy of the file like this one.

VTS_02_0 (copy).VOB

Not sure how to handle the syntax error [ bash: syntax error near unexpected token `(']

Googled it but all I got was to try to put in single or double quotes and that did not work.

Here are the ones left to remove.

Adssite Games Collection         Link to Fireworks.exe
AQUAZONE DESKTOP GARDEN.lnk      Link to notepad.exe
AQUAZONE OpenWater               mplayerplug-in-qt.so
AQUAZONE OpenWater.lnk           mplayerplug-in-qt.xpt
AQUAZONE VE                      mplayerplug-in-rm.so
FRONTIER GROOVE                  mplayerplug-in-rm.xpt
[COLOR=Red]GDG MAGICAL MISSIONS DOM[/COLOR]         mplayerplug-in.so
kaffeine (copy).png              mplayerplug-in-wmp.xpt
kate (copy).png                  mplayerplug-in.xpt
kiba-dock (copy)                 NAVIGON (copy)
kwrite (copy).png                NAVIGON fresh.lnk
libtotem-narrowspace-plugin.so   Open Studio
libtotem-narrowspace-plugin.xpt  [COLOR=Red]VTS_02_0 (copy).VOB
[COLOR=Black]
The ones in red are probably the biggest


TIA
[/COLOR][/COLOR]

---

### Post by pommattski on 2008-05-04
Does```
sudo rm /root/.Trash/GDG\ MAGICAL\ MISSIONS\ DOM/VIDEO_TS/VTS_03_2.VOB
```not work? (Using "/" to escape the spaces in the path.)

Also, if you're not already doing so, use <TAB> to autocomplete filenames and paths - it will insert any characters necessary to avoid the problem you are having.
In your example above, in terminal, cd to the directory containing the file "GDG MAGICAL MISSIONS DOM mplayerplug-in.so" and type```
 sudo rm GDG
```(don't press enter) then press <TAB>. If that is the only file in that directory which starts with the characters "GDG", terminal will automatically complete the filename 'escaping' any characters which may cause problems.

---

### Post by yogo on 2008-05-04
> **pommattski said:**
> Does```
sudo rm /root/.Trash/GDG\ MAGICAL\ MISSIONS\ DOM/VIDEO_TS/VTS_03_2.VOB
```not work? (Using "/" to escape the spaces in the path.)


WOW, that got me a gig back quickly!!! Tried it exactly like you had it and that worked.

Thanks, now I am only down about a gig to 1.5.

Thanks again.

---

### Post by yogo on 2008-05-04
Thanks to all but special thanks to  pommattski, I used what you posted above and altered that to remove an offending folder and got back all what I was missing terms of gigs.

This is marked as solved, there is no link on the thread tools to do that.

---

### Post by pommattski on 2008-05-04
> **yogo said:**
> ... that got me a gig back quickly!!!...That's good to hear. 
Just added more info to post above also which should help you remove the others.[SIZE="1"](I just type too slow!)[/SIZE]

---

### Post by yogo on 2008-05-04
> **pommattski said:**
> That's good to hear. 
Just added more info to post above also which should help you remove the others.[SIZE=1](I just type too slow!)[/SIZE]

I read your prior post but still do not understand, the tab instead of enter just produces a system beep but does nothing.

Here is what is left to remove

kaffeine (copy).png              Link to Fireworks.exe  mplayerplug-in.so
kate (copy).png                  Link to notepad.exe    mplayerplug-in-wmp.xpt
kiba-dock (copy)                 mplayerplug-in-qt.so   mplayerplug-in.xpt
kwrite (copy).png                mplayerplug-in-qt.xpt  NAVIGON (copy)
libtotem-narrowspace-plugin.so   mplayerplug-in-rm.so   NAVIGON fresh.lnk
libtotem-narrowspace-plugin.xpt  mplayerplug-in-rm.xpt  VTS_02_0 (copy).VOB

The Navigon  fresh.ink I can get rid of but the copies and links I am not sure of. Also I am adding a screen shot because there are colors to these files in terminal and am not sure why?
[IMG]http://i25.tinypic.com/2vxnkmq.png[/IMG]

---

### Post by yogo on 2008-05-04
Now I am only left with these, the copies are my only problems as well as two links.

kaffeine (copy).png  kwrite (copy).png      NAVIGON (copy)
kate (copy).png      Link to Fireworks.exe  NAVIGON fresh.lnk
kiba-dock (copy)     Link to notepad.exe    VTS_02_0 (copy).VOB

---

### Post by pommattski on 2008-05-04
OK... to delete all the .png images, try...```
cd /root/.Trash
ls -la
sudo rm *.png
```Note that "rm *.png" will permanently delete all files ending in .png in your current directory - hence checking first with "ls -la" to confirm where you are and what's there.
 
Matt.

---

### Post by yogo on 2008-05-04
> **pommattski said:**
> OK... to delete all the .png images, try...```
cd /root/.Trash
ls -la
sudo rm *.png
```
 
Matt.

Again thanks, I am definitely leaning a few new tricks around terminal.

That got everything whittled  down one file 
  NAVIGON (copy)  

I tried using the same command that I used to get rid of the kiba-dock (copy) folder but can not get rid of this 
[COLOR=Red]  NAVIGON (copy)

TIA
[/COLOR]

---

### Post by pommattski on 2008-05-04
OK. Lets try <TAB> autocompletes again...```
cd /root/.Trash
ls -la
sudo rm NAV<TAB>*then*<ENTER>
```... You should find that when you press <TAB>, the terminal completes the name for you so that you can go ahead and press <ENTER> to execute the command.  If you just get a system-beep, either type a couple more characters of the filename or press <TAB> again. Pressing <TAB> this 2nd time should make it give you a list of all the files in the current directory whose names start with the characters you just typed.

You will find that <TAB>/autocomplete is *SO* useful for working more quickly in terminal and for avoiding typos, especially in long filenames.

---

### Post by yogo on 2008-05-04
> **pommattski said:**
> OK. Lets try <TAB> autocompletes again...```
cd /root/.Trash
ls -la
sudo rm NAV<TAB>*then*<ENTER>
```....

Thanks again, I am sure that would have worked and almost want to put back the folder just to try it. :)

However I got rid of it with this 

rm -rf *

Now I understand the auto complete feature.

Thanks to your knowledge of CLI, my root directory is clean. No more using Nautilus to delete files, never knew they were not really gone. I think some came via Wine also.

---

