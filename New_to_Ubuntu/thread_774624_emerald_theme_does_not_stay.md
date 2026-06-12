---
title: "emerald theme does not stay"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-29
when i load an emerald theme, go into the terminal, and type 'emerald --replace', it shows the theme i am using. but when i exit out of the terminal, the theme leaves, and there is no border! when i restart my computer, though, it shows the theme chosen in Appearence Preferences. help!

---

### Post by Helios1276 on 2008-04-29
> **Zopiac said:**
> when i load an emerald theme, go into the terminal, and type 'emerald --replace', it shows the theme i am using. but when i exit out of the terminal, the theme leaves, and there is no border! when i restart my computer, though, it shows the theme chosen in Appearence Preferences. help!

> **medivh said:**
> You can add the command to sessions to start automatically.
System->Preferences->Sessions
Press ADD button and fill in the blanks
Name: Emerald
Command: emerald --replace
Comment: Anything you want or empty

try that

---

### Post by Ardrias on 2008-04-29
Or you can press Alt+F2 to run 'emerald --replace' from the gnome-applauncher.

---

### Post by Helios1276 on 2008-04-29
> **Ardrias said:**
> Or you can press Alt+F2 to run 'emerald --replace' from the gnome-applauncher.

I didnt read the situation properly, Adrias is also right, use Alt+ F2

---

### Post by Zopiac on 2008-04-29
> **Helios1276 said:**
> try that

tried this, nothing happens.

[QUOTE=Ardlas]you can press Alt+F2 to run 'emerald --replace' from the gnome-applauncher.[/QUOTE]

alt- f2 stopped working for me recently :(

---

### Post by diaz028 on 2008-04-29
Same problem here, cant get Alt-F2

---

### Post by Helios1276 on 2008-04-29
In the terminal try  'nohup emerald --replace &'.

---

### Post by diaz028 on 2008-04-29
Worked for me, emerald works and borders are solid!

Thanks,hopefully it works for zopiac too!

-> Came up with something about 'nohup.something & corrected' or something

-D

---

### Post by dje on 2008-04-29
> You can add the command to sessions to start automatically.
System->Preferences->Sessions
Press ADD button and fill in the blanks
Name: Emerald
Command: emerald --replace
Comment: Anything you want or empty

> **Zopiac said:**
> tried this, nothing happens.
You must log out and then back in for that to work

hope that helps,
dje

---

### Post by Helios1276 on 2008-04-29
> **diaz028 said:**
> Worked for me, emerald works and borders are solid!

Thanks,hopefully it works for zopiac too!

-> Came up with something about 'nohup.something & corrected' or something

-D

Glad I could help, hope zopiac gets sorted too, nothing worse than losing your Ubuntu bling lol

---

### Post by Zopiac on 2008-04-29
> **Helios1276 said:**
> Glad I could help, hope zopiac gets sorted too, nothing worse than losing your Ubuntu bling lol

yep im good ;)

---

### Post by diaz028 on 2008-04-29
Problem persists after a reboot :(

---

### Post by dje on 2008-04-29
> **diaz028 said:**
> Problem persists after a reboot :(
Did you add the command to System >> Preferences >> Sessions? if not it will not stick after a log out/reboot/shutdown

hope that helps,
dje

---

### Post by forrestcupp on 2008-04-29
Like was already stated, adding **emerald --replace** to your start up commands in Sessions should start up emerald every time you log in.  

It's possible you may need to go to System->Preferences->Advanced Desktop Effects Settings and in the Effects section, check the Window Decoration box.  Then click on the words and in its settings in the text box by Decoration Windows, change **any** to **emerald**.  You really shouldn't have to do that, though, if it's in Sessions.

---

