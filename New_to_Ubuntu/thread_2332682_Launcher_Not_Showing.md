---
title: "Launcher Not Showing"
date: 2016-08-02
forum: New to Ubuntu
---

### Post by rolfUser on 2016-08-02
Shortly after upgrading from Ubuntu 14.04 to 16.04, I had noticed two information bars on VLC player app. One for the The VLC window, and one above it, I think it's the task bar. I don't recall this ever happening in 14.04, so I opened **Unity Tweak**, thinking I can restore defaults to remove the bar of information at the top of the window when I open VLC player.
I had also tried making adjustments under the Appearance application, the one you use to change the desktop background, but no changes can be made.

I went through different options and found that nothing could restore it. Then I made a mistake. The taskbar at the top of the screen was gone!  The Launcher which I had move to the bottom of the screen, was also gone!   I tried pressing F12, but this made no difference.
My guess for a solution would be to start with the Terminal, but I have no idea how next to proceed.  
How do I bring back the taskbar and launcher?

---

### Post by rolfUser on 2016-08-03
[http://askubuntu.com/questions/72366/how-can-i-restore-the-unity-launcher](http://askubuntu.com/questions/72366/how-can-i-restore-the-unity-launcher)
[http://ubuntuhandbook.org/index.php/2014/04/reset-unity-and-compiz-settings-in-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/reset-unity-and-compiz-settings-in-ubuntu-14-04/)

Will anything like this help in Ubuntu 16.04?

---

### Post by ajgreeny on 2016-08-03
You have tagged this thread as Lubuntu; did you really mean that or are you using Ubuntu with the unity desktop?

---

### Post by rolfUser on 2016-08-03
Yes I am. Sorry I must have made a mistake. I'll try to fix that.
Also thought I should try to open Unity Tweak using the Terminal and see what I can do from there.
I've had no luck so far trying to see how that is done.

---

### Post by Frogs Hair on 2016-08-03
This link is valid for 16.04.

[http://ubuntuhandbook.org/index.php/...-ubuntu-14-04/]("http://ubuntuhandbook.org/index.php/2014/04/reset-unity-and-compiz-settings-in-ubuntu-14-04/")

---

### Post by rolfUser on 2016-08-03
Okay it looks like it's back to where it should be.
Problem is, the terminal is no longer in its own window. It has binded itself to the taskbar at the top of the screen when I typed in
```
setsid unity

```
The cursor you see blinking underneath the line that reads:
```
unity7 start/running, process 6164

```
Seems like it will continue indefinitely.  Should I just wait or is it safe to ignore it and restart my PC?

---

### Post by Frogs Hair on 2016-08-04
Have you rebooted since your last post ?

---

