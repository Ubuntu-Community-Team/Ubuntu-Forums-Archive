---
title: "Can't fine file"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by JPtux on 2008-08-16
I'm having troubles configuring ALSA to use my USB headset. I'm following a guide that tells me to add this to the "~/.asoundrc" file:

```
pcm.headset {

        type hw

        card 1

}

ctl.headset {

        type hw

        card 1

}
```
Yet, I am unable to find the "~/.asoundrc" file. Where is the file exactly located? Thanks in advance.

---

### Post by jualin on 2008-08-16
The **~** means your home directory. So the file is located under /home/your_user_name/.asoundrc

---

### Post by dje on 2008-08-16
it is a hidden file in your home folder ~ means your home folder and . means hidden. to edit it open a terminal and run:
```
gedit ~/.asoundrc
```
or open your home folder in nautilus (file browser) and press Ctrl + H, find the .asoundrc file and double click it to open with gedit 

dje

---

