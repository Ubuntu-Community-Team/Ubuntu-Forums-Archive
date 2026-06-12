---
title: "Two things I find annoying about Unity"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by kramer65 on 2012-01-04
Hello,

I've been using Ubuntu for about 5 years now and I'm loving it. I've been using Unity for about a week now and very slowly I am getting used to it. There are two things that I find highly annoying though.

First: When I rightclick on an icon in the left panel there is no option for "*Always on top*" anymore (something I use extensively).

Second: When I click the home folder it opens and I move to some folder on my system. I then often want to open another folder so that I can drag-and-drop things around my system. When I click the home folder for a second time though, it doesn't open but just shows the nautilus window I had open already. I cannot figure out how to open another window. There is no right click on the icon and "*Open another nautilus window*" or something like that.

Does anybody have any idea how I can avoid these annoyances?

Thanks in advance!

---

### Post by mcduck on 2012-01-04
For the first one, just right-click on the windows titlebar instead, you'll find the window options (including "always on top") in that popup menu.

...and for the second question, middle-clicking an icon in the launcher panel opens a new window.

(It's also possible to edit the launcher to add things like new window or shortcuts into specific locations into the right-click menu, but that requires editing the launcher file by hand as there isn't currently any graphical tool for the purpose)

---

### Post by kramer65 on 2012-01-04
Ah, thanks for those tips. That helps a lot!

I guess the main problem with Unity is that the learning curve is (in my opinion) a little too steep. I think that I am still fairly okay with trying it for a while even though it doesn't feel comfortable in the beginning. My sister and my girlfriend though (who both use 10.04 now) would never want to learn this, simply because they don't see the advantage of it and don't want the annoyance of learning it.

Well, thanks a lot! I'm back to work.. :) :S

---

### Post by kramer65 on 2012-01-04
One more question. How can I have the icon-panel on the left automatically disappear?

And when I move to the left to get the icon-panel to appear it takes some time for it to appear. How can I speed that up? It is quite annoying in my workflow when it always takes about a second to appear..

---

### Post by mcduck on 2012-01-04
No problem. :)

In the end Unity is actually pretty nice interface to use (at least if you enjoy using keyboard instead of trying to navigate it with mouse only), but I agree that many of the features that make it usable aren't that obvious to the user.

There's a nice guide collection of guides and information available here: [http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity]("http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity"), and I definitely recommend taking a look at the [mouse & keyboard shortcuts]("http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts").

---

### Post by mcduck on 2012-01-04
> **kramer65 said:**
> One more question. How can I have the icon-panel on the left automatically disappear?

And when I move to the left to get the icon-panel to appear it takes some time for it to appear. How can I speed that up? It is quite annoying in my workflow when it always takes about a second to appear..

Both these things can be configured through [CompizConfig Settings Manager]("apt:compizconfig-settings-manager"). Install it if you don't have it already, then go to Unity-plugin's settings. On the Behaviour-tab you'll find a dropdown box that allows you to choose the hiding mode for the left panel, and a slider for adjusting the delay. Also holding down the super key (the one that usually has a windows logo) will show the launcher panel and also shows you the shortcut keys for each launcher icon...

---

### Post by kramer65 on 2012-01-04
Thanks again for those tips.

> **mcduck said:**
> Also holding down the super key (the one that usually has a windows logo) will show the launcher panel and also shows you the shortcut keys for each launcher icon...

To test some python scripts I wanted to have Ubuntu running in a sandboxed environment. As a bonus I thought I'd give Unity a try and I therefore have Ubuntu 11.10 installed in Virtualbox. The windows button is unfortunately my Virtualbox Host-key. Is there any way that I can set another button to be the super key?

---

### Post by audiomick on 2012-01-04
Hi. I'd like to throw in a couple of things.

Firstly, in Nautilus, at least on 10.10, F3 will split the window into two panes. This would allow you to do a drag and drop too.

As far as customising Unity goes, I stumbled upon a thing called MyUnity the other day. It will be in 12.04, it seems, and can be installed on 11.04 and 11.10 from the ppa that you can get here.

[https://launchpad.net/~myunity/+archive/ppa]("https://launchpad.net/%7Emyunity/+archive/ppa")

---

### Post by kramer65 on 2012-01-04
> **mcduck said:**
> On the Behaviour-tab you'll find a dropdown box that allows you to choose the hiding mode for the left panel, and a slider for adjusting the delay.

I just installed the CompizConfig Settings Manager, but it doesn't have any Behaviour tab.

---

### Post by coffeecat on 2012-01-04
> **kramer65 said:**
> I just installed the CompizConfig Settings Manager, but it doesn't have any Behaviour tab.

CCSM -> Desktop -> Ubuntu Unity Plugin -> Behaviour Tab.

---

### Post by kramer65 on 2012-01-04
Ah, thanks. I was kinda lost in the millions of options.

I changed some settings to it, but nothing seems to have any effect. I set the "Hide Launcher" option to Autohide, but it still shows. And I also set the "Edge Reveal Timeout" to 1 millisecond, but it still waits a little while. Do I need to restart or something for it to take effect? Or doesn't it work in Virtualbox?

---

### Post by coffeecat on 2012-01-04
> **kramer65 said:**
> Or doesn't it work in Virtualbox?

This *might* be a problem. First make sure the system has not defaulted back to the Unity 2d desktop, which won't be affected by ccsm settings. You can tell the difference from the top panel. There's a shadow under the 3d version, not under the 2d version.

If you are running 2d and not 3d Unity in VirtualBox, make sure you have the guest addons installed and that 3d is enabled in the guest settings for that virtual machine.

---

### Post by mcduck on 2012-01-04
> **kramer65 said:**
> Ah, thanks. I was kinda lost in the millions of options.

I changed some settings to it, but nothing seems to have any effect. I set the "Hide Launcher" option to Autohide, but it still shows. And I also set the "Edge Reveal Timeout" to 1 millisecond, but it still waits a little while. Do I need to restart or something for it to take effect? Or doesn't it work in Virtualbox?

The changes *should* take effect immediately, but CCSM sometimes seems to "loose connection" with Compiz, requiring you to either log out and back again or reload Compiz.

What comes to binding the super key to some other key, take a look at Keyboard Layout in Ubuntu's settings. Click the "Options"-button and under "Alt/Win behaviour" you'll find plenty of options for this.

---

### Post by mc4man on 2012-01-04
> **kramer65 said:**
> Ah, thanks. I was kinda lost in the millions of options.

I changed some settings to it, but nothing seems to have any effect. I set the "Hide Launcher" option to Autohide, but it still shows. And I also set the "Edge Reveal Timeout" to 1 millisecond, but it still waits a little while. Do I need to restart or something for it to take effect? Or doesn't it work in Virtualbox?

You may be running unity-2d instead of unity(3d

Run this in a terminal, if it returns "ubuntu", you're on unity(3d), otherwise will be obvious
```
echo $DESKTOP_SESSION
```

---

### Post by kramer65 on 2012-01-04
Ah, I guess the 2d thing was indeed the problem. I don't seem to be able to start Ubuntu in the normal mode. Even when I select the normal Ubuntu in the login screen it says unity-2d when I try the "echo $DESKTOP_SESSION".

In Virtualbox I tried selecting the "Enable 3D Acceleration" option, but to no avail. Is there any other option or am I stuck with this 2D version in which I cannot adjust anything?

What does this actually mean for computers which can't run the 3D version? They can never adjust anything (without hacking into the source)? I'm just thinking of people like my sister again who has Ubuntu running on quite an old laptop... :S

Well, Unity would for now be out of her reach anyway, whether her computer would be able to run it or not.

---

### Post by JamButty on 2012-01-04
thanks, moved [here]("http://ubuntuforums.org/showthread.php?p=11586798#post11586798")

---

### Post by mcduck on 2012-01-04
> **JamButty said:**
> More than two, but I'll stick with the OP title...

1. Under Lucid, when searching for a file/directory, I could right click and choose properties to get the location of the file (though the fact that a search function does not automatically show the full path of the file is inexplicable to me). If the file is buried several layers deep or has a very long name, the full path of the file does not show in the standard properties pop-up (Lucid and Oneiric), but under Lucid, I could maximize or resize that window until the full pathname could display. Under Oneiric, there are no more minimize/maximize buttons on search/properties windows (and a few other window I've run into so far), only close. If you resize the window manually, you get a bigger window with lots of nice blank space and no new info! - the path as shown in the originally sized window does not extend into the larger window, meaning I am left to guess where it might be after the first couple of directory levels.

2. Search does not return info on hidden files/directories. Yes. "show hidden files" is checked.

Based on the fact that you are talking about being able to access the Properties window from the search (which you can't actually do from the Dash search), it sure sounds like you are now talking about Nautilus, the file manager of Gnome desktop environment instead of Unity... ;)

Anyway, the full path is there, even though it might not actually fit into the window, but you can still for example copy&paste it and get the full path. And it's not automatically shown because the search might actually return with many files instead of just one, and they could very well be in different locations. There sure isn't room to give full (perhaps rather long) path for each file at the same time.

By the way, the Properties window on my system definitely has all the window buttons...

(Anyway, you should probably make another thread about finding solutions to your problems as they aren't related to the ones discussed in this thread, or Unity...)

---

