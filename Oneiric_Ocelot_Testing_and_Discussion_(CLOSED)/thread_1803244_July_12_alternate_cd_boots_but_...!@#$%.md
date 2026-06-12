---
title: "July 12 alternate cd boots but ...!@#$%"
date: 2011-07-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-13
Hello everyone,

Yesterday's update borked my Oneiric because the mouse and keyboard didn't work.  Fixed the problem with the mv command shown below:

```

mv /run/udev /run/udev.old

```

then I made a mistake and borked it again! Recovery console brought a small black terminal on top of a reddish-purple desktop.  Could not load Gnome, ubuntu or ubuntu2D sessions, so I thought perhaps installing the July 12 alternate CD would solve the problem. I just burned the July 12 amd64 Oneiric alternate CD after sha256 check is OK.  The CD boots, but then the screen shows:

"[COLOR="Blue"]udev[89] runtime directory /run/udev not writeable.  Fallback to /dev/udev[/COLOR]"

"[COLOR="Blue"]INPUT NOT SUPPORTED[/COLOR]"
This "input not supported" message lasts too long, at least 30 minutes or more.  BTW, I have GT7300 video card, nvidia driver.

I don't see the login screen.  I got so frustrated that I have to post this, seeking answer.

The mouse light is ON but the keyboard light is [COLOR="Red"]OFF[/COLOR]

Would July 11 build or July 13 build work?

Any suggestions?

Thanks in advance for your help.

:confused:

---

### Post by Quackers on 2011-07-13
Does unplugging/re-plugging them allow them to work again?

---

### Post by iClouseau88 on 2011-07-13
Hi Quackers,

Thanks for your reply, but unfortunately nothing happens after a quick unplugging then replugging of the mouse and keyboard.

:-(

---

### Post by Quackers on 2011-07-13
I had this problem with 2 daily builds. I never got it to work, sadly :-)
Ctrl+Alt+F1 or F2 didn't get me to a prompt as the keyboard wouldn't work.
What did you use to install it the other time? Use that again, would be my suggestion. I went right back to Natty and updated/upgraded.

---

### Post by iClouseau88 on 2011-07-13
> **Quackers said:**
> I had this problem with 2 daily builds. I never got it to work, sadly :-)
Ctrl+Alt+F1 or F2 didn't get me to a prompt as the keyboard wouldn't work.
What did you use to install it the other time? Use that again, would be my suggestion. I went right back to Natty and updated/upgraded.

Hi Quackers,

The last time this type of problem occurred was July 1 when the daily build didn't work.  At that time I went back to the June 13 build to boot its CD and sudo updated & safe-upgraded.  I will do the same this time, perhaps wait 'til the /run/udev problem is resolved hopefully by Friday.  I would not touch Natty which is residing safely in another partition and which I use to send this post.

---

