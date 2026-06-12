---
title: "Newbie Questions Involving Software and Interface"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by nullified_nostalgia on 2012-03-02
I've got a couple of quick questions, they're probably answered somewhere but I'm not used to the layout of these forums.

1. I'm trying to install software using the Ubuntu Software Center, specifically Pigeon and VLC Media Player.  Every time I click the install button it looks like it's installing and then it tells me:

"Failed to download package files.  Check your internet connection", and after I click okay it says "Requires installation of untrusted packages.  The action would require the installation of packages from not authenticated sources."

I've tried ubuntu in the past and haven't encountered this problem before.  I'm obviously connected to the internet, I'm using the same computer to post on these forums.  What can I do to fix this problem?

2. I find the launcher at the left side of the screen highly annoying.  I don't mind it being there but I would like for it to auto-hide when I'm not hovering the mouse cursor on the left side of the screen.  How can I make it auto-hide?

3. Being used to microsoft windows I find it unsettling that the controls for closing, minimizing and maximizing are on the left side of applications and windows.  How can I move these to the right side?

4. How do I add and remove things from the menu at the top, such as the little email / chat button that I'll likely never use?  And similarly, if I wanted to, how would I move that entire menu from the top to the bottom of the screen, or even create an entirely seperate menu at the bottom of the screen?

Thanks!

---

### Post by bodhi.zazen on 2012-03-02
That is a wall of text, can you please edit your post to make it more readable.

---

### Post by nullified_nostalgia on 2012-03-02
My apologies, I had it nice and separated but when I posted it everything crunched together.  How do I make hard returns stay on this forum?

Noscript was causing it.  Apparantly Yahooapis is required to post here.  Got it fixed!

---------------

Just as an update to question 2, the only solution I've been able to  find, which seems to be repeated all over the internet, did nothing, and  that solution was:

sudo apt-get install dconf-tools
dconf list /com/canonical/unity-2d/launcher/

dconf write /com/canonical/unity-2d/launcher/use-strut 0

 The launcher auto-hides when an open program is near it, but I'm wanting it to hide at all times unless the mouse is in that area.

---

### Post by mastablasta on 2012-03-02
> **nullified_nostalgia said:**
> I've got a couple of quick questions, they're probably answered somewhere but I'm not used to the layout of these forums.
 
1. I'm trying to install software using the Ubuntu Software Center, specifically Pigeon and VLC Media Player. Every time I click the install button it looks like it's installing and then it tells me:
 
"Failed to download package files. Check your internet connection", and after I click okay it says "Requires installation of untrusted packages. The action would require the installation of packages from not authenticated sources."
 
I've tried ubuntu in the past and haven't encountered this problem before. I'm obviously connected to the internet, I'm using the same computer to post on these forums. What can I do to fix this problem?
 

You can check the sources and select another mirror server where you download the packages from.
 
> 
2. I find the launcher at the left side of the screen highly annoying. I don't mind it being there but I would like for it to auto-hide when I'm not hovering the mouse cursor on the left side of the screen. How can I make it auto-hide?

I am not sure but i think Ubuntu tweak might have a setting for that.
 
> 
3. Being used to microsoft windows I find it unsettling that the controls for closing, minimizing and maximizing are on the left side of applications and windows. How can I move these to the right side?
 
4. How do I add and remove things from the menu at the top, such as the little email / chat button that I'll likely never use? And similarly, if I wanted to, how would I move that entire menu from the top to the bottom of the screen, or even create an entirely seperate menu at the bottom of the screen?
 
Thanks!
 
plenty of things - such as customisability, moving things & pannels arround easy etc are found in Xubuntu that uses XFCE.
 
Ubuntu tweak is also a nice GUi to change hidden settigns: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
 
more infor on Ubuntu tweak here: [http://blog.ubuntu-tweak.com/2011/12/23/ubuntu-tweak-0-6-0-released.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ubuntu-tweak+%28Ubuntu+Tweak%29](http://blog.ubuntu-tweak.com/2011/12/23/ubuntu-tweak-0-6-0-released.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ubuntu-tweak+%28Ubuntu+Tweak%29)
 
also if you are more comfortable with traditional windows desktop interface you can try:
Kubuntu (uses KDE looks &feels very much like windows, especially with classic menu selected). KDE also has a lot of very good applications.
Linux Mint which is based on Ubuntu and has Cinnamon desktop (uses Gnome3 but modifies it to be moredesktop like)

---

### Post by 3rdalbum on 2012-03-02
> **nullified_nostalgia said:**
> 2. I find the launcher at the left side of the screen highly annoying.  I don't mind it being there but I would like for it to auto-hide when I'm not hovering the mouse cursor on the left side of the screen.  How can I make it auto-hide?

You can't do it without sorting out problem #1 unfortunately. Perhaps the command "sudo apt-get update" may fix Problem #1. I'm not sure how to fix it.

Anyway, the Launcher's default action is called Dodge Windows. This can be changed to Autohide which is the kind of action you want. You need to use Ubuntu Software Center to install the "compizconfig-settings-manager" package (or run the "sudo apt-get install compizconfig-settings-manager" command). When you have done that and it has completed successfully, hit Alt-F2 and type "ccsm". Click on the first result that appears.

Click on "Unity Plugin" in the new window and change the popup menu from Dodge Windows to Autohide.

> 3. Being used to microsoft windows I find it unsettling that the controls for closing, minimizing and maximizing are on the left side of applications and windows.  How can I move these to the right side?

You can't change it anymore, but don't worry - you'll get used to it quickly. I changed from Mac OS (left buttons) to Ubuntu/Windows (right buttons) and then back to left buttons when Ubuntu did it, and it's really not much effort to get used to the switch.

> 4. How do I add and remove things from the menu at the top, such as the little email / chat button that I'll likely never use?  And similarly, if I wanted to, how would I move that entire menu from the top to the bottom of the screen, or even create an entirely seperate menu at the bottom of the screen?

Unity is fairly well hardcoded for this kind of thing. You can remove the actual package that gives you the e-mail menu (sudo apt-get remove indicator-messages) but it's not possible to move the panel to the bottom or add a new panel.

It's restrictive, but at the same time I've had so many computer newbies accidentally moving their Windows taskbar to the left side or making it super fat and then getting frustrated because they can't figure out how to change it back. I've even seen plenty of new Ubuntu users accidentally deleting all their panels on old Gnome 2 or removing the network icon through experimentation, and not being able to get these things back without assistance. I do understand why the lack of personalisation of your workspace is what Ubuntu's enterprise customers would like, including computer manufacturers who have to provide telephone support to their customers!

If you really want a very flexible desktop that you can change to suit yourself, then you probably want XFCE, LXDE or Gnome Fallback. These desktops can be installed from Software Center and switched between at the login screen. But of course you need to fix Problem #1 first.

---

### Post by Torgas Prim on 2012-03-02
I had this problem when I used 11.10 and I changed from Unity to Gnome DE. Once I switched back my persmissions worked fine again and I was able to install updates and even get Wine updates again.
I am now running Mint and opensuse because of that and other issues I have with ubuntu

---

### Post by nullified_nostalgia on 2012-03-02
Thanks for the replies!  Somehow problem number 1 worked itself out when I woke up this morning.

I'm going to try a few of the different distros mentioned above, starting with Linux Mint.  What I'm really wanting is something that looks similar to a windows environment but is completely customizable down to every last detail.  Ubuntu 11.04 was somewhat close to what I'm wanting but it lacked in a couple of spots.  I was hoping 11.10 would be even more customizable but it looks like it's gone in the opposite direction.  Maybe I'll get lucky with one of these other distros.

---

