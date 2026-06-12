---
title: "After changing to ubuntu (gnome) over kubuntu (kde), Chrome not working"
date: 2020-05-06
forum: New to Ubuntu
---

### Post by magunto on 2020-05-06
Hi, I'm relatively new to linux. 
I had kubuntu 19.10 on my PC. I wanted to try out the Gnome desktop. So I installed ubuntu-desktop using tasksel app in terminal. The ubuntu-desktop installed without problems, the app changed also windows manager to gdm3 without problems. I can log now into gnome session and everything seems to work fine, except Chrome. I use Chrome for work and it  just won't start. Firefox and Chromium will start (Chromium takes lots of time to start), but Chrome will not. 
Can someone explain me what went wrong and how to fix it?  
Thanks!

---

### Post by magunto on 2020-05-07
Have tried running google-chrome from the terminal, and got following error:
[12450:12450:0507/065135.477410:ERROR:sandbox_linux.cc(374)] InitializeSandbox() called with multiple threads in process gpu-process.
What is it?

---

### Post by yetimon_64 on 2020-05-07
Try running google-chrome from the terminal with the next command and see if it works after disabling gpu hardware acceleration ...
```
google-chrome --disable-gpu --disable-software-rasterizer
```
Note: I've never come across this problem myself, information above sourced from a google search. [URL="https://simpleit.rocks/linux/ubuntu/fixing-common-google-chrome-gpu-process-error-message-in-linux/"][COLOR=#0000ff]Source.
[/COLOR][/URL]

---

### Post by ActionParsnip on 2020-05-07
Or rename it's configuration folder which is a subfolder of ~/.config
I forget it's name but it'll stand out. Rename the folder then launch the browser and you will get vanilla settings. You can then log in to Google to sync your settings and whatnot

---

### Post by magunto on 2020-05-12
Thanks both for your answers. I tried running chrome with these additional options but it didn't work. I got the same error. And I didn't want o mess with renaming system folders - I'm not that confident yet. I eventually gave up, uninstalled ubuntu-desktop, moved back to kde. Then installed some recent updates, did some cleaning with bleachbit, then installed ubuntu-desktop again, and now it works!!! I have no idea what went wrong the first time and it scares me a little. But now it works and I can enjoy gnome desktop on kubuntu with working chrome!

---

### Post by dino99 on 2020-05-12
If you want/need testing a new DE, then do a separate installation. Never mix them; you now know the result. ;)

---

### Post by magunto on 2020-05-18
**dino99** - And this surprises me. I thought that I am using the same distribution (ubuntu), the only thing that I was changing was the visual look and behaviour of windows on the screen. But the engine is the same (right or wrong?). So I thought that it shouldn't impact the working of applications ...? (they may look different, but shouldn't prevent them from running ....)

---

