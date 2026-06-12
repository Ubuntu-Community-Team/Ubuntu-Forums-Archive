---
title: "Item missing from Menu Bar"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by hunterrjh on 2013-10-27
The settings/shut down button has disappeared from Ubuntu 13.10.

Don't know what I did, or how to retrieve it

---

### Post by vanadium on 2013-10-27
There are issues with the indicators. Most notably is that the date-time indicator is sometimes not shown, but it also happens that other indicators are not properly initialized. It will reappear on reboot, or probably already upon logging out/logging in. That problem is know, and the fix should land soon in our system.

---

### Post by hunterrjh on 2013-10-27
Thank you vanadium. The time is showing, but not close down button. I'll wait for the fix. Thanks again

---

### Post by philinux on 2013-10-27
> **vanadium said:**
> There are issues with the indicators. Most notably is that the date-time indicator is sometimes not shown, but it also happens that other indicators are not properly initialized. It will reappear on reboot, or probably already upon logging out/logging in. That problem is know, and the fix should land soon in our system.

+1.

to restore the settings gear use this from a terminal.

```
setsid unity
```

---

### Post by hunterrjh on 2013-10-27
Great. Thanks Philinux

That terminal entry fixed my problem.

---

### Post by hunterrjh on 2013-10-28
> **hunterrjh said:**
> Great. Thanks Philinux

That terminal entry fixed my problem.

Yes. All was fine last night, but when I turned my computer on for the first time today, (about 3 hours ago), there is NO Menu Bar, and I cannot get Launcher bar to appear.

After much tinkering, I found how to get settings box to appear, and was able to change Appearance - Behaviour box to disable Auto-hide the Launcher, but still, nother appears. I was able to enter the Terminal box via Ctrl + alt + T, and nothing has changed, and still no laucher bar and no menu bar.

What can I do. I am typing this on another computer.

---

### Post by hunterrjh on 2013-10-28
> **hunterrjh said:**
> Yes. All was fine last night, but when I turned my computer on for the first time today, (about 3 hours ago), there is NO Menu Bar, and I cannot get Launcher bar to appear.

After much tinkering, I found how to get settings box to appear, and was able to change Appearance - Behaviour box to disable Auto-hide the Launcher, but still, nother appears. I was able to enter the Terminal box via Ctrl + alt + T, and nothing has changed, and still no laucher bar and no menu bar.

What can I do. I am typing this on another computer.

I just closed down my computer (only I can by turning power off), still no Meno Bar, and no Launcher bar, so I don't have access to any programs, or the web. I got back into terminal, and again re-entered

---

### Post by hunterrjh on 2013-10-28
> **hunterrjh said:**
> Yes. All was fine last night, but when I turned my computer on for the first time today, (about 3 hours ago), there is NO Menu Bar, and I cannot get Launcher bar to appear.

After much tinkering, I found how to get settings box to appear, and was able to change Appearance - Behaviour box to disable Auto-hide the Launcher, but still, nother appears. I was able to enter the Terminal box via Ctrl + alt + T, and nothing has changed, and still no laucher bar and no menu bar.

What can I do. I am typing this on another computer.

I just closed down my computer (only I can by turning power off), still no Meno Bar, and no Launcher bar, so I don't have access to any programs, or the web. I got back into terminal, and again re-entered                setsid unity.

It ran through all the normal entry lines. I notice the last line of data entry says     comiz (core) - error; Plugin 'composite' not loaded.



Any ideas?

---

### Post by vanadium on 2013-10-28
Try resetting the unity options: [http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/) From your broken unity session, you might be able to lauch a terminal using the hotkey Ctrl+Alt+T. Alternatively, use Ctrl+Alt+F1 to switch to a text console. I would probably only run the command to reset the config
```

dconf reset -f /org/compiz/

```
then restart the computer
```

sudo shutdown -r now

```

A post at the bottom here [http://askubuntu.com/questions/360472/ubuntu-13-10-unity-doesnt-load-after-upgrade](http://askubuntu.com/questions/360472/ubuntu-13-10-unity-doesnt-load-after-upgrade) shows a method to reset to defaults using Compiz Config manager, but then you need to be able to launch it first.

---

### Post by hunterrjh on 2013-10-28
> **vanadium said:**
> Try resetting the unity options: [http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/) From your broken unity session, you might be able to lauch a terminal using the hotkey Ctrl+Alt+T. Alternatively, use Ctrl+Alt+F1 to switch to a text console. I would probably only run the command to reset the config
```

dconf reset -f /org/compiz/

```
then restart the computer
```

sudo shutdown -r now

```

A post at the bottom here [http://askubuntu.com/questions/360472/ubuntu-13-10-unity-doesnt-load-after-upgrade](http://askubuntu.com/questions/360472/ubuntu-13-10-unity-doesnt-load-after-upgrade) shows a method to reset to defaults using Compiz Config manager, but then you need to be able to launch it first.

I entered the command line as you said, restarted but nothing  changed.

I started typing this message back to you, when I noticed I had left off the forward slash at the end.  I corrected that, and both the Menu bar and Launcher bar have reappeared.

Lets hope it'll be ok now.

Thank you very much.

---

### Post by Alan Bradley on 2013-11-03
Thank You, vanadium. :KS

---

### Post by dvdhudson33 on 2013-11-04
[FONT=arial]Thanks Philinux, [COLOR=#000080]**[FONT=courier new]setsid unity[/FONT]**[/COLOR] worked for me[/FONT].

---

### Post by MrAutumn on 2013-11-05
Thanks Philinux!
Yeah! Now I can see the clock! No more approximating the suns angle for this guy! 
 
Still having similar issues in Gnome, thou. Code::Blocks wont appear on my favourites bar (its still *there*, but no icon, just a blank slate) and my battery icon has disappeared from the screen (again, just a blank slate in the upper right conner of the screen. I can still open the tab if I move the cursor over it). Tried rebooting and even reloading Gnome via terminal but nothing happened.

Any thoughts? Some one

---

### Post by Sef on 2013-11-05
> [COLOR=#000000]to restore the settings gear use this from a terminal.[/COLOR]

[COLOR=#000000]Code:
setsid unity[/COLOR]


thank you philinux.

---

