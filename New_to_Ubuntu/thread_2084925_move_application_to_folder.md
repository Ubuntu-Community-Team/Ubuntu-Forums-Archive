---
title: "move application to folder"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by BeeeZeee on 2012-11-16
I would like to move Freecell to the Games directory. 

Freecell is in location:

/usr/share/app-install/desktop

Games directory is in the Home directory.

I tried this in a terminal:  mv freecell games

There is another game (GNUBackgammon) that I would like to move also but I would like to move them individually so that I can get some practise using the terminal.

So if you could help this beginner, I would appreciate it.

Bernie

---

### Post by cortman on 2012-11-16
That sounds like an odd place for the binary. To find out where the binary file actually is, run

```
which freecell
```

Next, why do you want to move it? Tell us what you're trying to accomplish, and we may be able to suggest a simpler way to do it.

---

### Post by BeeeZeee on 2012-11-16
In order to play Freecell Solitaire I have to do this:

Select Home , left pane select files system, select usr directory, select share directory, select app-install, select desktop, select FreeCell Solitaire.

Now that's a lot of selecting to play a game. I am still thinking of how I would do it in a Windows environment or a Mac for that matter. I am looking for a simple way of bringing up the game. I thought if I could create a folder in Home and call it "Games", I could then put Freecell in there and click on it and it would open up and I could start playing.

I guess I'm not use to the filing system on Ubuntu.

Bernie

---

### Post by newb85 on 2012-11-16
Yeah, you don't want to do that.  What you would do in a Windows or Mac environment is move a shortcut for the app from the default location to a more convenient location.  What you're trying to move is the actual binary file (not a shortcut), and moving it will probably cause problems.  Typically, one does not launch that kind of application by navigating to the binary in the file browser.

If you're running a newer version of Ubuntu, click on the Dash Home (at the top of the launcher on the left) and start typing freecell.  Much easier than navigating to a binary or a shortcut.

---

### Post by BeeeZeee on 2012-11-16
To newb85

I went to the dash and typed in freecell and a icon of a letter came up with a capital A and a small a, below that I believe is the file name, aisleriot:freecel I.desktop

I know that is not what will bring up freecell.  I tried to take a screen shot of it but was unable to.

---

### Post by BeeeZeee on 2012-11-16
Forgot to tell everybody that I am using Ubuntu 12.04. I'll have to update my profile.

Bernie

---

### Post by BeeeZeee on 2012-11-16
I figured out how to do a screenshot.


[IMG]http://i287.photobucket.com/albums/ll140/berzem/th_dash.png[/IMG]

---

### Post by BeeeZeee on 2012-11-16
Thumbnails don't work on this forum?

You may see this better.


[IMG]http://i287.photobucket.com/albums/ll140/berzem/dash.png[/IMG]

---

### Post by newb85 on 2012-11-16
Hmm...seems to be a weakness in the search engine built into the Dash.

Typing "free cell" will bring up FreeCell, but typing "freecell" or even "FreeCell" will not.  Similarly, "aisle riot" works for bringing up AisleRiot, but not "aisleriot".  Don't know where this inconsistency originates.

---

### Post by deadflowr on 2012-11-16
Nevermind newb85 posted exactly what I was gonna say.

Edit: Open the dash, go to the bottom, click the second icon, go to the right side click filters, choose games, then click the installed button on the main pane and scroll to find freecell.

---

### Post by newb85 on 2012-11-16
Aha! The search issue I mentioned is a bug.  Please mark it as affecting you to bump up the priority of its correction.

[https://bugs.launchpad.net/ubuntu/+source/unity-lens-applications/+bug/999765](https://bugs.launchpad.net/ubuntu/+source/unity-lens-applications/+bug/999765)

---

### Post by BeeeZeee on 2012-11-17
> Edit: Open the dash, go to the bottom, click the second icon, go to the  right side click filters, choose games, then click the installed button  on the main pane and scroll to find freecell.Thanks deadflowr

That is a whole lot easier way of bringing up the application.

> 
Typing "free cell" will bring up FreeCell, but typing "freecell" or even "FreeCell" will not.newb85

I typed "free cell" in the dash and it did come up.

Thanks to you both for helping me out. I am going to leave this open until tomorrow morning to see if any more suggestions come up. If no more suggestions , I'll mark it solved.

Thanks again and good night. Bernie

---

### Post by cortman on 2012-11-17
Looks like I'm a bit late in coming now. :) Glad you got it figured out.
You can also "pin" the Freecell icon to the launch bar on the left; when it's open just right click the Freecell icon and select "Pin to dock" or some similar option.

---

### Post by BeeeZeee on 2012-11-17
Cortman, thanks for the suggestion of pinning to the launch bar. Is there a limit to the number of icons that can be pinned?

---

### Post by Vaphell on 2012-11-17
no, but you will have to scroll if they don't fit. Also you can shrink the icon size down to 32px (default 48px) so more icons will fit at once - right click on desktop and select 'change background'

---

### Post by offgridguy on 2012-11-17
> **BeeeZeee said:**
> In order to play Freecell Solitaire I have to do this:

Select Home , left pane select files system, select usr directory, select share directory, select app-install, select desktop, select FreeCell Solitair

Bernie

I wouldn't want to do that either, with  12.04/unity  i click on dash, freecell is visible in 
apps. click it and there it is ready to go.:)
   If you haven't used it in a while you may need to click the *view more option.

edit; cortman's suggestion would get my vote.

---

### Post by BeeeZeee on 2012-11-18
> no, but you will have to scroll if they don't fit. Also you can shrink  the icon size down to 32px (default 48px) so more icons will fit at once  - right click on desktop and select 'change background'     Vaphell, the is a good suggestion to change the size of the icons. I'll do that today.

> edit; cortman's suggestion would get my vote.I agree offgridguy and I have already done that (pin to launcher).

Thanks to all of you that have made suggestions. It is much appreciated.

Bernie

---

