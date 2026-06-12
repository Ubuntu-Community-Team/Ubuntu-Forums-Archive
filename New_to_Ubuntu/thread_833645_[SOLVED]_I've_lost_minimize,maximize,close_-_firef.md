---
title: "[SOLVED] I've lost minimize,maximize,close - firefox and thunderbird"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by anewguy on 2008-06-18
I know there have been many updates that applied to my system over the last few days.  Today I find that in Firefox and Thunderbird I have lost the 3 buttons in the upper right for minimize, maximize and close.  If I select view/full-screen they are there if I force the mouse to the top of the screen.  Otherwise there is just a little gray Ubuntu circle there instead.

What happened and how do I get those buttons back?

Thanks in advance!

---

### Post by anewguy on 2008-06-18
Turns out it's not just Firefox and Thunderbird - the file explorer, games, everything has lost those 3 buttons!

---

### Post by anewguy on 2008-06-18
Okay, for some reason it seems to have something to do with desktop effects, particularly (I think) the window decoration button.  If I uncheck it, I lose those 3 buttons.  Why?

---

### Post by Duck2006 on 2008-06-18
Are you running compiz?

---

### Post by anewguy on 2008-06-18
I sure am - I just didn't think it could effect that part of how a window looks!  :)

---

### Post by Duck2006 on 2008-06-18
Did you try turning it off and see if the missing buttons are back?

---

### Post by nhasian on 2008-06-19
See if this resolves the issue for you.  If it does, dont forget to "thank" me :)

```
metacity --replace
```

Good luck

> **anewguy said:**
> I know there have been many updates that applied to my system over the last few days.  Today I find that in Firefox and Thunderbird I have lost the 3 buttons in the upper right for minimize, maximize and close.  If I select view/full-screen they are there if I force the mouse to the top of the screen.  Otherwise there is just a little gray Ubuntu circle there instead.

---

### Post by anewguy on 2008-06-19
> **Duck2006 said:**
> Did you try turning it off and see if the missing buttons are back?

As mentioned, it is the windows decoration option that hides/shows the buttons - I just don't understand why?

---

### Post by RequinB4 on 2008-06-19
> **anewguy said:**
> As mentioned, it is the windows decoration option that hides/shows the buttons - I just don't understand why?

Compiz is your window manager.  It manages your windows.  Part of managing is doing the borders and making it pretty.  Sometimes it doesn't work well, and you have to turn off a feature.

---

### Post by anewguy on 2008-06-19
> **nhasian said:**
> See if this resolves the issue for you.  If it does, dont forget to "thank" me :)

```
metacity --replace
```

Good luck

Sure -----IF I want to turn of desktop effects!  I would prefer to leave them on!

---

### Post by Immolatus on 2008-06-19
Try F11, some times toggling between full screen mode and regular brings them back.

---

### Post by colbobs on 2008-06-19
> **anewguy said:**
> I know there have been many updates that applied to my system over the last few days.  Today I find that in Firefox and Thunderbird I have lost the 3 buttons in the upper right for minimize, maximize and close.  If I select view/full-screen they are there if I force the mouse to the top of the screen.  Otherwise there is just a little gray Ubuntu circle there instead.

What happened and how do I get those buttons back?

Thanks in advance!

I've recently found this too (firefox only so far) and I wonder if it's a specific website that launches a new simple window (no address bar, no back, forward icons etc).
F11 doesn't help either.  I find my way out of it is to open a smaller window (if I happen to know that the page I am on happens to have someting that will do so), the bars at the top and bottom of the page re-appear and then I can close the offending window.

Not really sure what to do to stop this...
Not sure if I'm running compiz...I'll check when I'm back on my laptop.
Best of luck everyone finding a solution.

---

### Post by nhasian on 2008-06-19
Yeah that's a different issue.  the web page asks your browser to launch the new page without the toolbar.  alt-F 4 will close the window.  or you can use mouse gestures if you have that installed :)

> **colbobs said:**
> a specific website that launches a new simple window (no address bar, no back, forward icons etc).
F11 doesn't help either.

---

### Post by walter_j on 2008-06-21
I'm struggling with the same issue. I have a nvidia 6200 video, and it hasn't worked with hi res and 3d effects since upgrading from 7.10. i wonder if i should wipe and reinstall.

metacity --replace brings back the buttons, but turns off effects. i can live w/o the effects amd compiz, but it bugs me.

---

### Post by nhasian on 2008-06-22
Hello Walter,

Can you tell me the output of:

```
cat /proc/driver/nvidia/version
```

and

```
lspci | grep -i vga
```

Also, what happens when you go to System/Preferences/Appearance and click on the Visual Effects tab?  Can you choose either normal or extra?  Or are they both greyed out?

> **walter_j said:**
> I'm struggling with the same issue. I have a nvidia 6200 video, and it hasn't worked with hi res and 3d effects since upgrading from 7.10. i wonder if i should wipe and reinstall.

metacity --replace brings back the buttons, but turns off effects. i can live w/o the effects amd compiz, but it bugs me.

---

### Post by walter_j on 2008-06-23
walter@walter-ubuntu:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  173.14.05  Mon May 19 00:06:12 PDT 2008
GCC version:  gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
walter@walter-ubuntu:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
walter@walter-ubuntu:~$ 


When i select normal or extra in effects i lose the window borders. 

Thanks

Walter

---

### Post by anewguy on 2008-06-23
You should move your problem over to a different thread.  I already closed this one a few days ago, and your problem is different from that in this thread.

---

### Post by walter_j on 2008-06-23
> **anewguy said:**
> You should move your problem over to a different thread.  I already closed this one a few days ago, and your problem is different from that in this thread.

The problem is similar, but what's wrong with us continuing here? it shouldn't make any difference.

---

### Post by anewguy on 2008-06-23
> **walter_j said:**
> The problem is similar, but what's wrong with us continuing here? it shouldn't make any difference.

Be my guest - but people normally associate "SOLVED" appearing in the title of a message thread as one they don't need to keep following.  You'd get more exposure in your own thread.

---

### Post by Greg K on 2008-10-28
Hit F11 twice to fix Firefox when this happens.

Workaround for Thunderbird:

[http://ph.ubuntuforums.com/showpost.php?p=5705136&postcount=4](http://ph.ubuntuforums.com/showpost.php?p=5705136&postcount=4)

---

### Post by EndoliteMatrix on 2011-08-25
Okay, I ran the original code 
 metacity --replace... Now nothing in compiz works... How can i get it back to a functioning state again ?

---

