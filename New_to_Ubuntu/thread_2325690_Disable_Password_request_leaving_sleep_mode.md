---
title: "Disable Password request leaving sleep mode"
date: 2016-05-24
forum: New to Ubuntu
---

### Post by ociolino on 2016-05-24
Hello all,
[INDENT] 
I'm using Ubuntu 14.04 LTS 3.13.0-86-generic #130-Ubuntu SMP, I face a   stupid but very boring problem : I'm not able to remove the password   request after computer is leaving the sleep mode or even screen sleep   mode.
In the configuration panel, in the “Security” sheet I deselected request   of password in all cases, in “Luminosity & Lock” panel also I   deselected the locking of the screen.
But no way, my screen is always locking after leaving the sleep mode.
For information the command “gsettings get org.gnome.desktop.lockdown disable-lock-screen" returns “true”.

Any suggestion ? 

Thanks in advance for help.

Ollivier 				[/INDENT]

---

### Post by ajgreeny on 2016-05-24
Look for **Brightness & Lock** in the dash and disable it there; that should do it I think.

You can turn off Lock completely, or just try disabling the password when leaving lock.

---

### Post by ociolino on 2016-05-24
Thank you for the answer, but as I mentioned, I tried this and it does not work. This is actually the configuration I have now.
I tried also to use deconf-editor and gsettings to set disable-lock-screen to true. This also has no effect.

---

### Post by ajgreeny on 2016-05-24
In that case I'm afraid I don't know the answer.
Sorry.

---

### Post by peekaa2 on 2016-06-21
Same issue with me....

---

