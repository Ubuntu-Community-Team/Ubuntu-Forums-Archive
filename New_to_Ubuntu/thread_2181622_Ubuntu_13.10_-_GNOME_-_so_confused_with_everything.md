---
title: "Ubuntu 13.10 - GNOME? - so confused with everything!"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by jferreir on 2013-10-18
_Quick Background:_
I absolutely hate Windows, so I want to use Ubuntu as the main OS on my desktop computer. I have a separate SSD for each OS, reserving Windows 8 for work/gaming purposes (and syncing iPhone/iPad, if necessary). I haven't fiddled with computers for about 5 years, so I have the technical knowledge of a grandmother (i.e., not much). I briefly installed Ubuntu on my laptop in 2007, but I remember it being much more intuitive and a bit snappier than the current 13.10. I had to remove it because the driver for the wireless card would always crash. 

_Issue:_
I'm not a fan of Unity. I don't like the layout/navigation, and I despise the adware. I read somewhere that I can install the previous GUI, GNOME, but I also read some things about incompatibility and buggy PPAs (whatever those are). Basically, I want to know the following:
- Is GNOME safe, secure, and reliable? 
- Will GNOME remove all adware/privacy concerns?
- Will GNOME be supported for future releases? That is, if I install GNOME, can I continue to update to the newer versions of Ubuntu?
- Can I safely install GNOME/remove Unity without re-installing the OS? I know there's an install file for 13.10/GNOME, but I already installed the standard 13.10/Unity. 

Also, I need some help in figuring out how to best manage my media files and devices. I currently use iTunes with my iPhone 4S and iPad 4 (both iOS 7), and I have my media files/library stored on a separate HDD. To be clear, I have Windows 8 on SSD #1, Ubuntu 13.10 on SSD #2, and all media files (music, movies, etc.) on a third HDD. Ideally, I'd like to keep my music files on the HDD, but still be able to access them in BOTH Windows and Ubuntu, using their respective media programs (i.e., iTunes in Windows, Rhythmbox (or whatever) in Ubuntu). And I would also like to be able to sync my devices directly in Ubuntu so I don't have to reboot every time I need to do this. I know this is a lot to ask, but can it be done?

And is there an idiot-proof guide on what to do after installing Ubuntu? I'm talking about stuff like codecs, GUI tool for tweaking the OS, tricks for speeding up the OS (it seems a bit slow), etc.? The more I read/research, the more confused and scared I get. I just want a free OS that's reliable, fast, pretty, and easy to customize. Not sure if it matters, but I'm using an overclocked Haswell i5, 8GB of RAM, and a NVIDIA GTX 770.

I'd appreciate any help. Sorry for being so clueless :(

EDIT:
I'm open to other distros, if that's what you'd recommend. I just want to make sure that it's adequately supported, fast with robust features, easy to figure out, and visually similar to OS X.

---

### Post by fantab on 2013-10-18
If you don't like Unity, then have you considered Xubuntu, Kubuntu or Lubuntu which come with XFCE Desktop, KDE Desktop & LXDE Desktop respectively?
Unity has Gnome under the hood. Gnome you are talking about is Gnome-Shell... you must try them out yourself to see the difference between Unity and Gnome-Shell. Try them from a USB pen drive.

Since you already installed Ubuntu 13.10, may I suggest 'CINNAMON' which is fork of Gnome-Shell developed by Linux Mint. Its quite similar to older Gnome. You can Install it in Ubuntu along side Unity and choose it from the login screen. You have to click on the small White Ubuntu circle in the login box to choose either Unity or Cinnamon. To install Cinnamon:

```
sudo apt-get install cinnamon
```

Logout and Login to Cinnamon session. 
Linux Mint has also forked Nautilus, the file browser, they call it NEMO, you can install that too: 'sudo apt-get install nemo'.

For you itunes try Banshee:
```
sudo apt-get install banshee
```

Keep trying until you find your flavor of Linux.

Good Luck...

---

### Post by Frogs Hair on 2013-10-18
Installing and using a different desktop such as gnome-session-flashback or Cinnamon will prevent the web search results that are part of Unity from functioning. This search function can be easily disabled from the privacy application.

---

### Post by verymadpip on 2013-10-18
Hi there.
You could install GNOME Shell into your Ubuntu & then choose that (Gnome) instead of Unity (Ubuntu) at boot.  It's in Spoftware Centre, so no PPA needed.
There's a drop down list that appears when one clicks the cog symbol next to the password field at login to do the choosing thing with.
If you prefer the 2 panel look you could try XFCE desktop environment, which is very customizable, & less resource hungry.  (Might speed things up for you a tad).  Again, the cog thing at login.
I don't know if there's a GNOME fallback any more.
Oh, & there's Mate, which I know nothing about.

GNOME Shell & XFCE don't use the dash so you won't be bombarded by internet search results while looking for stuff, but that can be turned off anyway in Unity.

Is your drive set up working as you want it to at the moment?
If so, I see no reason to change anything, but I could be wrong.  Let's see what some other people have to say on that.

Have a look at Ubuntu Restricted Extras in Software Centre, that may be the thing you're after for codecs.

I'm unsure about your devices, let's wait for more help :)
I know nothing about optimization so, yet again, I'll let someone else deal with the important stuff.

Good luck dude :D

Aw gee, beaten to the punch again...

---

### Post by fantab on 2013-10-18
> **Frogs Hair said:**
> Installing and using a different desktop such as gnome-session-flashback or Cinnamon will prevent the web search results that are part of Unity from functioning. This search function can be easily disabled from the privacy application.
+1
Yes offcourse, I forgot to mention that. In fact, I uninstall unity-webapps from my Ubuntu.

---

### Post by jferreir on 2013-10-18
> **fantab said:**
> If you don't like Unity, then have you considered Xubuntu, Kubuntu or Lubuntu which come with XFCE Desktop, KDE Desktop & LXDE Desktop respectively?
Unity has Gnome under the hood. Gnome you are talking about is Gnome-Shell... you must try them out yourself to see the difference between Unity and Gnome-Shell. Try them from a USB pen drive.

Since you already installed Ubuntu 13.10, may I suggest 'CINNAMON' which is fork of Gnome-Shell developed by Linux Mint. Its quite similar to older Gnome. You can Install it in Ubuntu along side Unity and choose it from the login screen. You have to click on the small White Ubuntu circle in the login box to choose either Unity or Cinnamon. To install Cinnamon:

```
sudo apt-get install cinnamon
```

Logout and Login to Cinnamon session. 
Linux Mint has also forked Nautilus, the file browser, they call it NEMO, you can install that too: 'sudo apt-get install nemo'.

For you itunes try Banshee:
```
sudo apt-get install banshee
```

Keep trying until you find your flavor of Linux.

Good Luck...

I went to google and searched for screenshots of each of those desktop environments. Based on that, I still *_much_* prefer GNOME. It's clean, minimalistic, and very much like OS X. Everything else looks like a derivation of Windows, to some degree. The last Ubuntu build I used was 7.10, and I very much liked that look. So, I think I'll stick with GNOME. Is there any practical reason to avoid doing this? 

Is Banshee preferable to the native Rythmbox? Will either of them properly sync to my Apple devices, and what about the location of my music files? Can I share them across the two OS' while still keeping them in the same iTunes library folder?

---

### Post by deadflowr on 2013-10-18
Guess what, unity is gnome.

What you're really asking for is gnome version 2.

That version has gone the way of the dodo bird, and as such is no longer supported by Ubuntu.

However, there is a fork of that called [mate]("http://mate-desktop.org/install/"), which is trying to be a replacement for thew old gnome2 desktop.

---

### Post by jferreir on 2013-10-18
> **deadflowr said:**
> Guess what, unity is gnome.

What you're really asking for is gnome version 2.

That version has gone the way of the dodo bird, and as such is no longer supported by Ubuntu.

However, there is a fork of that called [mate]("http://mate-desktop.org/install/"), which is trying to be a replacement for thew old gnome2 desktop.



Thank you for the clarification. If it's not already painfully obvious, I clearly lack the basic concepts/understanding needed to interpret sound advice.

In light of this revelation, please allow me to repose the question:
- How can I disable all adware nonsense, turn off amazon recommendations, etc? 
- How can I hide the bar on the left?

And now for the doozy... what IS the difference between the current GNOME and GNOME 2? FML.

---

### Post by hhWnd8K on 2013-10-18
I too share you hate for unity and it's ad & spywere. I also like the look and feel of OS X. After a month of hopping around from distro to distro, I narrowed it down to 2 choices Xubuntu or Ubuntu GNOME. I settled on Xubuntu because it's very fast and light weight, it also has a bit of the MAC OS X feel with the button icon bar and other features. Gnome is bit "funky" in my opinion. No minimize button and other odd behavior.   

I would highly suggest you try Xubuntu. 

You can't move or hide the bar in Ubuntu it's fixed there. You can turn off all the online searches in Ubuntu by going to system settings then privacy then moving the slider turning off online searches. But after that, you are still greeted with the Amazon icon on the app screen. You have to start up the file manger as root and browse to your app's folder and delete the amazon app.

But make your life easy :P and just wipe your drive and put in Xubuntu or Ubuntu GNOME. Burn both to a live DVD and then make your choice.



     

> **jferreir said:**
> Thank you for the clarification. If it's not already painfully obvious, I clearly lack the basic concepts/understanding needed to interpret sound advice.

In light of this revelation, please allow me to repose the question:
- How can I disable all adware nonsense, turn off amazon recommendations, etc? 
- How can I hide the bar on the left?

And now for the doozy... what IS the difference between the current GNOME and GNOME 2? FML.

---

### Post by su:bhatta on 2013-10-18
I also, first tried Ubuntu 10.10 Maverick Meerkat and then came back to linux to try 13.04! Was greeted with Unity, which at first i hated, then I learned to live with by using customizations as said above, getting rid of Amazon etc. 

Then I tried Ubuntu with both Xfce & KDE. And finally, inspite of all the bad things I read about Gnome 3, which is currently available in version Gnome Shell 3.8 with Ubuntu Gnome, I quite liked it. 

There are a bunch of "extensions', add-on customizations, available at [www.extensions.gnome.org]("http://www.extensions.gnome.org") which according to me make Gnome 3.8 behave like old Gnome2. I settle for that.
Saying that, Xfce is pretty neat too.

You can add a dock at the bottom in both, using Docky, or in Xfce using its own toolbar and it gives the Mac feel and usefulness.

UbuntuGnome 13.10, seems pretty and fast and really usable.

P.S.: Old Gnome2 used to have a Menu based interface with a dropdown 'Applications' 'Places' & 'Settings' menu, which is not there in  Gnome3 and the Left Corner is made a 'HotSpot' from where you get entire Workspace overview and brings up a dock from where all Programs & Favourite Programs can be accesed. Also, the Tray is at the bottom of the screen, hidden. 

Using extensions all these features can be reverted back to Gnome2 behavior and some new ones can be added.

---

### Post by buzzingrobot on 2013-10-18
Sounds like you need to do a little more research and experimentation to decide what Ubuntu interfce you like best.

XFCE is on Xubuntu.

KDE is on Kubuntu.

Gnome 3 is on Ubuntu Gnome

Unity is on Ubuntu,

You can download live images for each of these, burn them onto a DVD or USB stick, boot them and run them.  Things will be a tad slower than usual, but you will get the chance to see what you like and don't like before you actually install something.

Several other interfaces are available from other sources.  Probably most popular among them are the Cinnamon and Mate interfaces. 

As to whether you should install these interfaces on an existing Ubuntu system, or reinstall directly... well, that's up to you,  Their presence on the drive will not interfere with any other interface you install and use, short of adding entries to menus,

---

### Post by craig10x on 2013-10-18
Actually, Unity is closest to the "mac like experience" as it has a dock (though on the left instead of bottom) a Global Menu a Top Panel and a Search all mac style features...
All you have to do is go into "system settings" and shut off all online searches in the dash search and you are all set...

As far as Gnome...Ubuntu w/unity is Gnome 3...gnome 3 shell is gnome 3....they are just somewhat different desktops...personally, i find unity more "lean and streamlined" then Gnome Shell...
And by the way, before discovering linux and after leaving windows, i spent about a year with a mac and to me unity is closest to a mac feel...
And my friend, who has my old IMAC has his Mac Dock on the left side anyway...i asked him, why did you move it there?  He said: makes more sense over there ;)

---

### Post by fantab on 2013-10-18
> **jferreir said:**
> Thank you for the clarification. If it's not already painfully obvious, I clearly lack the basic concepts/understanding needed to interpret sound advice.

In light of this revelation, please allow me to repose the question:
- How can I disable all adware nonsense, turn off amazon recommendations, etc? 
- How can I hide the bar on the left?

And now for the doozy... what IS the difference between the current GNOME and GNOME 2? FML.

First of all there is NO adware or spyware in Ubuntu. Those web-aps, lets say, integrate some online toos with Unity-Ubuntu desktop. However I don't like them myself and I remove them. You can also disable them.

To Un-install web-apps you can use 'Software Center' or 'Synaptic Package Manager' (you have to install Synaptic: *sudo apt-get install synaptic*) then search for unity-webaps package and remove it.
To Disable them use System Settings -> Privacy.

You can auto-hide Unity-Laucher (that bar on the left) from System Settings -> Appearance. You can also use CCSM (Compiz-config-settings manager), you have to install it. Search in Software Center. After Installing Navigate to 'Unity-Plugin' and you will find plenty other options as well. There are also some tweak tools like 'MyUnity', 'Ubuntu tweak tool' etc. to manage Unity.

Good Luck...



Now, the Gnome you USED was Gnome2... the current version of Gnome is 3. Gnome2 used Panels whereas Gnome3 uses gnome-shell. Unity is a fork of Gnome-shell, just like many others inclucing Cinnamon and Mate (not 100% sure if Mate is).

---

### Post by deadflowr on 2013-10-18
> **jferreir said:**
> Thank you for the clarification. If it's not already painfully obvious, I clearly lack the basic concepts/understanding needed to interpret sound advice.

In light of this revelation, please allow me to repose the question:
- How can I disable all adware nonsense, turn off amazon recommendations, etc? 
- How can I hide the bar on the left?

And now for the doozy... what IS the difference between the current GNOME and GNOME 2? FML.


For better clarity, think of it like this:
unity, gnome-shell, gnome-classic/fallback/flashback, and cinnamon are all just interfaces for the gnome3 desktop environment.
They all, for the most part, share same the basic gnome packages and toolkits.

On to what you ask:
To disable the the scopes and shopping lenses
click on the dash (the icon at the top of the left side panel) and when it opens type privacy.
This will open the privacy section of the system settings.
Forgive me here as I am right now on Precise, so my memory is scant, but I believe there is an option for search.
Choose this option and the tab will move and it will have an entry for "include online results", and a toggle for on/off.
Move the toggle to the off position.
This will disable the online results.

There are ways to completely remove scopes and lenses, but you can find those easy enough doing a web search.

To hide the launcher(left side panel)
if still in the privacy window, click on the all settings button in the top left corner, and it will bring you to the main system setting window.
Go to Appearance and when it opens, go to the section tabbed behavior.( Again, I'm on Precise, so the name might be wrong)
There is a section to enable hiding here.

And finally, what is the difference between gnome3 and gnome2?

Gnome3 uses a revised codebase, which is being designed to fix some of the legacy bugs and problems that where inherent in the gnome2 codebase.
Among other things...

---

### Post by craig10x on 2013-10-19
Yes...you can disable online searches in the "privacy" section of system settings...it is under the search tab...just turn it to OFF...
[ATTACH=CONFIG]247047[/ATTACH]

---

### Post by btolman on 2013-10-19
Daily Gnome user here.  I love the switching and there are a few things that it does very, very fast.

---

### Post by deadflowr on 2013-10-19
> **craig10x said:**
> Yes...you can disable online searches in the "privacy" section of system settings...it is under the search tab...just turn it to OFF...
[ATTACH=CONFIG]247047[/ATTACH]

Hey, look at that.
My memory is better than I thought.:P

> **btolman said:**
> Daily Gnome user here.  I love the switching and there are a few things that it does very, very fast.

Shell?
Is that the gnome you mean?

If so, I like it.
Even though I'm a unity user, mainly.
And I have a fondness for KDE.
Gnome Shell is actually quite usable, and like unity, after a little bit of usage, can become very likable.

But that probably just means I'm a DE glutton.

---

