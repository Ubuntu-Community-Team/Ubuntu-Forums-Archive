---
title: "Can't start Gnome session, changed ownership of /etc by mistake"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Atin Bhattacharya on 2008-05-24
Hi, I'm a newbie at Linux and I'm running my computer on Ubuntu 7.10 and this is my first post ...

I mistakenly changed the ownership of /etc to my own username. As a result, I can only log into a failsafe terminal session. I can't even log into a Gnome failsafe session. Again, after the failsafe terminal session starts, my login is no longer valid. When I try to login from the terminal I'm asked to login from "sh", which also fails, giving a "sh: Can't open login" message.

When I try changing the ownership of /etc from the terminal:
sudo chown -R root:root /etc

... I get the expected error...

sudo: /etc/sudoers is owned by uid 1000, should be 0

Any help would be really appreciated.

---

### Post by Sarah L on 2008-05-24
I'm not sure if this will help, but try entering a root terminal by using ```
su -
```

If you're really stuck and can't restore functionality, boot from a LiveCD and edit your filesystem. This is risky and can severely damage your files if you mess up, but it's worth a shot if you're careful.

---

### Post by Atin Bhattacharya on 2008-05-24
Tried it. "su -" "su - atin" & "su atin" don't work. (My username happens to be atin)

I get permission denied errors for /etc/profile & /etc/bash.bashrc

I'd appreciate some information about what kind of "correction" my filesys needs. Or is there any other way?

---

### Post by morgan141 on 2008-05-24
As sarah said, one way to solve it should be to boot from a live cd. Mount your / partition and then run chown as you did on /etc/. Whether that will solve it I don't know but you don't have much to lose. I'd highly recommend you backup all your personal files before doing ANYTHING. You'll probably have to do this using the livecd.

If you're not sure how to do the above, then run 'sudo fdisk -l' from the terminal on the live cd. Have a look and see if you can recognise the partition with / on. Then input the following:

```

sudo mkdir /mnt/ubuntu
sudo mount /dev/<yourpartition> /mnt/ubuntu
sudo chown -R root:root /mnt/ubuntu/etc/

```

Best of luck

---

### Post by drs305 on 2008-05-24
Better answer below.

---

### Post by nsche on 2008-05-24
It looks like you not only changed the ownership of /etc but all the files under it.  What you really need is to set the ownerships to the correct one which is not root in all cases.  It looks to me as if all of the files should be root except /etc/cups, /etc/cups/ssl, /etc/cups/ppd and the files under /etc/cups/pppd.  These all appear to properly be cupsys:lp.

For the rest of the files you should do the following:
Boot the system from a "live" cd like the ubuntu install cd.
mount the root file system from your installed system onto some file like /tmp/mountpoint.  command would be: 
```
mkdir /tmp/mountpoint
mount /dev/sda1 /tmp/mountpoint
cd /tmp/mountpoint
chown -R root:root etc

```
After doing this make sure you bring the system down in an orderly manner using the halt from the menu.

Where I put sda1 you will have to put the disk and partition you installed ubuntu on.

If you try chown root:root /etc you will not work.  What you want to change when you are booted from the cd is hard disk not the /etc you are running with.

You might be better off reinstalling unless you have some important files on the system.

---

### Post by morgan141 on 2008-05-24
edit: Nevermind, my mistake. Mods feel free to delete this post.

---

### Post by Steve413z on 2008-05-24
try choosing recovery mode in GRUB then change the permissions

---

