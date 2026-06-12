---
title: "Accessing Ubuntu From Windows XP"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Musick Man on 2008-06-27
Hello,

I am going on a trip soon, and i might need to access my Ubuntu 8.04 computer remotely from a different Windows XP computer. 

My question: Is this possible, and if it is, can you tell me how to do it. 

Thanks In Advance, 

Musick Man

---

### Post by wrtpeeps on 2008-06-27
> **Musick Man said:**
> Hello,

I am going on a trip soon, and i might need to access my Ubuntu 8.04 computer remotely from a different Windows XP computer. 

My question: Is this possible, and if it is, can you tell me how to do it. 

Thanks In Advance, 

Musick Man

yep:

```
sudo aptitude install ssh
sudo /etc/init.d/ssh start
```

Then just login to your ip on port 22. You might need to forward port 22 in your router.

---

### Post by Musick Man on 2008-06-27
Let me get this straight. (I am new to ubuntu)

Do that code on ubuntu, and then go to my windows XP computer, and do i use, remote desktop connection that XP came with, or do i need a special program. 

(Guess Example: XP: Remote Desktop Connection> (Dialog Box> IP: 22)

---

### Post by Xerp on 2008-06-27
You need a special program - something like PuTTY, for example.

If you need remote access to the Ubuntu GUI, try NoMachine.

[http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by wrtpeeps on 2008-06-27
You will want putty.

You should also note that unless you want to start tunnelling X, which can be laggy, you will only see a command line when you login. No GUI.

---

### Post by Musick Man on 2008-06-27
Hey thank you, i will test it out now, on my home computers, and leave some feed back on if it works. 

I have never seen a faster reply on a forum. It was like i was talking to you on the phone

---

### Post by scorp123 on 2008-06-27
... and on your Windoze PC you'd need a SSH client, e.g. Putty (which is free).

Once you have established a SSH connection (which means: you get your Ubuntu's terminal prompt on your Windows machine) you can pretty much launch anything you want remotely, e.g. a VNC server session? Once you have VNC up you can continue to work with your Ubuntu's GUI and would not have to bother with shell commands (if shell commands bother you, that is ... I personally am quite happy with the shell as all it takes is the right command and such an open shell prompt can give you everything you want ...)

These postings explains a little more about "VNC over SSH" ... maybe you'd be interested?

[http://ubuntuforums.org/showthread.php?t=609920&](http://ubuntuforums.org/showthread.php?t=609920&)
[http://ubuntuforums.org/showpost.php?p=4228752&postcount=5](http://ubuntuforums.org/showpost.php?p=4228752&postcount=5)
[http://ubuntuforums.org/showpost.php?p=3810489&postcount=3](http://ubuntuforums.org/showpost.php?p=3810489&postcount=3)
[http://ubuntuforums.org/showthread.php?t=726252&](http://ubuntuforums.org/showthread.php?t=726252&)

---

