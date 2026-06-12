---
title: "Problems starting Pidgin"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by Szise on 2012-10-03
I have [SIZE=2]Pidgin 2.10.3 (libpurple 2.10.6) and Ubuntu 12.04 LTS

When I want to start Pidgin the icon appears in Unity but not the window, to open the Pidgin window I have to click "quit" in laucher and start it again, only after trying 2 times I can open the Pidgin window, (Buddy List). 
[/SIZE]

---

### Post by daslinkard on 2012-10-03
Have you tried purging Pidgin and then reinstalling?  Would this be an option to purge it off your system and then try to reinstall?

---

### Post by illegal on 2012-10-05
I am facing the same problem too. The pidgin window never comes up though it shows the logo in the task bar. What I do is, I use the kill command to kill it manually - supplying the process id; and then open it. It is really annoying since I have to do it everytime when I open up pidgin. Any solution?

> **daslinkard said:**
> Have you tried purging Pidgin and then reinstalling?  Would this be an option to purge it off your system and then try to reinstall?

Could you please let me know how to do the same?

---

### Post by illegal on 2012-10-05
Update: Purged and reinstalled. Will update the status here - if it is working properly or in the same state.

EDIT: Commands I used-
```
sudo apt-get purge pidgin
```
```
sudo apt-get install pidgin
```

---

### Post by daslinkard on 2012-10-05
> **illegal said:**
> Update: Purged and reinstalled. Will update the status here - if it is working properly or in the same state.

EDIT: Commands I used-
```
sudo apt-get purge pidgin
``````
sudo apt-get install pidgin
```
These commands should get you where you need to be...let me know if they work for you.

---

### Post by illegal on 2012-10-06
> **daslinkard said:**
> These commands should get you where you need to be...let me know if they work for you.

Unfortunately, after a restart, things are back to square one. It just shows the Pidgin logo on the taskbar and I've kill it manually and restart inorder to see the Pidgin window and login. Any workaround/solution? This thing is bugging me a lot.

---

### Post by daslinkard on 2012-10-07
> **illegal said:**
> Unfortunately, after a restart, things are back to square one. It just shows the Pidgin logo on the taskbar and I've kill it manually and restart inorder to see the Pidgin window and login. Any workaround/solution? This thing is bugging me a lot.
I was gone all day yesterday and will be working on a solution for you later today!

---

### Post by illegal on 2012-10-07
> **daslinkard said:**
> I was gone all day yesterday and will be working on a solution for you later today!

Thanks man!
Btw, is this a common bug? Or a less frequent one? I guess many people should be facing the same (?)

Could you please suggest me a good GTalk client other than Pidgin and Empathy? I would like to try :)

---

### Post by daslinkard on 2012-10-07
What happens when you go to the terminal and call up pidgin that way?
```

pidgin
```
I had a similar issue with Skype not too long ago and this was one work around for me.

---

### Post by illegal on 2012-10-07
> **daslinkard said:**
> What happens when you go to the terminal and call up pidgin that way?
```

pidgin
```
I had a similar issue with Skype not too long ago and this was one work around for me.

Since I am already running Pidgin now, it says:
> Exiting because another libpurple client is already running.


I used to call Pidgin this way too (tried it when I started noticing this problem), but the result used to be the same.

---

### Post by daslinkard on 2012-10-07
> **illegal said:**
> Since I am already running Pidgin now, it says:


I used to call Pidgin this way too (tried it when I started noticing this problem), but the result used to be the same.
You can start by killing pidgin
```
killall pidgin
```
then
```
pidgin
```
See if that allows you to start the program correctly.

---

### Post by daslinkard on 2012-10-07
Quick question for you....are you using Yahoo or MSN for your account log in?  I've seen where some people where having issues with Yahoo but had no problems when entering in their MSN info....just thinking out loud....

---

### Post by illegal on 2012-10-07
> **daslinkard said:**
> Quick question for you....are you using Yahoo or MSN for your account log in?  I've seen where some people where having issues with Yahoo but had no problems when entering in their MSN info....just thinking out loud....

I just use my Google Talk account on Pidgin and rarely Yahoo account. Never used any other accounts.

Btw, will post the result of killall and restarting commands after a restart (since I see the problem only after a restart and right now it is working fine as I've already excecuted a kill -9 <proc id> command to kill Pidgin and then have restarted it). Will update the thread after I do so. Would take some time as I am in the middle of doing some official work... :) Thanks a lot man! :)

---

### Post by daslinkard on 2012-10-07
> **illegal said:**
> I just use my Google Talk account on Pidgin and rarely Yahoo account. Never used any other accounts.

Btw, will post the result of killall and restarting commands after a restart (since I see the problem only after a restart and right now it is working fine as I've already excecuted a kill -9 <proc id> command to kill Pidgin and then have restarted it). Will update the thread after I do so. Would take some time as I am in the middle of doing some official work... :) Thanks a lot man! :)
No worries at all...I look forward to reading your update.

---

### Post by illegal on 2012-10-08
> **daslinkard said:**
> No worries at all...I look forward to reading your update.

Update: *killall pidgin* and *pidgin* commands made Pidgin to work like a charm soon after a restart.

Hmm... But isn't this the same as the one which I was using before? *kill -9 <procid>* and *pidgin*? You mean to say that every time I've to execute these two commands to run pidgin? :shock:

---

### Post by daslinkard on 2012-10-08
> **illegal said:**
> Update: *killall pidgin* and *pidgin* commands made Pidgin to work like a charm soon after a restart.

Hmm... But isn't this the same as the one which I was using before? *kill -9 <procid>* and *pidgin*? You mean to say that every time I've to execute these two commands to run pidgin? :shock:
I don't believe you should have to use both commands to properly run pidgin.  However if you go to start it and you have that issue of not being able to call it up then you now have the commands to kill the process and restart it.

After doing the killall command and opening the pidgin from the terminal, did it require you to restart the PC before the program would work or does it work properly without the restart?

---

### Post by illegal on 2012-10-09
^^ I was using the kill and start command even before (I've mentioned it too) :)

No, after the killall and start Pidgin command, a restart is not required. The thing is, the problem is visible only after a restart - ie., if I do a fresh restart, Pidgin doesn't open unless and until I kill it manually and * restart the app *. Once I am done with my session and shutdown the machine, the same thing happens in the next restart. I need to kill it once again and restart the app. I guess there is no permanent solution for this :(

---

### Post by daslinkard on 2012-10-10
I will keep searching to see if I can find a solution for you...

---

### Post by illegal on 2012-10-10
> **daslinkard said:**
> I will keep searching to see if I can find a solution for you...
No worries man! :) And thanks for your help all the way! Meanwhile I'm also searching for a solution. Will update on this thread if I come across anything useful :)

---

### Post by illegal on 2012-11-02
Hey [daslinkard]("http://ubuntuforums.org/member.php?u=1565157"), I've actually managed to get rid of this issue. The problem got vanished after I installed GNOME and everything is working fine. The Pidgin issue which we discussed above is no more bugging me :)

---

