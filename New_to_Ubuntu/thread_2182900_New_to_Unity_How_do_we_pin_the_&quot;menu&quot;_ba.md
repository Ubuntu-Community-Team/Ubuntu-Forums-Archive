---
title: "New to Unity: How do we pin the &quot;menu&quot; bar BACK onto the application window?"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by Jim_Granite on 2013-10-22
How do we pin the application menu bar back onto the application window?

I've successfully moved the window control to the right corner:
$ sudo apt-get install unity-tweak-tool
[unity-tweak-tool]Window Controls->Alignment->Right

But, I haven't been able to get the application menus to stay with the application window. :(

This is (super) frustrating because:
a) Those fixed application menus belong with the application window itself, and, 
b) Those fixed application menus _still_ have the close buttons in the wrong location, and, 
b) You have to constantly hunt all over the screen for this hidden fixed menu just to iconify or close an application.

For example, **how do I bring the application menu, pinned to the top left of the screen (by default), onto the top of the Gimp window** (where they belong)?
[ATTACH=CONFIG]247168[/ATTACH]

Going through all the options in the unity-tweak-tool, I've made "some" progress:
/usr/bin/unity-tweak-tool
[unity-tweak-tool]Window Controls->Alignment->Right
[unity-tweak-tool]Window Manager->Window Snapping->Off
[unity-tweak-tool]Window Manager->Hot Corners->Off

But, still, the application menus appear fixed to the desktop and not to the application window where they belong.
[ATTACH=CONFIG]247169[/ATTACH]

---

### Post by QIII on 2013-10-22
Hello.

To get the global menu items back on the windows, do 

```
sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt
```

You might also want to remove firefox-globalmenu.

---

### Post by Jim_Granite on 2013-10-22
> **QIII said:**
> Hello.
To get the global menu items back on the windows 
$ sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt

I was hopeful when I tried that, and rebooted; but it made absolutely no difference in Ubuntu 13.10:
$ sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt
$ sudo reboot

But, after I rebooted and started Gimp, the application menus were _*still*_ in the wrong place:
[ATTACH=CONFIG]247170[/ATTACH]

**Q: What's the trick to simply get Ubuntu 13.10 application menus back where they belong, at the top of the application window itself?**

---

### Post by QIII on 2013-10-22
Hmmm...

Try reinstalling them

```
sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt
```

and instead of remove use autoremove.

---

### Post by squakie on 2013-10-23
I thought this was a long standing "issue" with unity - if a window is not maximized the "control" portion of the window still remains in the unity top bar.  Perhaps this was updated somewhere along the way and I didn't know it.

---

### Post by 3rdalbum on 2013-10-23
The menu changing thing should have worked, but you can't move the close button for maximised windows.

Nothing is in the "wrong location", everything you have described is in exactly the correct location for where it was programmed to be.

If you just reverse your changes and live with it for a week, you'll adapt. Unity is not Gnome 2, you have to expect some differences.

---

### Post by vanadium on 2013-10-23
To disable the global menu in Ubuntu 13.10, remove following packages ([http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu](http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu)):
```

sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu

```
As such, you lose the application menu of new gnome 3 applications (evince, file, ...). To also have these menu's integrated in the application menu bar, run the following command ([http://www.webupd8.org/2013/02/how-to-disable-gnome-shell-appmenu.html](http://www.webupd8.org/2013/02/how-to-disable-gnome-shell-appmenu.html)):
```

gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '@a{sv} {"Gtk/ShellShowsAppMenu": <int32 0>}'

```

Following commands revert both changes
```

gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '@a{sv} {}'
sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu

```

---

### Post by Jim_Granite on 2013-10-23
> **vanadium said:**
> To disable the global menu in Ubuntu 13.10
sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '@a{sv} {"Gtk/ShellShowsAppMenu": <int32 0>}'


I ran those commands verbatim, but, nothing changed (**the application menus are *still 10 inches away*** from the application window!):
$ sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu
$ gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '@a{sv} {"Gtk/ShellShowsAppMenu": <int32 0>}'
(After those two commands, nothing changed - the menus are still 10 inches away from the application window)
$ sudo reboot
$ gimp &
(After rebooting, nothing changed - the menus are still 10 inches away from the application window)
[ATTACH=CONFIG]247175[/ATTACH]

Perhaps you meant *these* commands? (which I'll try next & report back after the reboot):
$ sudo apt-get **remove** appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu
$ gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '@a{sv} {"Gtk/ShellShowsAppMenu": <int32 0>}'
(After those two commands, nothing changed - the menus are still 10 inches away from the application window)
$ sudo reboot
(Woo hoo! After rebooting, the application menus are pinned back onto the application window, where they belong!)
$ gimp &
[ATTACH=CONFIG]247176[/ATTACH]

Thank you for your help! 
It was so extremely frustrating to have the menus so many inches away from the applications
How did you **find** this wonderful fix anyway?

---

### Post by vanadium on 2013-10-24
Sorry indeed: I copied the wrong command on the wrong place. I have edited my post. I have included some references as well.

---

### Post by Jim_Granite on 2013-10-24
> **vanadium said:**
> Sorry indeed: I copied the wrong command on the wrong place. I have edited my post. I have included some references as well.

Thanks for updating, so that others aren't led astray.

The suggested fix is working (sort of).

What I mean by "sort of" is that the window menus are now clearly associated with the windows, which is a relief. And, the window controls are at the top right, again (which is a given requirement for dual-boot Windows/Linux systems).

However, whenever a windows is full screen (which happens a lot, unfortunately), it's sheer frustration to unpin the window. Basically, now I have to figure out how to ensure that a window is NEVER full screen.

For, when it's full screen, the window controls dissappear from the top right, and move (inexplicably) over to the top left, where I don't want them. So, I find that I'm constantly doubleclicking on the top bar of the window to ensure that the windows are NEVER full screen.

This is a crazy use model, of course. One would have thought that the Ubuntu team would have tested this before implementing it. 

Having had a Mac since the early days, I realized long ago WHY Apple put the menus on the top left on the absolutely tiny screens of the basically single-tasking machines of the 80's and early 90's. And, I also understand why Apple (once they realized their mistake when monitors got bigger and cpu's faster such that multiple applictions could run), couldn't go back and correct the mistake. 

What I don't understand though, is why, in this day and age, Ubuntu repeated the age-old Apple mistake of the 80's, without thinking this through even to the very next logical step.

Sigh.

---

### Post by 3rdalbum on 2013-10-24
> **Jim_Granite said:**
> For, when it's full screen, the window controls dissappear from the top right, and move (inexplicably) over to the top left, where I don't want them. So, I find that I'm constantly doubleclicking on the top bar of the window to ensure that the windows are NEVER full screen.

This is a crazy use model, of course. One would have thought that the Ubuntu team would have tested this before implementing it.

In Unity, the window buttons sit on the LEFT by default. When a window is full-screen, the window buttons appear on the LEFT of the top panel. Nothing crazy about that. It's consistent.

Now, if you go around changing hidden settings, you have to expect that some of the consistency in the desktop will be broken. It wasn't like you ticked a checkbox in a GUI, you used dconf-editor. The Ubuntu team did not "implement the option" of moving the window buttons, it's been an option in Gnome for years and the Ubuntu team made a conscious decision not to expose that function in the GUI - because it breaks consistency. Removing the option from dconf-editor would disadvantage the people running Gnome 3 on their Ubuntu desktops, so that's why the option is still around, albeit hidden in dconf-editor.

Unity is a desktop designed to save screen space - and that's no "mistake". 7-inch, 10-inch and 13-inch screens are not uncommon these days. Even on a large screen (I have a 22-inch monitor) it's better to be able to use your screen space for your work, instead of using it for lots of operating system and application chrome that is only used 10% of the time. Hence, the global menu and the disappearance of the window titlebar when you maximise a window. There are other space-saving features of Unity such as the Launcher (on the left side - otherwise wasted space on a widescreen monitor) and the overlay scroll bars.

I'm not ranting, I just wanted you to realise that there are design decisions in play on the Unity desktop, and just because you can't modify it to make it work like Gnome 2 doesn't make it illogical or deficient.

---

### Post by Jim_Granite on 2013-10-25
> **3rdalbum said:**
> It's consistent.
I very much appreciate your explanation, and, I certainly don't disagree with you.
When the window controls are left at the LEFT corner defaults, it's consistent.
It's only when the window controls are put on the RIGHT corner, that the inconsistencies begin to reveal themselves.
> **3rdalbum said:**
> 
Now, if you go around changing hidden settings, you have to expect that some of the consistency in the desktop will be broken.
In my defense, I don't know what's considered a hidden setting and what's not. 
I just know that it should be trivially easy to put your window controls on either corner.

I "guess", if all my other computers were Apples, I'd probably prefer a left control; while if my other computers are RHEL6 or Windows (which they are), then I'd prefer a right control. There's no value to either side, other than consistency with the rest of our equipment.

> **3rdalbum said:**
> the Ubuntu team made a conscious decision not to expose that function in the GUI - because it breaks consistency. 

It seemed to me that any good developer would enable both, since  roughly 2/3rds (e.g., Linux/Windows) of the systems out there have it on the  right by default, and 1/3 (e.g., Apple) have it on the left by default. So, it would be expected to have a check box, check it, and then be done with it. It should be that easy.

I had no clue WHO made the decision to move the window controls, but, had I made that decision (having been in management of software development teams and customer support for decades), I simply would have enabled the user to choose either corner since there is absolutely no added value in forcing inconsistencies across the users' platforms.

Certainly, I would NEVER have even considered moving window controls from the right corner by default to the left corner by default without that checkbox being in place that allowed the users to choose which corner they prefer (based on their other platforms).
> **3rdalbum said:**
> that's why the option is still around, albeit hidden in dconf-editor.
I didn't actually use dconf-tools. I used unity-tweak-tool instead:
```

$ sudo apt-get install unity-tweak-tool
$ /usr/bin/unity-tweak-tool
[unity-tweak-tool]Window Controls->Alignment->Right

```
Do you think the results would have been better had I used the dconf-editor instead?

> **3rdalbum said:**
> There are other space-saving features of Unity such as the Launcher (on the left side
Oh, if you only knew how much I AGREE with you!
for example, I have a 1920x1080 monitor, where up:down screen space is PRECIOUS!
Yet, most applications put the menus on the top, which wastes your precious up:down vertical real estate!

In fact, I've been posting for at least a decade on the USENET that it's more efficient to have all menus on the SIDES for such monitors!
I've even been an active participant in the longest-ever Gnome bug that prevents the desktop "launcher" from being on the sides!
* [**Bug 86382**]("https://bugzilla.gnome.org/show_bug.cgi?id=86382") -        Fix window list on vertical panels (with possible rotation)      *

> **3rdalbum said:**
> 
I'm not ranting, I just wanted you to realise that there are design decisions in play on the Unity desktop

I do appreciate your clarifications, especially as I'm wholly unaware of the design decisions being made.
I managed software development teams for a very long time, and, I know that most customers want usability first and foremost, while most developers consider algorithmic functionality the interesting stuff. The easy stuff (usability) often falls by the wayside, in favor of sheer functionality.
 
The key thing I asked for in this thread I've been able to accomplish with all your help (i.e., how to pin the menus back onto the application window).
That worked fine, except for full-sized windows, where the window controls bounced from the right to the left as a result.

So, I'm working on a simple one-pixel workaround to that bug, which is this thread:
* [How do we ensure that no application window is ever at full size in Ubuntu]("http://ubuntuforums.org/showthread.php?t=2183296") *

---

### Post by The Cog on 2013-10-25
@Jim_Granite

Can I suggest you try Xubuntu? You seem to dislike some of the the same things that I dislike about Unity and I am glad I tried Xubuntu. Not that I want to knock Unity, it's just not to my taste.

---

### Post by Jim_Granite on 2013-10-25
> **The Cog said:**
> 
Can I suggest you try Xubuntu? 

Since I have to reload the OS anyway (due to the Ubuntu 13.10 DVD crashing every time I had it attempt to create a partition), I may try that.
To be unabashedly honest, the main reason I switched from RHEL6 to Ubuntu 13.10 was that I left the employ of one company and I could now put whatever OS I wanted on the PC. 

The main thing I didn't like about RHEL6 was it was way back in the stone age, e.g., it couldn't mount my Samsung Galaxy S3 with Android 4.1.2 (earlier Android OS's worked but Google removed USB in favor of MTP in the newer Android OS's). Also, installing modern video editors was extremely problematic with Yum and the available repositories. 

When I asked my friends which Linux was better, they almost all said Ubuntu (althought none are on 13.10 like I am now). So, that's really the only reason I had chosen Ubuntu 13.10. It was simply the latest Ubuntu available. With so many users, I just blindly figured it worked out of the box. 

I'll do some research on [Xubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29"), to see if it's much better than Ubuntu. Thanks for the suggestion.
> 
Xubuntu's goals are to:[INDENT] provide an easy to use distribution, based on Ubuntu, using Xfce as  the graphical desktop, with a focus on integration, usability and  performance, with a particular focus on low memory footprint. The  integration in Xubuntu is at a configuration level, a toolkit level, and  matching the underlying technology beneath the desktop in Ubuntu.  Xubuntu will be built and developed autonomously as part of the wider  Ubuntu community, based around the ideals and values of Ubuntu.[SUP][[4]]("http://en.wikipedia.org/wiki/Xubuntu#cite_note-Strategy-4")[/SUP][/INDENT]
[INDENT]

EDIT: Looks like this is how to turn Ubuntu into Xubuntu:
[https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)
[/INDENT]

---

### Post by fantab on 2013-10-25
Unity-tweak-tool just brings the hidden dconf settings to the surface. In other words, its changes the dconf settings.
When I was a beginner with Ubuntu, the left side window controls were a welcome change. I had moved from Windows to Linux and have never used Mac. I liked the 'left side' controls idea so much that on all my linux distros I change the controls to the left. The other distros and Desktop Environs, are very consistent with either side window controls.

---

### Post by Vaphell on 2013-10-26
having window controls on the right simply doesn't fit the overall design of Unity.
Left side=opening/managing/closing programs, right side=user session+indicators
Window management fits the theme on the left.

Even if it was possible to have window cpntrols on the right side you would destroy consistency of layout. No window - indicators in their default spot, window open = controls appear in the corner, moving indicators to the left.
Also one of basic rules of UX says corners are best places to put most important features and min/max/close belong to that category. That makes your workaround idea a bad one because depending on the size of the window you'd either obscure the top panel or be required to be very accurate, eg 'hit corner and then go 40px down'.
And in case of standard multimonitor setup you can't even depend on the right border stopping your mouse (you just move onto the 2nd display), so you need to be very precise, which is not required on the left side (corner/border)

---

### Post by Jim_Granite on 2013-10-26
> **fantab said:**
> The other distros and Desktop Environs, are very consistent with either side window controls.
I agree. 
If a developer is going to change the default, they should at least make sure the prior default works.

> **Vaphell said:**
> having window controls on the right simply doesn't fit the overall design of Unity
This is an interesting position.

---

### Post by fantab on 2013-10-26
> **Jim_Granite said:**
> I agree. 
If a developer is going to change the default, they should at least make sure the prior default works.


However, Unity design is consistent with Ubuntu, which AFAIK always had left side window controls. If you look at Unity, the top bar also functions as a Titlebar-menu bar for maximized windows and as such is very 'space-saving'... if you consider this the design makes sense. Where else will you have your windows controls? On the right you have your Usercontrol,clock and systray. 

Unity has left hand window control as 'prior default'. It was designed and built for Ubuntu. 
The others DE's seem consistent because the don't have Unity. I didn't mean that Unity has a design flaw and other's don't. 

My two cents...

---

### Post by The Cog on 2013-10-26
> **fantab said:**
> However, Unity design is consistent with Ubuntu, which AFAIK always had left side window controls.. 
Ubuntu defaulting the window controls to the left is a fairly recent feature - just in maybe the last 3 years, I think. Until the introduction of Unity it was very easy to put them back where you want them again.

---

### Post by Jim_Granite on 2013-10-27
> **The Cog said:**
> Ubuntu defaulting the window controls to the left is a fairly recent feature - just in maybe the last 3 years, I think. Until the introduction of Unity it was very easy to put them back where you want them again.

While I don't have extensive experience, I must agree that, at least the 10.x Ubuntu's had window controls in a workable location.
Anyway, I've pretty much been forced to modify my default use model to make Unity workable; so, that's a good thing (as I'm less frustrated now).

So that others can also have as good a use model as possible, here's what I've done to solve the use model issues:

0. The very first thing to do is turn off these problematic settings:
$ sudo apt-get install unity-tweak-tool
$ /usr/bin/unity-tweak-tool
[unity-tweak-tool]**Window Controls->Alignment->Right**
[unity-tweak-tool]Window Manager->Window Snapping->Off
[unity-tweak-tool]Window Manager->Hot Corners->Off

1. **All windows are opened at less than full screen resolution** (the drawback being that we lose available pixels, of course). 
* (Luckily, the windows seem to remember their last location, so, that prevents most of them from going full size.)*

2. I've learned to **NEVER doubleclick on the top border of ANY window** (as that moves the window controls to the left!).
*[Is there a setting that will disable the full-screening that occurs when we doubleclick on the top window border?)*

3. I've **disabled pop-up windows** as much as I could (particularly for browsers), by any method I can
* (e.g., pop-up blocker, [mvp hosts file]("http://winhelp2002.mvps.org/hosts.htm"), etc.)*

4. Optionally, I moved the Firefox tab close button to the right also (but this is unrelated to the Unity window-control bug)
*    [Firefox]about:config->browser.tabs.closeButtons=3  (default is 1) *

With these changes, the window (and tab) controls stay to the right, for the most part, which is a blessed relief.
If you have further ideas for use-model consistency improvement, please let me know. 
(I'm going to mark this solved, in the interim.)

Thanks for your expert, kind, and patient help! Much appreciated!
(I hope I can pay it forward, in the future.)

---

### Post by vanadium on 2013-10-27
I am not sure why you should stick with unity (or gnome) as many design decisions do not suit your taste. If I were you, I would seriously consider Xubuntu, which has matured into a highly configerable desktop. It has the added benefit of having a lighter footprint. Cinnamon, the desktop of Mint, could also be a good option. There is no point in fighting one desktop, as in linux, you have the choice to select the one that suits me best.

The reason I remove the global menu is not because I do not like it (quite the opposite), but because issues remain. Notably, Alt+menu hotkeys are not supported for LibreOffice, which is a central piece of software. Since 13.10, I experience a slowness in loading the correct menu, which is notable with Gimp: when switching to the gimp, the global menu for a short time is still filled with the menu of nautilus or something else. Small issue, but severely interrupting the work flow. However, if you fundamentally dislike the global menu + several other features of Unity, then do not hesitate to move to a desktop environment that suits you better.

---

### Post by Jim_Granite on 2013-10-31
> **fantab said:**
> I liked the 'left side' controls idea so much that on all my linux distros I change the controls to the left.
I agree. On Windows and on Linux, I've always had my menus on the sides, and not on the top or bottom, where screen real estate is limited.

In fact, ever since I had an HD dimensioned screen, I've argued NOT to use the up:down space of such monitors, whether Windows or Linux.

It turns out that *most* operating systems allow us to put controls on the side, but, of course, [there's that infamous Gnome bug]("https://bugzilla.gnome.org/show_bug.cgi?id=86382") which makes side panels useless.
[http://youtu.be/NczFOlvaR9A](http://youtu.be/NczFOlvaR9A) [http://youtu.be/wdwaVfu2HHk](http://youtu.be/wdwaVfu2HHk)                            

Luckily, Unity Ubuntu 13.10 does not seem to suffer from that infamous Gnome affliction.

---

