---
title: "Permission Denied on imported folder"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Big Chris on 2008-10-11
Hi, could anyone help a new user of Umbuntoo Hardy Heron?
I have some back-up files from Windows (saved through Norton 360) which I want to import into Linux so I dragged them over and immediatly an orange padlock appeared above the folder and apart from opening it I can't do anything with it - I can't move it from the desktop to another folder or drag any of the contents out of it, I can't even put the thing into the bin, so it is stuck on my desktop - can anyone help?

---

### Post by SuperSonic4 on 2008-10-11
It would appear you have to be root to move it. You can either press alt+f2 and type ```
gksudo nautilus
``` navigate to it and delete/move/change ownership.

You can always chown (**ch**ange **own**er) it but I'm not sure of the code

---

### Post by Jaded Misanthrope on 2008-10-11
Navigating to the folder in question in the terminal (cd <pathname>) and typing in sudo chown <your username> * should shift file ownership to you and therefore allow you to move the folder as you like.

You may need to shift ownership of the actual folder to yourself as well, but that's just as easy:
cd <folder containing the folder you want to get>
sudo chown <your username> <folder name>

---

### Post by aysiu on 2008-10-11
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R $USER:$USER ~/Desktop
``` That will change ownership of all files and folders on your desktop to yours.

---

### Post by Big Chris on 2008-10-11
Hi

Thanks for the answers, but I am being very thick here.

The F2 gksudo keeps wanting to change just a file within the folder and not the folder.

And I am typing in terminal cd shared01 (shared01 is the name of the folder) and it keeps saying not found - what am I doing wrong?

---

### Post by Jaded Misanthrope on 2008-10-11
Try typing in the *full* pathname (i.e. not shared01 but, assuming the folder is on your desktop, ~/Desktop/shared01--of course, the pathname could be different. ~/ is shorthand for your home directory)

---

### Post by aysiu on 2008-10-11
Forget the typing and just *paste* in the command I gave you. It changes ownership recursively, so you don't have to change one by one on each file and folder individually.

---

### Post by Big Chris on 2008-10-11
Sorry Aysiu

I copy and pasted it in, but it didn't make any difference it just keeps saying 'permission denied'

HELP

---

### Post by Jaded Misanthrope on 2008-10-11
> **Big Chris said:**
> Sorry Aysiu

I copy and pasted it in, but it didn't make any difference it just keeps saying 'permission denied'

HELP

Try this exact sequence of commands (of course, replace the obvious fillers with the appropriate terms and bear in mind that I am assuming the folder is shared01 and on your desktop)

cd ~/Desktop/
sudo chown -r <your username> *

---

### Post by Kellemora on 2008-10-11
Hi Chris

I had a similar problem only earlier this week.  Couldn't figure out for the life of me what I did differently that caused it either.

After spending like 12 hours in ROOT using Nautilus to change most of the 600+ files I had moved.  
It finally dawned on me what I did wrong!

Made myself a BIG NOTE and taped it to my wall too!

It simply says NEVER PLACE document or folders on Another computer from your computer.  They get LOCKED!

Instead, make a shared folder an your computer first, THEN go draw those files or the whole folder FROM the originating computer from the computer you need them on.  This way they maintain their Permissions!

If you check, I'll bet every single file says "User NOBODY"  "Group NO ONE"

Folks here worked with me too for hours and we could never get the Folder and it's contents to have the correct permissions globally.

But by DRAWING the folder from the originating computer, all the permissions stayed exactly as intended, no more problems.

So, reload them on your Doze computer, make sure the permissions are how you want them.  Then go to your Ubuntu machine and Copy them over from the Doze machine.

If that's what you did and they still didn't work.  Then I'm even more lost than you.  And if it happens to me again, I'll be out of business, since everything vital is now running on Ubuntu.

TTUL
Gary

---

### Post by Big Chris on 2008-10-11
Hi The files came from a disk from this computer before I accidently wiped them all when I installed Linux so there is no way I can get to the original computer.

Does anyone know a way in which I can delete this folder or just get it off my desktop as I can't even move it at the moment?

---

### Post by handydan918 on 2008-10-11
Seems like it might be at least interesting to open a terminal and do ```
cd Desktop
```and
```
ls -l
```
just to see what that folder thinks it is....

---

### Post by handydan918 on 2008-10-11
> **Big Chris said:**
> Hi The files came from a disk from this computer before I accidently wiped them all when I installed Linux so there is no way I can get to the original computer.

Does anyone know a way in which I can delete this folder or just get it off my desktop as I can't even move it at the moment?

Yeah, that can be done, but it would involve using one of the politically incorrect sudo r* commands. We can't talk about those out loud.

---

### Post by Big Chris on 2008-10-11
Hi, Handydan918

Copied below, see what you think and the shared 01 (the problem file is in the colour blue)

christopher@christopher-desktop:~$ cd Desktop
christopher@christopher-desktop:~/Desktop$ ls -l
total 1600
-rw-r--r-- 1 christopher christopher 263952 2005-07-23 01:17 456.txt
-rw-r--r-- 1 christopher christopher  43840 2008-10-07 16:53 64a2_1.JPG
-rw-r--r-- 1 christopher christopher 593157 2008-09-25 17:15 Application For2.Home-start Andover and District.rtf
-rw-r--r-- 1 christopher christopher  64841 2008-09-25 17:15 Bank Details.pdf
-rw-r--r-- 1 christopher christopher 140288 2008-09-25 17:15 Home-Start Andover & District.doc
-rw-r--r-- 1 christopher christopher 118931 2008-09-25 17:14 Home-Start Andover & District.odt
-rw-r--r-- 1 christopher christopher 134656 2008-10-10 22:43 prog_reach_comms_opf.doc
-rw-r--r-- 1 christopher christopher  40785 2008-10-09 23:40 prog_reach_comms_opf.odt
-rw-r--r-- 1 christopher christopher 188496 2008-10-08 20:31 prog_reach_comms_opf.rtf
dr-xr-xr-x 2 christopher christopher   4096 2007-12-18 12:10 Shared 01
christopher@christopher-desktop:~/Desktop$

---

### Post by handydan918 on 2008-10-11
Try ```
chmod +w
``` since it looks like you are already the owner, all we need to do is set the write bit....

---

### Post by Big Chris on 2008-10-11
Hi

I can't get it to work please see below to where I am going wrong

christopher@christopher-desktop:~/Desktop$ chmod +w
chmod: missing operand after `+w'
Try `chmod --help' for more information.
christopher@christopher-desktop:~/Desktop$ chmod +wShared 01
chmod: invalid mode: `+wShared'
Try `chmod --help' for more information.
christopher@christopher-desktop:~/Desktop$ chmod +w Shared 01
chmod: cannot access `Shared': No such file or directory
chmod: cannot access `01': No such file or directory
christopher@christopher-desktop:~/Desktop$ chmod +w Shared01
chmod: cannot access `Shared01': No such file or directory
christopher@christopher-desktop:~/Desktop$ chmod +w  Shared 01
chmod: cannot access `Shared': No such file or directory
chmod: cannot access `01': No such file or directory
christopher@christopher-desktop:~/Desktop$  Shared 01
bash: Shared: command not found
christopher@christopher-desktop:~/Desktop$ chmod +w
chmod: missing operand after `+w'
Try `chmod --help' for more information.
christopher@christopher-desktop:~/Desktop$ chmod +wShared01
chmod: missing operand after `+wShared01'
Try `chmod --help' for more information.
christopher@christopher-desktop:~/Desktop$ Shared 01 chmod +w
bash: Shared: command not found
christopher@christopher-desktop:~/Desktop$

---

### Post by handydan918 on 2008-10-11
Oops. Forgot to specify the filename, which has spaces in it. Note the use of quotes below...

```
chmod a+w 'Shared 01'
```

---

### Post by Big Chris on 2008-10-11
Hi Handydan

A HUGE GREAT THANKS FOR THIS

The problem is now solved at last and just to make sure I tried it on another file and that works too.

---

### Post by handydan918 on 2008-10-11
> **Big Chris said:**
> Hi Handydan

A HUGE GREAT THANKS FOR THIS

The problem is now solved at last and just to make sure I tried it on another file and that works too.

Glad to hear it. For more info do ```
man chmod
```

---

### Post by Big Chris on 2008-10-11
Thanks again

---

### Post by bluebirday on 2008-10-11
I have the same problem since I need to copy fonts from windows font folder to Ubuntu font folder and I got the following message

Initializing nautilus-share extension
seahorse nautilus module initializedNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:8609): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root
--> file:///
--> file:///root/Desktop

(nautilus:8609): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 3 elements at quit time (keys above)

(nautilus:8609): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time
seahorse nautilus module shutdown

hope to help

---

### Post by maccawolf on 2009-03-19
NEver mind......

---

