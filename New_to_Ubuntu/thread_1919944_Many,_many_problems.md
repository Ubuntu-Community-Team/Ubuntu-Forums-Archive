---
title: "Many, many problems"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by qpnaosc on 2012-02-03
Hi there ubuntu users. I really hope someone can help me. My computer has, three separate times, failed on me, with a wide variety of symptoms. Here's what usually happens:

1) the internet gets very slow, and then the wireless network organizer keeps asking for my password whenever I log in to my account, or the wireless keeps disconnecting over and over (even though the connection itself is fine).

2) Firefox crashes as soon as I try to start it up. This is the message it gives me:
The application had a problem and crashed.
Unfortunately, the crash reporter is unable to submit a report for this crash.
Details: The application did not identify itself.

The first time this started happening, I was still able to run firefox from the terminal. this time, I couldn't, and Chrome wouldn't work either.

3) Clicking on the sound controller in the top right hand corner of the screen yields the message "Label empty," and even though it says it's muted, sound comes out of the speakers.

4)When I try to start up Synaptic Package Manager, I get the message: 
Failed to run /usr/sbin/synaptic as user root.
Unable to copy the user's Xauthorization file.

I can still update from the terminal, though, which is what I did last time this happened, and now both firefox and the package manager work.

5)Then at last the computer wouldn't run xubuntu at all. It took me to the login page, then accepts my password, only to go to a black screen which flashes the words "Stopping cold plugins [OK]" and then takes me back to the login screen. 

6) failsafe mode didn't work either. 

The first time this happened, I reinstalled Xubuntu from a disk. The second time it happened, I finally plugged the computer into a wired connection and repaired packages from the GRUB screen. It worked for a while, but now is malfunctioning again.:confused:

---

### Post by Frogs Hair on 2012-02-03
If the same installation cd has been used each time,consider burning a new cd . Run the checksum to make sure the installation media isn't corrupt .

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Rodney9 on 2012-02-03
Do the checksum, burn another CD at the slowest speed, then when you boot the CD have it check for errors.

Rodney

---

### Post by wolfen69 on 2012-02-03
Sorry to be a downer, but if the cd checks out OK and you still have all these issues, then it's obvious your computer isn't linux compatible. Btw, what is the make and model #? Is it a new computer? *And* we'll need the output of
```
lspci
```

---

