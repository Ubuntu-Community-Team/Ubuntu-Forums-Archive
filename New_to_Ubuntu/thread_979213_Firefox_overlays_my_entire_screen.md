---
title: "Firefox overlays my entire screen"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by egruber on 2008-11-11
Since I got 8.1, the updated Firefox completely fills my screen so I cannot see the desktop items such as applications, etc.  I also don't see the top menu bar to minimize and maximize it, and I cannot resize it smaller. To close it, I have to Alt-F4 or File Quit. All the other apps fill the screen in the proper way.  Any ideas why this is happening?  (I checked, and Firefox is NOT in full screen mode)

---

### Post by redseventyseven on 2008-11-11
> **egruber said:**
> Since I got 8.1, the updated Firefox completely fills my screen so I cannot see the desktop items such as applications, etc.  I also don't see the top menu bar to minimize and maximize it, and I cannot resize it smaller. To close it, I have to Alt-F4 or File Quit. All the other apps fill the screen in the proper way.  Any ideas why this is happening?  (I checked, and Firefox is NOT in full screen mode)

1. Do you have menu bars on the rest of your windows?
2. Do you have compiz enabled - does turning it off make any difference?
3. Can you move the firefox window around the screen using the "other" method: Hold down Alt and click and drag anywhere on the window (check that this works on one of your other windows first)?

---

### Post by sonu 1807 on 2008-11-11
Press F11

---

### Post by Crafty Kisses on 2008-11-11
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox

```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any

```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```

---

### Post by egruber on 2008-11-12
Codename...I don't know anything about Compiz.  Where is the Settings Manager and how do I edit it? (I'll try F11 tonight, too).

Redseventyseven...all other programs have menu bars.  I did notice though, that if I change the display attributes to Standard (no fancy swooping graphics) then Firefox displays properly.

---

### Post by shanep-server on 2008-11-12
switch ur background. I did that and it fixed mozilla for me.

---

### Post by egruber on 2008-11-12
Background?  You mean like the desktop wallpaper? Switch it to what?  Or did you mean something in Firefox?

---

### Post by tjwoosta on 2008-11-12
if you hold alt while clicking anywhere inside the firefox window, it should let you drag the window off to one side so you can reach the resize tab

---

### Post by egruber on 2008-11-12
> **Codename said:**
> I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox

```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any

```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```

OK. I installed the Compiz settings manager and found the Windows Decoration line.  I pasted the | class=Firefox so it looked like you said and then closed it (Do I need to add parentheses around 'any'?). I reopened it and then removed what I just pasted and then closed it again.  Was that right? It didn't seem to do anything.

Also, if I hit F11 twice is corrects itself.  Thanks!

---

### Post by Crafty Kisses on 2008-11-12
Yes you need parentheses around any, it should look like this:
```
(any) | class=Firefox
```
Copy and paste that in Decoration Windows, then close Firefox, then reopen Firefox, then switch:
```
(any) | class=Firefox
```
To:
```
any
```
Reboot Firefox and it should work.

---

### Post by jimmy the saint on 2008-11-12
Id bet 10 to 1 that you are in fullscreen mode in firefox.  if this is the case, don't mess with compiz, just use the f11 to exit fullscreen

---

### Post by egruber on 2008-11-12
I swear I followed your instructions and it didn't seem to do anything different.  But you were right that hitting F11 twice seems to correct it.  Thanks for the suggestion!

---

### Post by ghanagareth on 2008-11-20
I have been trying to figure this out and nothing was working.  What I found that worked eventually was to unmaximize firefox and move it around, then maximize it again.  Problem solved.

---

### Post by cstray on 2008-11-20
> **egruber said:**
> I swear I followed your instructions and it didn't seem to do anything different.  But you were right that hitting F11 twice seems to correct it.  Thanks for the suggestion!

the compizconfig trick didn't work for me either, but here's what i figured out that's worked for me so far:

-Press F11 twice
-'restore' firefox (now it'll be too big again, but aligned with the top of your screen)
-resize the window to fit on the screen
-close and restart firefox

you can maximize the window now and the next time you close/restart firefox it'll fit!

---

### Post by egruber on 2008-11-21
> **cstray said:**
> the compizconfig trick didn't work for me either, but here's what i figured out that's worked for me so far:

-Press F11 twice
-'restore' firefox (now it'll be too big again, but aligned with the top of your screen)
-resize the window to fit on the screen
-close and restart firefox

you can maximize the window now and the next time you close/restart firefox it'll fit!

Thanks for the tip.  But what do you mean by 'restore' firefox.  When I hit F11 twice it fits perfectly.  And when you say to resize to fit on the screen, do you mean drag the corner until the size is where it should be?

Thanks!

---

### Post by cstray on 2008-11-22
> **egruber said:**
> Thanks for the tip.  But what do you mean by 'restore' firefox.  When I hit F11 twice it fits perfectly.  And when you say to resize to fit on the screen, do you mean drag the corner until the size is where it should be?

By restore I mean press the button in between the minimize and close window buttons on the top-right windowframe.  It's a restore button when your window is maximized and a maximize button when the window is not maximized.

And by resize I mean yes, drag the corner until the window fits on your screen.  You'll have to drag the window smaller from the top edge/corner and then move it up because the bottom part of the window will be hanging below the bottom of your screen.  You don't have to resize it to fit perfectly, just so that it isn't larger than the screen anymore.

Pressing F11 twice does work, but right now you have to do it every time you restart your computer.  If you follow my steps you won't have to do that anymore.

hope that all made sense...

---

### Post by egruber on 2008-11-23
Yes, it did!  And it worked perfectly.  Thanks!!

---

### Post by diablo75 on 2008-11-23
> **sonu 1807 said:**
> Press F11

(Twice)

---

### Post by ostro on 2008-12-14
[http://174.129.128.200/ubuntu/1691-firefox-shows-no-windows-frame.html#post2135]("http://174.129.128.200/ubuntu/1691-firefox-shows-no-windows-frame.html#post2135")

i found this alternative solution. you delete the localstore.rdf

it worked for me but all my configurations on the toolbars and boockmarkbar where deleted with the file.

---

