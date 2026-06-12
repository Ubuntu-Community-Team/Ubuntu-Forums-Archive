---
title: "cannot change screen resolution after upgrade to 8.04"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by phread59 on 2008-04-29
I am stuck at low resolution after upgrading to 8.04.  I installed envy, it returns my system will not support envy.  I looked in many threads and tried to load restricted drivers to no avail.  I downloaded the new driver 173.08 onto my desktop.  Gedit cannot open it, sudo will not open it.  I see nothing in any thread that will help me.  I have an XFX GeForce 8600GT card.  I just cannot find a place to allow more than 800x600.  I'm heading to bed I'm about worn out.  Any way to fix this problem?  Thanks fi\or the help.

Mark Shuman

---

### Post by swoll1980 on 2008-04-29
install envy ng and run it it will set every thing up for you [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by alienexplorers on 2008-04-29
Envy is availible in the repositories.  Just run it and first unload any drivers you have loaded and restart.  Then run it again and select to Automatically load the new driver.

---

### Post by phread59 on 2008-04-30
I uninstalled my vidio drivers and attempted to install new drivers with Envy. Envy erased my drivers and then when trying to install them stated my system will not support Envy and refused to install any drivers.  Ubuntu is now totally useless.  The log in screen is ghosted with multiple log in boxes, resolution is nil and I have black bars all over the place.  I believe Ubuntu is now defunct.  I really am not sure how to proceed.  I may just put the 7.10 disc back in and see if it will rescue the system.  Any suggestions?  BTW I'm back using XP again.  Any help would be appreciated.  I gotta head out to work.  I'll be back later today.

Mark Shuman

PS the crash monitor kept deploying all througout the process.  I didn't read what was crashing.  It started going off immediatly after I updated.  This so far has not been a plesant upgrade.  I was looking to get the LTS of 8.04.  That is why I decided to upgrade 7.10 was working just fine.

---

### Post by hermes0710 on 2008-04-30
> **phread59 said:**
> I uninstalled my vidio drivers and attempted to install new drivers with Envy. Envy erased my drivers and then when trying to install them stated my system will not support Envy and refused to install any drivers.  Ubuntu is now totally useless.  The log in screen is ghosted with multiple log in boxes, resolution is nil and I have black bars all over the place.  I believe Ubuntu is now defunct.  I really am not sure how to proceed.  I may just put the 7.10 disc back in and see if it will rescue the system.  Any suggestions?  BTW I'm back using XP again.  Any help would be appreciated.  I gotta head out to work.  I'll be back later today.

Mark Shuman

Did you install envy or envyng? For hh8.04 you need the second one

---

### Post by phread59 on 2008-04-30
Yes I installed NG.  A coupla thoughts.  When I logged back in the second time I looked at the kernel notes in grub.  It looks like it is still using 14 generic (?).  It looks like it is the same kernel as 7.10 used.  Maybe I have a kernel issue?  I have a 7.10 live disc.  Should I try to get a 8.04 live disc and use system repair from the live CD menue.  Or can I use the 7.10 disc?  BTW I used Update Manager to update with.  I have been having issues with it.  I deleted it and reinstalled it a week ago.  It wouldn't calculate the update.  I have since determined that the updates it would not do was an update for itself.  Could Update manager have dorked me?   I'm at work and snuck this in for more info to help the diagnosis.

Mark Shuman

---

### Post by phread59 on 2008-04-30
Bump for the lunchtime crowd.

Mark Shuman

---

### Post by phread59 on 2008-04-30
Bump for the evening crowd.  Before I gab this bull by the horns and wrastle with it, any suggestions?

Mark shuman

---

### Post by phread59 on 2008-04-30
Well I sorta fixed my issue with the update to 8.04,sorta, kinda.  I had to kill Ubuntu.  I downloaded the 8.04 ISO and burned a new disc.  I tried to repair with a live session.  It would have none of it.  So I just bit the bullet and installed 8.04 anew.  I ended up killing everything I had done with 7.10.  And I gotta start all over again.  Oh well with the issues I had with Update Manager in 7.10 I guess it is all for the good.  I'm happy to have the LTS of 8.04.  Hopefully I will not need to upgrade for a long time.  And lo and behold although it has changed in appearance GRUB is still with me and configured properly for my dual boot with XP\\:D/.  At least I don't have to go through that hassle again.  It sorta takes the sting out of loosing everything.

As a side, if the developers see this post please take note.  I am not the only one dealing with a screen resolution problem from an update through Update manager.  I believe there should be an inquery into this problem.  I think a good solution would be to have an update ISO and just burn a disc and do it from the computer instead of over the NET.  I hope this can help some poor sole who is borked as bad as I was.

Mark Shuman

---

### Post by atoms4peace on 2008-10-19
I had the same issue today after upgrading some 7.X Ubuntu to 8.04 via the option offered in automatic updates: After the upgrade the machine only allowed standard display resolutions: 800x640 and below. In my case the high resolution was available again after DISABLING (!) the NVIDIA accelerated graphics driver ( system -> Administration -> Hardware Drivers ). Although this brought back the high resolution, special graphics options seem to be unavailable in this setup. But at lease this workaround allows some normal display for office + browsing applications.

Ralf

---

### Post by Kellemora on 2008-10-19
Hi guys

Here's an EZ Fix for most of the resolution problems, provided you have the correct video driver installed for your video card.

Screen Resolution Problems?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
This document is to address Changing Screen Resolution using Preferences causes Screen to Roll horizontally, vertically or just mess up royally.  Also, only 640 x 480 resolution available in Preferences.  This fix may or may not allow you to select other available resolutions from the Preferences Option without changing MODE lines in /etc/X11/xorg.conf which I am not addressing here.
If this fix causes log-in screen obesity (HUGE SCREEN), see my other post titled Huge Log-in Screen?  Easy fix!  Which addresses that problem separately and easily.

To get started we need the Tool called Screens and Graphics.
If it is not available under Applications/Other, then RIGHT CLICK on Applications, select Edit Menu (left click) and wait for the Main Menu screen to open.  From the Main Menu, left column (Menus) select 'Other' and a new list of text will appear in the right screen (items).  Place a check mark in the box to the left of Screens and Graphics, this will automatically select 'Other' if it was NOT in your drop down list under Applications.  Close this window.
You will have to REBOOT for the change to take affect.

Once you're up and running again, left click on Applications/Other/Screens and Graphics.
A log-in screen will appear, type your Normal log-in password.  Why it don't ask for Root I don't know.

In the Screens and Graphics Preferences window select Graphics Card first just to check to make sure your correct graphics card is displayed.  Normally these entries are correct, but check them anyhow!

OK, now select the Screen Tab and get things set up to run properly.

Click on the little Monitor icon to the right of Model:  It may currently say Plug n Play.  A new (Choose Screen) window opens, from the Left window, select the Manufacturer of your Monitor.  The screen on the right will change to the models that manufacturer makes.  Scroll through the list to find your Monitors model name and number and/or identification.
If you have an .inf driver for your particular monitor and it is not listed, select add and follow the directions there.  I've not found a monitor not already in the listing yet.  Then I never have many new things either, that might not be listed long before I get it, hi hi.........  IF a Test button comes up, just IGNORE IT, because your screen will mess up royally.  After selecting your monitor, select OK!  This will bring you back to the Screen and Graphics Preferences screen.
Here you will select the desired resolution you would like your DESKTOP to run in.  The proper bandwidth should self-select, but check to make sure it's right for your monitor.  A wrong setting could damage your monitor!
Select OK and it will change and ask you if you want to Keep this setting.  If all looks OK, select YES.
This change, and all the default parameters for your selected monitor WILL be written to the /etc/X11/xorg.conf file.  Also, the Screens and Graphics window may show UNKNOWN for your monitor.  The result of this Unknown Monitor or sometimes even if the Monitor is KNOWN and displays correctly the resultant change to the xorg.conf file, may cause your log-in screen to become OBESE (HUGE) and you might not be able to see your log-in boxes.

But don't worry, you KNOW they are there! 
Just type in your log-in name, hit enter and type your password, hit enter and wait for the log-in to complete.  Your xwindow (Gnome or others) should be at the desired resolution now.

IF you did have the HUGE log-in problem, see my post on Huge Log-in Screen?  Easy fix!

The above was tested on the following machines with complete success:
HP Pavilion 753n, 2.53GHz Intel P4, 512mb, Intel 82845G/GL video, Samsung SyncMaster 955df.
e-machines T4165, 1.6GHz Intel P4, 256mb, AGP 3D video, AOC monitor.
Compaq 5420, 1.47GHz Athlon XP1700, Savage 4 AGP video, Samsung SyncMaster 3Ne.


TTUL
Gary/aka Kellemora
9/10/08 &#8211; rev 9/15/08

---

