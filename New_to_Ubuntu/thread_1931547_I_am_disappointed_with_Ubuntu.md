---
title: "I am disappointed with Ubuntu"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by ahiung on 2012-02-25
This is the 5th time I installed Ubuntu in my same laptops. But it is also the 5th time I uninstalled it.
I forgot what the reason I uninstalled it before, but I had the similar problem which "things goes wrong if I installed something" problem.

This time, I got "new" disease on my ubuntu. It is new for me, but not the web. When I googled it, it shows bunch of thread talking about it.
the problem name is: rfkill is your boss.
"HE" is the boss, when "he" say yes it is "yes".

I tried many "MANY" different methods from the web. The pattern I found always the same..

some guy posted this problem
guy: help me please, the boss is killing my internet
helper: please post your blablabla (something related to network)
guy: <posted their system information>
helper: try this, try that, try whatever
guy: I tried, no working (duh)
unknown guy appeared from nowhere: yay, I solved it.
guy: I still Hardcore/Softcore blocked

and somehow the thread marked SOLVED which I would say FFFUUUU in my mind.

I sit in front of my laptop try to type:
rfkill unblock wifi
rfkill unblock 0
rfkill unblock all
with some restart after deleting /dev/rfkill file
FOR AN HOUR
the result always stay the same when I type rfkill list.

MANY! helpers say something terrible to "guy"'s device, but it is not the problem...the problem is from UBUNTU!

[COLOR="Red"]*please confirm this*[/COLOR]
I suspect that these kind of problem like machine fail, some driver not working like sound, vid, networking, etc. caused by installing "SOMETHING" from the out-source like the subversion of "SOMETHING" and which is not available from Ubuntu Software Center.
Especially the "sudo install lib1 lib2 libxxx libyyy" part.
[COLOR="Red"]*Please confirm this*[/COLOR]

last time was very HEALTHY really..I installed PCSXR SVN run with 60 fps..I was very happy. I must say my machine work its best condition, run smoothly along OpenBox mode.

AFTER I SHUTDOWN, and went to bed.
THE NEXT morning is the end of the world.
My only option is to put windows XP CD into the tray right now.

---

### Post by Iowan on 2012-02-25
Are you posting here to find a solution - or should this thread be moved to a commentary section?

---

### Post by ahiung on 2012-02-25
> **Iowan said:**
> Are you posting here to find a solution - or should this thread be moved to a commentary section?
Either. But, If you know "why" I would like to know what is the major problem which cause my problem. It is not only RFKILL problem you know, previously I got some audio problem from my previous installation, too. I am very confused right now.

---

### Post by alegomaster on 2012-02-25
The audio issues you have probably came from the drivers. Linux does not have the best audio drivers so there are sometimes issues with the sound.

I don't get what you are talking about with rfkill though.

---

### Post by HeroOfCanton on 2012-02-25
I don't mean this to be rude, but could you post the actual problem instead of a story? There are a lot of very helpful people on this forum, but in order to assist we need specifics as to what is wrong.

I can say without a doubt ubuntu is not the problem because many of us solve our individual configuration problems and love the power of the OS. I personally actually like a challenge, it's the hacker mentality. Even my windows system is customized to the point MS will not support it! Extra work is often the price you pay for more power and control though.

"Anything in life worth having is worth working for."
- Andrew Carnegie

---

### Post by ahiung on 2012-02-25
> **alegomaster said:**
> The audio issues you have probably came from the drivers. Linux does not have the best audio drivers so there are sometimes issues with the sound.

I don't get what you are talking about with rfkill though.
something like this....
[http://ubuntuforums.org/showthread.php?t=1610829](http://ubuntuforums.org/showthread.php?t=1610829)

---

### Post by wildmanne39 on 2012-02-25
Hi, I should be able to help with your wireless issue but we need to stick to just that topic in this thread so it does not get confusing.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Old_Grey_Wolf on 2012-02-25
> **ahiung said:**
> .....

After reviewing your other posts, I will refer you to the sticky on the first page of the  Absolute Beginner Talk forum "[Sticky: Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475")". In particular, pay attention to General Guidelines 4, 7, 8, 9, 10, and 11 in that sticky.

---

### Post by ahiung on 2012-02-27
> **Old_Gray_Wolf said:**
> After reviewing your other posts, I will refer you to the sticky on the first page of the  Absolute Beginner Talk forum "[Sticky: Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475")". In particular, pay attention to General Guidelines 4, 7, 8, 9, 10, and 11 in that sticky.

Sorry bout that, my passion was just run out. So, I also in need for my only working laptop, it just ruined my day.

---

### Post by ahiung on 2012-02-27
> **wildmanne39 said:**
> Hi, I should be able to help with your wireless issue but we need to stick to just that topic in this thread so it does not get confusing.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you


sorry about that dude, I appreciate your help but... I cleaned all my partition until sparking and installed windows XP in it, so I can't go with terminal anymore... I will mark this thread as somehow unsolved, hopefully this doesn't happen to other user.

---

### Post by wildmanne39 on 2012-02-27
Hi, okay I am sorry to see you go.

---

### Post by ahiung on 2012-02-27
Dear visitor,

This post is marked as SOLVED, but it actually doesn't. If you have similar problem as mine please post this code in your new thread to let other help you:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```

as you can see, I am not using ubuntu right now because I need to do something important.

Thank you

---

### Post by Geemonster69 on 2012-02-27
> **alegomaster said:**
> The audio issues you have probably came from the drivers. Linux does not have the best audio drivers so there are sometimes issues with the sound.

I don't get what you are talking about with rfkill though.

I agree with you there i found VLC had a very scratchy sound,but it's intermittent.
Saying that though VLC is better on Linux than Windows.

---

