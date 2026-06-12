---
title: "Cannot connect to internet on ubuntu"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by marc_2021 on 2008-11-02
Hello, I'm a new user to the linux world. I have been able to install ubuntu hardy heron and it works perfectly for me but the only major issue I have is that I can't connect to the internet. 

I've tried different things like ubudsl, I've downloaded the ueagle drivers and followed the procedures on this site about how to install but i've not been successful. can anyone please help me?

---

### Post by okey666 on 2008-11-02
You need to give us some specifications. Are you connecting via a router? Is it wireless? If so, what kind of adapter are you using? Usb or PCI?

---

### Post by marc_2021 on 2008-11-02
I'm using a "sagem fast 800" adsl usb modem.

---

### Post by Hazer on 2008-11-02
Take a look at this:

[http://www.bandstand.org.uk/~adamgray/fast800.html](http://www.bandstand.org.uk/~adamgray/fast800.html)

---

### Post by ugm6hr on 2008-11-02
This suggests it works with a driver: [http://brainstorm.ubuntu.com/idea/4864/](http://brainstorm.ubuntu.com/idea/4864/)

Of course - this gives a rather more helpful solution: [http://agafix.org/sagem-fst-800-adsl-modem-delivered-by-maroc-telecom-on-linux-finally-the-how-to-that-works/](http://agafix.org/sagem-fst-800-adsl-modem-delivered-by-maroc-telecom-on-linux-finally-the-how-to-that-works/)

---

### Post by marc_2021 on 2008-11-02
Can anyone give me a more simple and detailed solution to my problem coz I'm a newbie and these codes don't make any sense to me.

---

### Post by rhcm123 on 2008-11-02
Alright, do this:
1. Go to:
[http://www.ubudsl.com/en/download.php](http://www.ubudsl.com/en/download.php)
Download the appropriate driver (you said you were 8.04, i belive)

2. Click instructions on the same page, or this link:
[http://www.ubudsl.com/en/instruction.php](http://www.ubudsl.com/en/instruction.php)
Now, according to the instructions, all you have to do is download, type your password, and click install. Let us know if anything comes up.

---

### Post by clb137 on 2008-11-02
> **marc_2021 said:**
> Can anyone give me a more simple and detailed solution to my problem coz I'm a newbie and these codes don't make any sense to me.

Hi,

If you open this up in your web browser [http://www.bandstand.org.uk/~adamgray/fast800.html](http://www.bandstand.org.uk/~adamgray/fast800.html)

as you scroll down you will some code in white boxes, high light this and copy it into your teminal then press enter, to start a terminal go to applications-accessories-terminal.

have a go its fun, a little scary at first 

good luck
clint

---

### Post by rhcm123 on 2008-11-02
Also, it states that you must then go to System -> Administration -> ADSL and configure the system. Read the instructions and use the settings appropriate for you.

---

### Post by marc_2021 on 2008-11-03
> **rhcm123 said:**
> Also, it states that you must then go to System -> Administration -> ADSL and configure the system. Read the instructions and use the settings appropriate for you.

Hi, I installed the ubudsl succesfully and tried to configure it. It even detected my modem but I don't know why it can't connect to the internet. 

I've taken some screenshots to show that I've been able to run the configuration.

When I had entered my login details details, password, my country (Mauritius), and chosen ppp0A, the screen changed to the one as screenshot-4. There was no message whether something was wrong.

I waited about 5 mins. and there was still no message. So I clicked on quit, restarted my pc, logged on to ubuntu and ran the ubudsl applet but could not get connected (screenshot-2).

What should I do?

---

