---
title: "Installing 11.10 on HP dv6-6135dx"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by jlmatthews on 2012-02-17
So I am new at this, but I am a big fan of the opensource movement and want to give the ole Ubuntu a try.
 
I have been having some problems.
 
I have a HP dv6-6135dx.
 
When I try and run the installiation CD, the screen goes completely black. I press F3 and turn off modeset, then restart. Then it comes to a screen and I try hitting "Try Ubuntu before Install" to see what happens. It gives me a HUGE amount of failed messages and then goes to a command prompt.
 
I would like to get ubuntu going on my laptop and give it an honest try.
 
Help?

---

### Post by mörgæs on 2012-02-17
Hi, welcome to the fora.

Have you checked that the CD is burned correctly using the self-test option?

From the menu you can also test the memory. It takes quite a while but is well worth the time.

---

### Post by jlmatthews on 2012-02-17
Yes I have performed a disk check and a memory check!

---

### Post by jlmatthews on 2012-02-18
So I am new at this, but I am a big fan of the opensource movement and want to give the ole Ubuntu a try.
 
I have been having some problems.
 
I have a HP dv6-6135dx.
 
When I try and run the installiation CD, the screen goes completely black. I press F3 and turn off modeset, then restart. Then it comes to a screen and I try hitting "Try Ubuntu before Install" to see what happens. It gives me a HUGE amount of failed messages and then goes to a command prompt.
 
I would like to get ubuntu going on my laptop and give it an honest try.
 
Help?

---

### Post by mörgæs on 2012-02-18
Please don't create multiple threads on the same subject.
Merged.

---

### Post by waynefoutz on 2012-02-18
I looked that model up, it has a hybrid graphics card. I hate  to steer anyone away from Linux or Ubuntu, but to be honest, the support for that kind of technology on the Linux side is still pretty much still in it's infancy. Right now, you're going to get the best experience out of that machine running Windows.  I've been told the latest proprietary drivers support this, but I don't know for sure. Either way, that driver isn't in Ubuntu's repositories yet, and you have to install it yourself. If it were me, Id try again in a couple of months, in April when 12.04 comes out.

---

### Post by jlmatthews on 2012-02-19
First off, let me say sorry for the double post, but I thought I posed in the wrong place. 
 
Second, thanks Waynefoutz, I appreciate your advice.
 
Third, I REALLY want to get this to work, I know someone out there has a work around for me that can make this happen. You are all so smart and talented, there has to be something that can be done!

---

### Post by mastablasta on 2012-02-19
you can use alternate CD which has a text based installer to install ubuntu. you can do that to separate parittion if you have windows already installed. next you will need to download and install the latest AMD drivers which should support the graphics card and solve your issue.

regarding black screen - did you also perform a Md5sum check when you downloaded the iso file? this migh tnot be necessary if you used torrent to download it as this check is performed during download.

but the point is if your file doesn't match exactly (up to the single bit) to the file that is on server you would get error upon trying to boot the OS. Md5sum check checks this.

---

### Post by jlmatthews on 2012-02-23
So I downloaded the alternate CD, and has tried to install. However, I am new to all this and had problems when I got to the disk partitioner. I want to dual boot windows and ubuntu for a bit till I make sure it does everything I need it to. I am not sure exactally how to partition the disk to make this happen.
 
I appreciate all you guys' help.

---

### Post by mastablasta on 2012-02-24
go to your windows and use windows disk manager to paritition the disk.
 
first though defragment the disk 2 times (second time will be faster)
then do a checkdisk that will check the disk if any error are there and fix them.
backup any important data.
 
only then start partitioning. simply reduce your main disk and leave it as empty space to which you will later install linux (make it about 20-25GB big). then reboot.
 
now reboot with alternate CD and start install and install to largest empty disk space. the rest should be done automaticly. though i am not sure how it looks in alternate CD.
 
 
option 2 (might be faster) - if you have an 8GB USB drive you can install it there. should be big enough for the os and a few extra programmes. i am not sure what you want to try.
how?
again boot from CD and choose to install. at manual parittioning choose that / goes to USB drive. also GRUB has to go on USB drive. then when it's installed reboot and choose from BIOS to boto from USB.
 
option 3 is to install it in a virtualbox. here is a nice guide with pics on how you do it: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
i should say at this point that you are likely using hybrid graphics and you will need to download and install the drivers manually (the process should be easier in next OS version but for now...). it's a bit messy now, but if you could somehow get to GUI you could just copy & paste the commans: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 
note: if you install in virtual box then special drivers from virtual box will be used and not the real ones. of course perofrmance is also not the same. but it does give an option to try it out.

---

