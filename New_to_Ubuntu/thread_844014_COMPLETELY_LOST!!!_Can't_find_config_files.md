---
title: "COMPLETELY LOST!!! Can't find config files"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by climb.colorado on 2008-06-29
Hello

I am trying to access all sorts of configuration files either to read only or modify but can't access anything!  

For example, I want to see my grub config files, Apache2 config. files, Qmail and sendmail config files, dhcp server config files...How do I figure out how to access all those I want?

In the terminal when I change the directory to /etc and then type in dir, I assume you are able to access files to each of these that are listed?

---

### Post by LuisGMarine on 2008-06-29
Forgive me for being dumb, but did you try to open those files with **[COLOR="Red"]root [/COLOR]**privileges?

All programs/files in /etc are owned by the system, meaning that only logged in as root can modify these files and do what ever it pleases.

try putting *sudo* before the file.  For example:
```

sudo gedit /etc/apt/sources.list
```

---

### Post by cariboo on 2008-06-29
Most of the config files are in /etc for example a directory listing of the /etc/apache2

```
jimk@intrepid:/etc/apache2$ ls -l
total 40
-rw-r--r-- 1 root root 10826 2008-06-25 07:50 apache2.conf
drwxr-xr-x 2 root root  4096 2008-06-26 16:49 conf.d
-rw-r--r-- 1 root root   378 2008-06-25 07:50 envvars
-rw-r--r-- 1 root root     0 2008-06-25 10:52 httpd.conf
drwxr-xr-x 2 root root  4096 2008-06-25 10:52 mods-available
drwxr-xr-x 2 root root  4096 2008-06-25 10:52 mods-enabled
-rw-r--r-- 1 root root    59 2008-06-25 07:50 ports.conf
drwxr-xr-x 2 root root  4096 2008-06-25 10:52 sites-available
drwxr-xr-x 2 root root  4096 2008-06-25 10:52 sites-enabled
```

the listings with d at the start are directories, as you can see they are all owned by root. The way to edit them is to use the sudo command eg:

```
sudo gedit /etc/apache2/apache2.conf
```

Hope this helps.

Jim

---

### Post by climb.colorado on 2008-06-29
Well, this is the problem...

I see all of the files in the /etc directory but when I type them in it says: 

ryan@ryan-laptop:~$ sudo /etc/fstab
[sudo] password for ryan: 
sudo: /etc/fstab: command not found

It says this for EVERY file...WTF?  Please help - I guess you can't log in as root in Hardy Heron - you can only use the sudo command

---

### Post by conscious on 2008-06-29
Don't try to run these files. Instead, edit them:

Read-only mode:
```
gedit /etc/fstab
```

With root permissions:
```
sudo gedit /etc/fstab
```

---

### Post by climb.colorado on 2008-06-29
How do I go about viewing my server and various email programs' configuration files.  Nothing specific, but a little knowledge could help out a ton.  Thanks

---

### Post by bigtony on 2008-06-29
First, do you know how to move around and view the file structure?

Do you know which files you're looking for and where they are?

Also, sudo /somefile will try to execute it as root.  If you're wanting to open a config file to change it's text, you give a command to open it with some text editor (like gedit) as root. Hence:

sudo gedit /some filepath

---

### Post by conscious on 2008-06-29
First of all, do you know what the config files you need are? If you do, just open them with Nautilus. If you don't, I think you should read the documentation (of mail program, apache, or anything).

---

### Post by twright on 2008-06-29
if you aren't comfortable with the terminal then webmin might be an easier way to configure your server

also for individual config files you can probable find them with a quick google search :KS

---

### Post by ramjet_1953 on 2008-06-29
An observation here, if I may?

If you are unsure of how to find configuration files that are system files, owned by root, you do not yet have the knowledge to be fiddling with them.

It is very easy to totaly trash your system by altering system files and I suggest that you do a bit more study on how Linux works and how to safely alter config files.

If you don't do this, it will only be a short period of time before you are back on these forums pleading for help to recover your system.

Learn to crawl, before you walk.

Regards,
Roger :cool:

---

### Post by climb.colorado on 2008-06-29
I'm really not looking to edit anything.  I just want to view them but many are saying the best way to view them is by opening them the gedit way.

---

### Post by Elfy on 2008-06-29
As long as you don't open them as root (sudo or gksudo) you won't cause any damage, that said if you open a file that lives in your /home, some config files are in there you don't need to be root to edit them as they belong to you.

You don't need to open them with an editor to see the contents of a file either :)

```
cat /etc/fstab
```

would show you the contents of that file without opening it for editing, if you do want to edit you can alo use nano which is an editor you can use in a terminal

```
sudo nano /file/path
```

Use Ctrl+O and enter to save, Ctrl+X to exit

Also get into the habit of making backups before you do edit them, then if you do trash something, you can overwrite the trashed file 

```
sudo cp /file/path /file/path.bak
```

although I use the date rather than bak so I end up with files I've changed having timestamp backups - xorg I believe does so anyway if you reconfigure but I was never sure. T use the backup to overwrite a trashed file

```
sudo mv /file/path.bak /file/path
```

---

