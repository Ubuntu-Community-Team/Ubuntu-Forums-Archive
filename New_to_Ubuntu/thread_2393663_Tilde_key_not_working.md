---
title: "Tilde key not working"
date: 2018-06-06
forum: New to Ubuntu
---

### Post by martijntje on 2018-06-06
I have an Ubuntu 18.04 installation, upgraded from 16.04 where the tilde key doesn't work. The keyboard is definitely not broken - I see the cursor changing in the terminal when I press the key - but no character becomes visible. I am using the "English (US, euro on 5)" keyboard layout.

The problem also happens regardless of whether I use the built-in laptop keyboard, or an external keyboard. What could be the issue here?

---

### Post by TheFu on 2018-06-06
Create a new userid.  Does that fix it?
If you boot from Try-Ubuntu media, does that fix it?

---

### Post by martijntje on 2018-06-06
It works in a new account, so I guess it'll work in a live-cd environment.

---

### Post by TheFu on 2018-06-06
> **martijntje said:**
> It works in a new account, so I guess it'll work in a live-cd environment.

What that proves is that the issue is with the account, not the system.  Somewhere in the $HOME is the problem

If "it works" means that the ~ key works under a different userid. It isn't 100% clear from the statement.

---

### Post by steeldriver on 2018-06-06
Possibly the shell's readline bindings are messed up - you could check (from the troublesome account) using

```

bind -p | grep $'\x7e'

```

(the $'\x7e' escape sequence is just a way of inputing a ~ without typing it)

---

### Post by TheFu on 2018-06-06
[https://github.com/zzrough/gs-extensions-drop-down-terminal/issues/182](https://github.com/zzrough/gs-extensions-drop-down-terminal/issues/182) has some ideas.
Try it with and without the numlock enabled.
With and without shift pressed too.

---

### Post by martijntje on 2018-06-07
Ah, this indeed seems to be the problem. I have that extension installed and changing the hotkey indeed makes the tilde work like it should again.

I don't have a numlock key to test as neither my laptop- nor my external keyboard have a numpad on them, which is unfortunate, given reports that it works with numlock on.

---

### Post by martijntje on 2018-06-07
OK, I managed to get it working for now by toggling numlock using xdotool. Obviously I will have to do this on every reboot until the issue with the extension is fixed. At least I can work normally again. :)

---

### Post by sudodus on 2018-06-07
In terminal windows I get tilde with the F12 key, which is quite convenient.

(But it does not work everywhere, for example in LibreOffice and Firefox you need the special key (or key combination), that you are looking for.)

What do you see and get, with the on-screen keyboard **onboard**, when you select AltGr (press twice to lock it)?

---

### Post by danthonyd on 2018-06-08
Try all your keys and see if it's in a different location.

---

