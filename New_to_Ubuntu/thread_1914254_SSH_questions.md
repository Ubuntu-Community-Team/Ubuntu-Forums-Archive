---
title: "SSH questions"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2012-01-24
I set up an openssh server on my new install of xubuntu on a computer.  I have a question now though:

If I ssh into it, and start a program running (say rygel), is it possible to then close my connection and keep said program running?  If so, what do I need to do to do this properly?  I have almost no experience with ssh.

---

### Post by exodus_ on 2012-01-24
Absolutely!  There is a handy program called "screen" that you can "detatch" from, and leave whatever is running there to do it's thing.

You should be able to find screen using whatever method you use to install new software.

Its fairly easy to use, too.  You can also use it in the same kind of way you would use multiple virtual consoles on a real computer, too.

Let us know if you need more help :)

---

### Post by scared0o0rabbit on 2012-01-24
I'll look into it.

---

### Post by scared0o0rabbit on 2012-01-24
Is it possible to have a program run even if no one is logged in or has logged in yet?  If so, what do I need to do to make it happen?  The program will need access to my network.

---

### Post by haqking on 2012-01-24
> **scared0o0rabbit said:**
> Is it possible to have a program run even if no one is logged in or has logged in yet?  If so, what do I need to do to make it happen?  The program will need access to my network.

is this in relation to your other thread [http://ubuntuforums.org/showthread.php?t=1914254](http://ubuntuforums.org/showthread.php?t=1914254)

or a seperate question ?

cheers

---

### Post by scared0o0rabbit on 2012-01-24
It is in relation to my other question actually, but since it didn't have anything to do with ssh 9as far as I know) I thought it better to explore the question in another thread.

Ideally I'd like rygel to start when I turn the computer on without ever having to log in, but I'm not sure if that's possible, and if so how I'd go about setting it up.

---

### Post by cariboo on 2012-01-24
Please don't create multiple threads on the same question, I have merged your two threads/

---

### Post by lordievader on 2012-01-24
Not sure if this is the merged topic, if not I apologize.

Returning to the topic. If you add an & to your command, your program will be run in the background, you are then able to close/quit your ssh session and the program will remain running.

Another method of putting something in the background, for if you forgot to add the &, typing Ctrl + Z and then typing "bg" (without the quotes).

I hope that helps you.

---

### Post by scared0o0rabbit on 2012-01-24
> **cariboo907 said:**
> Please don't create multiple threads on the same question, I have merged your two threads/

No problem, I won't do it again.

[QUOTE=lordievader]Not sure if this is the merged topic, if not I apologize.

Returning to the topic. If you add an & to your command, your program will be run in the background, you are then able to close/quit your ssh session and the program will remain running.

Another method of putting something in the background, for if you forgot to add the &, typing Ctrl + Z and then typing "bg" (without the quotes).

I hope that helps you.[/QUOTE]

I'll give that a shot too.

---

### Post by scared0o0rabbit on 2012-01-26
Okay, so another question.  Suppose I start an X application, how do I go about logging out of my ssh session while leaving that running?

For instance, if I wanted to start qbittorrent but then be able to log out without closing that?

Once I have it started, if I try and logout I don't actually log out until I close the qbittorrent.

Is it possible to do what I want to do?

---

