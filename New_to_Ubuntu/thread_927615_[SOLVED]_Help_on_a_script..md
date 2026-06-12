---
title: "[SOLVED] Help on a script."
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Pictizm on 2008-09-23
[COLOR="Red"]RESOLVED! :D[/COLOR]
[COLOR="Silver"]Why hi thar.

I previously asked (a while ago though) about a script for resetting accounts on ubuntu after a boot.

[http://ubuntuforums.org/showthread.php?t=754825]("http://ubuntuforums.org/showthread.php?t=754825")

I'm having a problem though. When booting the system, the script deletes the files I'm asking for 'em to be replaced by the one from the backup folder, but they just won't copy. :([/COLOR]

Here's how I did it:

- Install Ubuntu
- Create an Administrator account
- Make all settings and fixes (resolution and stuff)

Then I've created the student account (I'm Flemish, so I've called it "leerling" here)
Made all changes in the menu's and edited the necessary restrictions.
Lastly, I made the backup copy using:
```
sudo cp -a /home/leerling /backup/
```
so the contents of the folder */home/leerling/* are copied to */backup/leerling/*
Note by using that code, the hidden files (dot-files) also got copied.

Then back as the Administrator, I made the script called *leerling.sh* containing the following piece of code:
```
#!/bin/bash
USER=leerling
rm -Rf /home/$USER
mkdir /home/$USER
cp -a /backup/$USER /home/
chmod -R 0755 $USER.$USER /home/$USER
```
[COLOR="Red"]New updated version![/COLOR]
This is an edited version of the code hyper_ch suggested in the previous thread to match this system. I think it's done correctly because it did delete the files.

I placed the *leerling.sh* file in */etc/init.d/* and used
```
sudo update-rc.d leerling.sh defaults
```
to make it run upon boot.

[COLOR="Red"]It all works now. Try for yourself.[/COLOR]

---

### Post by Orange_and_Green on 2008-09-23
Hello :)

If I understand the problem correctly (and there's no guarantee at all that I do ;)) you have a directory called /backup/leerling containing all the backup files, so shouldn't the fifth line of the script read

```
cp -a /**backup**/$USER/* /home/$USER/
```

instead?

---

### Post by Pictizm on 2008-09-23
> **Orange_and_Green said:**
> Hello :)

If I understand the problem correctly (and there's no guarantee at all that I do ;)) you have a directory called /backup/leerling, so shouldn't the fifth line of the script read

```
cp -a /**backup**/$USER/* /home/$USER/
```

instead?

Oh yes, I did edit it that way. I just edited it wrong in this thread. :P

---

### Post by Orange_and_Green on 2008-09-23
Oh I see.

Well, if you run the same script (with sudo) from your terminal instead of rebooting, you should most likely catch any error messages. Could you please give it a try?

---

### Post by Pictizm on 2008-09-23
> **Orange_and_Green said:**
> Oh I see.

Well, if you run the same script (with sudo) from your terminal instead of rebooting, you should most likely catch any error messages. Could you please give it a try?

Well, you've set me on the right path. I've started over and edited that script a bit so it simply copies the folder. So I won't need to mess with access and restrictions.

---

