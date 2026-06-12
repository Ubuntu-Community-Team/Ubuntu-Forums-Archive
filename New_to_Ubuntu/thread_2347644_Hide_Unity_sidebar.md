---
title: "Hide Unity sidebar"
date: 2016-12-27
forum: New to Ubuntu
---

### Post by Malacath on 2016-12-27
I don't really like the Unity sidebar being there while I'm browsing the Web.

I can find the auto-hide feature but that auto-hides the sidebar permanently.

Is there a way to set it to only auto-hide when there is a window open in maximised mode?

I want to sidebar to be there at other times but if I switch a program to full screen mode using the maximise window option I would like the sidebar to hide

Is this possible?

---

### Post by jimmy-frydkaer on 2016-12-27
You need to install Unity-tweak-tool

```
sudo apt install unity-tweak-tool
```

---

### Post by vanadium on 2016-12-27
That won't help. There is no such option. You can either show the launcher permanently or have it hidden.

---

### Post by Malacath on 2016-12-27
Ok. Thanks for replying.

I did further searching and found out how to create desktop icons. So now the sidebar being permanently hidden isn't as much of a problem.

---

### Post by Frogs Hair on 2016-12-28
Enter appearance preferences> behavior to autohide the launcher. I recommend turning the reveal sensitivity up for better response time.

---

### Post by Ogden on 2016-12-29
Install a dock, e.g. plank, add whatever apps you wish to it and set the behavior to "window dodge".

---

### Post by ricochu on 2017-01-02
> **Frogs Hair said:**
> Enter appearance preferences> behavior to autohide the launcher. I recommend turning the reveal sensitivity up for better response time.

Hi Frogs Hair,

The issue is that the Autohide in Ubuntu is always hidden unless you move your mouse over, I and others would like it to show when on desktop and only hide when a window covers the launcher. Do you know where we can lodge feedback/suggestions for Ubuntu? This should be an option and would like to suggest that Ubuntu adds it as a 3rd option (no autohide, autohide and intelihide). I've switched away from the main Ubuntu/Unity version multiple times purely because of this missing feature.

---

### Post by yetimon_64 on 2017-01-02
> **ricochu said:**
> ... This should be an option and would like to suggest that Ubuntu adds it as a 3rd option (no autohide, autohide and intelihide)...
Once upon a time in the very early days of Unity the "Window Dodge" option was one of the options available for use with the launcher. The devs took it out as Unity was developed further (myself, I have no idea why they did so). On Natty (11.04) I believe you could set both the launcher to "window dodge" and place it on the bottom of the screen, both of these features later were removed but from 16.04 you can again put the launcher on the bottom of the screen like in the early days of Unity. I hope the window dodge feature is returned one day soon, if possible, as well.

>  Do you know where we can lodge feedback/suggestions for Ubuntu?
There used to be a site, I think it has been shut down nowadays, where you could post feature requests for the devs to consider; I haven't seen it used or mentioned in many years around here though, someone else should know if that site is still available or not now.
 
In the meantime, until that feature is returned (if it ever is), the suggestion by Ogden a couple of posts up is what I use to get a dock/launcher with intelligent hiding capabilities in Unity. Cairo dock is what I use on the bottom of the screen with the Unity launcher set to autohide; when another dock is installed I will often set the Unity launcher sensitivity and edge pressure settings up in such a way as to disable the use of the launcher even if the mouse touches the activating edge (I set that activating edge setting to the top left corner to minimize any accidental usage of the launcher as well).

---

### Post by ricochu on 2017-01-02
> **yetimon_64 said:**
> 
In the meantime, until that feature is returned (if it ever is), the suggestion by Ogden a couple of posts up is what I use to get a dock/launcher with intelligent hiding capabilities in Unity. Cairo dock is what I use on the bottom of the screen with the Unity launcher set to autohide; when another dock is installed I will often set the Unity launcher sensitivity and edge pressure settings up in such a way as to disable the use of the launcher even if the mouse touches the activating edge (I set that activating edge setting to the top left corner to minimize any accidental usage of the launcher as well).
I've done that previously and it kind of works but then I find when I minimise a program (eg: Firefox) it'd minimise to the left side of the screen where its located on the sidebar rather than down to the dock. Find it annoying and being abit OCD hard to deal with :P.

Hope someone can provide a link or email for giving suggestions as this really should be included in my option.

---

### Post by yetimon_64 on 2017-01-02
> **ricochu said:**
> I've done that previously and it kind of works but then I find when I minimise a program (eg: Firefox) it'd minimise to the left side of the screen where its located on the sidebar rather than down to the dock. Find it annoying and being abit OCD hard to deal with :P...

Were you using cairo-dock or some other dock application ? 

I am currently booted into Unity (I also have the DE choices of xfce or ubuntu-studio etc) with the launcher hidden and the reveal pressure set to 1000 (to stop it accidentally popping up) I tried minimizing two file manager windows, a ccsm window and firefox; they all minimize to either the launcher icon on the dock (when they have one there) or to the running applications section of the cairo-dock (if they don't have a launcher on the dock, there is a running apps section for any icons of running apps). Either way they all minimize to the cairo-dock, including firefox here (see next screenshot thumbnail, repeatedly clicking any of the 4 icons marked as being minimized will toggle them between minimized and restored to the desktop). 
[ [IMG]https://dl.dropboxusercontent.com/u/30874719/UF/cairo-dock_with-4-minimized-windows_thm.png[/IMG] ]("https://dl.dropboxusercontent.com/u/30874719/UF/cairo-dock_with-4-minimized-windows.png")
Thumbnail, click for larger image.

Just be aware if the dock already has a launcher on it for the application being minimized, that is where the application will minimize to; if the app doesn't already have a launcher for it on the dock and you have launched the app from elsewhere and minimize it, it will be located to the running apps section of the cairo-dock.

I definitely don't see the behaviour you describe above when using cairo-dock as a replacement launcher where minimizing and maximizing applications is concerned. You may want to consider checking out cairo-dock if it were some other dock application that behaved as you describe above. Cheers, yeti.

P.S. I still can't remember the name of the feature requests/suggestions site that used to be for requesting/suggesting new features in Ubuntu, I'll keep on checking/looking around for it (if it still exists).

---

### Post by vasa1 on 2017-01-02
> **yetimon_64 said:**
> ...
P.S. I still can't remember the name of the feature requests/suggestions site that used to be for requesting/suggesting new features in Ubuntu, I'll keep on checking/looking around for it (if it still exists).
It had something to do with "brainstorm". I'm pretty sure it's closed down. Too many suggestions. Too few coders.

[http://askubuntu.com/a/321291](http://askubuntu.com/a/321291)

---

### Post by yetimon_64 on 2017-01-02
> **vasa1 said:**
> It had something to do with "brainstorm". I'm pretty sure it's closed down.
Yes, that's it "Ubuntu Brainstorm". Thanks.

@ ricochu,
> Hope someone can provide a link or email for giving suggestions...
Maybe this next link can help point you in the right direction ...  [[COLOR=#0000ff]Where can I send feature requests?[/COLOR]]("http://askubuntu.com/questions/28440/where-can-i-send-feature-requests") (from [noparse]askubuntu.com[/noparse]). Hope you do manage to get it back, it would be real nice to have that feature again (but I won't hold my breath waiting for it to happen, could take a very, very, long time if it ever happens). 

If you do find or log a bug classified as a [wishlist] request for this feature, please post a link to it here. That is one feature I'd re-open a launchpad account to support.
However one of the responses to the OP at the link I posted above states something most users asking for such features should at least be aware of ...

> Most feature requests are ignored, regardless of the venue. There simply are not enough volunteer developers to respond to the constant flood of requests. The best way to add a feature to Ubuntu is to create it, or find it in the wild and package it, or to help a project or team that is working on it. &#8211; user535733

Cheers, yeti.

---

### Post by Frogs Hair on 2017-01-02
> **ricochu said:**
> Hi Frogs Hair,

The issue is that the Autohide in Ubuntu is always hidden unless you move your mouse over, I and others would like it to show when on desktop and only hide when a window covers the launcher. Do you know where we can lodge feedback/suggestions for Ubuntu? This should be an option and would like to suggest that Ubuntu adds it as a 3rd option (no autohide, autohide and intelihide). I've switched away from the main Ubuntu/Unity version multiple times purely because of this missing feature.


I don't know of any plans for window dodging/smart hide for Unity 7+ with a new version of Unity on the way .

---

### Post by trivialpackets on 2017-01-03
> **ricochu said:**
> I've done that previously and it kind of works but then I find when I minimise a program (eg: Firefox) it'd minimise to the left side of the screen where its located on the sidebar rather than down to the dock. Find it annoying and being abit OCD hard to deal with :P.

I completely understand.  I had the same issue and went to Ubuntu-gnome to avoid this and just used the Dash to dock plugin for gnome.  From my experience, Unity works extremely well if you're willing to work with Unity in the same manner as the developers have designed it to be used.  It works well, is very efficient and quite polished as well, so long as you don't go against the grain.  I consider it a great environment, but not for everyone.

---

