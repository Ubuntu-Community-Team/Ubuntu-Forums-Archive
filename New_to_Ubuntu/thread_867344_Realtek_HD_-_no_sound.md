---
title: "Realtek HD - no sound"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by the_duality on 2008-07-22
Hello everyone - complete linux noob here :)

I recently installed Ubuntu 8.04 on my Acer Aspire 5920G laptop. All went well apart from the fact that I have no sound. If I test the sound in System > prefs > sound, I get nothing - but if I plug headphones in, I hear the tone. I have a realtek HD integrated soundcard.

I have searched these forums and found a few people with issues, but reading the threads I found myself in way over my head :p

I hope someone can help me sort this out - its the only thing stopping me using Ubuntu properly :)

Cheers

---

### Post by northern lights on 2008-07-22
Can you post the output of ```
cat /proc/asound/cards
```

Thank you.

---

### Post by the_duality on 2008-07-22
Cheers for the quick reply :)

```
matt@matt-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3600000 irq 22

```

---

### Post by northern lights on 2008-07-22
Are you not running Hardy? Cause in 8.04 the previously troublesome Intel High Definition Audio chips should work out of the box.

Anyhoo, you might wanna read [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by the_duality on 2008-07-23
Yes, I am running 8.04 - I was expecting it to work out of the box too to be honest :p

Cheers for the guide link - I followed it through and did all the commands, but still no joy. I will try to reinstall ubuntu and see if that makes a difference - something might have gone dodgy during the install.

---

### Post by the_duality on 2008-07-23
Well, I reinstalled - and no joy on the sound front. Anyone have an ideas? :(

---

