---
title: "Can't copy from share"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by lolwhites on 2008-09-02
I can access a shared folder of photos on my wife's XP laptop. However, when I try to copy the folder to my hard drive, it won't cooperate.

Dragging and dropping to a folder on my PC does nothing. When I try to copy and paste, the window of the folder I'm trying to paste into just closes. The only way I've found that works is to open a shared picture, then save it to a folder on my computer, but that's very long winded. Surely there's a better way!

---

### Post by luckyuser on 2008-09-02
have you tried doing it as root? what does it say if you try to cp the files using the terminal?

---

### Post by lolwhites on 2008-09-02
When I try to open the folder as admin, I get "Nautilus canot handle smb: locations"
When I try to cd to the folder in terminal I get "no such file or directory", even when I drag the folder into the terminal to get the address right.

---

### Post by Dedoimedo on 2008-09-02
Hello,

1. Did you install samba?
2. Did you try copying via command line?

Cheers,
Dedoimedo

---

### Post by luckyuser on 2008-09-02
> **Dedoimedo said:**
> Hello,

1. Did you install samba?
2. Did you try copying via command line?

Cheers,
Dedoimedo

i just assumed it was already installed since the rest seemed to work.

---

### Post by lolwhites on 2008-09-02
1. Isn't samba in Hardy by default? After all, I have no problem seeing the files, and when I drag the file into a terminal I get an address that begind smb:

2. I don't know if I can copy from the command line, but I ceratinly can't navigate to the directory via terminal.

---

### Post by luckyuser on 2008-09-02
I'm running Hardy and it does have Samba, so I'd say you have it too...by default.

You may need to configure Samba though (not sure if you current settings are correct).

here's a tute
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

edit: p.s. you can confirm if you have samba via synaptic, but it might be good to try and install it either way...some might say a reinstall is pointless on linux, but i beg to differ based on experience.

---

### Post by lolwhites on 2008-09-02
Oddly, I have no problem copying the folder to my desktop, it's only when I copy to a folder in ~/photos that it refuses to play ball.

---

### Post by luckyuser on 2008-09-02
are the permissions set differently for your pictures and desktop folders? beyond that, I can't think of why this is happening to you...

---

### Post by halitech on 2008-09-02
> **lolwhites said:**
> I can access a shared folder of photos on my wife's XP laptop. However, when I try to copy the folder to my hard drive, it won't cooperate.

Dragging and dropping to a folder on my PC does nothing. When I try to copy and paste, the window of the folder I'm trying to paste into just closes. The only way I've found that works is to open a shared picture, then save it to a folder on my computer, but that's very long winded. Surely there's a better way!

if the window is closing there is a reason why it is closing. What format are the picture ins? ie. jpg, bmp, tiff, gif?

---

### Post by lolwhites on 2008-09-02
Nope, the permissions appear to be the same :confused:

---

### Post by lolwhites on 2008-09-02
Halitech - the pictures are all jpeg.

I don't know if this is relevant, but I couldn't mount the original CD the photos came on, which is why we copied them onto my wife's laptop and shared them over the network.

---

