---
title: "Help with music"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by realunreal on 2008-09-25
Hi,

I'm a new Linux user and would like some help with the music player,  I have just installed Ubuntu for the first time.

I have a second USB harddrive which has all my MP3's on and I can access it,  however when I click an MP3 and try to play it I get the following error message.

Totem could not play file,  you do not have a decoder installed to handle this file.  You might need to install the necessary plugin.

How do I go about resolving this ? ? ?

---

### Post by cmay on 2008-09-25
in the add remove programs menu.
under music and video there is some packages. gstreamer extra plugins.

---

### Post by MarlonDean on 2008-09-25
Click system -> administration -> synaptic package manager and click on the search button. Type ubuntu-restricted-extras and click ok. select the package called ubuntu-restricted-extras and click apply. This will install a lot of useful stuff like codecs, java and flash player

---

### Post by realunreal on 2008-09-25
> **cmay said:**
> in the add remove programs menu.
under music and video there is some packages. gstreamer extra plugins.

Thanx for your quick reply, another quick question.

I have two sound cards installed and Ubuntu seems to have rocognised both of em' however I can't find a way of getting Totem to play through the second card.

Do you know how to set preffered playerback device.

I'll give a quick explanation of how I had my windows setup working,  I had one card as default primary device where all windows jingles and sounds cam from and then I had the Windows media player set to the second card.

---

### Post by billgoldberg on 2008-09-25
Run this command, should satisfy ALL you codecs needs:


```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by realunreal on 2008-09-25
Please check my post above yours I have a more pressing concern !

---

### Post by billgoldberg on 2008-09-25
> **realunreal said:**
> Please check my post above yours I have a more pressing concern !

It would be best if you create a new thread for your problem.

Use a good title like

"make totem use second audio card"

---

### Post by realunreal on 2008-09-25
kk,  will do

---

