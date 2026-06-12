---
title: "How to swap Alt and Control keys?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by nandaiyo on 2008-08-07
I've tried System -> Preferences -> Keyboard, but there's nothing there that allows a specific swap of the left Control and Alt keys.

I've tried System -> Preferences -> Keyboard layout to Macintosh / Macbook, etc. but it doesn't work.

I've tried using Xmodmap in combination with xev. I start xev, pressed the current Alt key and it gives me keycode 64. Control gives me 37. So i open up ~/.Xmodmap and map:
keycode 64 = Control_L
keycode 37 = Alt_L

keep in mind my Xmodmap already works and I load it on startup - I use it for other keys on my thinkpad. But adding in those two values doesn't work. 

I've searched through the forums a lot, but have not found a solution. Any help is appreciated. 

Thank you!

---

### Post by nandaiyo on 2008-08-08
Also, I've tried:
> sudo xmodmap -e "keycode 64 = Control_L"
> sudo xmodmap -e "keycode 37 = Alt_L"

so that when I run xev, indeed the keys ARE switched, and when I press the left Alt key it returns the keycode as Control_L. The problem is that none of the programs recognize the switch, and even the desktop environment still treats the keys as their default value.

---

### Post by unikuser on 2009-01-19
What you are doing is making left alt(64) = alt+ctrl. you did not remove alt, but added ctrl. You do not need sudo for this. It only few rare things that you need sudo for. Try following... 

```

remove mod1 = Alt_L
keycode 64 = Control_L
add Control = Control_L

```

---

### Post by simion314 on 2012-02-20
> **unikuser said:**
> What you are doing is making left alt(64) = alt+ctrl. you did not remove alt, but added ctrl. You do not need sudo for this. It only few rare things that you need sudo for. Try following... 

```

remove mod1 = Alt_L
keycode 64 = Control_L
add Control = Control_L

```

Thanks, this helped me.

---

### Post by gxlrygt on 2012-11-15
Here is a good answer: [http://earthviaradio.wordpress.com/2012/02/06/swapping-the-left-alt-and-ctrl-keys-in-ubuntu-11-10/](http://earthviaradio.wordpress.com/2012/02/06/swapping-the-left-alt-and-ctrl-keys-in-ubuntu-11-10/)

---

### Post by wildmanne39 on 2012-11-15
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

