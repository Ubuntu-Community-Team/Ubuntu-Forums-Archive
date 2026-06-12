---
title: "Bored with Windows now trying Ubuntu"
date: 2016-11-26
forum: New to Ubuntu
---

### Post by pdstead2 on 2016-11-26
Hi

I've been using windows for numerous years and now I'm getting bored with the OS and now I want to try Ubuntu.

All I'm doing with windows is using it to back up everything (Films Music Personal Files etc etc ) I have on all my NAS drives using a piece of software called ASCOMP SYNCHREDIBLE.  Inside the windows PC I have 4 x 1TB drives in which 3.6TB is Spanned and the remaining space is the operating system.

What I want to do is use Ubuntu to back up everything just like the PC is doing now. However, I do not know how to do the following.

1) Span the drives I have as I expect that when I install Ubuntu these drives will become separated thus making 3 separate 1TB drives
2) Install some backup software which will run and backup everything 
3) Get Ubuntu to see my 4 NAS Drives

I was thinking of using Ubuntu Server but as the PC has 8gb RAM its a waste of RAM therefore I was thinking of using Ubuntu 16.04 and at least I'll have use fo a decent GUI screen and internet.

I would welcome any support but please bare in mind I'm very new to Ubuntu so please don't get too complicated.

Many thanks

Paul Stead

---

### Post by ian-weisser on 2016-11-26
Advice: Start with Ubuntu in a Virtual Machine on your current system. Windows power-users sometimes unintentionally trash their first Ubuntu attempt (and their data) - their advanced Windows skills lead them astray.

Learn how to use Ubuntu - how to install and remove software, accounts, and permissions, before touching your data.
Learn how to use the [Ubuntu]("https://help.ubuntu.com/") [Wikis]("https://wiki.ubuntu.com/"), which explain how to "span the drives" (RAID, LVM), how to backup, and how to mount drives from the network.

---

### Post by DuckHook on 2016-11-26
Welcome to Ubuntu, Linux and the Forums, pdstead2

I have run across many reasons for wishing to switch to Linux, but boredom with Windows is seldom one of them. The Linux learning curve can be steep, especially for the sort of ambitious goals you have set for yourself. Boredom is a rather weak motivator for the sort of perseverence that you will need. But you are best positioned to determine your own level of commitment.

You  have asked a number of questions requiring rather complicated answers. I encourage you to start with the link in my sig: "Linux is not Windows", followed by my link to backing up: "BACKUP FIRST". The important one is the first; most new users coming from Windows tend to bring along their Windows preconceptions, which makes the transition harder than it needs to be.

The short answers to your questions are as follows:

[LIST=1]
[*]I don't know anything about how Windows spans disks. However, I suspect that Linux will have problems reading your currently spanned disks without special drivers (which may not even exist) because Windows likely uses proprietary technology to span them. Linux has many ways to do this too, from software RAID to Logical Volumes. For general users, RAID is far too needlessly complicated and the best option is an LVM. However, all disk spanning makes your system more brittle since one failed disk breaks the whole volume. The tradeoff for convenience is increased fragility.
[*]There are a multitude of backup apps and strategies in Linux, and everyone has their favourites. As a new Linux user, I would recommend starting with the backup app in my sig (if for no other reason than the fact that deja dup is already included as part of a standard install), then exploring other options once you are already backing up.
[*]Ubuntu will likely see your existing NAS drives right out of the box because it is designed to see standard Windows networked drives without further fiddling. Of course, if your NAS is *not* standard, then the above is inapplicable.
[*]
[/LIST]
The most problematic part of your thread is your wish to install a GUI onto a server. Many new users resort to a GUI because they are allergic to the command line. This is certainly a valid concern and I have long since made my peace with this very legitimate need. However, it is worth stating that the server philosophy behind Linux is historically and strongly command-line-only, not just for reasons of power and efficiency, but mostly for the sake of security. A GUI adds an incredibly large footprint onto a server, all of which also becomes an inviting attack surface. Server admins are some of the most security-conscious people around, and they do not want any more attack surface than absolutely necessary. As a side note, Linux makes excellent use of all available resources and your RAM will not be "underutilized" (though your CPU might be).

Last but not least, don't hesitate to ask questions on these forums. We are here to help. However, if inquiring, break your questions down to one per thread. It is easier to help dealing with one clear question at a time.

Good luck and Happy Ubuntuing!

---

### Post by RobGoss on 2016-11-26
Hello and welcome to the forum, I would recommend reading as much as you can about Linux in general it's a learning factor but yet very intriguing. Most new using have trouble migrating over to Linux just because it was not what they expected

I'm not sure if you already tried the live media yet but it will give you a running desktop and you can see how well it performs on your machine that way you know what you'll be getting your self into. Ubuntu it a great OS it has tons of great applications for just about anything you will need for a everyday desktop environment 

I would not trash your Windows OS just yet until you're sure it's a move you will be happy with that way there's no lose if you decide it's not your cup of Ubuntu. I think you find these forums very helpful in your process most of the people here are always willing to help you will all your questions

You can find some** helpful documentation** in my **sig **that can be of importance 

Best of luck with your new venture

---

### Post by mastablasta on 2016-11-28
8 GB ram is not that much if you go with ZFS and plan on doing plenty of data transfers.

4 drives spanned on a backup is realyl not a good idea. as mentioned one drive suddenly stops working - all data is lost.

---

