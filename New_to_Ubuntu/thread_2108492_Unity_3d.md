---
title: "Unity 3d"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by BrianV on 2013-01-24
I am setting up a new-to-me desktop with ubuntu 12.04.1 and have a few problems. I'll list them here in case they are related.

1. (The subject of this post): When 12.04.1 was first installed, Unity 3D was running. In trying to solve other problems I logged-off, then logged in in 2D, but that didn't resolve anything. Now I can't get back to the original Unity 3D. I did try unity -reset without benefit. The CPU is a core 2 Duo and the graphics are Intel 82945G/GZ Integrated Graphics Controller.

2. (Other, possibly related problem): This is a dual-boot machine and display rendering seems fine in WinXP (though I haven't tried it much). In ubuntu, rendering of text seems to have random errors - characters will have pixels missing, different characters on different windows, but all instances of the same character on a window will have the same defect. Sometimes the rendering problem applies to a text-surrounding fill that may have a line of missing pixels. The problem shows up in browsing files, in Firefos, and in Libre Office. (The font used for button text on this screen shows 't's very muc like 'i's.)

3. (Other problems, probably not related): In transferring Evolution I have lost my Personal Address Book contents, and Evolution seems to delete messages I try to transfer from Inbox to Save sub-folders.

Never a dull moment!

---

### Post by BrianV on 2013-01-26
Update.

I restarted in recovery mode, opened Terminal and input unity --reset. After lots of activity, including several warnings, my desktop disappeared but the unity and top panels remained. I was able to request a restart, although operating more-or-less blind, and I'm back in 3D!

So I will mark this closed and open another thread for the rendering issue.

---

### Post by grahammechanical on 2013-01-26
The rendering problems might be video driver related. Try a different driver. Open the Additional Drivers utility.

Regards.

---

### Post by BrianV on 2013-01-26
Thanks, Graham. Additional Drivers doesn't find anything available. Is there some other way to find what driver is needed/available?

---

### Post by sandyd on 2013-01-26
> **grahammechanical said:**
> The rendering problems might be video driver related. Try a different driver. Open the Additional Drivers utility.

Regards.
There aren't any - Intel Drivers

> **BrianV said:**
> Thanks, Graham. Additional Drivers doesn't find anything available. Is there some other way to find what driver is needed/available?
Have you tried to see if the drivers at xorg-edgers fixes any of your problems? I have found that graphical corruption, and other problems are fixed by installing drivers from that ppa, nomatter now experimental they may be.

---

### Post by AgentZ86 on 2013-01-26
to get back to unity 3D I'm assuming you have auto login setup or something so you can right click on the upper corner where you simply log out

Then when the login screen appears you will see next to your login name a button to click and select which interfact unity 2d, unity 3d, or if you have other interface installed like LXDE or FluxBox or something

Anyhow whatever desktop you select it will login with that everytime from then forward

Hope this helps

Also I think you can try this too from the console

unity --replace

That won't solve your other problems but it will get you back to desktop

---

### Post by AgentZ86 on 2013-01-26
> **BrianV said:**
> I am setting up a new-to-me desktop with ubuntu 12.04.1 and have a few problems. I'll list them here in case they are related.

1. (The subject of this post): When 12.04.1 was first installed, Unity 3D was running. In trying to solve other problems I logged-off, then logged in in 2D, but that didn't resolve anything. Now I can't get back to the original Unity 3D. I did try unity -reset without benefit. The CPU is a core 2 Duo and the graphics are Intel 82945G/GZ Integrated Graphics Controller.

2. (Other, possibly related problem): This is a dual-boot machine and display rendering seems fine in WinXP (though I haven't tried it much). In ubuntu, rendering of text seems to have random errors - characters will have pixels missing, different characters on different windows, but all instances of the same character on a window will have the same defect. Sometimes the rendering problem applies to a text-surrounding fill that may have a line of missing pixels. The problem shows up in browsing files, in Firefos, and in Libre Office. (The font used for button text on this screen shows 't's very muc like 'i's.)

3. (Other problems, probably not related): In transferring Evolution I have lost my Personal Address Book contents, and Evolution seems to delete messages I try to transfer from Inbox to Save sub-folders.

Never a dull moment!

One thing we need to know is to compare the Ubuntu resolution your useing with the resolution your using in windows XP and see if they are also using the same resolution to further narrow thing down a bit


Are you using Firefox on XP too ?

This could be related to the resolution and the font sizes that are used by the default firefox and ubunty system

Do the fonts on ubuntu seem large ? as if they should be slightly shrunk down to be able to fit into the text field in which they may allow the text to display the T tops better ? 
Sometimes when I put my firefox default text sizes up to high this happens a lot especially when trying to use it on my big screen tv which is too far away to view the small text, so I have to increase this size.
But then some text lines get bundled on top of one another or sometimes the tops of the text gets cut because it's too big to fit into the html field for viewing that size

Anyhow both firefox and the default gnome fonts sizes can be edited and that might solve some of this.

Hope this helps

---

### Post by BrianV on 2013-01-26
Hi sandyd,

O me!

I'm back in XP after following the instructions on the UnuntuUpdates.org site for xorg-edgers: Adding the ppa, then installing xserver-xorg-video-intel package.

This left me, after restart, with a blank screen and message window: "Your screen, graphics card, and input device settings could not be detected properly. You will need to reconfigure these yourself". Pressing Return led to another message window: "What would you like to do?" - followed by radio buttons with three choices, I think, but no further keyboard or mouse response. Is there a way out of this black hole?

---

### Post by BrianV on 2013-01-26
Thank you AgentZ86,

As you'll see from other replies, I have bigger problems at present. But, in both XP and ubuntu I have the same resolution set, I use FF on both, with default settings and the text looks like the same size. The rendering problem is not restricted to FF; it shows in LO,gedit, and the file manager.

---

### Post by BrianV on 2013-01-26
> **AgentZ86 said:**
> to get back to unity 3D I'm assuming you have auto login setup or something so you can right click on the upper corner where you simply log out

Then when the login screen appears you will see next to your login name a button to click and select which interfact unity 2d, unity 3d, or if you have other interface installed like LXDE or FluxBox or something

Anyhow whatever desktop you select it will login with that everytime from then forward

Hope this helps

Also I think you can try this too from the console

unity --replace

That won't solve your other problems but it will get you back to desktop
Thanks, AgentZ86,

I thought this problem (stuck in 2D) resolved itself, before my more recent screw-up. I'll have to check again after getting back operating with ubuntu. I think the problem resolved after I issued a unity --reset command.

---

### Post by frank604 on 2013-01-26
I'm not following on the corrupted fonts in ubuntu.  Could you take a screenshot and upload so we can see what you are seeing?

---

### Post by sandyd on 2013-01-26
Press Control + alt + F2, and login.

Running
```

sudo ppa-purge xorg-edgers
```
will reverse the xorg-edgers ppa back to the default video drivers - xorg-edgers is not compatible with some video drivers.

If ppa-purge is not installed,
```

sudo apt-get install ppa-purge
```

---

### Post by BrianV on 2013-01-27
> **sandyd said:**
> Press Control + alt + F2, and login.

Running
```

sudo ppa-purge xorg-edgers
```
will reverse the xorg-edgers ppa back to the default video drivers - xorg-edgers is not compatible with some video drivers.

If ppa-purge is not installed,
```

sudo apt-get install ppa-purge
```
Thank you, sandyd,

I am back with ubuntu unity 3D, so will continue to check out the rendering issue. Are there any other sources for possible video drivers? And is there anything available for me to better understand what we just went through? - I feel like a complete klutz, following instructions without really understanding their impact, then getting into a hole that I had no idea how to climb out of!

---

### Post by BrianV on 2013-01-27
Thanks to everyone who responded. I have used FF and LO about an hour since recovering ubuntu unity and have not seen the problem at all. That seems to indicate that restoring the original driver, per sandyd's post, has somehow cleared the problem. I'll be interested to see if things remain stable, with the 3D and the rendering problem, but for now will mark both posts solved. Thank you all.

---

