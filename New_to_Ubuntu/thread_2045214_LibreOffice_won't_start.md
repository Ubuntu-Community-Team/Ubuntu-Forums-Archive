---
title: "LibreOffice won't start"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by peterson43 on 2012-08-20
I've been having trouble with LibreOffice starting. I'm running Ubuntu 12.04, and I have two different user accounts on my computer. LibreOffice used to work fine, but for the past few days I can only use LibreOffice (calc, writer, or any of the programs) when logged in as one of the users. When I'm logged in on the other account if I click on the launcher icon it just blinks and does nothing. 

I also tried launching LibreOffice in several ways and nothing seems to work. I tried from the dash and from a terminal. If I was logged in as User1 (where LibreOffice works) and then I use a terminal to su as User2, running LibreOffice as User2 from the terminal still doesn't work. 

Any ideas what could be causing this?

---

### Post by richpri on 2012-08-20
Sounds to me like a user rights issue.
First check the permissions and ownership on the executable.

```
rich@rich2:~$ ls -l /usr/bin/libreoffice
lrwxrwxrwx 1 root root 34 Aug  7 19:44 /usr/bin/libreoffice -> ../lib/libreoffice/program/soffice
rich@rich2:~$ ls -l /usr/lib/libreoffice/program/soffice
-rwxr-xr-x 1 root root 6168 Aug  7 15:23 /usr/lib/libreoffice/program/soffice
rich@rich2:~$ 

```

The final x must pe present on both files.

---

### Post by peterson43 on 2012-08-20
> **richpri said:**
> Sounds to me like a user rights issue.
First check the permissions and ownership on the executable.

```
rich@rich2:~$ ls -l /usr/bin/libreoffice
lrwxrwxrwx 1 root root 34 Aug  7 19:44 /usr/bin/libreoffice -> ../lib/libreoffice/program/soffice
rich@rich2:~$ ls -l /usr/lib/libreoffice/program/soffice
-rwxr-xr-x 1 root root 6168 Aug  7 15:23 /usr/lib/libreoffice/program/soffice
rich@rich2:~$ 

```

The final x must pe present on both files.

I checked with my computer and got essentially the same output as you
```

jonpeterson@laptop:~$ ls -l /usr/bin/libreoffice 
lrwxrwxrwx 1 root root 34 Aug  7 20:44 /usr/bin/libreoffice -> ../lib/libreoffice/program/soffice
jonpeterson@laptop:~$ ls -l /usr/lib/libreoffice/program/soffice
-rwxr-xr-x 1 root root 6168 Aug  7 16:23 /usr/lib/libreoffice/program/soffice

```

---

### Post by richpri on 2012-08-20
The problem is that there are many files that could be messed up and cause this kind of problem.  Perhaps a Libreoffice expert will reply with more help.

Try creating another user and see whether it can access the ap.

As a last resort you could try reinstalling the application.

---

### Post by peterson43 on 2012-08-20
> **richpri said:**
> 
As a last resort you could try reinstalling the application.

I already tried uninstalling and reinstalling LibreOffice Calc and that didn't seem to work. Maybe I need to shut the computer down before I reinstall or maybe I need to uninstall the whole LibreOffice suite, but I suspect that wouldn't work either. There seems to be something else mixed up, but I don't know what.

---

### Post by richpri on 2012-08-20
One last suggestion. Check the logs. Try 

sudo rgrep -e Libre /var/log

Good luck.

---

### Post by peterson43 on 2012-08-21
> **richpri said:**
> One last suggestion. Check the logs. Try 

sudo rgrep -e Libre /var/log

Good luck.

Okay, I tried that command in a terminal and got the following
```

jana@laptop:~$ sudo rgrep -e Libre /var/log
[sudo] password for jana: 
/var/log/auth.log:Aug 21 06:45:46 laptop sudo:     jana : TTY=pts/3 ; PWD=/home/jana ; USER=root ; COMMAND=/usr/bin/rgrep -e Libre /var/log

```

---

### Post by The Cog on 2012-08-21
You could try removing all the libreoffice settings for the misbehaving user. Try this command to rename the folder with all the settings in it:
```
mv .config/libreoffice .config/libreoffice-old
```
and then start libreoffice again. 

If it starts then it's something in the settings that is causing the problem. You might as well delete the bad settings folder and just reconfigure from scratch:
```
rm -rf .config/libreoffice-old
```

If it still won't start, then I'm out of ideas and you may as well put the settings folder back:
```
mv .config/libreoffice-old .config/libreoffice
```

---

### Post by peterson43 on 2012-08-21
I tried moving the .config/libreoffice folder, but that didn't seem to solve anything. 

I finally fixed it by removing ALL of the LibreOffice programs in Ubuntu Software Center, restarting the computer, and then reinstalling the entire LibreOffice suite. Somehow that seemed to fixed it.

---

### Post by abriano on 2012-09-25
I just thought that I'd narrate my experiences here. I had the same problem as the thread originator (peterson43). I couldn't start any LibreOffice program. When clicked, the LibreOffice icon would just blink and then nothing would happen. The problem seemed to begin when I tried to open a Microsoft Office document that I had saved from our municipality's website. (I have previously opened the document without incident.) The other three other users on the computer could use LibreOffice, but I couldn't.

I tried peterson43's solution of deleting LibreOffice, rebooting, and reinstalling it, but that didn't change anything: the experiences remained the same for all users.

I then tried the solution offered by poster #7, The Cog, typing mv -rf .config/libreoffice .config/libreoffice-old and that worked (I did have to use sudo to remove that directory and its subdirectories).

So everything is fine now. 

I might mentioned that I exchange many LibreOffice documents with Windows users (texts and spreadsheets), though I always save the documents as Microsoft Office documents before I send them to others.

Many thanks for the postings! I appreciate them very much.

Brian

---

### Post by flocke77 on 2012-11-30
I had the very same problem here under kde and it turned out by dmesg to be a crash in 'libpolyester'. After 

sudo apt-get remove kde-style-polyester

(whatever this one user neededthe package for), it worked again.

---

### Post by ramsrom on 2013-04-26
I checkt program status with

```
ps -aux | grep libre
```

There I found oosplash --writer refering to some documents which were not open.

... then

```
sudo killall oosplash
```

Solved it form me.

---

### Post by andrew.gilbert on 2014-02-15
LibreOffice is important enough to me that I am actually replying here.

The solution for using the mv command worked.

```

drew@hightech:~$ sudo mv .config/libreoffice .config/libreoffice-old
[sudo] password for drew: 
drew@hightech:~$ ls .config/
akonadi    eog                 goa-1.0  libreoffice-old  software-center  ubuntuone
autostart  file-roller         gtk-2.0  menus            synaptiks        update-notifier
compiz-1   gedit               ibus     mousepad         totem            user-dirs.dirs
dconf      gnome-disk-utility  kde.org  nautilus         transmission     user-dirs.locale
enchant    gnome-session       Kitware  session-state    Trolltech.conf

```

it seems like something in the config files gets botched, but when they disappear, the software has to rebuild them from scratch.  

So, great idea, The Cog!  This post just saved me a ton of work!

---

