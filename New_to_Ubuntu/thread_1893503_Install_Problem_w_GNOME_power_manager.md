---
title: "Install Problem w/ GNOME power manager"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by antoiner_roquentin on 2011-12-10
I updated a bunch of packages using the update manager and restarted. Now, I get this error:

Install Problem!

The Configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your computer administrator.

I cannot open a terminal in order to use sudo apt-get and just get rid of the package for Gnome Power Manager. None of my input devices work, I have no mouse and the keyboard will not work at all, so I can't seem to do anything.

I'm using 10.04, but I really might be just going back to Windows because every time I turn around it's something new going wrong with one of my computers. I am super busy and don't have hours to spend trying to make them work once or twice a week.

What a headache.

---

### Post by yeats on 2011-12-10
Sounds like something interrupted your upgrade.  Try the steps in this thread (which is older, but still relevant):

[http://ubuntuforums.org/showpost.php?p=6685367&postcount=7](http://ubuntuforums.org/showpost.php?p=6685367&postcount=7)

---

### Post by antoiner_roquentin on 2011-12-10
Thank you, I will try this and post my results/steps in resolving this.

---

### Post by antoiner_roquentin on 2011-12-10
I am at a recovery shell trying to use the commands in the other post.

I tried apt-get install -f and I got:

W: Not using locking for read only lock file var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

I entered: sudo dpkg --configure -a
and Got:  dpkg: unable to accred dpkg status area: read-only file system

So, how do I change it from a read only file system?

---

### Post by antoiner_roquentin on 2011-12-10
I successfully logged into my netbook from the root command line thinking that perhaps it would grant me power to write to the drive. Sadly, I am getting the same results when actually logged into ubuntu through the terminal. 

I tried to use the command "mount" and this is what I got:

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem). It's possible that information reported by mount (8) is not up to date. For actual information about system mount points check the /proc/mounts file.

When I try to access location /proc/mounts it says permission denied.

---

### Post by antoiner_roquentin on 2011-12-11
Ok, new update as I try to fix this today.

I cannot even seem to get back into the recovery shell, which I accessed yesterday by using the manual recovery option when the fsdsk was checking the disk for errors. The OS loads the login screen, where I get the same "Install Problem - GNOME Power Manager default settings have not been installed properly. Etc."

From here I can do nothing. I have no mouse and no keyboard access on my netbook. It's like the OS just turns it off as soon as it loads the login screen.

I'm delving through all kinds of articles but without being able to actually access a terminal there's nothing I can try. There has to be someone out there who can help me or who has experienced similar problems.

---

### Post by antoiner_roquentin on 2011-12-11
Am going to try using Ubuntu Rescue Remix with a persistent home on a USB flash drive to see if I can use the shell there to issue commands.

---

