---
title: "backing up your distro"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by dougbooyens on 2008-10-30
Hi community,

I am absolutely 100% new to Linux. I have just installed Ubuntu 7.04 form a LINUX FORMAT MAG DISTRO and have downlaoded all the updates, I would however like to update to 7.10. My Question is how (if possible) do I go about making a backup / copy of my installed distro (with all the updates) just in case something goes wrong?
Thanks, Douglas

---

### Post by clancymf on 2008-10-30
Do you mean 8.10?  Today is that day that everyone is upgrading from 8.04 to 8.10.  Although, you can stick with 8.04 since it has long term support (LTS).  

Just make sure that your /home folder is backed up to either seperate drive, DVD, etc and then download the version you wanna upgrade to or use the upgrade function in Ubuntu but you will have to go from 7.04 to 7.10 to 8.04 to 8.10 so you are better just starting over.

You can use k3b to burn a data disk or if you have a seperate drive you can copy using the gui or there google command line backup as I dont know the code off the top of my head that compresses the data.  I cant imagine if you are new that you will have enough in the /home folder to copy.

---

### Post by dougbooyens on 2008-10-30
Its definitely 7.04 to 7.10, I'll hang back until everything is running smoothley!

---

### Post by cozmicharlie on 2008-10-30
I agree with clancymf - if you just installed it you probably don't have enough to worry about backing up.  You certainly should not have changed many settings so the only concern is your home folder (where your personal files are located) so all you need to do is back them up as clancymf suggested.  Just for future information though there is a nice utility that automates the backup.  It's called Quickstart and you can read about it here ([http://lifehacker.com/5064373/quickstart-configures-your-ubuntu-system-without-terminal-work](http://lifehacker.com/5064373/quickstart-configures-your-ubuntu-system-without-terminal-work).  There are lots of ways to back up in Linux but Quickstart will make it very easy - perfect for someone just starting with Linux.

Enjoy

---

### Post by mapes12 on 2008-10-30
Here you go:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

And best practice is to setup your HDD with diferent partitions for:

/root - this is where your OS files sit and where you can tinker around all you like with different versions of Ubuntu
/home - for the stuff you want to keep inc bookmarks, personal settings etc and other things like that.
swap - the partioner will take care of this one

Set up the partions with  GParted CD (Google it) to set up the partions.

---

### Post by bhadotia on 2008-10-30
You can use the sysres program([Sysres]("http://http://sourceforge.net/projects/sysres")). I advise this because I used it once and found it to be quite simple and powerful. If you are new then you are best off with this program. Especially backup your /var/cache/apt/archives/ directory , because it contains all the cached installation files(.deb) of your updates (if you did not remove them manually through synaptic). By default it will backup places like the system configuration directory (/etc) etc. but you can easily manipulate it to include the above directory or any other directories.

I myself, out pure habit use grsync ([(How to)]("http://theaddicted.wordpress.com/2008/05/12/how-to-backup-ubuntu/")).

But of course, there are other options that other users follow -advanced users use CLI tools like rsync, rdiff-backup, those comfortable with GUI use the likes of [Pybakup]("http://digiwanderlust.blogspot.com/2008/05/howto-backup-and-restore-configuration.html").

Lastly (and importantly), if you find all this to be way to much advanced just copy all your .deb files in /var/cache/apt/archives to a cd  (either manually or using [APTonCD]("https://wiki.ubuntu.com/APTonCD") )because that's where all the files required for the installation of the updates are (if you did not manually delete them). And then if something does go wrong restore those files to their original place (/var/cache/apt/archives) as root (using the 'sudo cp' command or the file browser bought up by the command :'gksudo nautilus'). Then you can reinstall your system and install the updates without having to download them again.

---

### Post by dougbooyens on 2008-10-30
Thanks! sounds fantastic, I'll give it a try.

---

### Post by Bakon Jarser on 2008-10-30
I prefer remastersys.  Very easy to use and you can make distributable live cd's or backups with your personal data on it.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by dougbooyens on 2008-11-03
Thanks for all the help! Now have a live CD of my UBUNTU 7.04 and I have 7.10 running on my system.
Douglas

---

### Post by Bakon Jarser on 2008-11-04
> **dougbooyens said:**
> Thanks for all the help! Now have a live CD of my UBUNTU 7.04 and I have 7.10 running on my system.
Douglas

For other people that find this thread and want to back up their system which method you ended up using and was it easy for you?

---

