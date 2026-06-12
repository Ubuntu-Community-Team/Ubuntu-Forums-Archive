---
title: "newb questions"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by chadwit on 2008-05-10
Allow me to preface by stating that I'm about 10 hrs. into replacing everything I have in XP into the U. So far, I've found that every app I use in XP has the same or better equivalent in Ubuntu. I'm absolutely blown away by how much better this manages memory, CPU time and overall efficiency than M$ OSes. That said, I have a few annoyances/issues that I'm hoping you guys can help me out with:

1) Is there a desktop clock I can install? The little one in the taskbar doesn't cut it. Also, it froze when I installed QBittorrent (very buggy). I don't know if that's related. I just switched to internet time/UTP but haven't rebooted yet. (I assume that's required for those settings to take effect cuz my clock is still frozen...)

2) Currently I'm using GNOME, but I'd like to play with KDE. Is there a way for both of them to co-exist, wherein import my GNOME settings and select which one I'd like to use before loading, or do I have to dust my current install to experience KDE?

3) Is there a more robust, feature-rich, intuitive file manager than the one that installs by default? The default one...well..sucks.

4) There's this extremely annoying popup window that appears every time I download something from a web site. It lists every file I've downloaded since I installed Ubuntu. Is there some way to disable that? Is that a Firefox function? I've searched high and low but so far I've been unable to find a way to shut it off. 

Thank you muchly for your input!!!

---

### Post by SOULRiDER on 2008-05-10
1)
Try gDesklets, you probably want that
[http://gdesklets.de/](http://gdesklets.de/)

2)
You can install the kubuntu-desktop package, thatw ill install KDE and several programs. When you log in you can select what you want formt he session menu. Mind you, both, the KDE and GNOME menus will have the same applications, so theyw ill feel a bit dirty.

3)
I used krusader in KDE, There are several others, but i just cant think of any.

4)
Is the window from firefox? Could you please give us some more info ?


If you have more questions, dont hesitate to ask.

---

### Post by drs305 on 2008-05-10
4. This could be the Firefox download manager. Edit, Preferences, Main, uncheck the Show the Downloads window box.

Some of your other observations have a lot of company but it's a great system!

Welcome to ubuntu.

---

### Post by marty1011 on 2008-05-10
2. In order to install KDE type the following in the terminal
```
sudo aptitude install kubuntu-desktop
```

---

### Post by dorkdork777 on 2008-05-10
1) I find the standard desktop clock is fine; what functionality are you after?

2) Yes, absolutely; [see here]("http://www.psychocats.net/ubuntu/kde"). However, the cluttered menu is a problem that isn't answered there; to get over this, right-click the Applications button in standard Ubuntu once you've installed KDE, and you can uncheck all the KDE-specific tools, such as Konsole, that you won't need in GNOME, and they won't show up in GNOME.

3) You could maybe try Konquerer? I know it's also a web browser, but it's also a very decent file manager.

4) If you're using Firefox to download, then that is indeed a Firefox function. To solve this, go to Edit -> Preferences in Firefox, and in the Main tab, uncheck "Show the Downloads window when downloading a file".

---

### Post by whitethorn on 2008-05-10
> **chadwit said:**
> Allow me to preface by stating that I'm about 10 hrs. into replacing everything I have in XP into the U. So far, I've found that every app I use in XP has the same or better equivalent in Ubuntu. I'm absolutely blown away by how much better this manages memory, CPU time and overall efficiency than M$ OSes. That said, I have a few annoyances/issues that I'm hoping you guys can help me out with:

1) Is there a desktop clock I can install? The little one in the taskbar doesn't cut it. Also, it froze when I installed QBittorrent (very buggy). I don't know if that's related. I just switched to internet time/UTP but haven't rebooted yet. (I assume that's required for those settings to take effect cuz my clock is still frozen...)

2) Currently I'm using GNOME, but I'd like to play with KDE. Is there a way for both of them to co-exist, wherein import my GNOME settings and select which one I'd like to use before loading, or do I have to dust my current install to experience KDE?

3) Is there a more robust, feature-rich, intuitive file manager than the one that installs by default? The default one...well..sucks.

4) There's this extremely annoying popup window that appears every time I download something from a web site. It lists every file I've downloaded since I installed Ubuntu. Is there some way to disable that? Is that a Firefox function? I've searched high and low but so far I've been unable to find a way to shut it off. 

Thank you muchly for your input!!!

1) There a couple things you could try.  
Screenlets ::   [http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home)
Desklets :: [http://www.gdesklets.de/?q=desklet/browse](http://www.gdesklets.de/?q=desklet/browse)
they are small widgets that u can install on ur desktop.
Or you can try setting up Conky and getting it to display the time
Here's a good howto :: [http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

2) You can both Gnome as well as KDE installed on ubuntu.  Just download the kde-base from System -> Administration -> Synaptic Package Manager and at the login screen you can choose to use either Gnome or KDE.

3)I wouldn't know but I heard PCMan File Manager is pretty good.  Not very feature rich but fast. Here's a howto to either install and if you like it then you can replace nautilus (the default windows manager) [http://ubuntuforums.org/showthread.php?t=692238](http://ubuntuforums.org/showthread.php?t=692238)

4) Sorry can't help you here

---

### Post by amninder on 2008-05-10
I have been using ubuntu for a day or 2 and on this site it taught me about Synaptic Package Manager. When I open it it says that I have 1 broken. I have no clue what it means. It also says that I have to fix it with the broken filter. How do I open the broken filter and clean this broken thing?

---

### Post by drs305 on 2008-05-10
> **amninder said:**
> I have been using ubuntu for a day or 2 and on this site it taught me about Synaptic Package Manager. When I open it it says that I have 1 broken. I have no clue what it means. It also says that I have to fix it with the broken filter. How do I open the broken filter and clean this broken thing?

In synaptic, you can find the broken packages by selecting the Custom Filter tab in the lower left and selecting Broken.

---

### Post by c4v3m4n on 2008-05-10
For a clock and other random stuff like that you can install screenlets.  In synaptic you should find it easily.

---

### Post by kansasnoob on 2008-05-10
Well, the first thing I would do is create a dual boot with a "toy" partition, so you can have one partition to deal with reality and the other to just mess with.

It's not hard. If you have an Ubuntu install that's working just well enough to get online but you want another to play with then boot from your Live CD and go to Administration > Partition Editor. Once there you are in Gparted!

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

From there you can shrink your original Ubuntu partition and leave some unused space for any other OS.

I'm doing that with Freespire on one of my computers (actually a triple boot). I just sit and watch while the boot process runs by and when the GRUB menu says I have 10 seconds I hit the ESC button, then I can choose where I want to go.

There are many different dual boot scenarios, most have some great screenshots, check 'em out! Just google/yahoo Ubuntu dual boot.

I YAHOO!

---

### Post by kansasnoob on 2008-05-10
Disregard what I said!

At two days in you just need to learn more. Do you know how to use the terminal? Accessories > terminal? That's gnome terminal.

It's always a safe bet to type in: sudo apt-get update

It'll ask for your password, enter it and hit enter.

If you have an icon in one of the system trays indicating a need for updates, go ahead and update.

Then there are other things to try. Some real simple like:

sudo apt-get -f install

Which may (or may not) resolve all unmet dependences!

Bust out a spiral notebook, hunker down, and learn to love Ubuntu! You really will love it once you learn the basics.

If you break it you can always just start over.

---

### Post by chadwit on 2008-05-11
Thanks for all of your input guys. I really appreciate it.

1) Looks like the desklet thing is what I'm looking for. Conky looks really cool but appears to be a bit too complicated for me at this point as far as the setup goes. 

2) Based on what you're all saying, I guess it's relatively safe to install both KDE & GNOME. As a followup question, can I run GNOME apps with the KDE interface, or do I have to dl duplicate KDE-version apps that I'm currently using in GNOME to use them with KDE? Also, does Compiz run under KDE? If not, is there a KDE equivalent? If so, do I have to reinstall it to use it in KDE, or will KDE see it's already installed?
It would be great if someone could please explain the ins & outs of having both installed. I'm kinda confused on how that would work...

3) Looks like I'm pretty much stuck with the manager I have....oh well.... 

4) It was indeed a Firefox setting. Thanks!

Thanks again for everyone's input!!!!:biggrin::biggrin:

---

### Post by dtrot55 on 2008-05-11
You can also download firefox plugins that will show you your downloads in a different way....i have the download bar that shows your progrss at the bottom of the browser....less annoying and you can still keep track of your downloads.

---

### Post by dorkdork777 on 2008-05-11
Having KDE and GNOME on one partition doesn't really have a parallel in the Windows world, so it's not really "like" anything. But here's the lowdown.

KDE mostly uses a blue colour scheme, and you never double-click in KDE - single-clicks do everything. That also applies to KDE apps, so they don't "fit in" as well as Gnome apps do on Gnome, but they do work on Gnome, and work well. The same applies for Gnome apps on KDE, but in reverse, and they do work fine.

And yes, Compiz-Fusion works great. Basically, if an app works in standard Ubuntu, it will look and work the same in KDE on Ubuntu, and vice versa.

---

### Post by amninder on 2008-05-14
Thanks for the help. I now have one more problem my speakers om my laptop don't work. I know that the speakers are fine because I tried them on my PC. Also the sound button on the sidebar is at full. And it is not muted.Any idea how I might be able to listen to songs? ( If it helps the sound on my laptop speakers and my earphones don't work anywhere but the one that is most important to me is youtube.com

---

