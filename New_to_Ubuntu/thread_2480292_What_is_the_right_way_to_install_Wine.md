---
title: "What is the right way to install Wine?"
date: 2022-10-24
forum: New to Ubuntu
---

### Post by sash5 on 2022-10-24
If i google then i find that first you have to install a public key for the wine repository:

 wget -O - [https://dl.winehq.org/wine-builds/winehq.key](https://dl.winehq.org/wine-builds/winehq.key) | gpg --dearmor | sudo tee /usr/share/keyrings/winehq-archive.key

Then add a repository  :

 sudo wget -NP /etc/apt/sources.list.d/ [https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources](https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources)
 
If we open winehq-jammy.sources then we see:
 Signed-By: /etc/apt/keyrings/winehq-archive.key

Why public key is located in /usr/share/keyrings/ and not in /etc/apt/keyrings and how is it working?

---

### Post by Dennis N on 2022-10-24
There are wine and related packages in Ubuntu Software. I would use that.

---

### Post by ActionParsnip on 2022-10-24
Wine is in the default repositories. Why are you adding a PPA?

---

### Post by Tadaen_Sylvermane on 2022-10-24
Because the repositories isn't the latest version. Quite out of date really. Jammy is at 6.03. Last time I checked they were at 7.19 or something now. While it is out of the repositories wine versions have more an impact than a version upgrade of say a text editor or something. 6.03 > 7.19 is huge and opens a ton of things up.

This is your wine place for the latest thing you can get. [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

Don't follow another one. This one is correct.

---

### Post by ActionParsnip on 2022-10-25
That's not how WINE works. Some apps run better with different versions. Don't go blindly chasing version numbers. If you don't need something in the later versions then upgrading gains you exactly zero.

---

### Post by kbarber3 on 2022-10-25
> **ActionParsnip said:**
> That's not how WINE works. Some apps run better with different versions. Don't go blindly chasing version numbers. If you don't need something in the later versions then upgrading gains you exactly zero.

In fact I'd go further (if I may add something as a very newbie Linux user).  There are some apps that will break entirely under a newer version of WINE.

---

### Post by ActionParsnip on 2022-10-25
Check the WineAppDb for compatibility. It may show you the ideal version of WINE for the application you want to run. Later isn't always better despite what your Windows brain is telling you

---

### Post by Dennis N on 2022-10-25
As to the version of Wine to use, PlayOnLinux may help too. It's in Ubuntu Software. It will install the optimum version of Wine for programs in its own database. Check the supported software:

[https://www.playonlinux.com/en/supported_apps.html](https://www.playonlinux.com/en/supported_apps.html)

---

### Post by Tadaen_Sylvermane on 2022-10-25
Nothing I run will work on anything lower than 7.0.4. So I'd debate that. Of course I don't know the technical reasons but that is what I've found thus far.

---

### Post by mIk3_08 on 2022-10-26
> **ActionParsnip said:**
> Later isn't always better despite what your Windows brain is telling you Lol. It's just that Linux is not MS Windows. :-D Regards and cheers.

---

