---
title: "Firefox's matter ... ???"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-06
Generally, when i download a file, firefox will opened a small download's window for me.
Let's say ... if I minimize both windows.
The window, which able to be re-maximized is the download's window only.
I unable to maximized the FF's main window.

**Is it normal?** how can it be solved?

In order to re-maximized the main window is:
I select **the downloading file**, and **open the download page**.

---

### Post by wilee-nilee on 2012-07-06
I might be helpful to name your desktop being used, in all the ones I use unity or gnome 3 the main FF window is available as well as the download window.

If you are using unity you should see a little dot left of the icon in the left panel I believe, just clicking the FF icon should bring up both I believe.

I rarely use unity anymore though I may not have this correct.

---

### Post by czgirb on 2012-07-07
> **wilee-nilee said:**
> 
... If you are using unity you should see a little dot left of the icon in the left panel ...

Yup I see it! If the download's window was showed ... it will be 3 dots/triangle.
But no matter which dot/triangle I click, the main FF's window would not show up.
How can it be fixed?

---

### Post by wilee-nilee on 2012-07-07
> **czgirb said:**
> Yup I see it! If the download's window was showed ... it will be 3 dots/triangle.
But no matter which dot/triangle I click, the main FF's window would not show up.
How can it be fixed?

Hard to tell if this is just user error, or not understanding the desktop, or you have tweaked say compiz, or who knows what, you might just try ```
unity --reset
``` in the terminal to reset the desktop.

---

### Post by krustenBrot on 2012-07-07
What if you double click *the icon in the side panel*? Unitys default behavior is to open the last opened window if clicking on a stack of minimized windows. 
Double clicking ti should bring up both windows and you can choose the one to reopen.

---

### Post by czgirb on 2012-07-07
> **krustenBrot said:**
> What if you double click *the icon in the side panel*? Unitys default behavior is to open the last opened window if clicking on a stack of minimized windows. 
Double clicking ti should bring up both windows and you can choose the one to reopen.
No matter, which I click ... **dot/triangle or Firefox's icon** ... the only show up window is the **download's window** only. the main window would not show up.
In order to make the main window to show up, I required to **choose the downloaded file**, **right-click**, and click **open the download page**.

---

### Post by krustenBrot on 2012-07-07
> No matter, which I click ... **dot/triangle or Firefox's icon** ... the only show up window is the **download's window** only.  Sorry. I must have gotten this wrong. Just wanted to see if it may be some Unity / User conflict  ;)
Have you tried using something like [this]("https://addons.mozilla.org/en-US/firefox/addon/download-statusbar/")? What if You open up 2 main windows? Should be the same. If not it is specific to the downloads window.

---

### Post by hypnot0ad on 2012-07-07
What happens when you try to ALT+TAB back to the main FF page?

Or;


Can you set up FF so that when you download something the little window doesn't pop up at all, and using a folder to get to your download, instead of the mini pop up?

---

### Post by blackbird34 on 2012-07-07
> **hypnot0ad said:**
> What happens when you try to ALT+TAB back to the main FF page?

Or;


Can you set up FF so that when you download something the little window doesn't pop up at all, and using a folder to get to your download, instead of the mini pop up?

A good firefox addon for that purpose is "Download Statusbar". It removes the Downloads window (stops it popping up) and keeps all your Downloads in a Chrome-like bar at the bottom. You can even reduce it to being a tiny little drop down menu on the addon bar.

To avoid  problems like your one with yuour firefox windows, I usually have a dock (Docky) on the other side of the screen opposite the Unity Launcher, which has icons for open applications only. That way i can haz the best of both worlds :D

---

### Post by czgirb on 2012-07-07
> **krustenBrot said:**
> 
...  wanted to see if it may be some Unity / User conflict ...


How to check it out? Please guide me.

According to what you said, the Download Statusbar is a HELP ... as you said ... it looks like Chrome. ;)
Can we change the Statusbar in a New Tab? Like Opera did.

> **blackbird34 said:**
> 
 ... I usually have a dock (Docky) on the other side of the screen ... 

Would you mind for doing a favor by telling which docky, is recommended?

---

### Post by vasa1 on 2012-07-07
> **hypnot0ad said:**
> What happens when you try to ALT+TAB back to the main FF page?
...
+1
With Unity, I find that Alt+Tab helps spread out **all** the windows and then tabbing will identify the desired window.

---

### Post by robtygart on 2012-07-07
Try Changeing your Theme.

---

### Post by kedarlasane on 2012-07-07
First Reboot your system.Then Try If any problem persist comment below

---

### Post by czgirb on 2012-07-13
The problem still occur even if I re-start the computer.
To do **Alt+Tab** and to give **Unity a Reset** ... SORRY! I'm not try it yet!

But now I change my **Unity** into **Gnome Classic**, so ... the problem is none.
Since using **Gnome Classic**, I think I don't need the **download status** add-ons anymore, so I remove it. But after it was removed and restart the Firefox:
now ... both my **Download **and** DownThemAll** won't work.
The **Download** windows will work only if I open it before I click the download link.
Regarding to the **DownThemAll** it won't work at all.
Why?

---

### Post by blackbird34 on 2012-07-13
> **czgirb said:**
> How to check it out? Please guide me.

According to what you said, the Download Statusbar is a HELP ... as you said ... it looks like Chrome. :wink:
Can we change the Statusbar in a New Tab? Like Opera did.

Would you mind for doing a favor by telling which docky, is recommended?

There are three docks I know of, "Docky", "Cairo-Dock" and "Avant Window Manager". Docky just sits there and acts like a dock and keeps out of the way, the other two are more advanced, more flashy and have more options.
They are all in the Software Center, you can look for them and read the reviews and make your choice and install them from there.
To install via command line : 
```
sudo apt-get install docky
``` or
```
sudo apt-get install cairo-dock
``` or
```
sudo apt-get install avant-window-navigator
```
and each will pull in several dependencies, mostly applets and addons. 

I have never used Opera much, so I don't really see what you are talking about, I don't know , but you can always right-click the status bar (= the "Addon bar") and "Customize" it (and the whole of Firefox) to your hearts content. 
For more information and questions about firefox functionality you can post in the [Firefox Mega thread]("http://ubuntuforums.org/showthread.php?t=1712247"), there is a great Ubuntu member running it and answering all the problems

---

### Post by czgirb on 2012-07-13
> **blackbird34 said:**
> 
I have never used Opera much, so I don't really see what you are talking about, I don't know , but you can always right-click the status bar (= the "Addon bar") and "Customize" it (and the whole of Firefox) to your hearts content. 

Sorry ... I never talked about Opera here.

> **blackbird34 said:**
> There are three docks I know of, "Docky",  "Cairo-Dock" and "Avant Window Manager". Docky just sits there and acts  like a dock and keeps out of the way, the other two are more advanced,  more flashy and have more options.
They are all in the Software Center, you can look for them and read the  reviews and make your choice and install them from there.
To install via command line : 
```
sudo apt-get install docky
``` or
```
sudo apt-get install cairo-dock
``` or
```
sudo apt-get install avant-window-navigator
```and each will pull in several dependencies, mostly applets and addons. 
....
For more information and questions about firefox functionality you can post in the [Firefox Mega thread]("http://ubuntuforums.org/showthread.php?t=1712247"), there is a great Ubuntu member running it and answering all the problems
Thank you for your guidance to **Dock **and thank you for show me the way **where to ask** ... So, the thread was marked as **SOLVED**. Cos I moved to the thread given.

---

