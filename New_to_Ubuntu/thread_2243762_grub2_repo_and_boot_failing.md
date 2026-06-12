---
title: "grub2 repo and boot failing"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by Oaklander114 on 2014-09-11
New to Ubuntu and trying to run boot-repair in recommended mode from cd. I followed these guidelines from the ubuntu site ([https://help.ubuntu.com/community/Boot-Repair):](https://help.ubuntu.com/community/Boot-Repair):) 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
sudo apt-get update sudo apt-get install -y boot-repair && (boot-repair &)


When I run the recommended mode I get this error: " Please enable repository containing [grub2] packages in software sources of ubuntu 14.04.1 LTS 9sda5). Then try again". 

Tried to do so by clicking "Add" in the software -properties-gtk window that pops up saying "Install software additionally or only from these sources? - You can either add the following sources or replace your current sources by them. Only install software from trusted sources." , and then enabling all entries allowable to download from the internet (main, universe, restricted, multiverse). Then pressing "Close".
What happens next is that an internet browser window opens diplaying this file:" ///mnt/boot-sav/sda5/etc/apt/sources.list" with these lines: 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security main restricted
deb [http://archive.ubuntu.com/ubunty/](http://archive.ubuntu.com/ubunty/) trusty-updates main restricted


but still can't get the boot-repair to work as the same messages keeps popping up.

I had Ubuntu working perfectly for a while, until it stopped showing up in the boot-manager. The other OS I have running is Win 7. 
Also, this is the URL that I received from boot-repair (without it making a change to my computer, but that might be able to help out with throwing a light on the issue): [http://paste.ubuntu.com/8315495](http://paste.ubuntu.com/8315495)

I found one other person having the same issue on this link: [https://answers.launchpad.net/ubuntu...uestion/195949]("https://answers.launchpad.net/ubuntu/+source/grub2/+question/195949")
but there was no real solution posted...I hope someone can resolve my issue...

Thanks a lot!

---

### Post by Oaklander114 on 2014-09-11
I tried running reboot-repair from a USB stick. The iso is working fine, however the boot-repair tool gives me the same message as before "Please enable repository containing [grub2] packages in software sources of ubuntu 14.04.1 LTS 9sda5). Then try again" and then shows the mozilla browser with the same file displayed...

---

### Post by oldfred on 2014-09-11
Boot-Repairs full uninstall and reinstall of grub fixes major issues. It chroots into your system to run the updates.
But it requires Internet to download packages and your sources list must not have errors.
Or did you have Software Center or synaptic open at same time? Sources list has a lock and only one update software can run at a time. Sometime lock gets set and not released also.

Are you using same version of Ubuntu live installer as your install? Not always required but better if it is. And must not be an obsolete version.

Is your sources list only those 3 lines? It should have a lot more. Mine is 52 lines but about half are comments.

Just noticed you have /var as a separate partition. I saw one other with same issue. 
You have to also mount that like you have to mount /boot. Most desktops only have / & swap. A few add /boot. But Boot-Repair is not configured to add all the other system partitions. Not sure if while in the middle of Boot-Repair you can also mount that or have to manually do a chroot. Many instructions even on chroot do not mention adding /boot or just footnote it, but you have to also mount /var.

Not sure what mount Boot-Repair does. 
Line 944 shows this for /boot:
       mount sda7 on /mnt/boot-sav/sda5/boot

so you need to manually add same thing for /var
mount sda9 on /mnt/boot-sav/sda5/var

If that does not work I can post details (I think) on full chroot & update manually.

---

### Post by Oaklander114 on 2014-09-11
Thanks a lot for looking into this oldfred. 

No, I had nothing else open during the boot-repair, so no Software Center or synaptic....
I am not sure if I have the same version of ubuntu on my cd as installed on the pc, but the USB stick only has the boot-repair software and I think this one is supposed to be independent of the version.... ? 

I would like to try as you said, to add that line saying "mount sda9 on /mnt/boot-sav/sda5/var" ... Where do I find the file to add the line, and, does it matter in where I enter this text in the file?

Thank you..

---

### Post by oldfred on 2014-09-11
I have never used Boot-Repair to chroot.
Does it not ask to copy commands into terminal box to chroot or does it do it all automatically?
If automatic then it may be possible to modify script but I have never done that. Then it may be easier to chroot yourself.

Examples of chroots, but do not include /var and may not include /boot.
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

      #This puts you into sudo for rest of command for this session only:
 sudo -i
mount /dev/sda5 /mnt
#if /boot
mount /dev/sda7 /mnt/boot
mount /dev/sda9 /mnt/var 

   for i in dev proc sys usr; do mount --bind /$i /mnt/$i; done
cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
chroot  /mnt

Then once chrooted you can uninstall & reinstall grub. sudo not required once chrooted:
      
 apt-get update
apt-get update && sudo apt-get upgrade  #this updates everything
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
#purge old and reinstall new to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
apt-get install --reinstall grub-pc
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
#When done:
exit

# anything after the # is a comment do not copy or type comments

---

