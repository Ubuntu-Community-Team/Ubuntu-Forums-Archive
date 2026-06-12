---
title: "Multimedia Keyboard buttons"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by biggiemokey on 2008-05-04
Hey I'm running Ubuntu 8.04 through Wubi, just installed yesterday.  I have a Microsoft Keyboard with Fingerprint Reader, which has a few buttons I'd like to use, most importantly Vol+, Vol-, Mute, Play/Pause, Stop, Next Track, Previous Track.

None of these work, and when I search for solutions I find people with different keyboards who have some buttons working, or the volume changing the bass rather than volume.  What I need is to first get it to work AT ALL.

Please very simple answers, I'm new to Ubuntu.

Thanks for any help

---

### Post by SunnyRabbiera on 2008-05-04
well you can try the built in keyboard shortcuts editor, located under system in preferences.
It is listed as "keyboard shortcuts"

Multimedia keyboards can be a little tricky, also you are using something by microsoft so logically it will work best in a microsoft system as they like to keep things tied to them... including your soul ;)

---

### Post by Sparkalo on 2008-05-04
Hey Biggiemonkey!

Have you tried installing KeyTouch?  Many Microsoft Keyboard users have had great luck with it, the documentation is over here: [https://help.ubuntu.com/community/KeyTouch]("https://help.ubuntu.com/community/KeyTouch")

Basically, just
```
sudo apt-get install keytouch keytouch-editor
```

After you install it, just launch it from System -> Administration and follow the onscreen instructions

---

### Post by biggiemokey on 2008-05-05
hey i downloaded keytouch, but my keyboard wasn't supported.  when i tried to open keytouch editor, it gave me an error message, basically saying it couldnt find a file or directory.  i downloaded it from the keytouch site so i dont see why it would be missing anything
im not at my pc now but when i am ill post the exact error message

---

### Post by gummygod on 2008-05-06
hrmm, after i upgraded to 8.04 i also lost functionality of some of my multimedia keyboard buttons.  i installed keytouch and tried using that, but that didnt change anything.  do i need to change my keyboard layout in System>pref>Keyboard?
im using a Logitech Media Elite keyboard, which is in keytouch but not System>pref>Keyboard.  right now its set to a generic 105 key keyboard.
and keytouch editor gives:
> Failed to execute child process "/usr/bin/su-to-root" (No such file or directory)

---

### Post by avtolle on 2008-05-06
Suggestion: System-->Preferences-->Keyboard, click on the Layout tab, then click on Keyboard model, scroll for manufacturer, find the keyboard you are using, select it, etc., then try it out. For example, I've a M$ Media keyboard (USB) that I've selected, and most of the "special" keys work. HTH.

---

### Post by gummygod on 2008-05-07
thanks. but thats the problem, my keyboard isnt listed there.  it IS listed in keytouch though.

EDIT: so i messed around with sys>pref>keyboard>layouts. changed it to super power multimedia keyboard. that didnt do it right away.  im not sure what did, i restarted/logged out a few times, and i noticed my extra keys work now. keytouch also lets me change the keys to whatever i want now instantly.

---

### Post by Coert on 2008-08-04
> **gummygod said:**
> thanks. but thats the problem, my keyboard isnt listed there.  it IS listed in keytouch though.

Can you tell me the keyboard you set up in keytouch ? I can't seem to find the "Microsoft Microsoft&#65533; Keyboard with Fingerprint Reader" ..

> im not sure what did, i restarted/logged out a few times, and i noticed my extra keys work now. keytouch also lets me change the keys to whatever i want now instantly.

Can you tell me the keyboard you set up in Keytouch? I changed Ubuntu settings to "Super Power Multimediakeyboard" ... but no luck with the special keys so far, even after rebooting/logout-login. The scankeys program from the maker of keytouch reports nothing when I press any special keys. 

To which event have you registered your keyboadrd? I'm assuming it's the one that says "Microsoft Microsoft&#65533; Keyboard with Fingerprint Reader"?

Thanks!

---

