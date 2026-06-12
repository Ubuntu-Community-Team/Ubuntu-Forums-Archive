---
title: "Ubuntu Server...multiple terminals?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Me_Rock on 2008-05-08
Hey there,

For a while now, I have been hosting a TeamSpeak, Call of Duty 4, and network fileserver on a server with desktop Ubuntu. I recently got an entire new computer that I want to make in to my new server. I decided to install Ubuntu Server on it. It works great, I have all of my services running on it, but I would really like to know how to have multiple terminals and switch between them.

The Call of Duty 4 server client "hogs" the terminal while it runs. My new server has a dual-core processor, so I would like to take advantage of that by hosting another game server or two. Being able to use more than one terminal at a time would be very helpful.


Thanks,
Phil McMillen

---

### Post by sujoy on 2008-05-08
get screen, its a real good thing, you can emulate as many terminal sessions as you want in one terminal

EDIT: alt+ctrl+{F1 to F6} gives you six terminals, and then in each run screen to maximise the no of terminal sessions

---

### Post by hyper_ch on 2008-05-08
have a look at "screen":  [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by Me_Rock on 2008-05-08
Thanks a lot! This is exactly what I was looking for. Now to find the next problem!

---

### Post by hyper_ch on 2008-05-08
You don't find problems... they find you ;)

---

### Post by njparton on 2008-05-08
Why not install openssh and putty into it? You can open multiple connections from putty at the same time.

---

### Post by hyper_ch on 2008-05-08
it's a server... when you run the program in terminal there and close the ssh connection it will also terminate the program...

This won't happen with screen.

---

### Post by njparton on 2008-05-08
Not if you stick an "&" after the command (without the quotes).

---

### Post by hyper_ch on 2008-05-08
but how will you then get the process back to take influence while it's running or see screen output?

---

### Post by njparton on 2008-05-08
It's possible to pause it and then restart it but I can't remember the commands to do that as I'm in from of my windows box at work at the moment.

---

### Post by hyper_ch on 2008-05-08
well, use detachble "screen" sessions and you'll experience what it's capable of... ;)

---

### Post by sujoy on 2008-05-08
> **hyper_ch said:**
> well, use detachble "screen" sessions and you'll experience what it's capable of... ;)

+1

thats why i love it, i can logoff and still resume work right where i left off

---

