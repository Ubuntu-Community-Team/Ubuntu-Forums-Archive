---
title: "[SOLVED] Package installer broken"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2008-04-30
Hi all,

Whenever I run synaptic or apt-get I get an error 
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

When I run the suggested command
```
sudo dpkg --configure -a
```
I get another error
```

Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

```

I don't know what to do next. BTW I wasn't upgrading. I enabled the backports and was updating several packages. Synaptic hung several times (I guess with all the hardy upgrades going on). Now it won't start.

Help please :)

Eric

---

### Post by bluefrog on 2008-04-30
you can have a look inside
/var/lib/dpkg/info
and
/var/lib/dpkg/status

may get rid of files inside and try again

---

### Post by frodon on 2008-04-30
Initramfs is the tools which handle your boot image so if it fails your kernel will indeed not boot except if you are lucky.
getopt packages seems not found so you should try to re-install the util-linux package which contain getopt :
```
sudo apt-get install util-linux
```Then update your system (if it works) :
```
sudo apt-get dist-upgrade && sudo apt-get update
```Then if this fail you will surely be asked to run the following command (again) :
```
sudo dpkg --configure -a
```

---

### Post by mano cazalet on 2008-04-30
take a look at [this]("https://answers.launchpad.net/ubuntu/+question/26400") entry. I hope it will answer your question

edit: oh frodon was quicker ;)

---

### Post by geeree on 2008-04-30
It seems like the problem is with initramfs-tools. The post-installation script that dpkg tried to run after updating the package gave that error. Now it will expect you to either finish that upgrade/installation manually or removing the package altogether. Maybe you should reinstall it manually? See a related thread: [http://ubuntuforums.org/showthread.php?t=604435](http://ubuntuforums.org/showthread.php?t=604435)

Girish.

---

### Post by frodon on 2008-04-30
This won't work if he miss the getopt package which seems to be the case here. I have seen this happen in the past for some users after some kernel updates.

---

### Post by nowhere@cox.net on 2008-04-30
In fact I cannot run any apt-get or synaptic functions so I cannot remove or install or fix any packages that way. I will review some of the other suggestions but in the meantime, any others?

Thanks,
Eric

---

### Post by nowhere@cox.net on 2008-04-30
OK I have some progress. I did
```
sudo mv /var/lib/dpkg/info/initramfs* /home/gemorgan/.Trash

```

then 

```
gemorgan@Legolas:/var/lib/dpkg/info$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
gemorgan@Legolas:/var/lib/dpkg/info$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-qt3 python-sip4 libmyth-0.20
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.

```

Now synaptic will start and I assume that I will boot correctly, yes?

Thanks for the help!

Eric

---

### Post by nowhere@cox.net on 2008-04-30
OK it rebooted fine but I still need a little help. When running synaptic for anything now, in the details it complains about no files listed for initramfs-tools and assumes no files are installed. I tried to re-install initramfs-tools and it terminated with the same error as listed above for initramfs-tools.

So I had to remove the files from the /var/lib/dpkg/info again and sudo dpkg --configure -a again.

I tried to remove initramfs-tools but the list of dependent packages I would have to re-install what HUGE and scary.



What can I do?

Thanks,
Eric

---

### Post by frodon on 2008-05-01
Do as suggested in post #4, so put back your /var/lib/dpkg/info* files as it was and then put manually the getopt files you need to solve your issue and run again the "sudo dpkg --configure -a" commnand :
[http://ubuntuforums.org/showthread.php?t=724273&highlight=dpkg+was+interrupted&page=5](http://ubuntuforums.org/showthread.php?t=724273&highlight=dpkg+was+interrupted&page=5)

If you need the getopt binary to put in /usr/bin/ i attached mine from gutsy in the post (remove the .txt extension).

---

### Post by nowhere@cox.net on 2008-05-01
Thanks Frodon,

I dropped the getopt file in /usr/bin and the rest works fine now. However, I have no idea what happened to getopt, nor do I have any idea what any of this stuff did to fix my problems. I don't like being clueless ;)

Thanks again!

Eric

---

### Post by frodon on 2008-05-02
Great !

I'm always happy to see users coming back here with a problem solved. This is strange indeed and i already noticed such issue after kernel updates with again the missing getopt package.
Now that all is back to normal i suggest you to reinstall the "util-linux" package so that you will be sure to have now all the good files well installed.

Hopefully this is the last time you have to bother with this.

---

### Post by nowhere@cox.net on 2008-05-05
Thanks again. It worked great. But I just did my fresh install of Hardy and it was a breeze. Everything seems to work perfectly with the exception of suspend with the nvidia drivers. It seems to hang on restore with a white screen occasionally.

Thanks!

---

