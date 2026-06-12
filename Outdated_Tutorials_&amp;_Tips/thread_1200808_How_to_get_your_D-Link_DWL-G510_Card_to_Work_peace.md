---
title: "How to get your D-Link DWL-G510 Card to Work peacefully with Gnome"
date: 2009-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Nyken on 2009-06-30
&#65279;Note: I'm making a edition to this as of July 16, 2009. It's my final revision and the summation of a lot of further research. This is the work around that WILL AUTOMATE your connection with this wifi card.  

It's my hope that an Open-Source programmer would create an installation routine .deb file to do this automatically.

-------

Okay, so it only took me a little over a week of research and trial and error to come up with this solution, which really is just a workaround IMHO, but it works. If it did not, then I couldn't be writing this, since I wouldn't have a working net connection.
 
The trouble with this card is that when the driver loads before or during the loading of GDM, the Gnome Desktop Manager, you'll have problems. The first symptom will be that you don't get that login screen tone you normally get. You will be able to login, but then your desktop will never finish loading. Annoying, yes.
 
This is how to save yourself all that grief.
 
[B]Installing the mrv8k51 driver for your DWL-G510 wireless card:
 [/B]
Insert the driver CD that came with your card and navigate to the /Driver/Manual and drag and drop the Win98 folder to your Home directory.
 
Open a Terminal window and then type cd /Win98 to switch to that directory.
 
Type ndiswrapper -i mrv8k51.inf and hit enter. That should install the driver. If you didn't get any message of any kind, then you should be good.
 
Type ndiswrapper -m to add it to the /etc/modprobe.d/ directory with a wlan0 alias.
 
Type modprobe ndiswrapper to set up the proper final configurations.
 
So far, these are instructions you can find just about anywhere. Where I diverge from those, is that you should NOT add ndiswrapper to /etc/modules. You simply will not need to, since Ubuntu 9.04 does this for you. It's no longer in mine, and I'm online. I'm not an expert, so I'm surmising that once it's listed in the modprobe.d directory, modprobe will call it up when it's needed later.
 
Check the /etc/modprobe.d directory for an ndiswrapper entry to be sure.
 

Starting your network connection:
 
After figuring that the only way for the card and Gnome to live peacefully is for the card to let her in first, I looked up how to get a wireless connection going from the command line. This is the sequence that I use on this card:
 
sudo ifconfig wlan0 up (to bring the connection up)
 
sudo iwconfig wlan0 essid KTLA (replace KTLA with your router's name)
 
sudo dhclient wlan0 (to get make a DHCP request from your router)
 
I made a script with all these commands named load-wireless and made it executable by typing sudo chmod +x load-wireless and copied it to /usr/bin (sudo cp load-wireless /usr/bin).
 
**** Here is the crucial change to this how-to -- ****

In our last episode, I stated:

Then, I created a laucher that referrences that script by adding a panel by right-clicking on the top bar and selecting "Add to Panel." Chose "Custom Application Launcher" and added typed load-wireless into the Command field, naming the panel appropriately and adding a comment ("Yay!") and clicking "ok."
 
You will have to click on that launcher after logging in to get online. 

[B]*** Don't bother with that part. You're never going to have to do this. Ever. I only leave it to show what changed ***
[/B]
The REAL key is for your wireless connection to be up and running long before Gnome, KDE, or Xfre even gets out of bed for the day. To automatically be loaded each boot time, the wireless driver needs to be already at the street corner as Gnome or it's K and X counterparts are getting their morning papers off the lawn.

This means adding load-wireless to Ubuntu's init-scripts. This process I found @ [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Slightly distilling the data there, this is what I did to get the much desired automated start up and shutdown of my connection with this card. 

In a Terminal:

1) type sudo cp load-wireless /etc/init.d
2) then type sudo chmod +x /etc/init.d/load-wireless
3) then, to make Bootup run it
    a) cd to /etc/init.d 
    b) type sudo update-rc.d load-wireless start 51 S .
       ** Make sure sudo update-rc.d load-wireless start 51 S . is typed EXACTLY like that - include the "." 
      Or just cut and paste that **
       ** I added the cd /etc/init.d part just to be safe. **

Shutdown your computer completely and turn it back on. I like to cold start changes like this becasue I'm a neat freak about things like this and don't want to risk something getting in the way.

You shouldn't have any trouble getting to your desktop now. Plus, notice your wireless gauge... looks good, huh?

This all works for me. I hope it does for you too.

---

### Post by jpeddicord on 2009-07-07
Approved, thank you for your tutorial contribution!

---

### Post by Nyken on 2009-07-09
Well, I got a heckova lot of help off this forum, so posting what I learn is just trying to give something back :o

---

### Post by Nyken on 2009-07-16
Changed the how-to since this new process gives those of us who use this card 100% of the results we sought. :D

Very happy right now.

---

