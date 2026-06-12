---
title: "just had a massive 10.4 update and now I can't find my drives in places"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by mrnewtothis on 2013-10-20
I have a dual boot of Unbuntu 10.4 and XP Pro, But Ubuntu updated after an absence with 536 updates. When i go into places it does not show my drives, as it used to under computer Even the recent documents links from before the update to anything on the xp side of the drive will no longer work. If I run ubuntu from disc then it works fine.
Anyone know where to look now?

Also when i shut this new updated 10.4 down it does not shut down, as it goes to a screen with a box with a small computer image and the desktop name and ubuntu name that is interchangeable if I click on it. there is a shut down icon and a clock bottom  right corner but I have tried to use them to shut down each option but nothing happens.
So anyone know how to shut down

Just started another update, this time with 163 updates and three new items so maybe that will fix it when it is done but any help would be appreciated.

Thanks

---

### Post by mrnewtothis on 2013-10-20
the last update sent it all back to normal.

---

### Post by coffeecat on 2013-10-20
You need to be aware that the desktop version of 10.04 went end-of-life last May. You will still get updates for those packages that are common to the server version (which is supported until April 2015) but you will not get updates now for any components of the GUI. Your web browser will go seriously out of date - if it is not already - and use of this unsupported OS for web browsing will be a security risk for you. With 563 plus 163 updates, my guess is that you were downloading some updates that pre-dated the end-of-life date.

I suggest you think about upgrading to a supported version of Ubuntu. In case you do not know this, the gnome2 desktop which you are describing is now obsolete and has been replaced by the Unity desktop in Ubuntu. There are other desktops you can choose from, and some which emulate the gnome2 desktop you are used to, but if you simply upgrade your 10.04 installation to 12.04, you wil be presented with the Unity desktop which will be unfamiliar to you. It is an excellent working environment with a dock but takes some getting used to after the panel/menu based environment you have at the moment. This is another thing you might want to consider.need

---

### Post by martinr on 2013-11-09
I'm also still on 10.04 because I can't get used to Unity.
Have a look at: [considering upgrading from 10.04LTS to 12.04LTS ]("http://ubuntuforums.org/showthread.php?t=2148394").
I'm considering XUbuntu 12.04 LTS now.

---

### Post by david98 on 2013-11-09
If would download xubuntu and have a play around with it. It is not recommended you use an end of life product as you get no security updates.

---

### Post by Jake Sweeney on 2013-11-12
you should be able to install Gnome 3.10 on Ubuntu 13.10, which would be different to the Uity shell-interface. To install Gnome 3.10 on your Ubuntu machine type the following into the terminal: 

"sudo add-apt-repository ppa:gnome3-team/gnome3-next"
followed by:

"sudo apt-get update"

Then:

"sudo apt-get install gnome-shell ubuntu-gnome-desktop"

---

### Post by oldfred on 2013-11-12
I use Ubuntu but with Classic or the old top & bottom bars with menus. My monitor is 4:3 so using space on the side is less useful. 

       Install 12.04.1 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things - Forum does not seem to allow wordpress sites? changes to * missing http://  and .com
                    [       ]("http://*********************.com/") d[ebianhelp.wordpress]("http://*********************.com/")


    Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)

      
 12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by monkeybrain20122 on 2013-11-12
> **Jake Sweeney said:**
> you should be able to install Gnome 3.10 on Ubuntu 13.10, which would be different to the Uity shell-interface. To install Gnome 3.10 on your Ubuntu machine type the following into the terminal: 

"sudo add-apt-repository ppa:gnome3-team/gnome3-next"
followed by:

"sudo apt-get update"

Then:

"sudo apt-get install gnome-shell ubuntu-gnome-desktop"

Yeah I am sure that is useful for OP. Gnome-shell is more similar to Unity than it is to gnome2 but even more radical in its departure from the "classic desktop paradigm". If someone still sticks to 10.04 because he can't let go of gnome2 he is going to have a massive heart attack when he sees gnome shell. :)

---

### Post by martinr on 2013-11-13
> **david98 said:**
> If would download xubuntu and have a play around with it. It is not recommended you use an end of life product as you get no security updates.
I followed your advise an went on and downloaded an XUbuntu 12.04.3 live CD, that seemed to work and went ahead and installed it.

Now I have nothing but trouble ([look over here]("http://ubuntuforums.org/showthread.php?t=2167092&p=12847109#post12847109")). X sometimes not starting, hibernate not working, after resume from suspend a frozen touch-pad and haywire keyboard input. Responsiveness feels sluggish. 

It's like I'm in 1997 again.

The same hardware ran Ubuntu 6.04 LTS (dapper), 8.04 LTS (hardy) and 10.04 LTS (lucid), before without any problems.

---

