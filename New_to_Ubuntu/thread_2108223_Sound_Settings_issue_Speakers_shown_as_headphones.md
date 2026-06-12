---
title: "Sound Settings issue: Speakers shown as headphones?"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by Craters on 2013-01-24
Just started using Ubuntu 12.04. When I turn on my speakers and go to Sound Settings/Output there are two options SPDIF and Headphones. Headphones is automatically highlighted and when I Test Sound it comes out my speakers. How do I fix this?
 
EDIT: I am using Ubuntu Desktop 12.04.1 LTS 32.bit installed via CD. I have only been using it for about 3 days, so I do not have much experience with it.
 
The Speakers I am using are Logitech Z313 which are connected into the green port at the back of my Dell PC. Also tried plugging in earphones into the headphone jack which show as headphones.

---

### Post by Craters on 2013-02-02
If anyone has any thoughts on why it might be like this please reply thanks.

---

### Post by Yellow Pasque on 2013-02-02
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by audiomick on 2013-02-02
> **Craters said:**
> The Speakers I am using are Logitech Z313 which are connected into the green port at the back of my Dell PC. Also tried plugging in earphones into the headphone jack which show as headphones.

As far as I know, the green audio port is a headphone output. The computer will, all things being equal, register that something is plugged in to that socket, but that is all. It has no way of knowing whether it is earplugs, headphones or a set of speakers, so it will probably think anything you plug in there is headphones.

---

