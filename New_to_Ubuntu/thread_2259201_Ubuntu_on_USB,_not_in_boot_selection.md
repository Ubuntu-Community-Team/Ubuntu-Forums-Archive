---
title: "Ubuntu on USB, not in boot selection"
date: 2015-01-02
forum: New to Ubuntu
---

### Post by arthur16 on 2015-01-02
I am new here but the site seems easy enough to use to know how to use it at least for this. hello everyone I just downloaded Ubuntu 14.1 *the latest one and made it bootable in a 8gb flash drive. Problem- I restart the laptop click F2, bootmenu shows up and in the actual boot  selection only shows windows and nothing else no matter what I use it will not read any of the usb port, just windows and that is it. What am I missing, is the thumb drive made wrong? I mean I used a very reliable youtube video to make the usb bootable with pendrix or something and it shows on the computer that is there with ubuntu but once i restart is not there. Help will be seriously appreciate it because I was thinking of buying me a new macbook and this Samsung I7 pass it on because of just flat out boring it has become to use it and also because of a few annoying issues with the windows and some software like skype doesn't work no matter what i do but I try it in another window in virtual pc and it works and a few others. Also just again i want to use something other than windows *boring*

---

### Post by Frogs Hair on 2015-01-02
Hello and Welcome 

What version of Windows and is it UFEI system ? Even on older Win 7, Vista or XP systems with a standard bios sometimes it's required to set a device to boot in the bios. Example : On my desktop in order to boot from a live DVD I had to include the optical drive as a boot device.

---

### Post by newb85 on 2015-01-02
More info on your motherboard would probably be helpful.  Often the deciding factor on what has to be done to make devices or drives the boot device (or in some cases, whether it's even possible).  My first PC was a Compaq Presario purchased in 2004.  As I recall, one limitation of the Motherboard was that it was not possible to boot from a USB, period.  Even in such cases, there are usually still ways to get Ubuntu onto the machine.

In fact, giving more details on your overall specs would help others in giving you suggestions.  (I searched for Samsung I7, and the first hit was for a camera.  I hope you're not trying to install Ubuntu on a camera.  :))

---

### Post by yancek on 2015-01-02
It would be helpful if you indicated the hardware or manufacturer of your computer, particularly if you are using some pre-installed version of windows which you do not mention.  The windows software, pendrivelinux, is usually pretty reliable so you may be having a problem with setting the boot priority in the BIOS as suggested above.

Personally, I think youtube videos are in general a poor source of accurate information although I've actually seen some that were good, not many.

---

### Post by arthur16 on 2015-01-03
Ok I have a Samsung ATIV 4 intel I7 windows 8 but liek all I changed to Windws 8.1 64x. I do not know how to find if it is UFEI thats a bit above my knowledge, I used to think my windows was busted because when it turns on it doesnt show the F2 word to go to the boot menu it really just snaps into windows which then it takes forever to load but the bootmenu is liek an eye wink fast. You mentioned dvd but this is a ultrabook i have no dvd thing only 3 usb port which is why i am trying to install it from usb flash drive (just pointing that part out to be sure I am following you here in every step)
I also want to say that the thign is ..should of mention this before. I used to have it I used to have ubuntu on it but the hardrive broke. I took it to best buy i have the insurance thing still running so they fixed it. That is when this whole thing happened. Ever since it came back I cant install ubuntu again in fact last tiem i installed it i had a problem because i didnt know the computer was reading 2 ways of installing from the boot menu ubuntu and i kept installing from one until i just pressed the second option it kept showing at the risk of brakign the laptop and it was the full version (i kept isntallign the temporary version). SO yea I know it should be able to be install but now it is just wont recognize the usb on the boot menu or at least it wotn show the option on the boot menu just shows windows as boot option.

---

### Post by arthur16 on 2015-01-03
UPDATE- ok problem is not entirely solved yet halfway. So what was the issue? Stupid fast bios was enabled and seen I am not good at this yet i was afraid i mess up my laptop but at the risk of trying somethign i made it disable the fast boot thingy option and now it reads the usb. PROBLEM- the problem now lies with the windows itself. Ok when i saw the boot menu shows me the 2 options 1 windows 2 usb ubuntu well I made 1 ubuntu and 2 windows. REstart and goes into a black window asking if i was to try ubuntu or install ubuntu. I tried for instaling ubuntu. Well it runs but the problem is when it says what do you want to do because it only says i can either choose to install ubuntu which will delete my hard drive because apparently there is no other operatign system it recognizes or do somethign else which sys do parton and soemthing. I went into the somethgn else make artition and wow I ran out of there i dont even know what i was lookign at. So yea is where i stand now either eraze my hard drive or do a partition which made me worry.

---

### Post by sudodus on 2015-01-03
Please post the output of the terminal window command

```
sudo parted -l
```

'... space minus ell'

It will give information about the available space on your drive(s).

-o-

First you should try to shrink the Windows partition from within Windows. Do not create any new partition. Leave the unallocated space.

Then boot again from the Ubuntu install drive (in live mode: Try Ubuntu)

Use ***gparted*** (while booted from the Ubuntu install drive). ***gparted*** has an intuitive graphical interface as is easier to understand than that of the installer.

If you want to hibernate you need at least as much swap as RAM in Gibibytes, otherwise 2 GB swap is enough. So create a swap partition with suitable size. Then use the rest of the unallocated space for a root partition (or if you wish, make something more complicated).

The start the installer and at the partitioning page select ***Something else***. This time you need not create anything. Only select the partition, that you made for a root partition, mark that you want it as **/** (symbol for root partition), and format it with the **ext4** file system. The swap partition will be selected automatically.

Finally check that the bootloader will be installed into the correct drive (usually **/dev/sda**, for the (first) internal drive). Use no digit, only the drive letter a (or b for the second drive ...)

*Edit*: I think you have UEFI. There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")

See also this link and links from it about booting from USB: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by arthur16 on 2015-01-03
Not working. So far I am not gettign the install alongside windows option. I want to dual boot not make it one OS.

---

### Post by Jonathan Precise on 2015-01-03
Hello arthur16.

Please run the command posted by sudodus in a terminal (press CTRL-ALT-T to open a terminal). Note that this command will not fix anything, it just gives us more info so we can better debug your problem.

What does it tell you? Please copy (SHIFT-CTRL-C copies in the terminal) and paste (CRTL-V works almost everywhere else). If you find it hard to do, you can also make a screenshot. If you don't know how to make a screenshot either, then try running in the same terminal:

```
pkexec apt-get install --yes --force-yes pastebinit
pkexec parted -l | pastebinit
```

(again, that's a minus and a lowercase L) and tell us the link that it generates.

It might be that Ubuntu isn't recognizing the Windows partition, or maybe it thinks the SSD is empty? Both have happened to me at least once.

Once the installer failed to recognize my Windows 8.1 install on my HP notebook, but that was in Ubuntu 13.10... Anyways, I just used the "Something Else" option, and I could install from there. It may work for you, but the manual partitioner is not the easiest way to install for everyone, especially for unexperienced users.

-Jonathan

---

### Post by yancek on 2015-01-03
The link below has a lot of useful information for a new user and if you scroll down about one third of the way on the page, there is a Step by Step guide on Installing using the manual method, "Something Else".  If you have windows 8, you are probably using UEFI/GPT which isn't really discussed in tutorial.  If you select the Something Else option, you should see the windows partitions on the Installation Type screen.  Under the column "Type", you should see ntfs.  If you don't see windows, stop.  Posting the info asked above should help someone help you.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2015-01-03
Best to use Windows own partition tools to shrink Windows, and reboot so it can update to its new size. Do not create partitions with Windows.

Make sure fast boot or always on hibernation is off, usually better to have secure boot off also.

some other Samsung threads.
 Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)


 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Another Something Else install, very similar to one posted by yancek.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by arthur16 on 2015-01-05
Been a busy this past days, I want to say i really am trying everything but nothing is working is as if the computer somehow when it got back to me from repairs as if they installed an imaginary windows 8 on the PC it just keeps saying wipe the hd and install ubuntu. I haven't tried the something else because I am not that good and I all i do know is making partitions can screw a hdd up (as far as i know and I dont have another 300 bucks to re-repair. I was hoping ot ask all of you...what do you think of just downloading an older version of ubuntu...could that work?

---

### Post by oldfred on 2015-01-05
No, with these very new systems you have to have the newest Ubuntu or even newer in some cases. Intel has made many updates not just to video, but to kernel & support software that is needed. And even after updates are submitted to kernel developers (Linus) it takes a while before all the is in the current distributions.

The issues is something to do with Windows and how Ubuntu scans system. They are trying to make fixes, but with current versions only Something Else is safe way to install. And you must have a good full backup of efi partition and Windows.

---

### Post by arthur16 on 2015-01-06
> **oldfred said:**
> No, with these very new systems you have to have the newest Ubuntu or even newer in some cases. Intel has made many updates not just to video, but to kernel & support software that is needed. And even after updates are submitted to kernel developers (Linus) it takes a while before all the is in the current distributions.

The issues is something to do with Windows and how Ubuntu scans system. They are trying to make fixes, but with current versions only Something Else is safe way to install. And you must have a good full backup of efi partition and Windows.
And there in lies the problem. I dont have a way to make a backup of my windows( the windows 8.1 that feels more fake than anything even though best buy "installed it') Aside that the partition part I feel so defensive on not wanting to break the laptp up because I never made partitions before I tried reading into how to do that I ended up more confused with the codes and this is windows but no this is not windows but this is something else that is in your hdd but is nothing and is like...really? I like the instructions when they are like - ok do this exactly and there bam your done! not with..name it how ever you know or will name it and is free game how ever you want..in other words if you screw it up is on you and this tutorial was just waste of time (is how i feel when a tutorial is not exactly 100% do this and that's it it works 100% all the it under all conditions) all in all i am just scared of doing the partition part because i don't know what im doing and fear of breaking it more than fixing it.

---

### Post by oldfred on 2015-01-06
Some suggestions on full Windows backups. I do not have Windows anymore so do not know.
And this you must do whether you install Ubuntu or not.
Systems to break and you need a way to recover if hard drive is damaged.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

