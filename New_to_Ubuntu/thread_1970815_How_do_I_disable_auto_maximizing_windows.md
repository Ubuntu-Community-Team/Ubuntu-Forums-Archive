---
title: "How do I disable auto maximizing windows"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by gerryl on 2012-05-01
I just upgraded to Ubuntu 12.04 (w/ Gnome 3.4.1) and found a new "feature."  If I move a window such that it touches the upper dash, the window automatically maximizes to full screen.  This is a royal pain.  How can I disable this "feature?"  I looked at gconf-editor and did not see an option to disable this, but perhaps it has some obscure name such that I did not recognize it.

---

### Post by mc4man on 2012-05-01
Depends on what session you are running. 
In gnome-shell it appears to be both a mutter option, path in dconf-editor (install dconf-tools) -  
org.gnome.mutter edge-tiling 
And a shell option - 
org.gnome.shell.overrides edge-tiling

So make sure it's disabled in both, should be in mutter by default so the shell option is the likely one
```
gsettings set org.gnome.shell.overrides edge-tiling false

```

In unity 3d it's the grid compiz plugin, I always disable it. Probably easier to do in ccsm though you could also do in gconf-editor, prefer ccsm here (compizconfig-settings-manager

Either way it will cause compiz to to 'reload' & things may freeze up for several seconds. If not returning then force a logout & all should be ok. (Ctrl+Alt+Delete or Ctrl+Alt+Print+k

(- myself if doing in ccsm would 1st. disable the unity plugin , make the change, wait a few seconds if need be & then re-enable unity.

---

### Post by gerryl on 2012-05-02
Thank you.  Installed Compiz, deselected Grid - worked fine.

---

### Post by alexyz on 2012-05-03
thank you mc4man!!

I'm running the rather unpopular gnome3 shell, I hate this edge tiling thing, and nothing worked, was driving me crazy.

looks like the setting 

>  org.gnome.shell.overrides edge-tiling

overrides the mutter setting, so it should work regardless.

---

### Post by gerryl on 2012-05-07
While I am very appreciative of mc4man's quick and easy soluition to this annoyance, I am concerned that, before posting to this forum I attempted to solve the problem on my own.  I found no reference to it on any help page or manual.  This is dangerously close to operating with MS Windows.  How are us mere mortals supposed to find out and address these kinds of issues?

And Compiz was not much help either.  I knew to deselect Grid from mc4man's directions, but without his input I would have no idea what Grid does or why it should be deselected.

---

### Post by spikn on 2012-05-13
I agree with the above poster.  Why do people love this new interface so much?  There may be a way to use it properly but I haven't found it.  For instance, I often forget if i'm supposed to type ccsm or something else.  If there was a menu I could search through it, but with the current method I'm supposed to always search by typing keywords?  I guess I'd be appreciative if anybody could point to a beginner's guide to working with Unity.

---

### Post by krytorii on 2012-05-13
To find applications, open the dash and there are some options on the right hand side or at the bottom (I forget which) that allow you to select different groups, such as games, office and so on.

---

### Post by PaulW2U on 2012-05-13
> **spikn said:**
> If there was a menu I could search through it, but with the current method I'm supposed to always search by typing keywords?  I guess I'd be appreciative if anybody could point to a beginner's guide to working with Unity.

The official guide for 12.04 can be found at [https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html), for other releases see [https://help.ubuntu.com/](https://help.ubuntu.com/).

---

### Post by markbl on 2012-05-13
> **gerryl said:**
> I just upgraded to Ubuntu 12.04 (w/ Gnome 3.4.1) and found a new "feature."  If I move a window such that it touches the upper dash, the window automatically maximizes to full screen.
It's not a "new" feature. Has been in Ubuntu since 11.04, i.e. this is the third release with it. Like all this stuff, it is a good idea once you get used to it.

---

### Post by DesertF0x on 2012-05-15
In 12.04 there is another new automaximize feature in gnome shell which always starts a application maximized if the window was larger than a certain value on close, does anyone know how to disable this?

---

### Post by arinekhen on 2012-07-05
Since, after installing dconf-editor, I could not find either 
org.gnome.mutter edge-tiling or org.gnome.shell.overrides,

I installed ccsm to see if disabling Grid as mentioned might work, and it did, no more auto-maximize.

I'm very grateful for the helpful information in disabling this feature.

But look at what I went through, to disable a GUI effect. Wow. As much as I love Ubuntu, it STILL tempts me to go back to windows at times. My brother would never have to put up with this on his Mac. How can I argue with him? Ubuntu, after all these years, after all the improvements and refinements, is still geeks-only linux. Like Android, it is fragmented and unnecessarily multi-layered. I'm glad it's an alternative to windows for me. I just wish it was a workable alternative for the general public. Ah well, onward and upward. Thanks again!

---

