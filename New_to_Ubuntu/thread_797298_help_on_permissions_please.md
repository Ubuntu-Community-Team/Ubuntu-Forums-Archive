---
title: "help on permissions please"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Davi0 on 2008-05-17
new to hardy heron. have installed virtual box and need to set write permissions for /dev/vboxdrv.

How do I go about this ?

I stuffed the 1st install of hardy by playing with permissions so don't want to do same again.

---

### Post by hyper_ch on 2008-05-17
just add your user to the vbox group and then logout and login again

---

### Post by shifty_powers on 2008-05-17
> **Davi0 said:**
> new to hardy heron. have installed virtual box and need to set write permissions for /dev/vboxdrv.

How do I go about this ?

I stuffed the 1st install of hardy by playing with permissions so don't want to do same again.

```
sudo adduser username vboxusers
```

in a terminal with your username in place of username of course ;)

---

### Post by Davi0 on 2008-05-17
How do I do this is what I am asking (steps involved/where do I go), I am a newbie.

---

### Post by hyper_ch on 2008-05-17
> **Davi0 said:**
> How do I do this is what I am asking (steps involved/where do I go), I am a newbie.

Where do you administer users and groups?

---

### Post by Xiong Chiamiov on 2008-05-17
[Here's]("http://www.psychocats.net/ubuntu/terminal") how to get to the terminal.  From there, type what shifty said.

---

### Post by Davi0 on 2008-05-17
Thanks shifty & xiong.

You guys answered my (however dumb) question. 

Hyper - you were not helpful, I am a beginner and you appeared to be mocking me.

---

### Post by hyper_ch on 2008-05-17
> **Davi0 said:**
> Hyper - you were not helpful, I am a beginner and you appeared to be mocking me.
Where did I mock you? Did you even try to find out where (except from the CLI) you can administrate users and groups?

---

### Post by Xiong Chiamiov on 2008-05-17
> **Davi0 said:**
> Thanks shifty & xiong.

You guys answered my (however dumb) question. 

Hyper - you were not helpful, I am a beginner and you appeared to be mocking me.
He most certainly was not mocking you.  The users here are very pleasant compared to what we normally find on the internet, and he's been very nice when I've seen him.  We run into people of all skill levels here (with almost all of them claiming to be beginners or newbies), so it's sometimes a little hard to tell just how specific we need to be.  Remember one of the good rules of Wikipedia: [AGF]("http://en.wikipedia.org/wiki/Wikipedia:Agf").

---

### Post by Davi0 on 2008-05-17
Thanks for replying chiong and if that is the case hyper my apologies

---

### Post by hyper_ch on 2008-05-17
> **Davi0 said:**
> Thanks for replying chiong and if that is the case hyper my apologies

Easy :) but I'm called hyper_ch ^^

Anyway, but not telling you where you administer users/groups in the system I wanted to you explore it a bit (as there is an easy administration tool to manipulate that stuff)...

---

### Post by Davi0 on 2008-05-17
hyper_ch it is then :).

 btw, I did not even realize permissions could be set in "users and groups" until now. Just had a look in there.

Guess I had better do some study in this area. I was just frightened to do the wrong thing and end up reinstalling yet again.
Thanks for your help.

---

### Post by hyper_ch on 2008-05-17
no, you don't set permissions in users and groups...

you have basically three permissions on a file/directory/device:
user / group / world

user is just one.... a user can be in multiple groups ... and world is everybody else

So, the vbox user group does have permissions to use that... HOWEVER you have not been part of that group yet. For that example you would be in the "world" part and you did not have permissions. So the solution was to add yourself to the vbox group and then you can use it ;)

Here's a bit more info:  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Davi0 on 2008-05-17
Thanks again. I will study this.

---

