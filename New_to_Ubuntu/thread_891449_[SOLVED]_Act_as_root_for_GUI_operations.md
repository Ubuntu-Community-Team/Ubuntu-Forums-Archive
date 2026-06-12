---
title: "[SOLVED] Act as root for GUI operations?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-08-16
Sorry to bring this old subject up yet again, but I have read endless pages & still don't get it.

I know I can run commands as root in terminal with sudo - no problem, except that is not what I want to do.

I know I COULD log in as root but that is severely frowned upon, so I won't (well, maybe...).

I have seen references to gksu & gksudo & sudo su - but can't figure if that is what I need or how to use them.

The particular operation I want to do today is to modify grub/menu.lst file which I can only do as root.
I have made a copy of the file OK (as me) & modified it OK but of course I cannot remove the old file or insert the new file except as root.
How can I become root for long enough to do this operation by drag & drop?

PLEASE don't tell me how I could do the whole thing in terminal, I want to find out in general how I can do this sort of thing graphically.

Thanks for any clear directions!

---

### Post by Bradtek on 2008-08-16
```
gksudo nautilus
```
Should enable you to copy / paste or drag or whatever you want to do

---

### Post by Elfy on 2008-08-16
The best thing would be to edit as root using gedit

```
gksudo gedit /boot/grub/menu.lst
```

You can run nautilus as root 

```
gksudo nautilus
``` so you could drag it.

But are you sure that the file you have edited has the same permisiions as the orginal menu.lst - not sure if that would be important, but probably is :)

This is the permissions for my menu.lst

> -rw-r--r-- 1 root root 6832 2008-08-16 09:09 menu.lst

This command to get that information

```
ls -al /boot/grub/menu.lst
```

---

### Post by iaculallad on 2008-08-16
Rule of thumb: As an example, the editing of the menu.lst file w/c requires the "root" privilege.

When using GUI application (gedit for example) to open the /boot/grub/menu.lst file, use: **gksudo**

```
gksu gedit /boot/grub/menu.lst
```

or use it's symbolic link:

```
gksudo gedit /boot/grub/menu.lst
```

When using terminal application (vi or nano, you're choice), use: **sudo**

```
sudo vi /boot/grub/menu.lst
sudo nano /boot/grub/menu.lst
```

OR, the graphical way:

```
gksudo nautilus
```

and you can freely change/edit files, create/delete folders using nautilus. Just be careful when using this mode.

---

### Post by Dill on 2008-08-16
So you don't have to do the WHOLE thing in the Terminal... only one command:

```
gksudo nautilus
```

This will prompt you for your admin password, and open up your File Browser (should open in your home directory). Near the top-left hand corner of the File Browser, click the up arrow until you get to your root directory (/), where you should see directories like bin, var, home, mnt, etc. . Double-click on the one labeled "boot", and once you're in boot, click on the one labeled "grub". Then just drag and drop your edited menu.lst file into there, it should tell you that it's overwriting the data, and you should be set.

NB: you should make a copy of your old menu.lst file, just in case!

I hope that's clear enough. Let me know if you need me to add screenshots, etc. .

Also, in case you want to try it in the Terminal, you can accomplish the same thing by doing this:

```
sudo mv /path/to/menu.lst/menu.lst /boot/grub
```

where /path/to/menu.lst is the directory where you have your edited version of menu.lst.

You can also do this:

```
cd /boot/grub
sudo gedit menu.lst &
```

If you want more details on what each of these commands do, please feel free to let me know. Don't be afraid of using the Terminal, mate! It's a rockin' good time!

Cheers, 
Dylan

---

### Post by Pioneer5000 on 2008-08-16
Could try:

```

gksudo nautilus

```

Which pretty much makes you root and you can open and edit files as needed as root while in this mode. Make sure to exit it once you are done, and you might want someone else to confirm this is the best option as i'm no linux expert.

---

### Post by 2CV67 on 2008-08-16
Thanks all you guys for so many good replies so quickly.

gksud nautilus seems to do the job I want, thanks, but not without problems/concerns, for the moment...

As you pointed out, dragging/dropping between root & (my) desktop changes the permissions. Not sure if that matters & I suppose I can always change them back afterwards, so long as I remember.

More surprisingly, I get error messages on opening & closing the root window, see below:
............................
chris@DESKTOP:~$ gksudo nautilus 
Initializing nautilus-share extension 

** (nautilus:5773): WARNING **: Unable to add monitor: Operation not supported 
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory 
Please ask your system administrator to enable user sharing. 


--- Hash table keys for warning below: 
--> file:/// 

(nautilus:5773): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above) 

(nautilus:5773): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time 
seahorse nautilus module shutdown 
..............................

Maybe I should point out that I have just made a fresh clean install of Hardy, replacing upgrades through Edgy, Fiesty & Gutsy, so probably still have a lot of setting up to do, but I don't understand the above warnings.

Thanks again!

---

### Post by 3rdalbum on 2008-08-16
If everything still works, then don't worry about the warnings. Gnome does spit out warnings for a lot of things.

I'm surprised nobody mentioned the **easiest and most convenient way of elevating to root in the GUI**.

Go into Synaptic and install the package *nautilus-gksu*. Log out, and log back in again. Now whenever you right-click a file or folder, you will have the option to "Open as Administrator". Use it wisely.

---

### Post by t0p on 2008-08-16
> **Dill said:**
> So you don't have to do the WHOLE thing in the Terminal... only one command:

Code:

gksudo nautilus

Actually, you don't have to do any of it in the terminal.  You can press **Alt+F2** and type the command in the Run box that appears. :)


> **2CV67 said:**
> chris@DESKTOP:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:5773): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS SSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///

(nautilus:5773): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:5773): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown

I don't know what the error messages mean either.  I always get them when I run gksudo nautilus in terminal.  But it all seems pretty harmless, so I don't think it's anything to worry about!

---

### Post by t0p on 2008-08-16
> **3rdalbum said:**
> 
I'm surprised nobody mentioned the **easiest and most convenient way of elevating to root in the GUI**.

Go into Synaptic and install the package *nautilus-gksu*. Log out, and log back in again. Now whenever you right-click a file or folder, you will have the option to "Open as Administrator". Use it wisely.

Wow! I never heard of that one!

Safely installed on my system now.  Thanks!

---

### Post by 2CV67 on 2008-08-16
> **3rdalbum said:**
> 
I'm surprised nobody mentioned the **easiest and most convenient way of elevating to root in the GUI**.

Go into Synaptic and install the package *nautilus-gksu*. Log out, and log back in again. Now whenever you right-click a file or folder, you will have the option to "Open as Administrator". Use it wisely.

Aha! That is really impressive!
Hope it gets more publicity, as I had not seen it in any of the countless articles I read.

Do you know lots more GUI-friendly tips like that one? ;)

Many thanks!

---

### Post by 2CV67 on 2008-08-17
Aha!

I just found I could have done the whole thing GUI without even needing to fiddle with menu.lst at all...

I added "Start-up Manager" via Synapt so now I can do everything to the boot process GUI-style!

This is how I like my Ubuntu.

One happy user! :D

Of course I like having nautilus gksu as well!

---

### Post by 2CV67 on 2008-09-08
Today I was trying to do something which, finally I found I did not need, but it showed up something about nautilus-gksu I don't understand.

I wanted to open /home/me/.mozilla/firefox/blablabla.default/chrome/userChrome-example.css as Administrator.

When I right-clicked on the file, the list started with "Open with Text editor" & included "Open as Administrator".
"Open with Text Editor" (or just double-click) opens it OK.
"Open as Administrator" leads to an error message:> Unable to determine the program to run.
The item you selected cannot be open with administrator powers because the correct application cannot be determined.
The file "Properties > Open-With" shows "Text Editor".

If I start with "gksudo nautilus" then navigate to the same file, right-clicking shows "Open with Text Editor" but not "Open as Administrtator".
"Open with Text Editor" or double-clicking opens the file OK - presumably as Administrator.

Seems to be the same with other .css files tried at random.

Is that normal?

---

