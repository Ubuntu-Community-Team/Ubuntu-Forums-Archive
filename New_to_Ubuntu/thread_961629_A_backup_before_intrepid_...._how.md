---
title: "A backup before intrepid .... how?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by bolex100 on 2008-10-28
What is the correct way to backup my system **and settings **before I take the leap to Intrepid?

I don't know how to install intrepid either, but that's another post.

---

### Post by dracayr on 2008-10-28
your settings and all your user information is in your home directory.. back that up (note: there are a lot of hidden files in your home directory. If you use nautilus (the file browser), press Ctrl+H to unhide them). You only have to make your user in intrepid having the same name as your current user. As for your system.. I guess you will have to re-install programs, to back them up, you would have to back up your entire system.

dracayr

---

### Post by Therion on 2008-10-28
Use [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11).  It's good for backups and lots of other stuff.

Be sure to READ the install instructions.  Very simple, but they need to be followed.

---

### Post by HighFrictionZone on 2008-10-28
Hrm. I could have sworn that there was a back-up feature built into Ubuntu. Might have been Kubuntu I was thinking of. Try messing around with tar. I'm pretty sure you can use TAR to backup your home directory and restore it in case of emergency. TAR is built into the system, but you'd have to figure out how to use it.

---

### Post by snova on 2008-10-28
Your personal program settings are stored in hidden directories inside your home folder. System-wide settings are placed in /etc.

Backup methods depend on the options available to you. I find an external HD is the simplest route, but what do you have available?

How are you planning to upgrade? A complete reinstallation or a full system update over the internet? The latter case shouldn't need a backup. (But make one anyway if you don't already have one, you never know.)

---

### Post by bolex100 on 2008-10-28
I was intending to backup to CD or DVD. Maybe even a SB memstick  There's not much data. Its the system that I'm interested in.

---

### Post by rickycodie on 2008-10-28
then go to your home folder and hit ctrl+h and copy over ALL of the files with a period in front of them. like .dmca or .mozilla.

this will NOT back up any of your personal files like music or videos.

---

### Post by rickycodie on 2008-10-28
whoops two posts, sorry!

---

### Post by Crafty Kisses on 2008-10-28
I just backup everything on a external HDD, the easiest way I think.

---

### Post by billgoldberg on 2008-10-28
Copy your entire /home directory (hidden files included).

After you installed it, paste the contents of them in the new home folder.

Override the new files if needed.

You will have to reinstall your apps.

--

I haven't actually done this, so I'm not 100% that will work or if it may provide issues.

---

### Post by louieb on 2008-10-28
A  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and **[partimage]("http://ubuntuforums.org/showthread.php?t=287522").**

---

### Post by k3lt01 on 2008-10-29
Do a search for making a LiveCD of your own system. You have a few options UCK (Ubuntu Customization Kit), Remastersys, and I think ISOMaster.

If your /home is a seperate partition you do not need to touch it unless you really want to format it for the new install. If it isn't seperate make sure you back it up so you can restore it later in Intrepid.

You can also do a search for Applications List which will bring up a few threads on how to restore the applications you are using if you have added more to your system from the standard repositories.

Hope this helps.

---

