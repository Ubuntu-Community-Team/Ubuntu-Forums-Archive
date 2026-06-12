---
title: "No such partition"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by Faan on 2012-06-17
A few times I was prompted to download 12.04.  I ignored it and decided to wait for a CD.  Eventually I downloaded it to my regret.
I went through the whole process in a number of hours.  Then got to the point of restarting to only get the message that there is no such partition and no further.  I have 2 hard drives and get no further.  
It gives me the screen where it provides the option to log onto different OS.  Enterering on any one of those gives me
error: no such partition
press any key to continue and when I do this it takes me back to the log on screen.
Please help,how do I solve this?
Thanks 
Faan

---

### Post by audiomick on 2012-06-17
Hallo.
Do you have a live CD or USB installer that you can boot to (and access the internet from) ?

The first thing I would do is boot into the live environment and try and have a look at the two drives and see what is on there.

The next thing would be to obtain and run the boot info script available here

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

This is a great tool that prints out a lot of output on the state of your drives and your bootloader (grub). It is very likely that somewhere in this output there could be a clue to what has gone wrong. 

I would suggest posting the output here (use the code tags, the # button at the top of the post window) in the hope that someone will answer who can read it. Look at it yourself carefully. A lot of it is actually fairly easy to understand if you  don't let your self be fazed by it. I don't know if I will be able to get back here for the next few days, so I hope that some one else  can help.

edit: just rediscovered this thread
[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

which might be an easier way to do the same thing, and might offer some other help.

---

### Post by Faan on 2012-06-17
The only CD I have is of a previous version and I presume that if I use that the old version would be installed(?)
I am not sure how to access the PC.  What I am doing now I am doing from my laptop with access to the internet.
Whatever I download now will come onto the laptop and not the "problem PC". I cannot post here as I have to physically type in everything on here and not copy it onto the forum.

When I boot I get the following:
GNU GRUB version 1.99-21ubuntu 3.1 and the first choice then:
UBUNTU, with Linux 3,2.0-25 generic
and recovery mode and a few more alternatives, but when I enter I receive the "no such partition" message.
When I press F2 the result is:
"grub" and the rest of the screen remains blank.  Perhaps I can enter something after this, but do not know what.

---

### Post by westie457 on 2012-06-17
Hi, boot your system using the LiveCD and select 'Try' mode. Open a web-browser and go to here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Follow the instructions to install and run the program. Everything should be fixed to allow you to boot normally. If not then run the option for the BootInfoScript.

Post back here with the news.

Thank you.

---

### Post by audiomick on 2012-06-17
> **Faan said:**
> The only CD I have is of a previous version and I presume that if I use that the old version would be installed(?)

Just to make it clear: If you actually install from the older version CD, of course the older version will be install. What you need to boot into the live environment is the "try without installing" option when you boot from the CD. This is quite safe. It will not do anything to the existing install.

---

### Post by Faan on 2012-06-18
I did what you guys suggested and booted up from the CD and did the "try thing" and downloaded the program.  The next problem was to get the UBUNTU CD out of the PC to burn the new program onto a CD.  I just could not do it, so I am still stuck and could not run the repair program.  I could therefore not install and run the repair program. 
I cannot understand that this process is so difficult.  Is it only me or are others having similar problems?

---

### Post by Faan on 2012-06-18
Just over a year ago I experienced the exact same problem to the extent that I had to re-install everything and loosing all my work which I did not do a back up in time.  

When asking a question on the forum my impression is that the answers come from people who work on the inside of the programs regularly. I use the OS of the PC to get my daily work done which I need for running my business.
There is no one close I could phone and explain my situation to.

My impression all along was that UBUNTU was something Mark Shuttleworth had initiated and that his foundation was sort of looking after it.  If UBUNTU is intended to provide the less fortunate with a free OS I just cannot see how they can get a problem solved if they have to use the internet to find a solution to the problem they might have.

The business where I buy most of my PC related equipment from does not even want to listen to a problem experienced with UBUNTU / Linux. His attitude is that if you want to use a free OS you have to suffer the consequences that go with it.

---

### Post by westie457 on 2012-06-18
You can run Boot Repair by loading into RAM using the LiveCD. It should make the necessary changes to your Hard drive automatically.

---

### Post by sudodus on 2012-06-18
> **Faan said:**
> I did what you guys suggested and booted up from the CD and did the "try thing" and downloaded the program.  The next problem was to get the UBUNTU CD out of the PC to burn the new program onto a CD.  I just could not do it, so I am still stuck and could not run the repair program.  I could therefore not install and run the repair program. 
I cannot understand that this process is so difficult.  Is it only me or are others having similar problems?
It should be possible to eject the CD pushing the button, at least just after a reboot. Or is there something wrong with the CD drive?

---

### Post by Mark Phelps on 2012-06-19
> **Faan said:**
> My impression all along was that UBUNTU was something Mark Shuttleworth had initiated and that his foundation was sort of looking after it. Basically correct --but Mark actually FUNDS Ubuntu.

> If UBUNTU is intended to provide the less fortunate with a free OS I just cannot see how they can get a problem solved if they have to use the internet to find a solution to the problem they might have.
As far as I know, Canonical (the suppliers of Ubuntu) can provide options for you to PURCHASE support from them -- an option that appeals to companies using Ubuntu that want to get direct support, not resort to Forums.

As to using the Internet -- given that Ubuntu is free, just how would you expect them to support you?  Forum support (using the Internet) is pretty much how everyone gets support these days.

If you want direct support, without using the Internet, expect to have to pay for it.

---

### Post by Faan on 2012-06-19
The intention is not to receive everything for free. However if I am prompted all the time to download an OS then I think it is only fair for it to work.  This is, as I have said, that I lost everything that was on my PC previously when I did the download thing. 

This time round I decided to download as I thought why would the guys develop something which is not going to work. 
I do not expect miracles from people on a forum, but perhaps some advice as to what could have caused the problem.  
I did not do anything in terms of adjustment or entered something which I was not suppose to do.  The whole process took a couple of hours only to get to the restart point to end up with the system not able to boot as it says there is no such partition.

My own knowledge of PC's is very basic.  I find this for example difficult to understand: "You can run Boot Repair by loading into RAM using the LiveCD. It should make the necessary changes to your Hard drive automatically."  My understanding of this is to boot from the CD (previous version), try to remove the CD and then somehow try to burn the downloaded repair program and then insert this into the CD drive and reboot and hopefully the repairs will take place automatically (?)

I will go and try this now.

---

### Post by YannBuntu on 2012-06-20
> **Faan said:**
> A few times I was prompted to download 12.04.  I ignored it and decided to wait for a CD.  Eventually I downloaded it to my regret.
I went through the whole process in a number of hours.  Then got to the point of restarting to only get the message that there is no such partition and no further.  I have 2 hard drives and get no further.  
It gives me the screen where it provides the option to log onto different OS.  Enterering on any one of those gives me
error: no such partition
press any key to continue and when I do this it takes me back to the log on screen.
Please help,how do I solve this?
Thanks 
Faan

Hello
You were "prompted to download 12.04" means that you were already using a previous version of Ubuntu (10.04 or 12.04 i guess), that you upgraded via the "Update manager" (not via a CD), and that this upgrade failed?
If yes, here is what i would do:
1) Download a Ubuntu 12.04 ISO, burn it on a CD or USB
2) Boot on it, choose "Try Ubuntu", check that all (graphics, internet..) is fine
3) Open a file browser and backup your documents ("gksu nautilus" may help)
4) If you can't access your documents, indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1"). We will check that your filesystem is still ok
5) Reinstall 12.04 above your broken system via this method: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by Faan on 2012-06-20
> **YannBuntu said:**
> Hello
You were "prompted to download 12.04" means that you were already using a previous version of Ubuntu (10.04 or 12.04 i guess), that you upgraded via the "Update manager" (not via a CD), and that this upgrade failed?
If yes, here is what i would do:
1) Download a Ubuntu 12.04 ISO, burn it on a CD or USB
2) Boot on it, choose "Try Ubuntu", check that all (graphics, internet..) is fine
3) Open a file browser and backup your documents ("gksu nautilus" may help)
4) If you can't access your documents, indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1"). We will check that your filesystem is still ok
5) Reinstall 12.04 above your broken system via this method: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

You are right.  I started with 10.10 upon recommendation of someone and downloaded it on a partition with windows on the other partition and all was fine.  I could either using UBUNTU or Windows when booting up.  I updated several times as I received notification thereof.

Then something went wrong, after an upgrade I think, and lost everything.  I just could not get anything to work.  Eventually I started the whole process all over again by re-installing both UBUNTU and Windows.  I had no choice as this was the PC I used for work purposes and was desperate to get the PC going again.

After this everything worked fine except that I had to use to use another program to listen into webinars which I needed.  I also have a program or two which only works in a Windows environment.  This I must say is a little bit of a frustration.

As previously I was prompted to download a new UBUNTU version, bit instead of downloading someone who is much more knowledgeable  installed the new version for me from disk.  This happened about three months ago.

As I have two hard drives I thought it to be ideal to delete the partitions to have UBUNTU on one hard drive and Windows on the other.  This person however did not do this for me as he said it would be too time consuming to do so. Due to lack of experience I left it at that.

Then as said I was prompted to download 12.04 a few weeks ago and thought I would wait until I can obtain a CD to do it from. After looking at this several times I decided to download and could also not find a CD with the new version

The download went well up to the restart point and the rest is history.

I still do not know whether it is possible to have the two OS on the two different hard drives in order tio decide at boot up which OS I would like to use.

Last night I tried again to what has been suggested by the other guys, but again could not get the CD ejected.  I would again prefer not to format everything and start from afresh and loose everything that has not been backed up yet.  Apart from this it takes hours with my download speed to get everything downloaded which I need again.

Sorry about this long explanation, but I will try your suggestion tonight to see how far I may get.

What I am doing right know gets done on my laptop.

Thanks for the help so far

---

### Post by sudodus on 2012-06-21
> **Faan said:**
> As I have two hard drives I thought it to be ideal to delete the partitions to have UBUNTU on one hard drive and Windows on the other.  This person however did not do this for me as he said it would be too time consuming to do so. Due to lack of experience I left it at that.

It is possible to have one drive with Windows and one drive with Ubuntu (and/or other linux distros). One way to do this is first to repair the Windows bootloader, so that the Windows drive can work by itself (if the other one is disconnected). Then you install Ubuntu to the second drive. When you come to the dialogue screen about partitioning, you should install the bootloader grub to that second drive (maybe /dev/sdb). Do *not* install it to a partition (/dev/sdb1 or /dev/sdb2 ...)!!!
> 
I still do not know whether it is possible to have the two OS on the two different hard drives in order tio decide at boot up which OS I would like to use.

Last night I tried again to what has been suggested by the other guys, but again could not get the CD ejected.  I would again prefer not to format everything and start from afresh and loose everything that has not been backed up yet.  Apart from this it takes hours with my download speed to get everything downloaded which I need again.

Try to eject the CD disk pushing the button right at/after reboot, before the computer has started to read from it!

---

### Post by Faan on 2012-06-24
I have now been able to get to 12.03 as I downloaded it earlier.  I used the 11.1 disk to start and after a little bit of a battle got to the "try out" option which I did and then got to the option of testing the system and then log into 12.04.  
However when I shut down and start up again I have to go through the same process otherwise I get to the original problem of the error report of now such device.
I tried the boot repair download, but could not succeed in installing it and running it.
At this point I leave the PC running and from what I see it is in 12.04, but the problem is still there.
Thanks

---

### Post by sudodus on 2012-06-24
It's a step forward that ***you can run a live session*** ('try' or 'test' Ubuntu) :KS

But you have to start from the same beginning after shutdown or reboot (unless you make a persistent live system and I do not recommend that in your case).

If it starts and you get decent graphics and can run applications in a live session, it is also possible to get an installed system with the same properties (or better with some tweaking).

---

### Post by Faan on 2012-06-29
I am hesitant to reboot as I am afraid it is going to require a performance again to start up again.  I need the PC for work and cannot afford to battle for hours to get it going again.  I have not shut down for the past few days.

I downloaded the " /home/faan/Desktop/bootinfoscript-061.tar.gz" , but I am not sure what this is suppose to be doing.

You guys have recommended that I download 12.04 ISO, but I am running I presume on "try out" on 12.04 TLS. What is the difference between these two?

Is it not at all possible to install without rebooting first?

Thanks

---

### Post by cryptotheslow on 2012-06-29
Regarding the bootinfoscript:

If you double-click on that bootinfoscript-061.tar.gz it should open up and show you the three files inside. Drag the file called bootinfoscript onto your Desktop.

Then open a Terminal (either find it via the dash menus or press Ctrl Alt T) and enter this command:

```
sudo bash ~/Desktop/bootinfoscript
```

When it has finished running you will find a new file called RESULTS.txt on your desktop. Open this by double-clicking on it and copy the contents of that file into the forum here using the # button on the post toolbar to wrap it in CODE tags so it is easily readable.

---

### Post by Faan on 2012-06-29
Do I just insert that into the terminal or do I insert and enter?

---

### Post by Faan on 2012-06-29
Do I just copy into the terminal or copy and enter?

---

### Post by sudodus on 2012-06-29
> **Faan said:**
> Do I just copy into the terminal or copy and enter?
Yes!

Copy the text into a terminal: that is the command line.

Press the Enter key to tell the computer to start running the command.

---

### Post by Faan on 2012-07-04
Fortunate by the unfortunate.
People broke into our home over the weeekend and stole our flat screen TV, my PC with the UBUNTU OS, my laptop, my camera and a few smaller items.  This solved my logging in problem into UBUNTU.

---

### Post by YannBuntu on 2012-07-04
ouch. sorry for you.

---

### Post by sudodus on 2012-07-04
> **YannBuntu said:**
> ouch. sorry for you.
+1

I hope that your insurance covers the costs. But your feelings and the extra work to fix everything ...

and I hope that you come back to the Ubuntu Forums, when you have time for Ubuntu again.

---

