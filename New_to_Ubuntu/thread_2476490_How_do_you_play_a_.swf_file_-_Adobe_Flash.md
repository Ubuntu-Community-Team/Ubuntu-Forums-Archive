---
title: "How do you play a *.swf file - Adobe Flash?"
date: 2022-06-27
forum: New to Ubuntu
---

### Post by cwmoser on 2022-06-27
How do you play an Adobe Flash file on Ubuntu?

---

### Post by cyberkingdom on 2022-06-27
It seems that you can use FlashArch from the snap store [https://snapcraft.io/flasharch](https://snapcraft.io/flasharch) . I have not tried it but I hope it helps.

---

### Post by cwmoser on 2022-06-27
I tried FlashArch but the program displays text in some Asian language.

---

### Post by Dennis N on 2022-06-27
I have some flash games that are .swf files. You run them with the Flatpak "Adobe Flash Player" which is the same as Adobe's old Flash Player Projector.

```
dmn@Tyana:~$ flatpak remote-info flathub com.adobe.Flash-Player-Projector

Adobe Flash Player - Player for content created using Adobe Flash

        ID: com.adobe.Flash-Player-Projector
       Ref: app/com.adobe.Flash-Player-Projector/x86_64/stable
      Arch: x86_64
    Branch: stable
   Version: 32.0.0.465
   License: LicenseRef-proprietary=https://wwwimages2.adobe.com/content/dam/acom/en/legal/licenses-terms/pdf/Flash_Player_30_0.pdf
Collection: org.flathub.Stable
  Download: 2.8*MB
 Installed: 7.2*MB
   Runtime: org.freedesktop.Platform/x86_64/20.08

       Sdk: org.freedesktop.Sdk/x86_64/20.08
    Commit: 8d8e8ee984ee06714188f888214b8f64d651de2730ba7e2b815b7211a797fdbc
    Parent: a5861f4fdc8eb6cf9b3148b01ebeb1b204377c699bd6ed0bd568ab96e7980e15
   Subject: Update runtime to 20.08 (de808b3f)
      Date: 2020-12-08 09:43:32 +0000

```

It works!

---

### Post by Holger_Gehrke on 2022-06-28
I used to use gnash for that. Sadly that project hasn't seen an update since 2011 and won't compile with modern libraries. It used to be in the repositories up to Ubuntu 18.04. There is a snap of it named 'gnash-raymii'. Finally a situation where snap does make sense (making a program available which can't run with the new libraries).

Holger

---

### Post by ActionParsnip on 2022-06-28
Just open it with your favourite web browser. Does that not work?

---

### Post by cwmoser on 2022-06-28
I tried all of the above but no joy.

---

### Post by Dennis N on 2022-06-28
> **cwmoser said:**
> I tried all of the above but no joy.
Does the player launch? 
Perhaps it's not the player, but a problem in the file itself? 
Do you have other .swf files to try?

---

### Post by ActionParsnip on 2022-06-28
[https://forums.linuxmint.com/viewtopic.php?t=278082](https://forums.linuxmint.com/viewtopic.php?t=278082)

Seems VLC can

---

### Post by Claus7 on 2022-06-29
Hello,

> **ActionParsnip said:**
> [https://forums.linuxmint.com/viewtopic.php?t=278082](https://forums.linuxmint.com/viewtopic.php?t=278082)

Seems VLC can

good to know. I had used gnash as well a long time ago and now it cannot be found under synaptic using jammy, as already mentioned.

Regards!

---

### Post by #&amp;thj^% on 2022-06-29
I know snaps are not a popular choice here, but it is in the snap store:
```
snap install gnash-raymii          # install gnash
```
to run it:
```
gnash-raymii.gnash filename.swf    # use gnash
```
Source: [https://raymii.org/s/blog/Ive_packaged_up_Gnash_as_a_Snap_for_modern_linux.html](https://raymii.org/s/blog/Ive_packaged_up_Gnash_as_a_Snap_for_modern_linux.html)
```
snap install gnash-raymii
gnash-raymii 0.8.11-2 from Remy (Raymii.org) (raymii) installed

```

---

### Post by nomarkeu on 2023-04-20
Thanks. That worked.

---

