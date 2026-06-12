---
title: "Problem with the beta"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-10-26
I had 8.04 and wanted to try the new beta and donate feedback. I just installed it and was asked to reboot. I rebooted and it is stuck at the black screen that is there after the startup sound. Sorry about my grammer, I have to type on iPod touch. I guess what I'm asking is how can I fix this or go back to 8.04 without reformatting?

---

### Post by ImThatNerd on 2008-10-26
Since it won't boot I went into recovery and updated packes and removed obsolete software and it still won't boot.

---

### Post by Peter09 on 2008-10-26
Go into recovery mode and type at the command prompt

```
startx
```

see if you get a GUI. Also post the output of

```
lshw -C video
```

---

### Post by ImThatNerd on 2008-10-26
when I do starts it says server error and no such process. I did the other command and some text showed up. But seeing as I'm on my iPod there is no way for me to post all this so can I just tell you what you are looking for? I just did starts agaign and got a black screen.

---

### Post by Peter09 on 2008-10-26
Server Error does not sound right:confused:

Just to check - you typed startx at the command prompt in recovery mode?
When you type ```
lshw -C video
``` is shows you what Ubuntu has found for your video card and drivers. Can you find out what video card you have and what driver Ubuntu is using for it. It should be in the output.

---

### Post by ImThatNerd on 2008-10-26
once I click recovery mode and enter it I hit drop to root shell prompt, right? It says fatal server error lockup.   Once I type the other command it says chipset integrated graphics device. I am not sure where to look for the driver name.

---

### Post by Peter09 on 2008-10-26
At the recovery command prompt type the following to try and reconfigure your xserver

```
dpkg-reconfigure -phigh xserver-xorg
```

Try ```
startx
``` afterwards

---

### Post by ImThatNerd on 2008-10-26
I ran the first command and it worked and then I ran starts and there was just green boxes on the screen. Ijust rebooted and it is still black. I have the 8.04 live cd and I was wondering if I can keep allmy files and go back to 8.04?

---

### Post by Peter09 on 2008-10-26
Just another thought, as you have deleted stuff it may be worth checing that you have all the necessary files. At the command prompt type

```
apt-get update
```
followed by

```
apt-get upgrade
```

then reboot to the recovery prompt and try startx again.

---

### Post by ImThatNerd on 2008-10-26
I got failed to fetch errors. So in recovery I went to the fix broken packages option and it said no updates found and I got failed to fetch errors too.

---

### Post by Peter09 on 2008-10-26
Failed to fetch suggests that you have no internet connection. Not sure what happened with you upgrade but it does look a problem.

---

### Post by ImThatNerd on 2008-10-26
I remember when using the live cd I had to go into firefox and go to about:config and enable something for my Internet to work, same with 8.04.   Well thanks for all the help I guess I will make a thread in the morning asking about keeping my partion and files and going to 8.04.

---

