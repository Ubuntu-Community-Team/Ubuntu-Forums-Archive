---
title: "Possible probelms with new glib2.0 2.29.4-0ubuntu1"
date: 2011-06-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-08
Please be carefull if upgrading the glib2.0 package.

The new version (2.29.4-0ubuntu1) does not work with the recent package
glib-networking (2.28.7-1).

1. The system shows you do not have a network connection, even though you have one.

2. Also the power off (reboot, power-off) does not work, they freeze the system.
Sysrq REISUB works.

---

### Post by sparker256 on 2011-06-08
> **Harry33 said:**
> Please be carefull if upgrading the glib2.0 package.

The new version (2.29.4-0ubuntu1) does not work with the recent package
glib-networking (2.28.7-1).

1. The system shows you do not have a network connection, even though you have one.

2. Also the power off (reboot, power-off) does not work, they freeze the system.
Sysrq REISUB works.
Do you have a workaround to back up a revision? I did a ctrl+alt+F1 then did a sudo reboot after logging in. I have a hard time remembering the other way :D

Logout looks like it is broken also.

Bill

---

### Post by sparker256 on 2011-06-08
Fixed a bug report against this.

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/795203](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/795203)

Bill

---

### Post by sparker256 on 2011-06-08
Do not know if related but in terminal I used to be able to scroll through previous commands with the arrow up and down. Now it gives me a screen shot dialog box.

Bill

---

### Post by mc4man on 2011-06-08
> **sparker256 said:**
> Do not know if related but in terminal I used to be able to scroll through previous commands with the arrow up and down. Now it gives me a screen shot dialog box.

Bill
Seems to  do that also (reverted back here to previous

---

### Post by sparker256 on 2011-06-08
> **mc4man said:**
> Seems to  do that also (reverted back here to previous
I looked at un installing to reinstall but looked like it would break to many things. Is there a better way?

Bill

---

### Post by mc4man on 2011-06-08
> **sparker256 said:**
> I looked at un installing to reinstall but looked like it would break to many things. Is there a better way?

Bill
To revert, (downgrade),  you'd need to grab the previous package or in this and many cases the set of packages.
You'd place them in a folder, cd to the folder and run
```
sudo dpkg -i *.deb
```

(in some cases the 'data' and or 'doc' packages don't have to be downgraded though I usually do anyway.

To give you an example here - for 32 bit install
[https://launchpad.net/ubuntu/oneiric/+source/glib2.0](https://launchpad.net/ubuntu/oneiric/+source/glib2.0)

Under "Releases in Ubuntu " pick the version you want - in this case the middle one
[https://launchpad.net/ubuntu/+source/glib2.0/2.28.8-0ubuntu1](https://launchpad.net/ubuntu/+source/glib2.0/2.28.8-0ubuntu1)

 pick the arch you want under "Builds" 
[https://launchpad.net/ubuntu/+source/glib2.0/2.28.8-0ubuntu1/+build/2555962](https://launchpad.net/ubuntu/+source/glib2.0/2.28.8-0ubuntu1/+build/2555962)

Under "Built files" you'll see 8 packages listed, pick all the ones you need and download into a folder (in your case likely #'s 1, 4, 5, and 7 listed.
 Only add a -dev package to the group if it's already installed, otherwise you'll get broken packages from dpkg
(I just drag & drop the links into a folder created for this, easier and quicker

So because _I do have_ the dev package installed this is the list I grabbed
> :~/Desktop/glib$ ls
libglib2.0-0_2.28.8-0ubuntu1_i386.deb
libglib2.0-bin_2.28.8-0ubuntu1_i386.deb  
libglib2.0-data_2.28.8-0ubuntu1_all.deb  
libglib2.0-doc_2.28.8-0ubuntu1_all.deb

libglib2.0-dev_2.28.8-0ubuntu1_i386.deb


---

### Post by sparker256 on 2011-06-08
> **mc4man said:**
> To revert, (downgrade),  you'd need to grab the previous package or in this and many cases the set of packages.
You'd place them in a folder, cd to the folder and run
```
sudo dpkg -i *.deb
```

(in some cases the 'data' and or 'doc' packages don't have to be downgraded though I usually do anyway.

To give you an example here - for 32 bit install
[https://launchpad.net/ubuntu/oneiric/+source/glib2.0](https://launchpad.net/ubuntu/oneiric/+source/glib2.0)

Under "Releases in Ubuntu " pick the version you want - in this case the middle one
[https://launchpad.net/ubuntu/+source/glib2.0/2.28.8-0ubuntu1](https://launchpad.net/ubuntu/+source/glib2.0/2.28.8-0ubuntu1)

 pick the arch you want under "Builds" 
[https://launchpad.net/ubuntu/+source/glib2.0/2.28.8-0ubuntu1/+build/2555962](https://launchpad.net/ubuntu/+source/glib2.0/2.28.8-0ubuntu1/+build/2555962)

Under "Built files" you'll see 8 packages listed, pick all the ones you need and download into a folder (in your case likely #'s 1, 4, 5, and 7 listed.
 Only add a -dev package to the group if it's already installed, otherwise you'll get broken packages from dpkg
(I just drag & drop the links into a folder created for this, easier and quicker

So because _I do have_ the dev package installed this is the list I grabbed

Thank you Thank you Thank you   

I am going to lock them at this version for the time being.

ps. got the i386 working but the amd64 build is broken. Trying to build my own but no luck so far but still trying.

Bill   \\:D/

---

### Post by ronacc on 2011-06-08
thanks for the warning .

---

### Post by sparker256 on 2011-06-08
Until I can get something built or find a 64bit build I had to go back to 2.28.6. A few issues but at least all the issues that 29 caused are not present. Time for bed.

Bill

---

### Post by mc4man on 2011-06-09
> amd64 build is broken
Go back to the first O version for amd_64 - glib released twice today (or there-abouts), this was the version prior to today
[https://launchpad.net/ubuntu/+source/glib2.0/2.28.6-0ubuntu1](https://launchpad.net/ubuntu/+source/glib2.0/2.28.6-0ubuntu1)

(same deal to downgrade

Edit: - I guess you got it...

---

### Post by Harry33 on 2011-06-09
> **sparker256 said:**
> Fixed a bug report against this.

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/794761](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/794761)

Bill

Yes, that is fine.

---

### Post by Quackers on 2011-06-09
I seem to have 2.29.4-0ubuntu1 packages installed already. When did that happen? Latest version appears to be 2.29.6-0ubuntu1. 
As I'm not sure when they got installed I daren't reboot now :-)

---

### Post by ronacc on 2011-06-09
probably with yesterdays update , refresh your sources and update again , 2.29.6-Oubuntu1 is now in , hopefully that fixes it , updating now .

---

### Post by Quackers on 2011-06-09
Ok thanks ronacc, will do.

Actually, I just had occasion to run sudo update-grub and I got a very strange output! The only OS that's missing is Windows Vista.
Could this be connected, do you think?
```
ocelot2@ocelot2-VGN-AR51SU:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-3-generic
Found initrd image: /boot/initrd.img-2.6.39-3-generic
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

Found Ubuntu 11.04 (11.04) on /dev/sdb6
Found Ubuntu oneiric (development branch) (11.10) on /dev/sdb8
done
ocelot2@ocelot2-VGN-AR51SU:~$ 

```

---

### Post by lucazade on 2011-06-09
> **Quackers said:**
> Ok thanks ronacc, will do.

Actually, I just had occasion to run sudo update-grub and I got a very strange output! The only OS that's missing is Windows Vista.
Could this be connected, do you think?
```
ocelot2@ocelot2-VGN-AR51SU:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-3-generic
Found initrd image: /boot/initrd.img-2.6.39-3-generic
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

Found Ubuntu 11.04 (11.04) on /dev/sdb6
Found Ubuntu oneiric (development branch) (11.10) on /dev/sdb8
done
ocelot2@ocelot2-VGN-AR51SU:~$ 

```

weird output...
have you tried also "sudo os-prober " ?

---

### Post by ronacc on 2011-06-09
I don't know , I haven't updated grub from oneric lately , I've got multiple installs and am booting off of Lubuntu's grub bight now .I rebooted after updating libglib and wireless and scrolling of terminal previous cmd's are both ok .

---

### Post by Quackers on 2011-06-09
Sudo os-prober gave the same result.

Please ignore me. I'm a stupid duck! It must be a while since I rebooted. In an all-nighter two days ago I edited mtab to try something. I forgot about that particular experiment! I just ran sudo rm /etc/mtab~ and everything is fine now.

Completely unrelated to glib updates.

Thanks for the update ronacc!

---

### Post by ronacc on 2011-06-09
I don't know if that is what did it , I only let any of my installs mount its own / and /home at boot and they seem to find all of my other installs (most of the time lol ) . As I said I have multiple installs 6 drives and a large and constantly varying amount of partitions so any thing else would be a huge zoo :p not I do not have windows on any of my boxes I am an MS hater .

---

### Post by Quackers on 2011-06-09
I know what you mean :-)
I need the unmentionable OS to play Blu-Ray discs, I'm afraid to say. (Until something more permanent appears in Linux :-) ).

---

### Post by sparker256 on 2011-06-09
> **ronacc said:**
> probably with yesterdays update , refresh your sources and update again , 2.29.6-Oubuntu1 is now in , hopefully that fixes it , updating now .
Bug report says 2.29.6-Oubuntu1 still broke.

Bill

---

### Post by Quackers on 2011-06-09
Hmm in what respect? Seems fine here so far. Certainly I've got wireless icon showing and connected ok.

---

### Post by dino99 on 2011-06-09
still broken on wire (eth0):
- but can download

strange thing is firefox refuse to load (silent crash)

---

### Post by ronacc on 2011-06-09
I'm not seeing that here with liglib-2.29.6-0ubuntu1 installed , wired and wireless both working , bash completion ok both old and newly entered cmds , maybe the problem is not glib this time .

---

### Post by sparker256 on 2011-06-09
> **ronacc said:**
> I'm not seeing that here with liglib-2.29.6-0ubuntu1 installed , wired and wireless both working , bash completion ok both old and newly entered cmds , maybe the problem is not glib this time .
After testing a updated liglib-2.29.6-0ubuntu1 on one of my usb startup disks and all was fine I then  updated my 11.10 64bit install. All the previous problems seem to be fixed. I still need to test lightdm and that will be my next test.

Bill

---

### Post by ronacc on 2011-06-09
that probably explains it , seeing harry's warning yesterday I had held off on updating until I saw a new version of libglib was available then "marked all updates" in synaptic and did so .

---

### Post by sparker256 on 2011-06-09
> **ronacc said:**
> that probably explains it , seeing harry's warning yesterday I had held off on updating until I saw a new version of libglib was available then "marked all updates" in synaptic and did so .
lightdm will break it I am going to start a new thread.

Bill

---

### Post by ronacc on 2011-06-09
doy you want to start a new bug on that ? if so I'll confirm . I re-configured for lightdm and rebooted networking disabled for both wired and wireless , scrollback ok .

---

