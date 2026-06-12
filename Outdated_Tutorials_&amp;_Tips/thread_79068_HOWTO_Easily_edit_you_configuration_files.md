---
title: "HOWTO: Easily edit you configuration files"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by zipmegabyte on 2005-10-19
I use to mess around with configuration files all the time and just got sick of having to type "sudo gedit /etc/fstab" or "sudo gedit /etc/X11/xorg.conf" over and over or search for them in the terminal cache.

So I came up with a solution that might be useful for some of you.
I just created some shell scripts in my /usr/bin with the same names of the configuration files I edit the most, so whenever I type "fstab" it will open /etc/fstab for edition with root privileges, using gedit if I'm in Gnome or nano if I'm in pure terminal. All automated and hassle-free.

**STEP 1:**
So first we need the main script, that I'll call "easyedit.sh". Open a terminal window and type:

```
sudo gedit /usr/bin/easyedit.sh
```

Paste the following text into gedit:

```
#!/bin/sh
[COLOR="Green"]TERM_EDITOR="nano"
X_EDITOR="gedit"
X_SUDO="gnome-sudo"[/COLOR]

FILE=$1
TERMINAL="`tty`"
if [ $? -eq 1 ];
then
TERMINAL="none"
fi
case $TERMINAL in
/dev/tty[1-8])
if [ `whoami` = "root" ];
then
$TERM_EDITOR $FILE
else
sudo $TERM_EDITOR $FILE
fi
;;
/dev/pts/*|/dev/ttyp*|none)
if [ `whoami` = "root" ];
then
$X_EDITOR $FILE&
else
$X_SUDO "$X_EDITOR $FILE"&
fi
;;
*)
esac
```

Ok, save the file, return to terminal and type:

```
sudo chmod 777 /usr/bin/easyedit.sh
```

**STEP2:**
Now all we need are the files that will have the same name as the ones you edit the most. Here is how to do fstab:

```
sudo gedit /usr/bin/fstab
```

then paste this into gedit:

```
#!/bin/sh
[COLOR="Red"]FILE="/etc/fstab"[/COLOR]

easyedit.sh $FILE
```

Save file and make it executable using 'sudo chmod 777 /usr/bin/fstab'.

That's it. Repeat STEP 2 for any configuration file you want, just remember to save them into /usr/bin with the same name as the original files (for easy remembering) and to change the value of [COLOR="Red"]FILE[/COLOR] to match the path to the original file. I also created scripts for /boot/grub/menu.lst, /etc/X11/xorg.conf and /etc/apt/sources.list.

Remeber: you can use this command wherever you want, be it in gnome, KDE or pure terminal. You can also change [COLOR="Green"]TERM_EDITOR[/COLOR], [COLOR="Green"]X_EDITOR[/COLOR] and [COLOR="Green"]X_SUDO[/COLOR]  in easyedit.sh to match your tastes.

---

### Post by Saiboogu on 2005-10-19
Great little howto.. Never thought to do that. Just read this on my lunch break, and already have several setup. Thanks!

---

### Post by zipmegabyte on 2005-10-19
I just found a bug that prevented it from running from a .desktop file or the run dialog (ALT+F2) and updated the howto. You'll have to redo Step 1, cause I changed the /usr/bin/easyedit.sh file.

---

### Post by Turgon on 2005-10-19
Nice idea. 

If you got time to make further improvements, a list with all the config with a little discription for each of them would be great. You could write f.eks configoverview, and a text file with the overview would pop up. 

Turgon

---

### Post by zipmegabyte on 2005-10-19
Can you explain wat you mean? What is f.eks configoverview? I googled it but found nothing in a language I could undestand.

Btw I updated the script again. Seems like I forgot to declare a variable in the first script. At least now I tested the steps and it's ok.

---

### Post by majikstreet on 2005-10-19
That's really neat!

I like typing vi /etc/fstab LOL-- but that's just me ;)

This is a good idea, and should be considered to be included in Dapper Drake *by default*

---

### Post by Velox Letum on 2005-10-19
Very nice...I'm using it now for my fstab and xorg configs...thanks for the tip! :)

---

### Post by Stormy Eyes on 2005-10-19
Nice work. It's not something I'd use myself, as I prefer to do all config tasks manually in order to focus on the task at hand, but I can this being useful to newbies.

---

### Post by mhael on 2005-10-20
> 
Ok, save the file, return to terminal and type:

```
sudo chmod 777 /usr/bin/easyedit.sh
```


It would be better to use 755 as permissions instead of 777. To have world-writable files (especially executables) on system is a serious security risk.

---

### Post by zipmegabyte on 2005-10-20
You're probably right. As I don't care much about security in this machine I tend to be a little too permissive.

---

