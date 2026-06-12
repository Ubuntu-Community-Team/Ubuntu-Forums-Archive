---
title: "How to play FLV and RM files..?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by anubhav2k on 2008-11-09
I have installed repositories from medibuntu and w32 codecs also, bur i cant play flv files and rm files in my M PLAYER ??
what can i do to play flv and rm files ?

---

### Post by cariboo on 2008-11-09
Do you also have the ubuntu-restricted-extras installed?

Jim

---

### Post by Raouf on 2008-11-09
> **anubhav2k said:**
> I have installed repositories from medibuntu and w32 codecs also, bur i cant play flv files and rm files in my M PLAYER ??
what can i do to play flv and rm files ?

for *.flv It'll be automatically tells you which codec to add

for *.rm Install Real Player

take care
- Raouf

---

### Post by MasterSander on 2008-11-09
sudo apt-get install vlc --> plays almost everything

---

### Post by Ryadt on 2008-11-09
> **MasterSander said:**
> sudo apt-get install vlc --> plays almost everything
vlc doesn't play .rm files.

---

### Post by anubhav2k on 2008-11-09
> **cariboo907 said:**
> Do you also have the ubuntu-restricted-extras installed?

Jim

i don thnk so , how to do that ?

and i have downloaded vlc player and from where to download real player

---

### Post by MasterSander on 2008-11-09
> **Ryadt said:**
> vlc doesn't play .rm files.

I said almost ;P 

You can add the repository graphically or through terminal, graphically it's somewhere in the package manager and through terminal I need to look up myself

---

### Post by Ryadt on 2008-11-09
To install restricted-extras, open  terminal and type```
sudo apt-get install ubuntu-restricted-extras
```
To install vlc, do ```
sudo apt-get install vlc
```

You don't need real player. Install gnome-mplayer instead, it will play rm files.```
sudo apt-get install gnome-mplayer
```

---

