---
title: "Frostwire?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by linux_newf on 2008-09-25
How do i update it guys? I haven't used the terminal in mths.

---

### Post by Crafty Kisses on 2008-09-25
I don't use FrostWire but I'm certain that FrostWire has the .deb package on their website, or you could try the following:
```
sudo apt-get install frostwire
```

---

### Post by lisati on 2008-09-25
I instaleld a copy of frostwire a month or so back on my Ubuntu was via a ".deb" package, which didn't need the CLI to install - I downloaded it to the desktop and opened it by clicking on its icon. I then clicked in "install package" to install it. 
I'm not sure how well this will work if you have an older version installed.

---

### Post by linux_newf on 2008-09-25
> **Codename said:**
> I don't use FrostWire but I'm certain that FrostWire has the .deb package on their website, or you could try the following:
```
sudo apt-get install frostwire
```

I just want to update it i already have it.

---

### Post by semitone36 on 2008-09-25
Search "frostwire updates" under Synaptic maybe?

---

### Post by Crafty Kisses on 2008-09-25
I'm pretty sure FrostWire's website has the latest version of FrostWire on their website.

---

### Post by billgoldberg on 2008-09-25
> **linux_newf said:**
> I just want to update it i already have it.

Since you didn't installed it from a repo, you are going to have to remove frostwire manually and install the newest package from their website.

I don't even know if there is a repo that has frostwire in it. 

Does anyone know one?

---

### Post by Therion on 2008-09-25
It MIGHT be in one of the Ultimate Edition repo's... but the solution here, really, is to uninstall via Synaptic and reinstall the latest version off the website.  It's a deb package on their site, so it's a slam dunk.

---

### Post by Tatty on 2008-09-25
> **billgoldberg said:**
> Since you didn't installed it from a repo, you are going to have to remove frostwire manually and install the newest package from their website.

I don't even know if there is a repo that has frostwire in it. 

Does anyone know one?

It was a differnt poster who said he installed from a .deb, not the OP :)  I nearly made the same mistake just now. lol.

@ the op - How did you install frostwire?

---

### Post by billgoldberg on 2008-09-25
> **Tatty said:**
> It was a differnt poster who said he installed from a .deb, not the OP :)  I nearly made the same mistake just now. lol.

@ the op - How did you install frostwire?

Oh, lol.

I get confused sometimes.

:p

---

### Post by linux_newf on 2008-09-25
> **Tatty said:**
> It was a differnt poster who said he installed from a .deb, not the OP :)  I nearly made the same mistake just now. lol.

@ the op - How did you install frostwire?

Can't remeber actually, i'm not a big linux user but i have found hardy the best linuk distro i have used. I don't really play around with anything.

---

### Post by Tatty on 2008-09-25
Well it appears that it is not in the repos.  I am assuming you probably installed it by .deb.

If you installed by .deb or if you compiled it with checkinstall then it should have added an entry into your package manager, so you can remove it via synaptic.

After you have removed the current version then you can simply download the .deb from the frostwire website and then install the new version.

Theres a page on frostwire on the community wiki

[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

---

