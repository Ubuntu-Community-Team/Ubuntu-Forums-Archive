---
title: "Is it possible to run 2 Linux systems from the same Image?"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by Wiking on 2013-04-27
I have a laptop with ubuntu set up just the way I like it, instead of repeating the process of installing and customizing ubuntu on a desktop can I just restore an image from a laptop onto a desktop? Thus running the same installation on different computers.

---

### Post by Lars Noodén on 2013-04-27
All the settings specific to your account are in /home/wiking or whatever the username is.  These include the changes you've made customizing specific applications which you have run.  If you have more than one user on your system, you will have to copy the other users' files, too.  There will be a few 'hidden' directories there, too, for some apps.

All the global configuration settings are in /etc   You'll probably know if you messed with them.  If you did, just copy the directory.

For both of these, I would recommend using [tar](https://help.ubuntu.com/community/BackupYourSystem/TAR).  It's a very useful program in situations like this. 

If you have added or removed a lot of programs from the base installation, that is easy to track, too.  On the configured system you can make a list of what's changed:

```

dpkg --get-selections > /home/wiking/packages.txt

```

Then copy that file to your new system, load them in and have it deploy the changes:

```

sudo apt-get update
sudo dpkg --set-selections < /home/wiking/packages.txt
sudo apt-get dselect-upgrade

```

It should go rather easily.

---

### Post by pfeiffep on 2013-04-27
> **Wiking said:**
> I have a laptop with ubuntu set up just the way I like it, instead of repeating the process of installing and customizing ubuntu on a desktop can I just restore an image from a laptop onto a desktop? Thus running the same installation on different computers.

Not exactly answering your question because I have dis-similar systems, but I have successfully used [Remastersys]("http://www.remastersys.com/ubuntu.html") to back up and restore to a dvd both my laptop (32bit) and tower (64bit).

---

### Post by Wiking on 2013-10-05
So all I would need to do is get the list of packages, then install the list of packages using:

```
sudo apt-get update
sudo dpkg --set-selections < /home/wiking/packages.txt
sudo apt-get dselect-upgrade
```

And once all packages are installed I just need to copy paste the /etc folder and all applications will  be the same configuration?

Does that include desktop settings as well? 

thanks

---

### Post by Lars Noodén on 2013-10-05
All your desktop settings will be in your home directory /home/wiking/ also known as **~**  In  that directory you find all kinds of "hidden" files, those starting with dots, which will either be settings files or directories containing settings files.

---

### Post by heir4c on 2013-10-05
> **Wiking said:**
> I have a laptop with ubuntu set up just the way I like it, instead of repeating the process of installing and customizing ubuntu on a desktop can I just restore an image from a laptop onto a desktop? Thus running the same installation on different computers.

I have don something but a little bit different. 
I took a Hard Disk out of a old Laptop and plug it in a (newer) desktop and boot Ubuntu up. It work fine. No errors, no need to change a configuration.
So I think you can do.

---

### Post by oldfred on 2013-10-06
The issue can be proprietary drivers. Most often video as you may have one system on laptop and another on desktop. Also could be wireless but desktop may not even have that.

---

