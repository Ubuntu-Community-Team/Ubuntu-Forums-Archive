---
title: "[SOLVED] XSane totally fills screen"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-08-26
Hi community!

I just managed to install my Epson V200 scanner in Hardy (it worked OK in Gutsy) but I found a strange problem.

Preview works OK but when I make a full scan (depending on the final image size) then the viewer screen takes over my whole screen & cannot then be closed.

I Googled about this & found several reports of the same problem, but no solutions...

All suggestions (even just escape routes) gratefully received!

Thanks!

---

### Post by marufaberlin on 2008-08-26
what's your screen resolution?

what size are the images you scan?

can you choose "save" instead of "viewer" before scanning and open the file in a different program? The XSANE viewer is not the best image viewer I know... It has a few problems with zoom too.

A problem I often find with GTK+ Applications is that the windows become "jumpy" if they are larger than the screen and move if you focus them. Is that the case?

have you installed compiz? If yes, is the plugin "Wobbly Windows" activated?

---

### Post by 2CV67 on 2008-08-27
Thanks for your reply.

Screen resolution is 1280 x 1024

I was just playing with XSane to see if/how it works, having only just re-installed my scanner.
I let it run it's default settings: A4 - 300dpi - binary
This makes a 1.1MB image.
Nothing excessive!

I had never heard of compiz or wobbly windows, but a check in Synaptic shows compiz is installed (must be standard - is that why I get grey dimming windows?).
I don't know if wobbly windows is installed or not.
I have certainly not installed it.
I have not yet found out how to check that (still Googling...).
Am I better with/without wobbly windows & with/without compiz?

> A problem I often find with GTK+ Applications is that the windows become "jumpy" if they are larger than the screen and move if you focus them. Is that the case?
Sorry - I don't quite follow that...

I suppose I could "save" but I would prefer to try getting XSane to work, if it's just a question of setting/correcting something.

In the meantime, I found I could "escape" by "Alt-Tab" then closing the Xsane window - not very elegant, but better than switching off the PC!

---

### Post by 2CV67 on 2008-08-27
> A problem I often find with GTK+ Applications is that the windows become "jumpy" if they are larger than the screen and move if you focus them. Is that the case?

Further playing around shows that when the Viewer window is "big" (covering the Ubuntu desktop panel) then if I hover the mouse cursor over any of the Viewer buttons (rotation, zoom etc) then the screen does indeed get "jumpy" - I couldn't put it better!

If I use Alt/Tab to bring up the little XSane window, then I get the desktop panel, but lose the Viewer buttons.

I tried uninstalling & reinstalling XSane, with no effect.

Any suggestions?

Thanks

---

### Post by 2CV67 on 2008-08-27
I added Configuration Editor in the Applications > System Tools menu, so can now see stuff about compiz & wobbly, but I don't understand any of it...

I could certainly answer simple questions or upload screenshots of anything relevant...

Thanks! (said hopefully...)

---

### Post by 2CV67 on 2008-08-28
> **marufaberlin said:**
> can you choose "save" instead of "viewer" before scanning and open the file in a different program? The XSANE viewer is not the best image viewer I know... It has a few problems with zoom too.

Yes, that works OK so no urgency to get XSane viewer working, I suppose.

I would still like to know how to fix it though, if anybody has any ideas...

---

### Post by marufaberlin on 2008-08-30
well, can you maybe post some screenshots?
what happens if you scan an area of 32*32 pixels or so?
a small area at a low resolution?

pleas post screenshots of those situations.

---

### Post by zepotus on 2008-08-30
Same problem here!!

If i scan small picture (that fits in screen) then viewer works BUT pictures i want to scan are always bigger. So the automatic zoom doesn't work.

If i choose SAVE to picture target it works okay. But it makes more job, because i want to see picture scanned before i save it.

I have compiz working, but it makes same thing without compiz.

I think this is small flying thing that is between relay contacts... :(

BUG.

---

### Post by marufaberlin on 2008-08-30
Could be :)

---

### Post by 2CV67 on 2008-08-30
Deleted - sorry!

---

### Post by 2CV67 on 2008-08-30
marufaberlin said:
> well, can you maybe post some screenshots?
what happens if you scan an area of 32*32 pixels or so?
a small area at a low resolution?

pleas post screenshots of those situations. 

Thanks for your interest!

Screenshot of preview (OK):

[ATTACH]83418[/ATTACH]

Screenshot of small scan (OK):

[ATTACH]83419[/ATTACH]

Screenshot of bigger scan (less than half page at min resolution, 300 dpi)
This takes up all the screen.
Sometimes "jumpy" at this stage - not always:

[ATTACH]83420[/ATTACH]

If I try to close from the previous screen, I get this grayed out screen & can only escape by Alt/Tab:

[ATTACH]83421[/ATTACH]

So that is the problem.

Thanks for any suggestion.

---

### Post by marufaberlin on 2008-08-31
Ok, I agree with Zepotus, I think its a bug.

Have a look at [http://www.xsane.org/xsane-contact.html](http://www.xsane.org/xsane-contact.html) 

But otherwise, I'm baffeled. :confused::-k

---

### Post by 2CV67 on 2008-09-01
I was digging around on the XSane homepage, hoping for clues, when I came across this request on the "contact" page:
> If you have problems and you are not sure if your problems are caused by XSane or by the backend you use please try if the problem also occurs when you scan with scanimage or xscanimage.

I had never heard of scanimage or xscanimage, so I Googled a bit & found scanimage was a terminal-based scan frontend (so not for me) but xscanimage was a GUI frontend.
I looked in Synaptic with no success, but a bit more Googling suggested it was usable through GIMP.
(Sorry if everybody else knew all this - I didn't).

I went : Applications > Graphics > GIMP > File > Acquire > xscanimage > epkowa:libusb:004:006 (that's my Epson V200...)
and then > "Preview Window" which gave a decent preview
and > "Scan" which gave a decent scan in a viewer window which can be as big or small as I like but never gets out of hand or freezes.

I noticed I could also go : Applications > Graphics > GIMP > File > Acquire > XSane > epkowa:libusb:004:006
This opened the usual XSane window (but without the option button for scan/view & a few other details).
The usual XSane preview window can be opened via the menu.
A scan can be made from the Scan button, but this does not open the XSane viewer, it opens the same viewer as using xscanimage, with no problem of getting out of hand or freezes.

I have not attempted to compare these various methods of scanning, in terms of flexibility, scope & convenience, but clearly entering via GIMP avoids the major problem of XSane viewer freezing, at least for me.

---

### Post by 2CV67 on 2008-09-21
I contacted Oliver Rauch (Mr Xsane...) & he said:

> the problem with the viewer window will be solved in xsane-0.996

So that sounds hopefull.

---

### Post by CEB2nd on 2008-09-21
Try disabling visual effects before you open XSane.

Right-click your desktop > change desktop background > visual effects > none

---

### Post by 2CV67 on 2008-09-21
> **CEB2nd said:**
> Try disabling visual effects before you open XSane.

Right-click your desktop > change desktop background > visual effects > none

Thanks, CEB2nd, that fixed it instantly!

I had been on the default "normal" setting and am not interested in fancy visual effects.

Not sure what I am losing with that change though - is it defined anywhere?

---

### Post by CEB2nd on 2008-09-21
In June or July of this year I installed a Compiz update listed in the  Pre-Released Hardy-Proposed Updates. The problem with the viewer window was fixed and has never returned. The update made no mention of the XSane problem, but it did fix it.  You might try enabling Pre-Released Hardy-Proposed Updates and Recommended Hardy-Updates in your Software Sources. Let the list refresh itself, then install any Compiz updates you find in Update Manager.  I don't know if the update I installed is still available.

Good luck.

---

### Post by 2CV67 on 2008-09-22
Thanks for that extra suggestion!

As I have 2 satisfactory workarounds now & a promised solution sometime soon from Xsane, I guess I will stick at that.

I am deliberately a "late adopter" to avoid teething troubles as far as possible (I usually only update my Ubuntu version 4 or 5 months after release, etc) so opening the back door to pre-release stuff is something I would only do in desperation!

I really appreciate the information though.

Thanks again.

---

### Post by marufaberlin on 2008-09-22
Well, I am glad you got your problem solved.

I am currently using Intrepid (Pre-Release) and I must say that it is very stable now. I would recommend you the upgrade, as it brings a variety of new features.

---

### Post by corradoventu on 2008-10-05
to me in intrepid (beta?) the problem disappears using appearance visual effects = none

---

