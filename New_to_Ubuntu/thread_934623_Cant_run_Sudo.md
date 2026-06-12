---
title: "Cant run Sudo"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by tjkoch on 2008-09-30
Hey everyone, 

When I try to run a sudo command I get the error that I am not in the sudoers file. Anyone know what I have to edit to fix this problem? Also how do I edit files in the terminal window? I used to use pico in the old days but what is the cool text editor now?

Thanks in advance!

---

### Post by Zzl1xndd on 2008-09-30
Is this your primary account (meaning the first one you made) or a secondary?

---

### Post by jamesrl on 2008-09-30
The open-source editor similar to pico is nano.  Emacs/vim are more powerful editors, but if you liked pico nano is the way to go.

Again, if you aren't in the sudoers file, it seems you don't have permission to run sudo, and need the original account to grant you sudo priveleges.

---

### Post by karlr42 on 2008-09-30
You **have** to use vi to edit sudoers for some reason. The command is visudo. Someone else will tell you what to add to it, I don't know :)

Oh wait, you have to be su to run visudo.. that could be a problem..

---

### Post by tjkoch on 2008-09-30
I figured it out. Had to login as root and run visudo. Had no idea how to use it so I googled visudo and got some info how to edit with vi. Little by little I'm learning how to work this Linux thing. :>

---

### Post by karlr42 on 2008-09-30
So you can sudo now?
[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]

---

### Post by Nepherte on 2008-10-01
> **karlr42 said:**
> You **have** to use vi to edit sudoers for some reason. The command is visudo. Someone else will tell you what to add to it, I don't know :)

Oh wait, you have to be su to run visudo.. that could be a problem..You don't have to use vi at all, it's just a little trickier to do:
```
EDITOR=nano visudo
```
You can replace nano with whatever editor program you like.

---

