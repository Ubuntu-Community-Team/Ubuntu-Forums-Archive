---
title: "Login as Root - ok it is a bad idea - an alternative specific to me please :-)"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by West Swan on 2013-04-10
Hello,

I have a computer repair business and have successfully completed (many years ago now) the Comptia A+ certification.

To recover files from hard drives that won't boot into Windows I previously used a different option but now have Ubuntu installed on my computer (Dual boot with Windows 7).

So I am an absolute beginner with Ubuntu.

So far I am happy with Ubuntu 12.04 as by attaching drives that won't boot into Windows anymore via a docking station I can access personal files and copy them onto my external drive.

I usually don't work with Apple computers at all but my Niece has one and I found that logging into Ubuntu as myself and then recovering her files requires more permissions than I have.

From what I understand I could login as root but a newby to Ubuntu like myself could screw things up :-)  So my question is how can I login as myself and then temporarily allow myself enough privileges to copy and paste my Nieces files to an external drive in advance of reloading OSX and copying the files back for her?

PS, getting used to a Command Line (I mean Terminal) again is quite a bit of fun.  Although requiring learning, it seems a lot more can be done this way :p

Cheers,

Paul

---

### Post by lisati on 2013-04-10
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ajgreeny on 2013-04-10
To read/write files on a mac formatted partition you will also need to install hfsplus and perhaps some other hfs packages, I think, but once you can mount the disks/partitions after that, you should manage to copy the files from the disk using sudo, just like any other files.

---

### Post by p-dh on 2013-04-10
If you *have* to login as root, just run the command:
[FONT=Courier New]sudo su[/FONT]

However, read the above referenced post as all of the warnings about working as root apply. I find that the 15 minute window for sudo is usually plenty of time. Or, if necessary, running a shell as root (as mentioned in the thread) does what I need to do.

Peace,
Paul :cool:

---

### Post by Toxic64 on 2013-04-10
You cuold go with the terminal.
don't log as root, use sudo + command (I guess you'd use the 'cp' command )  for privilege elevation during the commands execution in terminal

---

### Post by 3rdalbum on 2013-04-10
> **West Swan said:**
> So my question is how can I login as myself and then temporarily allow myself enough privileges to copy and paste my Nieces files to an external drive in advance of reloading OSX and copying the files back for her?

You can run a command as root by prefacing it with 'sudo', or you can run a graphical program as root using "gksudo".

Now, you want to copy a file, not exactly run a command or a program; but this is all interlinked. You can use the terminal to copy files, in which case you can use 'sudo':

```
sudo cp /media/MacOSX/* /media/Backup/
```

Or, to make it easier for yourself, you can run the standard file manager program as root by putting this into the terminal:

```
gksudo nautilus
```

(Nautilus is the file manager program)

Within the file manager window you've opened as root, you can copy the files.

---

