---
title: "[SOLVED] Ubuntu &amp;amp; Fujitsu Siemens Computers Amilo Li2735mWiFi issues."
date: 2008-09-30
forum: New to Ubuntu
---

### Post by calrogman on 2008-09-30
Hello all, I recently recieved a Fujitsu Amilo Li2735 Laptop, preloaded with Winsucks Vista (:() and upon trying my Ubuntu 8.04 LiveCD, I found that the only way to turn on my WiFi, was to use some Windows only software that came with the computer.

I was wondering if their are any other users who have experienced this and have had the problem resolved and, if you have, how.

Thanks in advance! :-D

---

### Post by talsemgeest on 2008-10-01
I'm sorry but I'm very new to wi-fi on ubuntu, but if there is no linux driver, you will have to use ndiswrapper. That will let you use the windows driver under linux, but I have never had to use it so I cant give you directions. Google should give you some good help though.

---

### Post by calrogman on 2008-10-01
Thanks for the feedback, but I guess I should of mentioned that it isn't a driver I need, it's a way of actually turning the WiFi on, seeing as even in Windows Vista I have to go through a piece of Windows only software, to turn on my WiFi, and yes I have updated my Windows WiFi drivers, and no I can't tell it to do it automatically, not that that is surprising, I mean, it *is Vista*.

---

### Post by shifty_powers on 2008-10-01
that is very, very strange. i have yet to come across a modern laptop that does not have a radio button to turn on/off the wireless. it might be on the front, top or side...

i'll have a look at that model...

---

### Post by shifty_powers on 2008-10-01
ok, not found any evidence of one, which is very strange.

my advice would be to go into the bios. i cannot believe that there is no option to have the wireless turn on automatically when it boots up...

---

### Post by calrogman on 2008-10-02
I'll have a peek at the BIOS, thanks.

---

### Post by calrogman on 2008-10-02
Got a couple of mixed signals, The BIOS says my WiFi is on, Windows thinks it isn't at startup, and Linux agrees with Windows, so I'm disabling the startup of the application that turns the WiFi on, and checking to see if it also turns it off at startup.

If it's being turned off at Windows startup, then I'll need Linux drivers, otherwise the WiFi turns itself off automatically.

Also, Vista, being Vista kept being incredibly irritating and high-jacking my system when I tried to get in the BIOS, but thats Vista for you.

Yes, I hate Vista.

---

### Post by calrogman on 2008-10-05
Bumping
Up
My
Post
:lolflag:

---

### Post by calrogman on 2008-10-09
Never mind, I have found a solution to the problem [here]("http://ubuntuforums.org/showthread.php?t=644899").

---

### Post by talsemgeest on 2008-10-09
Glad you got it working. Just don't forget to mark this thread as solved.

---

