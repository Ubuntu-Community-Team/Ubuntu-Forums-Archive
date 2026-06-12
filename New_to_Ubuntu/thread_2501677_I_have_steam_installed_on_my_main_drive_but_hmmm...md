---
title: "I have steam installed on my main drive but hmmm..."
date: 2024-10-17
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-17
[COLOR=#000000][INDENT]I have steam installed on my main drive but want games to install on a different drive, and I have done that successfully, but when I reboot it says the drive isn't there and I have to repoint it to that drive again, how to I stop that from happening and make sure it stays to the drive like um save it?
[/INDENT]
[/COLOR]

---

### Post by nicolasdentremont on 2024-10-17
It sounds like the drive or partition doesn't mount when the system  starts. You can add the drive or partition to the /etc/fstab file and it  will mount when the OS starts. I have a drive for music and movies that I had to mount every time before VLC would remember it.

There's some good info on that here: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by shadowtabby on 2024-10-18
Heyo,

Thank you for your reply.  I read this, and beccause I am new to this, I am a bit unsure of doing it cause I am worried I will screw up the disk mounting.  Yes IK it's bluh, at the moment I got used to installing things.  Enjoying that experience.

But I will see if my mate can do it for me since he is more experienced on linux then me with mounting.  He wanted me to ask here first.

Thank you so much.

---

### Post by Perfect Storm on 2024-10-18
How did you install Steam? Via Software center (snap?) (flatpak?) (.deb from steam homepage?)
The reason I am asking is that snap and flatpak are running in sandbox and can't default see outside it. I don't have snap and I know you need flatseal for flatpak to set up permission for steam to see outside its sandbox.

Yuo should try the .deb steam from their homepage, though you might want to setup i386 package enable on your Ubuntu to do so.

```
sudo dpkg --add-architecture i386
sudo apt update
```

Then install the .deb from Steam homepage

---

### Post by shadowtabby on 2024-10-18
Heyo,

I will take this into consideration if steam gets annoying.  But Honestly I don't remember where i installed it from, I always try and get the commands for it on the site like obs from obs site, etc, or from the store.  I do get iffy where I get installers from.

---

### Post by shadowtabby on 2024-10-19
Heyo,

I just installed steam from their website.  Also I noticed that I cannot load cyberpunk where as when I had the app store version I could.

---

### Post by nicolasdentremont on 2024-10-19
> **shadowtabby said:**
> Heyo,

I just installed steam from their website.  Also I noticed that I cannot load cyberpunk where as when I had the app store version I could.

Did you enable compatibility for all games in the steam compatibility settings?

---

### Post by shadowtabby on 2024-10-19
Heyo,



NICE!!!  THANK YOU!!!!

---

