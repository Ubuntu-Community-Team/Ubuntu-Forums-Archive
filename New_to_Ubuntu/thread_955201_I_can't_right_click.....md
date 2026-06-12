---
title: "I can't right click...."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by toasty_ghosty on 2008-10-22
Hello

I feel like I'm on a Mac. I cannot seem to right click. Everything seems to work besides that. Theres nothing lagging and nothing seems slower than normal. Help please.

Thanks.

*To further clarify things: I can right click. It just fails to bring up the menu that typically starts when you right click. But if I put my mouse in a window. It allows me to right click. I believe I may have screwed something up with Compiz. I also just installed VMWare. That may have screwed something up. Also, if I boot into Enlightenment I can right click. It seems to be a Gnome only issue.

---

### Post by toasty_ghosty on 2008-10-22
Through process of elimnation I thought it might be nautilus. here is what I got when I tried to open it in the terminal. 
> 
king@Anubis:~$ nautilus &
[1] 7141
king@Anubis:~$ Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:7141): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown

---

### Post by eternalnewbee on 2008-10-22
Had the same problem a few weeks ago and after a few reboots I had it back again...
No worries.

---

### Post by taseedorf on 2008-10-22
try ctrl alt backspace...

also, make sure compiz isnt ******* something up.

---

### Post by eternalnewbee on 2008-10-22
That's right! I remember now. It happened after I had enabled the wallpaper plugin.

---

### Post by toasty_ghosty on 2008-10-22
I've tried control alt backspace a few times not to mention a bunch of restarts...

What wallpaper plugin?
> 
That's right! I remember now. It happened after I had enabled the wallpaper plugin. 

---

### Post by eternalnewbee on 2008-10-22
The wallpaper plugin in compiz.

---

### Post by toasty_ghosty on 2008-10-22
I must be missing something. I haven't installed a wallpaper plugin. Or is it a very obvious setting that I am somehow missing? I've looked under all the desktop cube options and cannot seem to find it... 

Thanks for helping someone who is being incompedent today.

---

### Post by toasty_ghosty on 2008-10-31
I've tried the wallpaper plugin, and everything else I could think of. My ability to right click seems to just go away. I had it back but I just started my computer and now it is gone...

Any help?

---

### Post by toasty_ghosty on 2008-10-31
Bump? 

I just upgraded to Intrepid. Thought that would fix it. Still has not. Any help?
Could it be Compiz? I could have messed something up there. If I remove it will it restore everything to default settings?

Thanks.

---

### Post by lifestream on 2008-10-31
Do you have any icons on your desktop? If not, I think you setup nautilus so it does NOT manage the desktop.

I forgot what option in gnome-conf or whatever it's called. If someone knows what I'm talking about, please post :)

---

### Post by toasty_ghosty on 2008-10-31
THANK YOU! For some odd reason, if anyone knows let me know, when I got rid of icons, it kills my right click. I tried Ubuntu Tweak for the first time and that is what messed it up. Is there a way to get rid of icons without using Ubuntu Tweak and without killing my right click?

---

### Post by lifestream on 2008-11-03
Hey toasty, you're welcome.

I ***THINK*** that if you use PCManFM (PC Man File Manager), you can tell it to show the wallpaper but not show icons. I THINK.

Did you know that if you hit ALT+Mouse click on any window, it will bring up the window menu? I looked for a similar shortcut to bring up the Desktop menu. Couldn't find it. Wouldn't that be cool?...

---

