---
title: "HOWTO: Install Wine from CVS with my script!"
date: 2006-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by smack on 2006-07-11
[http://seth.dnsdojo.net/scripts/wine-cvs.sh](http://seth.dnsdojo.net/scripts/wine-cvs.sh)

I tried the other wine CVS script and didn't like it much so I made my own. It's real simple and short but it does the job.

This script makes a directory in your home directory called .cvs. If you need to navigate to that hit ctrl-h in nautilus so you can see dotfiles.

Instructions:

Step 1) Download the script and save it anywhere.
Step 2) Navigate to where you saved it in a terminal and 'chmod +x wine-cvs.sh'
Step 3) './wine-cvs.sh' No need to run the script as root. It'll sudo on it's own when it needs to.

You'll be presented with this menu:

Wine CVS build/install script! v1.01
Make sure you have libgl1-mesa-dev, cvs, and gcc installed before starting.
1) Download wine from CVS.
2) Build wine.
3) Install wine.
4) Uninstall wine.
5) Quit.
Your choice(1,2,3,4,5):

Make sure you've got libgl1-mesa-dev, cvs, and gcc before using the script. If there are any dependencies I missed let me know!

Step 4) Follow the steps!

If you need to apply a patch just make sure it's in ~/.cvs/wine/ before you do step 2. If there are any errors patching the patch program will bug you about it.

If you want to see exactly what this script is doing look at all the stuff after takeAction(). Using CVS and building wine is pretty dang simple. Also, the CVS wine installs everything in /usr/local so it won't muck up your filesystem. It uninstalls totally clean also. Needless to say uninstall the wine you installed via apt if your going to install the CVS version. :)

---

### Post by roger6106 on 2006-07-12
I haven't had a chance to try this yet, but I will.

---

### Post by Eazy© on 2006-07-14
Hi!

I testing your skrip while writing this. I had to do some changes in your script to get it going.

First I tried with changing under: "[COLOR="SlateGray"]# BEGIN get source[/COLOR]" to the Europe server to this:
```
export CVSROOT=:pserver:cvs@rhlx01.fht-esslingen.de:/home/wine
```

but that didnt work so then under: "[COLOR="SlateGray"]# Check to see if .cvs pass has the right info. If not insert it.[/COLOR]" I removed the portnumber (:2401) then it started.

---

### Post by rejser on 2006-07-14
I changed mine to use checkinstall so I get inte in deb form and installed

---

### Post by amgeex on 2006-10-20
You're missing flex and bison in your dependencies. Also, most people do not have the build-essential package installed, so you should add it too.

:)

---

