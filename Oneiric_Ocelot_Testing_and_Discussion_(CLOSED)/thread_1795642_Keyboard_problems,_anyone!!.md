---
title: "Keyboard problems, anyone?!?!?"
date: 2011-07-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-07-03
I keep waiting for someone to mention this, but...

Maybe I'm the only one having this problem.  :)

I'll be keyboarding along, when all of a sudden, my keyboard indicator lights start flashing (Num Lock, Caps Lock, Scroll Lock), as I type.

Then...

BOOM! I'm tossed out of the desktop, to TTY (weird ascii symbols all over the place), then into the login screen.

Never seen this behavior before.  Started around 26-Jun.  Fully updated HDD install and/or Daily Build Live-CD. And, it happens on different machines.

Ubu 10.10 runs without a hitch, for hours, on this dual-booter, so it isn't a hardware failure.  UbuOO borks in minutes (but only while I'm typing).

Like playing with dynamite, it is.  Anyone else having this problem?!?!?

---

### Post by lucazade on 2011-07-03
no issue with keyboard but I have seen those weird ascii symbols in my machine..
there was a post about it:
[http://ubuntuforums.org/showthread.php?t=1791366](http://ubuntuforums.org/showthread.php?t=1791366)

I've seen anyway something similar using a livecd and trying to open "gnome-session-properties", it drops to a tty and then to login page.. nice :)

---

### Post by VinDSL on 2011-07-03
Yes, sir.  That would be it...  :D

The screenie (in that thread) looks just like what I'm experiencing.

I see that the bug report is triaged & marked critical, so I'll wait it out.

Must have overlooked the post, and the 'search feature' didn't snag it...

Thanks!  ;)

---

### Post by dino99 on 2011-07-03
have not these problems but others:

- gnome its ok, but kde dont use my azerty keyboard config (it use qwerty)
- my main trouble is with mouse sensibility: very hard to select block of texte at once, control is lost, and grab/drag&drop is a nightmare
(its a serial mouse with an usb adaptator)

---

### Post by VinDSL on 2011-07-03
> **dino99 said:**
> my main trouble is with mouse sensibility[...]
I've had an ongoing problem with the mouse (pointer) locking up when booting from a USB Flash drive.

Putting the Flash drive in a different USB port fixes the problem.  LoL!  :D

I have a *feeling* Oneiric is suffering from input woes right now.

EDIT

BTW, I generally use a PS/2 mouse and keyboard.  Old habits die hard...  ;)

---

### Post by sparker256 on 2011-07-03
> **VinDSL said:**
> I've had an ongoing problem with the mouse (pointer) locking up when booting from a USB Flash drive.

Putting the Flash drive in a different USB port fixes the problem.  LoL!  :D

I have a *feeling* Oneiric is suffering from input woes right now.

EDIT

BTW, I generally use a PS/2 mouse and keyboard.  Old habits die hard...  ;)
Yes I am also seeing that behavior and to make thing even more interesting I use UBS keyboard, mouse and KVM. I did a me to on that bug so will see what happens down the road. Every once in a while while typing the KVM switches and I am on my second machine thinking what was that. :shock:

I still have a Small list of bugs that if not addressed by alpha 2 will start being more vocal. When you do the testing and submit the bug reports give as much info as is possible and it still says incomplete I wonder am I the only one with this problem?:confused:

PS your welcome on the conky forecast. Boy that is a rough crowd over there at times. :)    

Bill

---

### Post by kuvanito on 2011-07-03
it's funny
at last my keyboard works properly
i use a Microsoft Blue Light Technology Wireless Keyboard and Mouse Combo and it never work properly with Natty,had to replace batteries almost daily,now with Oneiric it works like a champ and I have not change batteries in a week.isn't that funny? :guitar:

---

### Post by xeizo on 2011-07-03
My keyboard doesn't work at all as soon X is started, I can only use the commandline. And the mouse requires to be removed and inserted again. As the keyboard works in CLI this seems to be desktop or X related.  It worked fine earlier today, but I haven't done a reboot in a week or so, the problem started after a reboot. I've tried different kernels and different displaymanagers and desktops. All the same.  So, I can't use any desktop at the moment and are back at my backup-natty on another drive ...  I use a normal keyboard, mabe it works with a USB-keyboard, but I haven't got one. Or haven't I? I think I saw an old HP-keyboard with usb in the wardrobe, I'll try that and check back  :)

---

### Post by xeizo on 2011-07-03
+1

It works with a USB-keyboard, but the symptom is the same as with the mouse: I have to remove and insert both mouse and keyboard at the login-screen to get them working. But it works!

A "normal" keyboard with the old kbd-connector only works in bare CLI.

Something is wrong, very wrong if one can't even use any desktop with the most common keyboard-type. Or is a touchscreen obligatory nowadays?  ;) :P

---

### Post by VinDSL on 2011-07-03
> **sparker256 said:**
> PS your welcome on the conky forecast. Boy that is a rough crowd over there at times. :)
LoL!

Yeah, there is a LOT of competition and BIG egos in that community.

They should have called it "Cranky", instead of "Conky"...  :D

---

### Post by Quackers on 2011-07-03
Not really the same problem at all but still on topic, a bit.
I'll be making a post on the forum or a reply and the keyboard just stops working - halfway through the post. No error message or anything. No keys work at all but the mouse still works. 
There are only 2 ways out of it for me. One is to log out and back in and the second is to reboot. Then the keyboard is fine again.
This only seems to happen after the laptop has been booted for some time (a good few hours).

---

### Post by dino99 on 2011-07-03
well i've googled a little and found hidpoint url to get a custom hidpoint1-0.bin for my mouse/keyboard. Now i need to test and see if its better.
I've running different distro with gnome (2&3) and kde, but all running 2.6.38 kernel or newer:
- they all have this problem now, so dont know where the problem is
- everything is okay with 2.6.35 & lower kernels

hope my previous tweak will fix that mess, otherwise i have to find which module to blame.

---

### Post by cariboo on 2011-07-03
I might as well add the problem I was having with GDM. After being away from the computer for several hours, GDM wouldn't except input when trying to unlock the screen. Clicking the Switch user button, showed the input, and allowed me to login to my desktop. The problem doesn't affect me anymore, as I'm using lightdm.

---

### Post by VinDSL on 2011-07-04
Whoa!  I *think* *Hernando Torque* just fixed my keyboard problem.  :D


SOURCE:  [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271/comments/9](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271/comments/9)
> 
Setting 'vt=7' in the '[seat-0]' portion of '/etc/lightdm/lightdm.conf' seems to have stopped the crashing (which I got from time to time - NOT always - using the '2' and 'Enter' key).


I edited the file:
```

$ sudo gedit ../../etc/lightdm/lightdm.conf

```

Here' the pertinent section:
```

**[COLOR="Blue"]<snip>[/COLOR]**
# Seat configuration
#
# vt = Virtual terminal to start on (0-n or 'active')
# greeter-theme = Greeter theme
# greeter-user = User to run greeter process as
# session = Default session
# default-user = Username of default user to log in as
# default-user-timeout = Delay before logging in in seconds (use 0 for automatic login)
# pam-service = PAM service to use
# display-number = Display number to use (overrides automatic display number selection)
# xserver = X server to use
# xdmcp-manager = XDMCP manager to connect to
# xdmcp-port = XDMCP UDP/IP port to communicate on
# key = Authentication key to use
#
[seat-0]
[HIGHLIGHT]vt=7
#vt=active[/HIGHLIGHT]
#greeter-theme=example-gtk-gnome
#greeter-user=lightdm
#session=gnome
#default-user=
#default-user-timeout=5
#pam-service=lightdm
**[COLOR="Blue"]<snip>[/COLOR]**

```


Here's how my TTYs looked before the modification:
```

$ ps -e |grep tty
  [HIGHLIGHT]764 tty1     00:00:09 Xorg[/HIGHLIGHT]
  999 tty4     00:00:00 getty
 1004 tty5     00:00:00 getty
 1013 tty2     00:00:00 getty
 1014 tty3     00:00:00 getty
 1016 tty6     00:00:00 getty
 [HIGHLIGHT]1159 ?        00:00:00 getty[/HIGHLIGHT]

```

And, here's how they look now:
```

$ ps -e |grep tty
  [HIGHLIGHT]771 tty7     00:00:05 Xorg[/HIGHLIGHT]
  965 tty4     00:00:00 getty
  969 tty5     00:00:00 getty
  978 tty2     00:00:00 getty
  979 tty3     00:00:00 getty
  981 tty6     00:00:00 getty
 [HIGHLIGHT]1110 tty1     00:00:00 getty[/HIGHLIGHT]

```

Haven't had a recurrence since!  Feels like a whole different machine, actually.  :)

I'll see how it holds up, and report back.

---

### Post by MacUntu on 2011-07-04
You're welcome. ;)

Just note, that it's likely just a workaround and that updates to lightdm will overwrite it.

---

### Post by VinDSL on 2011-07-04
> **MacUntu said:**
> You're welcome. ;)

Just note, that it's likely just a workaround and that updates to lightdm will overwrite it.
Yes, TY!  

I didn't know you and he were the same person...  :oops:

It's working great, so far!

---

### Post by vulfgar on 2011-07-10
Unfortunately this fix doesn't take care of the other keyboard/mouse problem, where neither work at login screen.

---

