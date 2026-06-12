---
title: "VLC theme problem"
date: 2015-12-10
forum: New to Ubuntu
---

### Post by rolfUser on 2015-12-10
I have VLC player installed and saw this today:
[http://www.noobslab.com/2015/12/vlc-media-player-with-skins-for.html](http://www.noobslab.com/2015/12/vlc-media-player-with-skins-for.html)

So I went ahead and installed the new repository. Next I installed the news skins. Installation worked out for both, but a problem occurred when I selected one of the  new skins.   I went ahead to **/home/.local/share/vlc/skins2** and selected, I think it said PSP-black or something.   When I did this and saved the preferences, I re-started VLC and it was as if my computer froze. I could still move the cursor, but cannot select any of the programs from the Launcher.  Further, I could not manually shut down the computer and was unable to save a screenshot.

I thought I could restart the computer, uninstall VLC and then re-install it again. I thought that if I did this, VLC Player will open with its original default skin and these problems would cease to persist.  

I am thinking that I should uninstall the packages that I got from that website. Problem is, I'm not sure if this is the right thing to do.   Will this confuse VLC when I open it again?    How should I remove the packages... if that is how this problem is to be solved?

---

### Post by llamabr on 2015-12-11
I would have thought that you could just remove the skins.  If you really want to turn your vlc back to stock, try:

rm ~/.vlc/
and 
rm ~/.local/share/vlc/*

Let us know what happens

---

### Post by rolfUser on 2015-12-14
> **llamabr said:**
> I would have thought that you could just remove the skins.  If you really want to turn your vlc back to stock, try:

rm ~/.vlc/
and 
rm ~/.local/share/vlc/*

Let us know what happens

I got 'no such directory' error messages hitting these commands in my terminal.   Instead, I just went with sudo nautilus command and deleted the file folder from there. I only deleted the skins2 folder, not vlc folder.
VLC was uninstalled. I re-installed and there were no more problems on startup.

---

