---
title: "A few questions from a newbie"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by Tubby on 2015-03-04
First of all hi to everyone here, I just installed Ubunta yesterday and needing to know a few things, like the following.
After installing ubunta you have to install any chipset drivers or other drivers ?
Do you have to  install any antivirus, malware or firewall programs ?
Also are updates automatically installed ?
One last thing for now ;) ,were the time, email etc that are up in the top right hand corner, is there any way to increase the size of them, being an old bugger I am having trouble seeing them.

thanks in advance for any help.

---

### Post by craig10x on 2015-03-04
Welcome to the linux side...and ubuntu is a great choice (personally, it's my favorite and it think it is the best linux distribution around)....To get the ball rolling (i am sure others will comment):
No antivirus needed, but i would install GUFW (which you can find in the software center) and just turn it on...that is the linux firewall...
Updates should pop up any day there are any updates, then you click it on and have it install them (the software updater icon would appear on your unity launcher dock)....

Personally, i think ubuntu is a lot easier to use the windows and is a LOT more secure...just in the nature of the way it's built...and requires no defragging (it has very neat filing system) and doesn't have that tendency to slow down in time like windows does...

---

### Post by papibe on 2015-03-04
Hi Tubby.
> **Tubby said:**
> After installing ubunta you have to install any chipset drivers or other drivers ?
Short answer: no.

If you have a relatively modern Nvidia or AMD graphic card, you may open 'Additional Drivers' to see if there are additional proprietary drivers you can install. 
> **Tubby said:**
> Do you have to  install any antivirus, malware or firewall programs ?
Not really (read more here: [Basic Security]("https://wiki.ubuntu.com/BasicSecurity"))
> **Tubby said:**
> Also are updates automatically installed ?
No. The default is to call your attention when there's one, and let you decide if you want to install them.

Hope it helps.
Regards.

---

### Post by mastablasta on 2015-03-04
> **papibe said:**
> 

No. The default is to call your attention when there's one, and let you decide if you want to install them.

.

that is not to say that one can't make it to auto update.... : [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

---

### Post by buzzingrobot on 2015-03-04
A long-winded response:

1.  In all but a very few cases, the hardware in your machine will be detected and the appropriate drivers will be installed and used automatically. Those very few cases typically involve components that are so new that Linux developers have not had time to study them and write drivers, or components manufactured by vendors who do not release enough data about the part to allow anyone else to write a driver. *If a specific component presents a problem, your best bet is to post a specific question here.*

2. Video comes in three forms:  Nvidia cards, AMD cards, and on-board Intel video integrated with Intel's CPU's. (If you have an Intel CPU, you will have the option of using Intel video unless the machine is especially ancient.) Open-source drivers for Nvidia and AMD and Intel will be used automatically depending on which card is actually active. Most users find these open-source drivers to be more than adequate for typical use.  A system that will see demanding gaming or video use will benefit from installing the appropriate closed-source proprietary from Nvidia or AMD (Intel open sources its drivers). These drivers are developed by Nvidia and AMD independently of the Linux community and are released without source code. Occasional incompatibilities and crashes do arise when the proprietary drivers are, in effect, out of sync with Linux development.  Ubuntu provides an "Additional Drivers" tool that will detect your video card and offer to install the appropriate driver (this may not be the very latest proprietary driver).  Importantly, you can also use "Additional Drivers" to remove a proprietary driver. *Recommendation:  Stay with the open source drivers if performance is acceptable.*

3. Viruses, malware and other attacks are criminal businesses.  Like any other business, they look for the greatest return on investment.  For those businesses, that's still Windows, by a very large measure. While no software is invulnerable, especially software that exists on a network (like the internet), it is a fact that Linux is used by a much smaller number of people and, therefore, is a much less lucrative target. So the usefulness of running one of the few anti-malware programs available for Linux to detect and counteract viruses/malware installed on your system is also greatly reduced. (I've never used any on Linux.) 

Caveat One:  If your system is on a local network with Windows machines or your share files with Windows users, or you dual-boot into Windows yourself, using an anti-malware program will help detect and remove *Windows* malware in files you relay to those folks. Malware built to attack Windows code won't affect Linux but it's a good practice to avoid passing it along.

Caveat Two:  Arguably, most attacks these days simply try to trick a user into doing something dangerous, like clicking on a link in a fake email, or exploiting vulnerabilities in the servers we point our browsers at. Software on your machine won't magically protect you from either. 

4. Automatic updating is provided, i.e, you're told updates are available and then you launch the updater. You can also run the Software Updating tool manually whenever you choose. 

5. I'm not aware of any standard way of enlarging the icons in the panel used in Unity, the default Ubuntu interface. There may well be fixes and hacks out there, though.  This is an accessibility issue.

---

### Post by grahammechanical on 2015-03-04
You will find an icon for System Settings in the launcher (side panel) or in the menu of the power/cog. Open System Settings and go to Screen Display and on the panel that opens there is a slider labelled "Scale for menu and title bars." That will increase and decrease the text and icons of the top panel. I think the default settings is 1 but we can go below and above 1.

This works whether we have an open source video driver or a proprietary video driver running. Other functions of Screen Display only work with the open source video driver. When we install a proprietary video driver we also get a setting utility for it and we can launch that from the Dash.

Also, if you go to System Settings>Appearance there is slider that lets us increase and decrease the size of the icons in the Launcher. The Behaviour tab gives us the options to autohide the launcher so that it remains off screen until we move the mouse either to the left side of the screen of the top left corner, depending on our choice.

While you are in System Settings go to Software and Updates>Updates tab. There you will have control over updates. It is only security updates that can be set to download and install automatically. The default is Display Immediately.

Regards.

---

### Post by JKyleOKC on 2015-03-04
> **buzzingrobot said:**
> 5. I'm not aware of any standard way of enlarging the icons in the panel used in Unity, the default Ubuntu interface. There may well be fixes and hacks out there, though.  This is an accessibility issue.One way to enlarge type, but not the icons, in the display is to change the DPI setting for the display. Since I use Xubuntu rather than the main-line Ubuntu, the sequence of menu entries that I use to do this is undoubtedly different; I'm pretty confident that there's still a setting you can use, however.

What I do is to click the "whisker" icon at the top left corner of my screen, and select the "Settings>Settings Manager" choice from the resulting menu. On the dialog which comes up from that, I select "Appearance," and in that dialog, the "Fonts" tab. Near the bottom of the Fonts screen is a setting for DPI; it defaults to 96. The larger this number, the larger will be all displayed type; I set mine to 104 to provide comfortable reading for my aging eyes.

The main thing for which you must watch out is that setting DPI (Dots Per Inch) to a value that's too large; critical buttons of dialogs, such as "OK" or "Cancel," are then pushed off the screen to the bottom where you cannot click them. For this reason, it's best to increase the setting only a small amount at a time, and verify that dialogs remain usable. Otherwise you can anticipate a frustrating time trying to get back to the dialog to reduce the setting!

Hope this helps.

---

### Post by Tubby on 2015-03-04
Thanks very much for such a detailed explanation, I have got a few things on  today so I will try the advise later on.

many thanks to all.

---

