---
title: "A new screen and some new headaches"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by jasontu on 2008-08-19
I recently became heir to a pretty nice 32" LCD monitor/TV.  It functions okay with Ubuntu, but I have a couple of issues I could use help with.

Firstly, it will not stay at 1280x768 upon reboot.  It always wants to boot up in 1024x768.  It's easy enough to change the resolution back, but it's a pain to do that everytime it boots.

Secondly, it is currently registering as a generic display.  It is a WinBook display, so yeah... it's generic.  Generics are often name-brands in a different suit.  Is there a way I could see if there is a name-brand that Ubuntu could recognize for this display?  Would it make a difference?

What does make a difference I have noticed is going from my graphics card's VGA port to DVI.  When I was going VGA to VGA I was getting some ugly ghosting and blurring.  Now I am going DVI on the card to VGA on the monitor and the ghosting/doubling is only slightly noticeable on text.  Please let me know if you have any pointers on that.  Should I invest in a DVI to DVI cord?  Is the adapter degrading the signal?

Thanks!

---

### Post by meindian523 on 2008-08-19
Please post ```
cat /etc/X11/xorg.conf
```

---

### Post by Dark Hornet on 2008-08-19
I am pretty sure the reason why your monitor won't maintain the resolution upon reboot is because it is not saving it.  When you edit your xorg file, you need to make sure you are in "root" while doing it.  For example, if you have a nVidia gfx card, and you are using the "nvidia-settings" to make your changes...make sure you open it while as root, otherwise it will not allow you to save.  Just something I learned the hard way myself...:lolflag:

Good luck!

PS  What kind of gfx card do you have anyway?

---

