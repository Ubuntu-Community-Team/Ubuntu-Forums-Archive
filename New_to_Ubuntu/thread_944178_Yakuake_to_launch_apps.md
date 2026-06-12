---
title: "Yakuake to launch apps"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by HavocXphere on 2008-10-11
I've installed yakuake and its pretty cool.:D

Since its so conveniently accessible anyway, I figured I could also use it to launch apps by creating aliases for apps I use a lot. (e.g. adept_manager -> adept)

The main problem atm is, that the konsole doesn't return as soon as the app start. It's unresponsive until the app closes.

I know there is some or other symbol that I need to include in the alias to make it return immediately, but unfortunately google doesn't understand "some or other symbol". So, whats this tweak I'm looking for.

Another thing: Is there a way to disable the sudo password prompts? e.g. if I'm launching Adept from Yakuake. Would it go away if yakuake is launch with sudo? I realize its very bad style/dangerous to do this, but atm the moment I'm "learning through breaking" and getting sick & tired of the gazillion password prompts. (Running in a VM until 8.10 anyway) I guess I could add my username to the root group, but if possible, I'd like to make it apply to yakuake only, not systemwide.

Thank you

---

### Post by hellion0 on 2008-10-11
If you put a "&" after the command, such as:
```
thunar ~ &
```
...the program will open and give you back your prompt.

---

### Post by HavocXphere on 2008-10-11
> **hellion0 said:**
> If you put a "&" after the command, such as:
```
thunar ~ &
```
...the program will open and give you back your prompt.
Thanks.

Any takers on the sudo thing (last paragraph)?

---

