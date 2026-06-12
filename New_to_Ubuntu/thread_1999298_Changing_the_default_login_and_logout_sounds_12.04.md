---
title: "Changing the default login and logout sounds 12.04"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-07
How do I change the default login and logout sounds of 12.04.
I'm not running Unity, I'm running Classic Gnome.

I have looked at this article:
[http://www.linuxandlife.com/2012/05/how-to-turn-off-or-change-login-sound.html](http://www.linuxandlife.com/2012/05/how-to-turn-off-or-change-login-sound.html)

With regards to changing the defaults but I couldn't get it to work.

Anyone have a better plan?

---

### Post by MG&amp;TL on 2012-06-08
When you say Classic Gnome....there's a lot of Gnome 2.x clones around at the moment. Which package did you install to get it? Failing that, can you tell me which howto you followed to get it?

---

### Post by Senior_Buckethead on 2012-06-08
you know, having to reinstall  a few days back its all a bit of a blur. I know I used gnome-session-fallback.
Its all because I just cant stand unity (its a personal thing).

---

### Post by MG&amp;TL on 2012-06-08
Well, if it's the default "drums and insect life" that irk you, it's stored in /usr/share/sounds/ubuntu/stereo/desktop-login.ogg - just replace that file with (presumably an OGG) file of your choice.

---

### Post by Senior_Buckethead on 2012-06-12
Ive played the desktop-login.ogg file with banshee and it  plays just fine.

But I just can't get it to play at start. Ive gone to startup applications in gnome and made sure play login sound is checked.

Just to check, the command from the gnome login sound is:
```

usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

```

I can't get the sound to play. Any ideas?

---

### Post by MG&amp;TL on 2012-06-12
> **Senior_Buckethead said:**
> 
```

usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

```


should be:

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```

Note the first '/'. Unless that was a typo?

---

### Post by hansdown on 2012-06-12
I've always liked the borealis startup sounds.

[http://kde-look.org/content/show.php?content=12584](http://kde-look.org/content/show.php?content=12584)

---

### Post by Senior_Buckethead on 2012-06-14
I double checked that I had the correct command:
```

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

```
And still no joy. 
So I thought I would check Ubuntu Tweak, and in Sounds, I changed sound theme from Freedesktop back to Ubuntu. I logged out and then back in and hey, I have my sound!

Stupid me had changed from Ubuntu to Freedesktop sound theme.

Thank you all.

[SOLVED]

---

