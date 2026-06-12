---
title: "Running off cd..."
date: 2011-09-19
forum: New to Ubuntu
---

### Post by jacknet52 on 2011-09-19
I have win7 installed and run Ubuntu from a cd (trial) Does it save anything and to where? How do you permanently install it next to win7 ie: another partition on hard drive and will it act as if it's a complete install? Isn't there something in the bios that switches the OS's back and forth? tia, Jack

---

### Post by TeoBigusGeekus on 2011-09-19
Check [this]("https://help.ubuntu.com/community/WindowsDualBoot") out.

---

### Post by seawolf167 on 2011-09-19
+1 for the link Teo posted

[Here ]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")is how to resize your Windows partition, the Ubuntu download [location]("http://www.ubuntu.com/download/ubuntu/download"), [how ]("https://help.ubuntu.com/community/BurningIsoHowto")to burn the iso file, the [installation ]("https://help.ubuntu.com/community/WindowsDualBoot#Install_Ubuntu_after_Windows")guide, and the [graphical ]("https://help.ubuntu.com/community/GraphicalInstall#continueinstall")install how-to.

---

### Post by jacknet52 on 2011-09-19
Thanks guys...I'll try these ideas tonight when I get home from work and let you know if it went ok. I already have Ubuntu iso on cd ready to install. I just have to set up the partitions and it sounds like it would be best to let Ubuntu do that during setup. I'm guessing it will show me the windows partitions already there?

---

### Post by seawolf167 on 2011-09-19
Yea, if you choose the "automatic" partitioning it will install it by default alongside your Windows installation. During the installation you'll see a graphical indicator showing the relative sizes of your partitions as well.

---

### Post by jacknet52 on 2011-09-19
Question: Can I tell Ubuntu what size I want the partitions? I have a 500gb drive and would like to let each OS have 250gb.

---

### Post by seawolf167 on 2011-09-19
> **jacknet52 said:**
> Question: Can I tell Ubuntu what size I want the partitions? I have a 500gb drive and would like to let each OS have 250gb.

You'll need to decide that (and set up) your primary partitions when you resize your Windows installation. So if you want "even" sized partitions, you'll remove 465/2=232 GB from the Windows NTFS partition.

---

### Post by the.phantom on 2011-09-19
you might want to do a defrag on win7 BEFORE install or resizing partition !

i usually do it two times just to make it easier and probably a bit safer to make a windows partiton smaller

---

### Post by jacknet52 on 2011-09-19
What a mess. Everything was proceeding ok then: Installer Crashed. and then they apologized and asked me to file a bug report whatever the hell that is. And then they told me a developer will attend to the problem asap; yeah right. Where do I go from here guys. 
Thanks, Jack

---

### Post by seawolf167 on 2011-09-20
Try again:

[LIST]
[*]Redownload the iso file
[*][MD5Sum ]("https://help.ubuntu.com/community/HowToMD5SUM")it to ensure there is no data corruption
[*]Burn it to a cd on the slowest possible write setting
[*]Boot off the cd and run the Disk Check
[*]Re-install Ubuntu
[/LIST]
Are you using 11.04 or 10.04 LTS?

---

### Post by jacknet52 on 2011-09-20
thanks Seawolf for bearing with me so long. Can I do the MD5SUM to the file while it's on the cd drive? Or does it have to be on the hard drive. I've gotten errors with a copy of 11.04 desktop I386.iso that I got off the internet and like I said earlier it installed fine on the same computer a week earlier. When that first failed I installed a copy of 10.10 from a book called Ubuntu Unleashed. It failed. Then I went back and installed win7 fine. And remember it doesn't fail until the r/w of files. All the preliminary stuff does fine. I have to take off for a couple hours. I'll try what you said when I return. Thanks again for taking the time to help me. Jack

---

### Post by seawolf167 on 2011-09-20
You'll need to [md5sum ]("https://help.ubuntu.com/community/HowToMD5SUM")just after you finish downloading it to your hard drive from ubuntu

---

### Post by jacknet52 on 2011-09-20
@Seawolf - I left you a long post about 3 hrs. ago and apparently it didn't make it here. What I wanted to reiterate was I used a cd of Ubuntu 11.04 that I got off the internet and created a bootable iso disk. I loaded it on this computer ( celeron 2.66ghz core 2, 2gb mem, asus mother w/onboard directx 9 400mhz/ 224mb ram graphics. It loads all drivers fine. It worked great for about a week and I took it to the library where I work and had it hooked up to the public server unattended mostly for a whole day and I think someone hacked in messed up all my files because I couldn't access using sudo or anything. So I decided to just wipe the HD and reinstall complete, I hadn't really saved much. I know there are better ways to fix it but I just wanted it to work again and took the easy way out. It blew up with read/write errors all over the dmesg file. So I just got the book "Ubuntu Unleashed" and it came with a bootable U-10.10 cd and the same thing happened. So I thought it had to be hardware now because it shouldn't happen to two different installs. So I loaded win7 back with no trouble. So that's when I got involved with you guys and have been trying to load a good copy of U-11.04 next to win7 seeing as how I have a 500gb HD. Can I use the md5sum program to check against the cd in the drive or do I have to download to harddrive because at this point I think ubuntu is running off the cd? What do you mean boot off the cd and run the disk check? And burn a new one from the internet or off the cd? Forgive my newness. Also seawolf I appreciate all the time you've given me thank you, Jack

---

### Post by jacknet52 on 2011-09-20
Now I really feel dumb...I didn't know this rolled over to another folder and didn't see your reply. So like copy and paste the cd to the hard drive?

---

### Post by wildmanne39 on 2011-09-20
Hi, you have to set your bios to boot from the cd, then you should try ubuntu out when it loads and make sure it works good, then you will see the installer on your desktop to install it and here is a guide.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Thank you

---

### Post by jacknet52 on 2011-09-21
Thanks everyone...I'm burning a whole new dvd to try so I'm starting fresh. Take Care...see you in new thread.

---

### Post by seawolf167 on 2011-09-21
If it works are you are able to get it to boot off your cd you can mark this thread as solved then open a new one with any other questions you may have - but be sure to post back about it working or not!

---

### Post by jacknet52 on 2011-09-23
@seawolfe - Just wanted to let you know I got everything running ok again. I have a win7/Ubuntu dual going now. I don't know what happened. I ran both the cd's I had at work and had errors installing and thought I'd try it again while I was at lunch and came back and the burned copy of 11.04 completed install perfectly. I don't know I have one theory that I'm using older computers with Celerons in them and 1gb mem and older mother boards so I don't know can they get hung on install in older computers? That sounds crazy (something you'd expect from windows) I know someone said to burn at the slowest speed possible. I did that on a DVD to start from scratch on my home computer and it loaded first time just fine. Anyways I just wanted to let you know and thank you for taking time to help me.

---

### Post by seawolf167 on 2011-09-23
Awesome :) glad it is all working now. Make sure to make a backup (with something like [Clonezilla]("http://www.clonezilla.org")) to ease the headache of a reinstall in case something bad happens!

Please mark this thread as solved under Thread Tools.

---

