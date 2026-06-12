---
title: "Yet another root/sudo thread - sudo cd lost+found"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by NaN010101 on 2012-03-27
I didn't want to hijack BlueScientist's thread so here's yet another  root/sudo thread. I've used the search box but didn't really find my answer.. so..

I've gone through about 6 hours of CBT videos on Linux from 10 years ago and it's time to get my hands dirty on the Ubuntu 10.11 VM I've got installed.

I manage to cd all the way up to / (I assume because "user" is an admin I am not stuck at /home/user).. I do an "ls /" and see the dirs from my videos in addition to one called lost+found.. cool! .. I "cd lost+found" and I get "permision denied".. alright.. after the replies to last nights question I try "sudo cd lost+found".. I get asked for my password then "cd: command not found". What to heck? 

I try ls -l from / and see the entry for lost+found (and root's home dir as well) are different than /lib, etc. I try a "sudo ls lost+found -la" and I can see there's nothing but the . and .. entries there, but now I'm wondering about root's home directory.. same thing.. apparently I am forbibben from writing to the .bashrc and .profile files there..

This is like the first time you try to look at C: in windows and it tells you it's hidden.. Who to heck is the OS to tell ME what I can and can't do on my own machine?

My question is: Are these going to be the only 2 things/places that Ubuntu (in it's infinite wisdom) is going to forbid me from accessing or am I going to be hitting this elsewhere as well (if I don't cut my losses).

TIA

---

### Post by Azdour on 2012-03-27
Hi,

I think you should be able to find the answer to your first question here:

[https://answers.launchpad.net/ubuntu/+question/3656](https://answers.launchpad.net/ubuntu/+question/3656)

---

### Post by SeijiSensei on 2012-03-27
I'm not sure why "sudo cd lost+found" returns a "command not found".  Try running "sudo su -" and you'll get a root prompt (the hash mark #). Now you should be able to use "cd /lost+found".  There shouldn't be anything in there, though, and you should hope nothing ends up there.  lost+found contains orphaned file fragments that are collected if you run the fsck command on a filesystem with errors (think "chkdsk" in Windows parlance).  Once you're done looking around, type "exit" at the prompt to return to your own account.

The administrative user, root, has a home directory just like all other users called /root.  (Ordinary users have home directories under /home.)  Only root can read and write to this directory for security reasons, just as, on Ubuntu, users can only read and write in their own home directories.  These limitations can be changed by changing the "[permissions]("https://help.ubuntu.com/community/FilePermissions")" on these directories, but I wouldn't do this until you have lot more experience with Linux.

Remember that Unix is, by nature, a multiuser system so there are lots of restrictions on what ordinary users can see or do.  Normal users can only write to /home/username and to /tmp; the root user can do anything, which is why Ubuntu puts strict limitations on being root.  It's quite possible to do serious damage to your OS and data running commands as root unless you know precisely what you're doing.

> Who to heck is the OS to tell ME what I can and can't do on my own machine?

As I said, it's possible for you to do anything you want on your machine.  Ubuntu tries to protect you from doing stupid or dangerous things.

---

### Post by dfreer on 2012-03-27
Yes, that link is correct.

If you really want to explore your filesystem, use a root session as mentioned in that link and then browse away with root permissions.

---

### Post by NaN010101 on 2012-03-27
>  Ubuntu tries to protect you from doing stupid or dangerous things. Did microsoft's patent on that approach finally expire?

(Oh.. and THANKS! for the link(s).. I'm just cranky this morning )

---

### Post by Paddy Landau on 2012-03-27
> **NaN010101 said:**
> Who to heck is the OS to tell ME what I can and can't do on my own machine?
The master!

Just as a motor car won't allow you to go into reverse while driving forwards, and a very modern car will stop you from driving into a wall, the security model is there to stop you from doing something stupid.

Unlike a car, though, you can easily circumvent the security model by using sudo (or gksudo for GUI programs) and your password.

If you don't like the security model, install a distro of Linux that doesn't do this; for example, [Puppy]("http://puppylinux.org/"). But Puppy doesn't have the security model for the simple reason that it is tiny, and so you'll lose out on plenty of functionality.

---

### Post by NaN010101 on 2012-03-27
> ...  the security model is there to stop you from doing something stupid..I have learned many (if not most) of the things I know today BECAUSE I did something really stupid... : -)

I remember when Macs were fairly new and there was a Mac lab at university.. it took about 5 minutes for me to HATE the Mac because I had to "ask" the operating system if it would agree to give me my floppy back instead of just listening to tell when the OS was done with it then hitting the eject button..

Anyway.. again I have posted while annoyed.. I will type 500 times.. Take a breath, then post.. Take a breath, then post.. 

thanks

(@Paddy, that's not a pic of Vladimir Putin your sporting there is it?)

---

### Post by jerome1232 on 2012-03-27
Despite what others say, these things aren't actually there to stop you from doing something stupid, they are there to keep the programs you run from doing whatever they please to your system files with out you giving them your permission.


See the difference?

---

### Post by yetiman64 on 2012-03-27
> **NaN010101 said:**
> I have learned many (if not most) of the things I know today BECAUSE I did something really stupid... : -) ...
Glad you point that out :) As a warning from a new user and like yourself inquisitive about root use, be warned "Have Good Backups".

The less you do as root the better if you tend to "just explore" a system rather than doing in depth research into what you are doing first. It is possible to destroy a lot of data in split seconds as root, ouch, thanks for that memory :p .

Edit: Note link #4 in my sig OP.

---

### Post by Paddy Landau on 2012-03-27
> **nan010101 said:**
> (@paddy, that's not a pic of vladimir putin your sporting there is it?)
:lol: I hope I'm not that ugly!

---

