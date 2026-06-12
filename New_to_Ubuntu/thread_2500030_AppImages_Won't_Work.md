---
title: "AppImages Won't Work"
date: 2024-08-19
forum: New to Ubuntu
---

### Post by ndptal85 on 2024-08-19
Hello Everyone,

I'm a new Ubuntu user but no matter what I try I can't get AppImages to work. Steps I've taken so far:

1. sudo apt install libfuse2
2. sudo apt install gnome-shell-extension-manager

I even considered:

3. sudo add-apt-repository ppa:appimagelauncher-team/stable 
but did not proceed as I was given warnings that PPAs don't auto-update so does that mean my AppImage wouldn't update either?

On Mint and Debian AppImages work pretty much out of the box. Would like to get them working on Ubuntu as well. Any help anyone can provide would be appreciated.

---

### Post by &amp;KyT$0P# on 2024-08-19
What specific AppImage are you trying to run?
What version of Ubuntu?

When you try to run the AppImage and it doesn't work, what does happen instead?  Do you see an error message when you try to run this AppImage in Terminal?

> **ndptal85 said:**
> On Mint and Debian AppImages work pretty much out of the box. 

What version of Mint?
What version of Debian?
Is it working with the exact same AppImage that you're trying to run on Ubuntu?

---

### Post by Holger_Gehrke on 2024-08-19
Could you please explain in more detail what you mean by "won't work" ?

In my experience all that's needed for using AppImages is making them executable and then double clicking them in the file manager. In the few cases were that didn't work, I started them from the command line and got back error messages that either gave me an idea what was wrong or told me that the AppImage was looking for a library that was not possible to install (an old AppImage that expected some ancient version of a library; installing that on my system would have broken a lot of stuff; and yes, the author should have put that library into the image, but he didn't ...).

Holger

---

### Post by TheFu on 2024-08-19
I use a few appimages daily on an Ubuntu 20.04 system.  No problems. They just work, which is why I use them.

---

### Post by ndptal85 on 2024-08-19
halogen: 
I'm running Ubuntu 24.04 LTS. The AppImage is an app called Buttercup from [www.Buttercup.pw](www.Buttercup.pw). The versions of Mint and Debian that it worked on are Mint 22 and Debian 12. When it doesn't work on Ubuntu I get prompted to report an error message to Ubuntu and then nothing happens. Yes I am making the AppImage executable.

---

### Post by #&amp;thj^% on 2024-08-19
I got mine here:[https://buttercup.pw/](https://buttercup.pw/)
Made executible, and ran as:
```
 '/home/me/Downloads/Buttercup-linux-x86_64(1).AppImage' --no-sandbox

```
Also works with:
```
firejail --noprofile '/home/me/Downloads/Buttercup-linux-x86_64(1).AppImage' --no-sandbox
```
 (See Screenshot)

---

### Post by Holger_Gehrke on 2024-08-19
Just tried buttercup on my Xubuntu 22.04 system and it ran without trouble. The only thing I can say about it that it's not for me, I ... dislike ... Elektron applications because they are big and inefficient. For comparison: keepassxc (it's in the repositories) starts up faster and is a fifth of the size (21 MB vs 104 MB; there might be a bit more than 21 MB for keepassxc since .deb packages allow for dependencies which are downloaded and installed automatically). Also buttercup is **only** available as an AppImage because the developers insist on the program being able to update itself and not trusting to any external automatic update ...

Holger

---

### Post by #&amp;thj^% on 2024-08-19
> **Holger_Gehrke said:**
> Just tried buttercup on my Xubuntu 22.04 system and it ran without trouble. 

They are making it harder on purpose for 3rd party applications since 23.10 thru 24.10 which I'm currently on.

---

### Post by &amp;KyT$0P# on 2024-08-19
> **1fallen said:**
> They are making it harder on purpose for 3rd party applications since 23.10 thru 24.10 which I'm currently on.

How so?

---

### Post by TheFu on 2024-08-19
+1 for KeePassXC.  The DB it uses can be used by any keepass compatible client regardless of platform.  KeePassXC was security audited in 2023. [https://keepassxc.org/blog/2023-04-15-audit-report/](https://keepassxc.org/blog/2023-04-15-audit-report/)  Audits are far from perfect. They are really just an indication that the project team considers security important, since funding an audit usually costs real money and takes more and more time the more detailed it is.  Plus, someone with both a security and expert-level coding background IN THE LANGUAGE the project uses is not easy.  The audit was provided free to the KeePassXC team and was fairly limited in scope.  At least 1 finding that could be important was reported.  It has been known for about 10 yrs. Other KeePass DB-compatible software may not have the same issue.

I'm also not a fan of any Electron-Apps.  They are basically a limited version of Chromium/Chrome (which you probably already have loaded anyway) with settings to violate the web-browser protections for your system.  So, you get the bloat and less protections. Nice.  Google this: "Electron security issues" to better understand the major security issues.  

But everyone is different. There are a few F/LOSS password manager that work really great. I'd be surprised if you couldn't find a better option, but only you can decide what "better" is.  Be certain to look for security and corruption issues in all the "finalists" in your search.  A corrupted password DB isn't very useful.  

I replicate my DB to about 6 systems and a few of those have automatic, daily, versioned, backups, so if a corrupted DB is found, I'll likely have 120+ days to notice. Since I use the password manager almost daily, that length of time is extremely unlikely.

---

### Post by currentshaft on 2024-08-20
30001

---

### Post by #&amp;thj^% on 2024-08-20
> **halogen2 said:**
> How so?

I'd rather not post any links of proof...sorry. ;)
Here is one that will help a little bit: [https://discourse.ubuntu.com/t/flatpak-is-a-missed-opportunity/34189](https://discourse.ubuntu.com/t/flatpak-is-a-missed-opportunity/34189)
It's one that I can show without ******* someone off. 
Also this same appimage works flawlessly on Arch, and as Holger points out on 22.04 it works without issue, you will find it harder with newer releases.

> **TheFu said:**
> +1 for KeePassXC.  
Also +1

But I also don't like second guessing the OP's choice. (I'm not a Nanny type)

---

