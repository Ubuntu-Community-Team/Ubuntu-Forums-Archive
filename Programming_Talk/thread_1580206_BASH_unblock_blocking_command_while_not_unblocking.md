---
title: "BASH: unblock blocking command while not unblocking password prompt"
date: 2010-09-23
forum: Programming Talk
---

### Post by chewearn on 2010-09-23
Okay, I am trying to write a BASH script to connect to bluetooth modem.  The relevant command is:
```
gksudo rfcomm connect 4
```So, here is the problem.  The rfcomm will block until cancelled by CTRL+C, upon which it will disconnect.  What I want is the command to be sent to background so the script can continue.

Now, this looks like the solution:
```
gksudo rfcomm connect 4 &
```However, it actually unblock not just "rfcomm", but "gksudo" as well.  Essentially, the script does not wait until I enter the password.

So, let's say I have this:
```
gksudo rfcomm connect 4 &
notify-send "Connected!"
```I will see the connected notification immediately, regardless of the opened password prompt.

So, how do I make the script block at the password prompt, but not afterwards at "rfcomm" command?

---

### Post by SaintDanBert on 2010-09-23
> **chewearn said:**
> 
...
So, let's say I have this:
```
gksudo rfcomm connect 4 &
notify-send "Connected!"
```I will see the connected notification immediately, regardless of the opened password prompt.
...


Check out **job control** and **redirection** in the BASH man pages. When a command ends in ampersand, it goes into the "background". That is "job control." There are ways to wait for something running in the background.

There are ways that use redirection and pipes to get details from one command process to the next.

I've done this before, but do not remember the details as I write ... zzzz ... this. I'll blow some dust off and post more later. Please post if you solve the problem. Please mark this question solved. And please report your solution so others will know.

Bonne chance,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-09-23
Take a look here:
[http://unstableme.blogspot.com/2008/06/bash-wait-command.html](http://unstableme.blogspot.com/2008/06/bash-wait-command.html)

~~~ 0;-Dan

---

### Post by chewearn on 2010-09-23
> **SaintDanBert said:**
> Check out **job control** and **redirection** in the BASH man pages. When a command ends in ampersand, it goes into the "background". That is "job control." There are ways to wait for something running in the background. 

Thanks for the reply.

Yeah, as I already explained, I tried the ampersand to send the command to the background, but it ended up sending the entire lot: both "gksudo" and "rfcomm".  What I wanted was for the gksudo to remain in the foreground, blocking the script and wait for me to enter the password.  Then, "rfcomm" will execute into the background and not blocking the script.

> There are ways that use redirection and pipes to get details from one command process to the next.

Well mate, this what I have been reading and googling on with no success.

> Please post if you solve the problem. Please mark this question solved. And please report your solution so others will know.

I have decided to work around this problem, skip notification in the script itself.  Instead I am currently playing with udev event to trigger the notification.

---

### Post by SaintDanBert on 2010-09-23
I'm sorry if I did not understand your original problem well enough and so I wasted your time with responses off in the weeds.

In the late 90's, I used linux to run industrial instruments on a LAN. Scripts and programs as processes -- all talking and waiting for each other -- was our bread and butter. We didn't have udev or similar. Without knowing more, it is hard to tell if udev is overkill or "just right." Either way, a udev-based solution would make wonderful reading.

Please keep posting your progress.  I'll help if I can.
~~~ 0;-Dan

---

### Post by chewearn on 2010-09-23
> **SaintDanBert said:**
> I'm sorry if I did not understand your original problem well enough and so I wasted your time with responses off in the weeds.

No problem :).

> In the late 90's, I used linux to run industrial instruments on a LAN. Scripts and programs as processes -- all talking and waiting for each other -- was our bread and butter. We didn't have udev or similar. Without knowing more, it is hard to tell if udev is overkill or "just right." Either way, a udev-based solution would make wonderful reading.

Please keep posting your progress.  I'll help if I can.
~~~ 0;-DanIt turned out udev solution is quite simple.  I added an arbitrary named text file in "/etc/udev/rules.d/" with the following line:
```
KERNEL=="rfcomm?", RUN+="/usr/bin/bt-dun-stat.sh"
```So then, when "/dev/rfcomm?" is created or deleted, the script "/usr/bin/bt-dun-stat.sh" is executed.  The script then run a notify-send command.

The full details of what I am doing, well it will take quite a bit to write and I might add it to my blog.  But at the moment I'm too lazy. :)

Thanks for your assistance, I will mark this thread as solved.

---

