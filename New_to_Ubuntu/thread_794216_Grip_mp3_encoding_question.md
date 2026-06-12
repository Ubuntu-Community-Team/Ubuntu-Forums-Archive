---
title: "Grip mp3 encoding question"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by paker on 2008-05-14
I installed 8.04 and Grip is not doing mp3 encoding. I entered "-V 6" in the command line and hit enter. Prompt says "invalid encoder executable." What did I miss? Thanks.

---

### Post by quelx on 2008-05-14
try ```
sudo apt-get install lame
``` or the same with synaptic

---

### Post by Het Irv on 2008-05-14
Did you install the Codecs?  Because Ubuntu is free, and the MP3 format is propietary, it cannot be legally included on the CD, (in the US).  Look for gstreamer in Add/Remove.

---

### Post by paker on 2008-05-14
1. LAME: It was not installed. Installed and rebooted. Same message.
2. GSTREAMER: When I searched for gstreamer, movie player pops up with gstreamer in parentheses. Movie Player is already installed.
3. CODEC: Being not much computer savvy, after fresh installation of ubuntu, I always installed Automatix. Now it's not available for 8.04. I don't know where to get the codecs. If you can give me a general pointer, I will read up the material.

Thanks.

---

### Post by Oldsoldier2003 on 2008-05-14
> **paker said:**
> 1. LAME: It was not installed. Installed and rebooted. Same message.
2. GSTREAMER: When I searched for gstreamer, movie player pops up with gstreamer in parentheses. Movie Player is already installed.
3. CODEC: Being not much computer savvy, after fresh installation of ubuntu, I always installed Automatix. Now it's not available for 8.04. I don't know where to get the codecs. If you can give me a general pointer, I will read up the material.

Thanks.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by stchman on 2008-05-14
> **paker said:**
> I installed 8.04 and Grip is not doing mp3 encoding. I entered "-V 6" in the command line and hit enter. Prompt says "invalid encoder executable." What did I miss? Thanks.

If you have 32bit Hardy do this:

```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

This will install all the CODECs you need.

---

