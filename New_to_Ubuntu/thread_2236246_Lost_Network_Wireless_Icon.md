---
title: "Lost Network Wireless Icon"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by mountainman70 on 2014-07-25
Running Ubuntu 14.04 with Mate.
I had to replace the battery in my Dell 745 SF computer the other day. 
Now I notice I connect to the wireless network okay, but I have no icon.
Also when I get an update in the task bar and click on it desktop acts like it is minimizing update screeen to the task bar even though no screen is there.
I click update again and update screen opens on desktop.
Is there a setting I need to adjust to get icon back?
Thanks.

---

### Post by mountainman70 on 2014-07-26
> **mountainman70 said:**
> Running Ubuntu 14.04 with Mate.
I had to replace the battery in my Dell 745 SF computer the other day. 
Now I notice I connect to the wireless network okay, but I have no icon.
Also when I get an update in the task bar and click on it desktop acts like it is minimizing update screeen to the task bar even though no screen is there.
I click update again and update screen opens on desktop.
Is there a setting I need to adjust to get icon back?
Thanks.

It seems to be a previous update that is causing this problem. 
I have found a temp solution. 
I put sudo nm-applet in the terminal and get the wireless icon but I must do it every time I boot up computer.

Will keep searching for a permanent solution.

---

### Post by kira-yamato-2008 on 2014-07-26
I know that in Lubuntu 14.04 you open "Default Tools for LXSession" under "Preferences" then in the window that comes up go the "Autostart" tab. Under "Manual autostarted applications" in the little text box you enter "nm-applet" (without the quotation marks) and press the add button. Is there a standard Ubuntu way to do this?

---

### Post by mooreted on 2014-07-26
Pretty much the same in Unity. Find "Startup Applications" and add "nm-applet" to the list.

---

### Post by kira-yamato-2008 on 2014-07-26
One interesting thing that I found when I reinstalled, is that if you use the "Run" option to start the nm-applet when running the Live DVD before you install it autostarts after the install.

---

### Post by varunendra on 2014-07-26
> **kira-yamato-2008 said:**
> Is there a standard Ubuntu way to do this?

The standard was to not require to add it manually at all. The nm-applet not loading by default is a bug in Lubuntu - there are no standard ways to workaround bugs.

However, when you need to manually add a program to autostart list, the 'standard' varies depending on various desktop environments. What you mentioned is the standard for Lubuntu, could be different for Mate (I'm not familiar with it), but yes a 'way' should be there somewhere in the menus.

> **kira-yamato-2008 said:**
> One interesting thing that I found when I reinstalled, is that if you use the "Run" option to start the nm-applet when running the Live DVD before you install it autostarts after the install.
In Lubuntu?

---

### Post by kira-yamato-2008 on 2014-07-26
> **varunendra said:**
> In Lubuntu?

Yes in Lubuntu. I'm not even sure if this an issue with Ubuntu as a whole or just certain flavors like Lubutu. But it seems like the former, not the latter, maybe?

*Edit: When I said "standard" I meant something that's either universal to all the flavors, or something specifically for the base Ubuntu it self.*

---

### Post by varunendra on 2014-07-26
> **kira-yamato-2008 said:**
> Yes in Lubuntu. I'm not even sure if this an issue with Ubuntu as a whole or just certain flavors like Lubutu. But it seems like the former, not the latter, maybe?
No, the users of Ubuntu default or Kubuntu don't face that issue. So far, only Lubuntu (14.04) has been reported to have this nm-applet bug.

> **kira-yamato-2008 said:**
> *Edit: When I said "standard" I meant something that's either universal to all the flavors, or something specifically for the base Ubuntu it self.*
Yes, I understood your meaning. I wish there was a 'universal' way, I'm not sure if there is one, but I *believe* there isn't any.

Since Unity became the default DE for Ubuntu, it shifted the method of launching applications from traditional launchers to ".desktop" files. In unity based setup, these ".desktop" files are located in "**/usr/share/applications/**" directory and their contents may vary depending on various factors. When an application needs to be autostarted, its .desktop file is simply copied into "**/etc/xdg/autostart**" directory (sometimes the contents of the .desktop files may also need to be modified).

Now if these .desktop files are standard for all Desktop Environments, plus their running mechanism is the same involving these two directories (**/usr/share/applications** and **/etc/xdg/autostart**), then we may cook up a 'universal standard' way to do things - just copy the desired .desktop file from **/usr/share/applications** to **/etc/xdg/autostart** using a simple 'cp' command. But I believe this .desktop method is limited to Unity DE, and other DEs have their own different ways to launch and autostart applications.

I used to be a curious tester, but ever since Unity came out, and I installed Ubuntu 12.04 on my laptop, I never found time nor enough space on my hard disk to experiment with different DEs and confirm if there can be a 'universal' way to deal with launchers.

Maybe users with different DEs like you can confirm?

---

### Post by mountainman70 on 2014-07-26
> **mooreted said:**
> Pretty much the same in Unity. Find "Startup Applications" and add "nm-applet" to the list.

What should I put in the command and comment boxes?

---

### Post by mooreted on 2014-07-26
> **mountainman70 said:**
> What should I put in the command and comment boxes?

Click "Startup Applications"
Click "Add"
Enter any name you want, perhaps "Network"
Enter "nm-applet" without the quotes in the command field
Under "Comment" you can leave it blank or add a descriptive title like "Network Connections"

---

### Post by mountainman70 on 2014-07-26
> **mooreted said:**
> Click "Startup Applications"
Click "Add"
Enter any name you want, perhaps "Network"
Enter "nm-applet" without the quotes in the command field
Under "Comment" you can leave it blank or add a descriptive title like "Network Connections"

Just checked and I have Network already there. 
Name---Network
Command--dbus-launch nm-applet
Comment--Manage your network connections

Does this need to be changed some way?

---

### Post by mooreted on 2014-07-27
Hmm, that's weird. Ok, try this. Open a terminal and do:

sudo service network-manager stop

sudo rm /var/lib/NetworkManager/NetworkManager.state

sudo service network-manager start

---

### Post by mountainman70 on 2014-07-27
> **mooreted said:**
> Hmm, that's weird. Ok, try this. Open a terminal and do:

sudo service network-manager stop

sudo rm /var/lib/NetworkManager/NetworkManager.state

sudo service network-manager start

Thank you mooreted. 
That seems to have solved the problem. I have logged off, also restarted, also shut down, rebooted and each time the applet saying it is either disconnected or connected shows and the wireless applet is now visible. I am sure I tried those same commands from another web site and got no results. Maybe the commands were a little different or has something else I have done caused it to finally work. I will try to find that site and check. 
But it looks like my problem is solved for now.

Thanks for your help.
.

---

### Post by mooreted on 2014-07-27
That's great, glad I could help.

---

### Post by mountainman70 on 2014-07-27
> **mooreted said:**
> That's great, glad I could help.

I checked the other web site and those were the same sudo commands as yours. I had tried them 2 0r 3 times and they would not work. This was a test HD I was working on and when I tried the commands on my regular HD they did not work. So I just cloned the test HD to the regular HD and it is still working normal. Must have been something else I tried that got the sudo commands to finally work. Just glad everything is working now.

Thanks Again. :D

---

