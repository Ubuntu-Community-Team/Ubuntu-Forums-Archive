---
title: "&quot;File Edit View...&quot; not part of FF windows"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by ubunt10 on 2012-03-08
I just installed Ubuntu 11.10 and opened Firefox. My back button and address bar are part of the same window that web pages and tabs are part of. But then I try to click a button on the menu that looks like this. 
> File Edit View History Bookmarks Tools HelpIt is not part of the same window. It is in the bar all the way at the top of my monitor, above the desktop. I do not want it there. 

How do I get that Firefox menu to be part of the normal menu like most of my other programs? 


Thanks.

---

### Post by forrestcupp on 2012-03-08
Unfortunately, that's a new "feature" of Unity, called the global menu. Whatever window has the focus will have its menus in the global menu bar at the top. They wanted to force this change so much that they didn't make it optional. So your choices are to either install and use Gnome Shell, which doesn't screw with your apps like that, or to [follow these instructions](http://www.addictivetips.com/ubuntu-linux-tips/how-to-disable-global-menu-in-ubuntu-11-10-tip/) to force it to be disabled.

I've heard they may make it optional in a future release.

---

### Post by Diametric on 2012-03-08
Give Unity a try and see if you like it.  I did and found myself installing Gnome - but it's at least worth giving it a shot.

---

### Post by ubunt10 on 2012-03-08
> **forrestcupp said:**
> Unfortunately, that's a new "feature" of Unity, called the global menu. Whatever window has the focus will have its menus in the global menu bar at the top. They wanted to force this change so much that they didn't make it optional. So your choices are to either install and use Gnome Shell, which doesn't screw with your apps like that, or to [follow these instructions]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-disable-global-menu-in-ubuntu-11-10-tip/") to force it to be disabled.

I've heard they may make it optional in a future release.

I tried that link before creating this thread and it did not work. I tried it again and this is what I saw. 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package appmenu-gtk is not installed, so not removed
Package appmenu-gtk3 is not installed, so not removed
Package appmenu-qt is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It claims none of those are installed, but I rebooted and it does the same thing. Any suggestions? 

> Give Unity a try and see if you like it.  I did and found myself installing Gnome - but it's at least worth giving it a shot

I think this would normally be a great idea, but I have to use Windows at work. So it is a pain to keep expecting a button to be somewhere it isn't when I switch back and forth between Windows and Ubuntu.

---

### Post by forrestcupp on 2012-03-08
Wow. That's the only way I've seen to disable it.

In that case if Unity is not your thing, you may just want to try out Gnome Shell. You can install it from the Software Center. Then when you log out, you can click the gear icon next to your user name in the login screen and choose Gnome instead of Ubuntu when you log in. I like Gnome Shell a lot, and it leaves the menus in the app's window.

If you have space on your hard drive, it's worth at least checking Gnome Shell out. If you don't like it, you can just uninstall it. But for now, that's just how Unity works, like it or leave it. Hopefully they'll make the global menu optional in future releases.

---

### Post by Diametric on 2012-03-08
I think this would normally be a great idea, but I have to use Windows at work. So it is a pain to keep expecting a button to be somewhere it isn't when I switch back and forth between Windows and Ubuntu.[/QUOTE]

Which is exactly why I switched back to Gnome shell

```
sudo apt-get install gnome
```

---

### Post by jerome1232 on 2012-03-08
> **Diametric said:**
> 
Which is exactly why I switched back to Gnome shell

```
sudo apt-get install gnome
```

and by that you mean gnome-shell

Am I the only one that get's an eye twitch every time someone says "gnome is better than Unity", Unity is built on Gnome3 people, the difference is Gnome-shell vs Unity, both are on Gnome 3. Both are Gnome ...gah.

---

### Post by forrestcupp on 2012-03-08
> **jerome1232 said:**
> and by that you mean gnome-shell

Am I the only one that get's an eye twitch every time someone says "gnome is better than Unity", Unity is built on Gnome3 people, the difference is Gnome-shell vs Unity, both are on Gnome 3. Both are Gnome ...gah.

You're right. But it's probably confusing to some people when they go to choose which DE to log into and they're options are Gnome and Ubuntu.

---

### Post by Diametric on 2012-03-08
I could care less if Unity is built on/from Gnome - the Unity interface, IMHO, is subpar, while the Gnome environment does what I want it to do.  It seems like you're splitting hairs when asserting your irritation, as opposed to contributing to the OP issue.

Cheers.

---

### Post by jerome1232 on 2012-03-08
Yes, I am splitting hairs, it's annoying. It's like someone calling firefox chrome repeatedly, it's not correct. Your preference for which one is better suited to your needs is irrelevant to what you call it.

I am contributing since apt-get install gnome wont install gnome-shell, whereas apt-get install gnome-shell will, as I stated in my post.

---

### Post by Diametric on 2012-03-08
Fair enough, mate - your annoyances could be better communicated though.  Try being helpful or take the time to politely educate as opposed to "you know what makes my eye twitch".  Most of us are still learning this and are trying to help others who are doing the same.

Cheers.

---

### Post by jerome1232 on 2012-03-08
> **forrestcupp said:**
> You're right. But it's probably confusing to some people when they go to choose which DE to log into and they're options are Gnome and Ubuntu.

I agree, and it's a funky (yes, funky) naming convention on the part of the Ubuntu devs in my opinion.

The reason for the menu being up there in unity is an upcoming feature, the HUD, which actually looks pretty interesting imho.

---

### Post by jerome1232 on 2012-03-08
I apologize if I came off as abrasive I didn't mean to, I didn't mean it as "you irritate me" I meant "it annoys me that it's so common for people to say"

---

### Post by forrestcupp on 2012-03-08
Well, like Diametric said, a lot of people are still learning this stuff, so it's probably better to just teach them. ;)

Until recently, the Gnome desktop environment was just called Gnome, and everyone knew what you meant when you said "Gnome". Now you have multiple shells built on top of Gnome, so it's still a relatively new thing to *not* just call it Gnome.

But for people who are learning, in case it hasn't been made clear yet, Gnome's user interface is called Gnome Shell. If you have Unity installed, you already have Gnome installed because Unity is just a shell that uses Gnome's framework. If you want to use Gnome's user interface instead of Unity, then Gnome Shell is what you are looking for, and you would use the previously mentioned command:
```
sudo apt-get install gnome-shell
```

---

### Post by Diametric on 2012-03-09
Thanks for clearing that up.  If the apt-get command you mention is run, can we then safely remove Unity with a

```
sudo apt-get remove Unity
```

?

Thanks!

---

### Post by Erenith on 2012-03-09
> **ubunt10 said:**
> I just installed Ubuntu 11.10 and opened Firefox. My back button and address bar are part of the same window that web pages and tabs are part of. But then I try to click a button on the menu that looks like this. 
It is not part of the same window. It is in the bar all the way at the top of my monitor, above the desktop. I do not want it there. 

How do I get that Firefox menu to be part of the normal menu like most of my other programs? 


Thanks.

 I don't know if this will work on Unity, or if this is exactly what you prefer, but if you right click on the part of Firefox with the tabs and select "Menu Bar" and it becomes unchecked, that should get rid of the menu and it will become condensed into one button where you can select all menu option of firefox through that button (It will be on the Firefox window).  I apologize if thats not exactly what you are looking for, but it might get rid of the menu on that bar.

---

### Post by 3rdalbum on 2012-03-09
After a little bit of getting used to it, then you will "automatically" move your mouse to wherever the menu is. If there's no menubar in the program, you'll go to the top panel. This will happen without you even thinking about it.

The global menubar is done primarily to save space on the screen, giving you more space for your work/content.

> **Diametric said:**
> Thanks for clearing that up.  If the apt-get command you mention is run, can we then safely remove Unity with a

```
sudo apt-get remove Unity
```

?

Thanks!

The parts of Unity you can safely remove only take up a couple of megabytes anyway. Besides if you install Gnome Shell and for any reason you lose 3D acceleration, you'll have nothing to fall back on. Unity 2D is preinstalled and can work without 3D acceleration, so you might as well keep Unity installed. You can switch between desktops from the login screen.

I would suggest that you give Unity a fair try; a lot of people here stick with Unity after using it for a week or two. I think Gnome Shell is wonderful but I always find myself back at Unity.

---

### Post by forrestcupp on 2012-03-09
I'm with 3rdalbum about just keeping Unity. It doesn't take up much space, and it will save you *a lot* of headaches if you just leave it on there.

After you have Gnome Shell installed and you log into it, you'll never have to choose it again. Every time after that, it will automatically log into the last desktop environment you used. So you don't even have to think about Unity being there.

I agree with 3rdalbum about keeping Unity installed, but I'll have to disagree about wasting your time trying to get used to it. Some people grow to like Unity. But for me, I couldn't justify forcing myself to like it when I loved Gnome Shell from the first time I used it. First impressions mean a lot.

---

### Post by ubunt10 on 2012-03-09
I used this command:
> sudo apt-get install gnome
It prompted me for my password and I installed it. 

Then I read more of this thread and used this command afterward. 
> sudo apt-get install gnome-shell

The Terminal returned this.
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-shell is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I rebooted my computer. For the first time, when I first booted, I saw "Debian" in the lower-right corner of the monitor. (That was before even seeing the purple screen.) 

However, I logged in and my interface is exactly the same.

---

### Post by jerome1232 on 2012-03-09
You have to press the gear icon, and select the session you wish (Gnome in this case) After you do this once it will remember your choice in the future

---

### Post by ubunt10 on 2012-03-09
> **jerome1232 said:**
> You have to press the gear icon, and select the session you wish (Gnome in this case) After you do this once it will remember your choice in the future

It worked. My interface is different. Can I now customize it to be like Windows XP? I am hoping to have everything I minimize at the bottom of the screen and nothing whatsoever at the top and sides. Is that possible?

---

### Post by maniandram on 2012-03-09
> **ubunt10 said:**
> I just installed Ubuntu 11.10 and opened Firefox. My back button and address bar are part of the same window that web pages and tabs are part of. But then I try to click a button on the menu that looks like this. 
It is not part of the same window. It is in the bar all the way at the top of my monitor, above the desktop. I do not want it there. 

How do I get that Firefox menu to be part of the normal menu like most of my other programs? 


Thanks.

You can install KDE (A great desktop environment).
sudo apt-get install kubuntu-desktop
Just log out and choose KDE and log in.

---

### Post by jerome1232 on 2012-03-09
Linux has quite a few interfaces avaible

Here are some screenshots and summaries of the more popular ones, maybe that will help.

[http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce)

---

### Post by ubunt10 on 2012-03-09
I bookmarked that link with pictures of each interface. KDE looks the closest to Windows and I used the command (given in this thread) to install it. 

I noticed that the command has "kubuntu" in it. When I start a thread in this forum from now on, should I start tagging the title with "[kubuntu]"?

---

### Post by jerome1232 on 2012-03-10
> **ubunt10 said:**
> I bookmarked that link with pictures of each interface. KDE looks the closest to Windows and I used the command (given in this thread) to install it. 

I noticed that the command has "kubuntu" in it. When I start a thread in this forum from now on, should I start tagging the title with "[kubuntu]"?

It will clue people into the fact that your using kde without you having to say it specifically so yeah :D

---

### Post by ubunt10 on 2012-03-10
Okay. Just for clarification:  Is KDE considered a GUI? Is it more than a GUI? Is it correct to say that kbuntu is not an operating system, but rather a convenient label for KDE with Ubuntu? Is it pronounced "kay-ubuntu" or "koo-boon-too"?

---

### Post by cmcanulty on 2012-03-10
try classic gnome by installing gnome-fallback it is quite tolerable

---

### Post by jerome1232 on 2012-03-10
> **ubunt10 said:**
> Okay. Just for clarification:  Is KDE considered a GUI? Is it more than a GUI? Is it correct to say that kbuntu is not an operating system, but rather a convenient label for KDE with Ubuntu? Is it pronounced "kay-ubuntu" or "koo-boon-too"?

KDE is a Desktop Environment, it includes a suite of programs, the window manager, your file browser, etc... Gnome, Xfce, LXDE and etc... are all Desktop Environments, this means they not only shape how your interface works, looks and feels but they come with an entire suite of desktop applications, from your music player to your browser.

[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)

TL;DR, yes Kubuntu is just Ubuntu with KDE instead of Gnome.

---

### Post by Krytarik on 2012-03-10
> **ubunt10 said:**
> Is it pronounced "kay-ubuntu" or "koo-boon-too"?
And yes, it's pronounced "koo-BOON-too" :D :

[http://en.wikipedia.org/wiki/Kubuntu](http://en.wikipedia.org/wiki/Kubuntu)

Regards.

---

