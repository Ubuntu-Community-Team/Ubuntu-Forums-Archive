---
title: "audio problem xubuntu_ sound card recognised but not working"
date: 2017-01-22
forum: New to Ubuntu
---

### Post by enrico-miki on 2017-01-22
Hi guys, sorry for my bad english, I'm Italian.
I've just installed a xubuntu distro on my old laptop (Acer Aspire-5040)
but I dont hear any sound.
I tried to follow some indications on this page ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting))
 but I'm not really able to do something useful.

Can someone please help me? I'm sure this problem can be solved
 (I had same problem with Lubuntu's distros but the sound worked with Ubuntu 10.10 LTS if I remember correctly)

Enrico

---

### Post by bitsnpcs on 2017-02-07
Hello Enrico,
unsure what you have tried from the tutorial link -

1/ do you hear sound using headphones ?
2/ from the tutorial, open a terminal (ctrl alt t), and copy/paste this in -
```
 lspci -v | grep -A7 -i "audio" 
```

copy/paste the results in your reply, this may help people to assist you.

Before the pasted results in the forum type the word **code** inside square brackets, after the copy/paste on the forum type **/code** in square brackets.

---

