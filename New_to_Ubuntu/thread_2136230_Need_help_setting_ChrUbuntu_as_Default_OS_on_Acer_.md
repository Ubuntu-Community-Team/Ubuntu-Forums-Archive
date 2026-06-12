---
title: "Need help setting ChrUbuntu as Default OS on Acer C7 Chromebook"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by Chatise on 2013-04-16
New to Ubuntu forums here.
So, if you're reading this, I pray you are somewhat experienced with ChrUbuntu, as I am not. So, on my Acer C7 Chromebook, I installed ChrUbuntu. After, it immediately loads ChrUbuntu. But on reboot, it boots directly into Chrome again, which I DO NOT WANT. On ChrUbuntu's dev blog site, it says I can open the dev console in ChromeOs and type
sudo cgpt add -i 6 -P 5 - S 1/dev/sda
Apparently, this sets ChrUbuntu to the default OS. 
WRONG. 
Upon reboot, it flashes the warning sign for developer mode (it will ALWAYS do this, no matter what) and boots ChromeOS. At this point, I have 291 GB of storage dedicated to a OS I can't access. Any help?

---

### Post by Chatise on 2013-04-16
And if no one can help me set it as Default OS, can someone give me a command that will boot ChrUbuntu from the ChromeOS dev terminal? Thanks again in advance. Remember, it's the Acer C7, not the Pixel, the 5, or the Samsung ARM.

---

### Post by TheTestBear on 2013-04-17
Hi Chatise, I've recently installed Chrubuntu on C7 and it's been working fine for me. I'm constantly switching between the two the OSes.

I see two things wrong with the command: [COLOR=#000000]sudo cgpt add -i 6 -P 5 - S 1/dev/sda, and that is that you need a space between the 1 and the /dev/sda, and no space between the - and the S

So it should read: sudo cgpt add -i 6 -P 5 -S 1 /dev/sda
That should work.
Oh! And don't forget to log in as Chronos first, no password required.

And you'll get the developer mode warning regardless of which OS you're using.

If you want to run both OSes at the same time, try checking out [this]("http://craigerrington.com/blog/arm-chromebook-chromeos-and-xfceubuntu-at-the-same-time/") site. I've not tested to see if it'll work or not, but I intend to as soon as I have some free time.

Bonne chance, monseigneur.[/COLOR]

---

### Post by Chatise on 2013-04-17
> **TheTestBear said:**
> Hi Chatise, I've recently installed Chrubuntu on C7 and it's been working fine for me. I'm constantly switching between the two the OSes.

I see two things wrong with the command: [COLOR=#000000]sudo cgpt add -i 6 -P 5 - S 1/dev/sda, and that is that you need a space between the 1 and the /dev/sda, and no space between the - and the S

So it should read: sudo cgpt add -i 6 -P 5 -S 1 /dev/sda
That should work.
Oh! And don't forget to log in as Chronos first, no password required.

And you'll get the developer mode warning regardless of which OS you're using.

If you want to run both OSes at the same time, try checking out [this]("http://craigerrington.com/blog/arm-chromebook-chromeos-and-xfceubuntu-at-the-same-time/") site. I've not tested to see if it'll work or not, but I intend to as soon as I have some free time.

Bonne chance, monseigneur.[/COLOR]

Okay, is there any particular message I should recieve? Or will it just load a new command line?

---

### Post by TheTestBear on 2013-04-17
Once you've put the command in you shouldn't receive any messages, there should just be a line for you to put another command in. Just type exit into that line, Ctrl+Alt+F1 to return to Chrome OS, shut down, then turn your Chromebook back on.

If it helps, watch [this]("http://www.youtube.com/watch?v=4qpjTzav3kw") video from about 11:50 onwards I think. I'm at work so can't verify the  exact starting time, but for me it was good to have the instructions in video form.

---

### Post by Chatise on 2013-04-19
Wow, man, thanks so much. Finally got ChrUbuntu up and running, and I'm digging it's performance. 
Thanks again for the help, next to upgrade the internals :guitar:

---

### Post by oldrocker99 on 2013-04-29
I am running ChrUbuntu 12.04, with razor-qt for my desktop, and it rocks, with a glmark2 score of 419. 0AD and Warzone 2100, pretty graphics-intensive RTS games, run like a champ. Torchlight failed to run, though, which bears further investigation on my part.

Not to mention having Libre Office, GIMP, and all the other wonderful programs I've been using for my five years as a GNU/Linux user. I've never had more fun with computers than the last five years.

---

