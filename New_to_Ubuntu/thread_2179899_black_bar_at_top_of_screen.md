---
title: "black bar at top of screen"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by NedraE on 2013-10-10
My husband does my installs as he's very experienced with Ubuntu, which I am not.  I like it and can use it and do basics. 
My computer is set up with dual boot   Ubuntu 13.04 / Windows Vista.  
My husband set my desktop view to look like my older version of Ubuntu with a black bar across the top showing the ubuntu logo on the left with the words Applications and Places.  On the right end were the icons for restart/shutdown, the date, the wifi indicator and  cloud icon.  That was apparently an applet.

Important online things I do in Ubuntu and I do screen captures that I move to a folder on the Windows side so I can view what I did online in Ubuntu. 
I entered the picture album and cropped and renamed a screen capture I wanted to move to a Windows folder.  

I tried to drag and drop this screen capture to my desktop.  I dropped it too high, and instead of dropping onto my desktop, it dropped onto the black bar at the top where the ubunto logo is on the left with Applications and Places on the left side, and an applet shows the date and the icon for rebooting or shutting down on the right. 

So, my black bar now shows the top lines of my png file from the screen capture just to the right of Places. 
I tried to right click it to move it or put it into the trash, and it did not respond to right clicking.  I tried to click it and to double click it and that did nothing.
I did a restart to see if it would be dropped then, and when the system restarted, the top of the png file may have triggered a failure of the applet to load, and so I sent an error report on that.  

Can someone tell me how to remove the png from the screen capture from the top black bar?
I can't get help from my husband as he's out working and I won't see him again for weeks, and he can't stop his working to help me by phone till maybe late tonight. 
SO.. if any of you can help, I'd greatly appreciate it.

Nedra   :(

---

### Post by heir4c on 2013-10-10
Weird...
Normally for bring back the old bar your husband must have installed gnome-panel.
So, Open UbuntuSoftwareCenter and search for gnome-panel (empty field in the right corner at the top)
If that is installed (see the little titles next to the icons, and the green circle with checkmark) than close SoftwareCenter.
First we must know if you know the password for root privileges. Log you in with a password?

---

### Post by NedraE on 2013-10-11
I feel foolish for creating this problem.  I also cannot find my trashcan to remove a file I accidentally sent to the trash.

Than you for your reply.  I have UbuntuSoftwareCenter and it is apparently installed (see attached png file). 
It is my computer, so I do know the password for root privileges.  I do login with my password. My husband set me as administrator.

I'm not 100% used to this forum format and don't know if you will be able to see the image I tried to insert.

[IMG]http://s192.photobucket.com/user/4EGP/media/Screenshotfrom2013-10-11002552-ubuntu.png.html?sort=3&o=0[/IMG]  Do you have a size limitation for attachments? ah... found it...  I think I attached it though I don't see it.

---

### Post by newb85 on 2013-10-11
Used to be Right-click>Add to Panel, but I think now it's Alt+Right-click>Add to Panel to get your trash can back.

---

### Post by heir4c on 2013-10-11
Edit: Before you do what I write here, look at the next post by mcduck!!!



> **newb85 said:**
> Used to be Right-click>Add to Panel, but I think now it's Alt+Right-click>Add to Panel to get your trash can back.

If that not work than you can do a reinstall of the gnome-panel type in the Terminal:

```
sudo apt-get install --reinstall gnome-panel
```
Click Enter and let the computer do his work, is it don than reboot your system. Hope it work.

---

### Post by mcduck on 2013-10-11
reinstalling the panel won't help,. as that won't have any effect on user's configuration files.

Anyway, it shouldn't be needed anyway. Gnome-panel just has an option that allows you to use any picture as the panel background image, and you can just drag & drop the image file to panel to apply it. Which sounds pretty much like what happened here...

To fix that you'll just need to get to the panel's settings, and tell it to use the system theme instead of the image background. It's been ages since I've used gnome-panel, bout you should be able to open it's settings by right-clicking (or possibly alt-right-click) on an empty space in the panel.

---

### Post by heir4c on 2013-10-11
ThanX, mcduck for telling this. I make a note in my post too see first your post.

---

### Post by NedraE on 2013-10-11
Tried tose, newb85, and no luck.  thanks for trying.

---

### Post by NedraE on 2013-10-11
I cut my teeth (don't laugh) on DOS 2.1 and am only now using Ubuntu regularly, so I wait for my hubby to be here to fix things in case I royally screw things up.  He won't be home till December...  so I worry about reinstalling gnome panel.  
I have done sudo commands under his guidance.  
I am used to Midnight Commander since it looks like one of my favorite DOS programs.

---

### Post by NedraE on 2013-10-11
McDuck, your description sounds like what I think happened, but if you can see the area I cropped out of the png file, you might recognize that the same photo appears to be shown twice to fill all the bar to the right of -applications-  and -places- So I have NO blank spaces in the bar... just -applications--places--png file a few top lines 2x side by side-

I told my hubby about the trash can.  I don't want to distract him from his work (driving a big  truck) so I didn't tell him about the Gnome-panel bar. 
He told me to logoff and restart.  

The reason he installed the Gnome Panel was my comfort level.  I was running Ubuntu 9.04 o 9.09 or 9.10 till he upgraded me to 13.04, so you can see how out of date I was. 
When I boot the computer, my login includes a place to select one of four (4) Gnome Environments:  Gnome, Gnome fallback, Gnome fallback with no effects, and Ubuntu (default).  The mistake was made in Gnome fallback Environment.

He told me to change to Ubuntu and when I did, I had my trash can.  Couldn't find the photo I lost, but I found the trashcan and made note of where it's "hiding" 

Interestingly, when I boot Ubuntu Environment, I get a clean black bar at the top that has the cloud, wifi icon, sound icon, time stamp icon, and the gear for logging out or restarting.  SO... for now I have a clean looking background and am trying to get used to the Ubuntu Environment!  

If you can tell me how to get to the Panel's settings, McDuck, I'd appreciate it.  I'll keep looking for it and will let you know if I find it on my own.   Meanwhile, since I'm working with a large batch of screen captures I need to move to Windows to backup to a wifi drive that my Ubuntu does not seem to see, I'll work in the Ubuntu Environment for a little while and will look for the panel here first.  Finding it in this environment may help me. 

Nedra

---

### Post by stinkeye on 2013-10-11
alt+windows key+Right Click on an empty area of the panel. (windows key should be next to the left alt key)
In the popup menu, click on properties then the background tab.

If it is set to "**background image**", change to "**none(use system theme)**"

You can also use the **alt+windows key+Right Click** menu to add items to the panel.
ie if you can't find trash...add a trash item.

---

### Post by squakie on 2013-10-12
What happens if you try just right-clicking on the image and selecting delete from Panel?

---

### Post by NedraE on 2013-10-13
Squakie,
I tried right clicking and left clicking, and even alt-right clicking to no avail. NO response. 
I'm willing to try anything that can help, but so far... no luck.
Nedra

---

