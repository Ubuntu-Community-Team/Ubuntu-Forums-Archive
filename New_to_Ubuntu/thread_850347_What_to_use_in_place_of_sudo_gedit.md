---
title: "What to use in place of sudo gedit?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by rsnow on 2008-07-05
The last time I wanted to edit (change the timeout) in grub I did it using sudo gedit. Now I find that doesn't work. Apparently something has changed during my absence. What do I use in place of sudo gedit to get into the /boot/grub/menu.lst?****

---

### Post by cariboo on 2008-07-05
Nano is the default command line editor. To use it in a terminal type:

```
sudo nano /grub/boot/menu.lst
```

Jim

---

### Post by sisco311 on 2008-07-05
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by Dr Small on 2008-07-05
Try different multiple ways:
```
sudo vim /boot/grub/menu.lst
```
```
sudo nano /boot/grub/menu.lst
```
```
gksudo gedit /boot/grub/menu.lst
```
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by philinux on 2008-07-05
Or if you prefer a gui install and run startupmanager the menu item gets placed in system>admin.

---

### Post by RiceMonster on 2008-07-05
```
sudo apt-get install vim
```

Then, edit /etc/vimrc and comment out "set compatible" (with a "),

then use:

```
sudo vim /boot/grub/menu.lst
```

Vim will suck on Ubuntu if you don't do that. Also, if you want help/want to know how to use it, type "vimtutor" in a terminal, or open up vim and type ":help" then hit enter.


If you don't want to learn vim, just use nano.

---

### Post by rsnow on 2008-07-05
gksu gedit worked fine. Thanks to all for the replies.

---

### Post by bodhi.zazen on 2008-07-05
lol @ command line geeks :)

```
sudo -e /boot/grub/menu.lst
```

If you want to change editors, set your editor in .bashrc :

```
export EDITOR=/usr/bin/nano

export EDITOR='gksu gedit'
```

---

### Post by kansasnoob on 2008-07-05
> **philinux said:**
> Or if you prefer a gui install and run startupmanager the menu item gets placed in system>admin.

Absolutely! Just install startupmanager from Synaptic and then you'll find it in System > Administration > Startup Manager.

Then:

[ATTACH]76545[/ATTACH]

Just change the "timeout" and/or whatever you wish! Just be careful!

---

### Post by kansasnoob on 2008-07-05
> **bodhi.zazen said:**
> lol @ command line geeks :)

```
sudo -e /boot/grub/menu.lst
```

If you want to change editors, set your editor in .bashrc :

```
export EDITOR=/usr/bin/nano

export EDITOR='gksu gedit'
```

I had to change from vi to gedit yesterday to properly restore my sudoers. So, do different progs in 8.04 use different text editors. Still learning here:confused:

NOTE: This is not applicable to this thread!

---

### Post by ibuclaw on 2008-07-05
+1 bodhi.zazen :popcorn:

```
sudo sed -i '/findline/s/matchstring/alteredstring/' file
```

Also,
```

sudo apt-get install vim-gtk
cat >> ~/.bashrc << EOF
alias vim='gvim'
export EDITOR=gvim
EOF

```

Regards
Iain

---

### Post by bodhi.zazen on 2008-07-05
> **kansasnoob said:**
> I had to change from vi to gedit yesterday to properly restore my sudoers. So, do different progs in 8.04 use different text editors. Still learning here:confused:

NOTE: This is not applicable to this thread!

no, the default editor (from the command line) is now nano (was vim in the past) and can be set in .bashrc

---

### Post by sisco311 on 2008-07-05
> **bodhi.zazen said:**
> no, the default editor (from the command line) is now nano (was vim in the past) and can be set in .bashrc
In Hardy the default text editor is vi(or vim) and in Gusty
(and earlier versions???) was nano.
Maybe I'm wrong, but at least visudo uses vim.

---

### Post by bodhi.zazen on 2008-07-05
> **sisco311 said:**
> In Hardy the default text editor is vi(or vim) and in Gusty
(and earlier versions???) was nano.
Maybe I'm wrong, but at least visudo uses vim.

seems you are correct :redface:

---

### Post by kyphi on 2008-07-05
I have read the above posts with great interest.

What puzzles me is that on Hardy Heron, without ever having configured any preferences for an editor, gedit works fine as does nano, vim and jed.

---

### Post by sisco311 on 2008-07-05
> **kyphi said:**
> I have read the above posts with great interest.

What puzzles me is that on Hardy Heron, without ever having configured any preferences for an editor, gedit works fine as does nano, vim and jed.
default = you don't need to define it explicitly
ex: double click on avi files will open totem
right click -> Open with ... -> mplayer = explicite decision (will work)

sudo -e *filename*= edit the file with the default editor
man sudo:
>  -e  The -e (edit) option indicates that, instead of running a command,
           the user wishes to edit one or more files.  In lieu of a command,
           the string "sudoedit" is used when consulting the sudoers file.  If
           the user is authorized by sudoers the following steps are taken:

           1.  Temporary copies are made of the files to be edited with the
               owner set to the invoking user.

           2.  The editor specified by the VISUAL or EDITOR environment vari&#8208;
               ables is run to edit the temporary files.  If neither VISUAL
               nor EDITOR are set, the program listed in the editor sudoers
               variable is used.

           3.  If they have been modified, the temporary files are copied back
               to their original location and the temporary versions are
               removed.

           If the specified file does not exist, it will be created.  Note
           that unlike most commands run by sudo, the editor is run with the
           invoking user&#8217;s environment unmodified.  If, for some reason, sudo
           is unable to update a file with its edited version, the user will
           receive a warning and the edited copy will remain in a temporary
           file.


---

### Post by kyphi on 2008-07-05
Thank you sisco311 for that detailed information.

I was referring to the OP's dilemma in not being able to use "sudo gedit".

"sudo gedit" works for me every time - perhaps there was a syntax error (such as the one in the first reply).

---

### Post by rsnow on 2008-07-06
I think this thread needs to be closed because I've accomplished what I wanted to do as far as the timeout of grub is concerned. Thanks to all!!

---

