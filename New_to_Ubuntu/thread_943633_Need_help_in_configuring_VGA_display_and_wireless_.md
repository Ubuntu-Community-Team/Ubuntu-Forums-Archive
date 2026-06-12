---
title: "Need help in configuring VGA display and wireless connection"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Sonadow on 2008-10-10
Hi, i'm new here, just tried out Ubuntu, and i'm completely in a corner with lots of problems now T.T

Before we start, maybe i should list down the specs of my computer first:

Processor: Intel Celeron D 320
Mainboard: Biostar P4M80-M4
IGP: VIA P4M800
RAM: 512MB DDR1
Harddisk: 80GB Samsung IDE Spinpoint

Currently, when i insert in the LiveCD of Hardy, i get thrown into a 1024 x 860 display resolution, which i find rather ugly and disgusting, since back in Windows XP and Vista, Windows can detect a huge range of display resolutions, and even above 2000+ display resolutions. At the very least, i want a 1600 x 1200 display resolution, because that is the display res which i use back in Windows. How do i go about doing this?

Secondly, i have read about the problems involved in getting a WUSB54G v4 wireless usb adaptor to work in Ubuntu, and i also heard about the GUI-oriented NDISgtk utility for installing Windows wireless drivers on Ubuntu. Unfortunately, even after using NDISgtk, the wireless adaptor still refuses to work, so now my computer is essentially an oversized paperweight on my desk, with no internet connection and a crappy display res. 

I have yet to install Ubuntu, but according to some people, a LiveCD boot is pretty much the same as an installation. And also, i'm not prepared to install Ubuntu onto my harddisk and then find out later that the instructions posted do not work, which is why i'm still in the process of trying everything out through the LiveCD.

Greatly appreciate it if the community can assist me so that i can make the jump.

---

### Post by Sonadow on 2008-10-10
...no one?

---

### Post by Sycron on 2008-10-10
Open up a terminal, type ```
xrandr
``` and post the output.

---

### Post by baizon on 2008-10-10
Hi, try this: [http://ubuntuforums.org/showthread.php?t=750284]("http://ubuntuforums.org/showthread.php?t=750284")

---

### Post by overdrank on 2008-10-10
> **Sonadow said:**
> ...no one?

Hi and please do not bump your post so quickly. If you do a search of the forums you will see others that have a issue with the VIA graphics but you should be able to get a resolution to suit you. As for the wireless I can not comment. :)

---

### Post by WWSmith36 on 2008-10-10
You can use a simple tool to reset you video setting.

Open a terminal from the menu Applications-> Accessories-> Terminal, and type

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install displayconfig-gtk
```

You will be ask for your password, type it, you won´t see the cursor move. Hit enter.

Then to configure your monitor resolution:

```
sudo displayconfig-gtk
```

You can select your monitor from the list or add it by using the .inf file from driver disk or download

If this does not help you may to install the proper drivers for you video card.  Hopefully after installing drivers you can just restart x rather than rebooting.  If you have to reboot, it would be pointless since you are running LiveCD

---

### Post by Sonadow on 2008-10-11
ok, this was what happened.

using sudo displayconfig-gtk, i managed to get a res of 1280 x 960. Was unable to get it up to 1280 x 1024, because the monitor would crap out on me immediately and display an 'out of range' message, which is a huge disappointment, since Windows to push 1600 x 1200 on it. (although for some reason, 1280 x 960 looks somewhat like Windows 1600 x 1200. Maybe it's my eyes playing tricks on me.

But it's still viewable, so i'll leave it at that.

Now for wireless.

Using instructions as posted in [http://ubuntuforums.org/showpost.php?p=3450169&postcount=1](http://ubuntuforums.org/showpost.php?p=3450169&postcount=1), i was able to follow the steps until THIS one:

sudo ndiswrapper -i <your_ralink_driver>.inf

attempting to carry out this step threw up a 'Permission Denied' line on Terminal. Anyone can walk me through this one please? Greatly appreciated.

-NOTE: If the VIA P4M800 and Linksys WUSB54G experiment works out well and i get my wirelesss internet connection working, then i'll experiment it on my main box, which has an Intel GMA 950 and D-Link DWA-110. Can i assume that the steps needed to get the DWA-110 working is the same as getting the WUSB54Gv4 to work?

---

### Post by Sava8420 on 2008-10-11
Well as for your graphics the lower resolution isn't as noticeable due to the cleanliness of the desktop in Ubuntu.  Now for your problem it is for some reason denying you acess to root but if you are on a live disk I'm not too sure how that is going to work.  When you ran: sudo displayconfig-gtk did it ask you for a password?  Or did it just work.  I wonder this because if you are on live disk you have no password to enter when it would normally prompt you to enter one the first time you used a sudo command.  I'll look into the tread you are using to see if there is something there causing your problem.  Otherwise I can tell you that if you have the room to dual boot it just install it as I'm certain you will ultimately get it all set up and working.  Also, look around the different sections on this forum or search it here or google and 9 out of 10 times the answer is already posted somewhere.

---

### Post by Sonadow on 2008-10-11
> **Sava8420 said:**
> Well as for your graphics the lower resolution isn't as noticeable due to the cleanliness of the desktop in Ubuntu.  Now for your problem it is for some reason denying you acess to root but if you are on a live disk I'm not too sure how that is going to work.  When you ran: sudo displayconfig-gtk did it ask you for a password?  Or did it just work.  I wonder this because if you are on live disk you have no password to enter when it would normally prompt you to enter one the first time you used a sudo command.  I'll look into the tread you are using to see if there is something there causing your problem.  Otherwise I can tell you that if you have the room to dual boot it just install it as I'm certain you will ultimately get it all set up and working. ** Also, look around the different sections on this forum or search it here or google and 9 out of 10 times the answer is already posted somewhere**.


NO password was required, sudo automatically just invoked te root privileges. Otherwise, i would not have been able to sudo displayconfig-gtk.

Yes, do please look into it. If i can sudo all the steps for wrapping the RT2500usb driver until the sudo ndiswrapper -i <your_ralink_driver>.inf part, i don't understand why it failed at the last part. the feeling of 'so close and yet so far' is downright frustrating.

but more importantly, when i finally get around to experimenting on my main box, will the steps for getting the D-Link DWA-110 to work in NDISwrapper be the same as the steps used right now for getting the WUSB54Gv4 to work?

And regarding your comment that 9 out of 10 times the priblem has been mentioned in the forums, yes, you are right, but mostly those 9 usually have like, different instructions.

---

### Post by Sava8420 on 2008-10-11
Ok so when you are running the code: sudo ndiswrapper -i <your_ralink_driver>.inf  you are using the new .inf file from the file you just extracted correct?  Have to be sure.  Cause as I read through the steps and see that it uses the same <textinside> as the one you just blacklisted it's gonna say no regardless.  Oh and while at first I was thinking your comment was a little "smart", we'll say, when your right your right.  Can be frustrating and confusing finding the right one that ultimately works.

---

### Post by Sonadow on 2008-10-11
yes, it's the new .ini file extracted. Ubuntu extratcted in into a folder within a folder, so the path is ```
sudo ndiswrapper -i WUSB54Gv4/wusb54g/drivers/wusb54gv4/rt2500usb.inf
```

I'm not doing anything wrong, am i?

---

### Post by Sava8420 on 2008-10-11
Ok so are those all .inf files? or just the last one?

Actually it is just the last one I take it and that is the directory you are listing there.  Ok so try just using 

code: sudo ndiswrapper -i rt2500usb.inf

---

### Post by Sonadow on 2008-10-11
the folder contains a .sys, a .ini and an additional file. unfortunately, cannot remember off hand what te last file is cause i need to rush to work.

i'll post back tomorrow and see how it goes from there.

---

### Post by Sava8420 on 2008-10-11
> **Sonadow said:**
> the folder contains a .sys, a .ini and an additional file. unfortunately, cannot remember off hand what te last file is cause i need to rush to work.

i'll post back tomorrow and see how it goes from there.

Sounds good just to be sure the .ini file is not the .inf file you are looking for.  Well have good one maybe will catch ya later on.  If your having troubles getting help just message me I should be around.

---

### Post by Sonadow on 2008-10-11
> **Sava8420 said:**
> Sounds good just to be sure the .ini file is not the .inf file you are looking for.  Well have good one maybe will catch ya later on.  If your having troubles getting help just message me I should be around.

Urm, so is that the correct  .ini file i should be using? It's the one i got after Ubuntu unzipped the WUSB54Gv4.exe file.

If it's not the correct .ini file i should be using, then which .ini should it be?

I'll need you to make yourself clearer since command-line is really like greek to me.

---

### Post by Sonadow on 2008-10-11
Sorry to bump, need to ask a few more questions.

1) Is the way to NDISwrapper a windows wireless driver is pretty much consistent for various wireless adaptors? And also, is it consistent for different distros? (Eg: Foresight, Fedora, Debian?)

2) Will the instructions for NDISwrapping window drivers change across different desktop environments? eg: Ubuntu, Kbuntu and Xubuntu. Because i'm currently downloading Xubuntu. Taking advantage of the office's LAN network for a fast download, and intending to try it out again as on my PC as a LiveCD.

3) Last, but not least, does anyone have an update on why i get Permission Denied when following this how-to at [http://ubuntuforums.org/showpost.php?p=3450169&postcount=1](http://ubuntuforums.org/showpost.php?p=3450169&postcount=1), as stated in my previous posts when trying to NDISwrapper my WUSB54Gv4, and as stated in the previous post, am i using the correct drivers?

Very sorry if i sound like hassling you all, but i can get very carried away when i crave knowledge, and unfortunately, i don't understand most of the UNIX talk you get when googling for what i want.

---

### Post by Sonadow on 2008-10-11
Bump for a Sunday morning before i knock off from work in 30min time. (working Sat 9pm to Sunday 6am)

---

### Post by Sava8420 on 2008-10-11
> **Sonadow said:**
> Urm, so is that the correct  .ini file i should be using? It's the one i got after Ubuntu unzipped the WUSB54Gv4.exe file.

If it's not the correct .ini file i should be using, then which .ini should it be?

I'll need you to make yourself clearer since command-line is really like greek to me.

Ok sorry for not getting back to you sooner.  I was meaning that the .ini is not the file you need there should be a .inf file that unzipped and that is the file you need.  I'll download the file you are talking about and see where it is.

---

### Post by Sava8420 on 2008-10-11
> **Sonadow said:**
> Sorry to bump, need to ask a few more questions.

1) Is the way to NDISwrapper a windows wireless driver is pretty much consistent for various wireless adaptors? And also, is it consistent for different distros? (Eg: Foresight, Fedora, Debian?)

2) Will the instructions for NDISwrapping window drivers change across different desktop environments? eg: Ubuntu, Kbuntu and Xubuntu. Because i'm currently downloading Xubuntu. Taking advantage of the office's LAN network for a fast download, and intending to try it out again as on my PC as a LiveCD.

3) Last, but not least, does anyone have an update on why i get Permission Denied when following this how-to at [http://ubuntuforums.org/showpost.php?p=3450169&postcount=1](http://ubuntuforums.org/showpost.php?p=3450169&postcount=1), as stated in my previous posts when trying to NDISwrapper my WUSB54Gv4, and as stated in the previous post, am i using the correct drivers?

Very sorry if i sound like hassling you all, but i can get very carried away when i crave knowledge, and unfortunately, i don't understand most of the UNIX talk you get when googling for what i want.

Ok so as for NDISwrapper I'm not sure how compatable it is with other distros but it should work for any *buntu distro you use.  There is also a graphical frontend for NDISwrapper that you can use to configure wireless. Run:
sudo apt-get install ndisgtk

If that works then under system/admin/windows wireless drivers you can then drop the .inf file you intend to use for your hardware.  A very good doc. on using ndiswrapper is here:  
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

As for the problem you are having the reason it is denying you access is because the .ini file is not the file you should be using.  When you extract the files from the setup.exe file there should be .sys and .inf among other files.  The .inf file is the target file you should be using.  The command you are running: sudo ndiswrapper -i <filename>.inf    is meaning the file you want is the .inf file. 

If you decide to install ndisgtk you won't have to worry about the terminal use.  You can also try to use synaptic package manager to install ndisgtk without using the terminal.  Synaptic can be found under system/administration/synaptic package manager.  Then just search for ndisgtk and check the box to install and then click apply tab.   Good luck hopefully this will function properly for you.  Let me know if any other questions

---

