---
title: "Undefined video at start-up."
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Stunt Double on 2008-04-29
When I start in Hardy,the screen shows:
"Starting up...
 Undefined video mode number: 2f6
 Press <ENTER> to see video modes available, <SPACE> to continue, or
 wait 30 secs."
   Entering any of the modes shown, presssing Space, or waiting, starts the
up-splash screen and the computer works perfectly.
  Is there any way to get rid of the message so it will skip that step or is it necessary in Hardy?
  Thanks

---

### Post by shearn89 on 2008-04-29
It isn't necessary - check your xorg.conf for errors, and make sure that your resolution doesn't have a typo. You could also check the grub boot line in menu.lst for typos in the framebuffer command. Apart from that, i'm out of ideas...

---

### Post by Stunt Double on 2008-04-29
Thanks for the help.

---

### Post by bjornmatsson on 2008-06-12
I've got the same problem and I'm wondering if you've solved it or if anyone else has solved it? For me the problem started to appear when I used a VGA screen instead of DVI.

---

### Post by Vegetarianrage on 2008-06-16
I was having the same problem where it would say that I had an undefined video mode and would just give me some choices.

Silly enough when you look at the choices it says something like...

```

1 80x50 0F02
2 80x20 0F01 

```

or something to that effect. All I actually did to get around this was decide which one of the choices that i preferred and wrote down the "0F02" part. Then I edited my menu.lst boot options to say vga=0F02 instead of vga=795 or whatever it was originally. Worked without a hitch.

```

sudo nano /boot/grub/menu.lst

```

and near the bottom is the list of your boot options. the different kernels you have available and Windows if you have it. Find the kernel that you use and simply change the vga=XXX part to one of the choices that you see during boot up (ex. 0F02)\\:D/. Save and reboot. Good luck!

---

