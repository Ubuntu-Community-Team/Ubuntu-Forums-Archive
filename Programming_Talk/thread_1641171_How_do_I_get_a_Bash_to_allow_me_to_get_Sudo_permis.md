---
title: "How do I get a Bash to allow me to get Sudo permissions?"
date: 2010-12-08
forum: Programming Talk
---

### Post by argedion on 2010-12-08
I am working on a small bash to replace my grub splash screen. I have set up my grub.cfg file to look into /boot/grub/splashimages and find the file bootsplash.jpg I wrote this bash to help simplify the task however i keep getting a permission denied can I do what i am trying to do or do I need to sudo gsplash.sh instead?

here is the code
```
/bin/bash
set -e

####################################################################
#####                   Argedion                               #####    
#####        Wed 08 Dec 2010 06:53:09 PM EST                   #####
#####               File Name: gsplash.sh                      #####
####################################################################
#version: 1.0.0
# A File to change the Grub splash screen by copying file and changeing
#the name of the file I wish to use for the splashscreen to bootsplash.jpg
#
newsplash = "%1"
################Start Script####################
sudo
cp $newsplash /boot/grub/splashimages/bootsplash.jpg
```

---

### Post by argedion on 2010-12-08
Seems no matter how I try to write it or run it I get a permission denied even if I run it as root. I am unsure of what is going on anyone with any insight? Thanks a lot

---

### Post by amsterdamharu on 2010-12-08
```
sudo bash /full/path/gsplash.sh
```And remove the sudo from the gsplash.sh

If you don't want it to ask for your password (scripts that you only run a lot) than copy the script to /bin. Now change the owner and permissions so only root can access it:
```
sudo chown root:root /bin/gsplash.sh
sudo chmod 700 /bin/gsplash.sh
```
Now edit sudoers so it won't ask you for a password when executing the script:
```
sudo visudo
```Add the following line at the end of the file:
```
yourUser ALL=NOPASSWD: /bin/gsplash.sh
```Press control + o 
Press enter
Press control + x

---

### Post by sisco311 on 2010-12-08
```
...
**newsplash="$1"    # the first argument is $1 (not %1)**
################Start Script####################
sudo cp $newsplash /boot/grub/splashimages/bootsplash.jpg
```


**set -e** means exit immediately if a pipeline exits with a non-zero status.

In your script sudo fails because, by default, it needs a command as an argument.

---

### Post by argedion on 2010-12-08
Thanks for the info however the script is not working at all I'm not sure what my problem is but here

```
/bin/bash
set -e

####################################################################
#####                   Argedion                               #####    
#####        Wed 08 Dec 2010 06:53:09 PM EST                   #####
#####               File Name: gsplash.sh                      #####
####################################################################
#version: 1.0.0
# A File to change the Grub splash screen by copying file and changeing
#the name of the file I wish to use for the splashscreen to bootsplash.jpg
#
newsplash=$1
################Start Script####################
cp $newsplash /boot/grub/splashimages/bootsplash.jpg
```
maybe someone can figure out why its not working I can type the full path into the command line and change out the picture so i'm not sure why i can not do it from the bash file. At this point I would just settle to get the script working then worry about setting it up for root use.

---

### Post by argedion on 2010-12-08
> **sisco311 said:**
> ```
...
**newsplash = "$1"    # the first argument is $1 (not %1)**
################Start Script####################
sudo cp $newsplash /boot/grub/splashimages/bootsplash.jpg
```


**set -e** means exit immediately if a pipeline exits with a non-zero status.

In your script sudo fails because, by default, it needs a command as an argument.

yeah i forgot the " " also when i redid this that was a typical typo though

---

### Post by sisco311 on 2010-12-08
I'm not sure (it's 3:12 AM here), but using quotes is always a good idea. 

```
newsplash="$1"
################Start Script####################
cp "${newsplash}" /boot/grub/splashimages/bootsplash.jpg
```

Here is a good bash tutorial:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by argedion on 2010-12-08
Thanks you guys I have it working now :D this will help simplify the task a little bit. 

sisco311 genius helped me to get it working thanks a bunch 

amsterdamharu thanks for the info i will definitely have to use it for those bash files i need to run as root

---

