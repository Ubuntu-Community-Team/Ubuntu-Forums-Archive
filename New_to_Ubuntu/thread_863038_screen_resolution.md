---
title: "screen resolution"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by hedrian on 2008-07-18
i have set my screen resolution to 1152x864
but the whole screen is not appearing the ubuntu logo on the top right is half seen


btw,is there a way i can write the pixels down instead of choosing whats already given?

and one more ques, is there another instant messeging software other than pidgin? like live messenger

---

### Post by schauerlich on 2008-07-18
> **hedrian said:**
> i have set my screen resolution to 1152x864
but the whole screen is not appearing the ubuntu logo on the top right is half seen


btw,is there a way i can write the pixels down instead of choosing whats already given?

and one more ques, is there another instant messeging software other than pidgin? like live messenger

What is the native resolution of your monitor?

And to answer your second question, there is kopete.

---

### Post by hedrian on 2008-07-18
my native resolution of the monitor is 1024x768

---

### Post by schauerlich on 2008-07-18
First, backup your xorg.conf:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Open up your xorg.conf:
```

gksudo gedit /etc/X11/xorg.conf

```

In the Section "Screen" add:
```

SubSection "Display"
    Depth    24
    Modes    "1024x768"
EndSubSection

```
If that subsection already exists, just edit the existing one to look like that. Save it and restart X by hitting Ctrl+Alt+Backspace. Try logging in, and if all goes well you should have the right resolution.

---

### Post by ktrnka on 2008-07-18
You could also try running this from a terminal

```
sudo displayconfig-gtk
```

It's nowhere near perfect but it I have found it to be fairly easy to use in some cases.

---

### Post by hedrian on 2008-07-20
my native screen resoulution of the monitor is 1024x768. but when i choose that, the screen is too big, when i choose 1152x864 it is ok but i cant see a small bit of the left side..heres a screen shot
[http://i45.servimg.com/u/f45/11/55/76/81/screen10.png](http://i45.servimg.com/u/f45/11/55/76/81/screen10.png)
how can i fix this?
and by the way,when i post the screenshot from the BBCODE, the screen shows fully..

---

### Post by ktrnka on 2008-07-21
If you're using the display-gtk, what is selected as your model? I have seen a few instances where selecting "Generic" worked better than selecting the actual model. Try "Model: Monitor 1024x768" if yours is currently set on "Plug 'n' Play" or vice versa.

---

### Post by a0u on 2008-07-21
> **hedrian said:**
> and one more ques, is there another instant messeging software other than pidgin? like live messenger

Of course...with GNU/Linux there's always the freedom of choice. :)

Windows Live Messenger doesn't run natively in Ubuntu (as if M$ would offer Linux support), and it [doesn't seem to work well with Wine either]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9426").

On the other hand, there's [aMSN]("http://www.amsn-project.net/"), a free Messenger clone for Linux.
```
sudo apt-get install amsn
```

---

### Post by hedrian on 2008-07-22
thanx alot now everything is fine

---

### Post by ktrnka on 2008-07-22
If it is fixed, then please mark this thread as solved. 

Thanks!

---

### Post by jolx on 2008-07-22
u may also want to try emesene for an msn messenger

---

