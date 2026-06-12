---
title: "64bit issue"
date: 2016-06-02
forum: New to Ubuntu
---

### Post by william_Methven on 2016-06-02
I am new to ubuntu. I want to download unity desktop in a virtual setting in a 64bit format but I can only get 32 bit so it won't load. I've tried 14.04 & 16.04.
What am I doing wrong?:confused:
I'm currently using Windows7

---

### Post by QIII on 2016-06-02
Hello!

What do you mean by you can only get 32 bit?

---

### Post by william_Methven on 2016-06-02
The version that downloads is 32 bit. There is no option to download 64bit. When I go to Virtual box to create new machine I am only given 32bit operating systems to chose from.

---

### Post by ashwin.kj on 2016-06-02
Hi!
Check if you enabled the Visualization Technology in BIOS. If you haven't VirtualBox won't provide option to simulate 64 bit OS. Depending on your system, the exact naming might be different in the BIOS. 
Also check if this is relevant to your case --[https://forums.virtualbox.org/viewtopic.php?f=1&t=62339]("https://forums.virtualbox.org/viewtopic.php?f=1&t=62339")

---

### Post by QIII on 2016-06-02
Just a moment.  What/how are you trying to download?  Please give some details.

---

### Post by mastablasta on 2016-06-03
> **william_Methven said:**
> I am new to ubuntu. I want to download unity desktop in a virtual setting in a 64bit format but I can only get 32 bit so it won't load. I've tried 14.04 & 16.04.
What am I doing wrong?:confused:
I'm currently using Windows7

alternative downloads are available here: [SIZE=2][http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)
[/SIZE]
To be able to install 64bit in virtualbox your CPU needs to be 64 bit and it needs to support virtualization which has to be enabled in BIOS. CPU virtualization is branded VT-x on Intel based BIOS and AMD-V on AMD bios. this needs to be turned on in BIOS in order for you to be able to install 64bit os in virtual box.

Make sure you have enough RAM available on windows host and dedicate it enough to the OS you are trying ot run (64bit needs a bit more than 32 bit).

Old but for the most part still valid guide: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by william_Methven on 2016-06-03
Thanks!

---

### Post by oldrocker99 on 2016-06-03
If your problem is fixed, please mark this thread as [SOLVED].

---

