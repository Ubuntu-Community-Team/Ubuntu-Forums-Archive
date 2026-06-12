---
title: "Terminal session hijacking?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by cosmocrazy on 2008-09-06
I was playing with a computer booted into Ubuntu and I was on an admin account without a password. One of my friends saw that I was in Ubuntu, not Windows and said "Ooooo! Ubuntu! Can I see??" He's a lot more knowledgeable about computers and UNIX than I am.

I let him use the keyboard and he proceeded to try something out. He opened a terminal window, and immediately proceeded to typing a few commands. I don't remember all of them though.

```
ifconfig eth0
sudo apt-get openssh
```

He then proceeded to start the SSH service. Then he went back to his laptop and I poked around Ubuntu some more, looking in the /etc and /var directories from the terminal among other things. He was excited to get back to his laptop. On his laptop he opned PuTTY and connected to my computer. Soon he got a nice little prompt: root@ubuntu~#

All the while I watched and didn't really care because the Ubuntu instance was pretty close to default anyway. But he did something weird. He sent messages to my terminal session. He then proceeded to shutdown the computer. So all the while I'm staring at a terminal window that would look like this: (I'm doing this all from memory so it's not going to be totally accurate)

```
ubuntu@ubuntu / $ ls
bin    lib    etc    var    home    media
I CONTROL YOUR COMPUTER! 
ubuntu@ubuntu / $ 
HAHAHAHA
The system is shuting down NOW. Please save all work.
```

Luckily it was a live CD...heh...but can anyone tell me what he did?

---

### Post by jordanmthomas on 2008-09-06
probably something like this:
1.  Type w and press enter in a terminal.  Now you can see where you're logged in at.
2.  As root (or the same user) type something like 
```
echo hello > /dev/pts/0
``` in any terminal and the appropriate terminal will get the message.  Change /dev/pts/0 as needed.  If you're logged in in one of the six ttys (ctrl - alt - F1-F6) then you'll be at /dev/tty1, etc

---

### Post by cwsnyder on 2008-09-06
You were signed on as root (SuperUser) without a password.

That allowed him during that short typing session to connect to his laptop, and since you were STILL root, he could take full control of your computer, even to shutting you out of the computer, shutting down your keyboard.  At that point, he simply shut you down.

That is the reason you never sign on as root, and run sudo only for commands you must, with a good password, especially if you are in a public area.

---

### Post by jordanmthomas on 2008-09-06
> **cwsnyder said:**
> You were signed on as root (SuperUser) without a password.

That allowed him during that short typing session to connect to his laptop, and since you were STILL root, he could take full control of your computer, even to shutting you out of the computer, shutting down your keyboard.  At that point, he simply shut you down.

That is the reason you never sign on as root, and run sudo only for commands you must, with a good password, especially if you are in a public area.

I think you may be slightly confused.  His friend didn't disable his keyboard, just sent messages to his terminal and then rebooted the system.  Obviously, since his friend was root he could have done whatever he wanted...anything from the simple messages he sent to formatting the hard drive.  

Even if it is a live session, you can still mess things up, so keep that in mind OP.

---

### Post by cosmocrazy on 2008-09-06
Well..I wasn't technically logged in as root, I was logged into the "Live session user" of the live CD which is still a passwordless admin but not root :) 

jordanmthomas, that's very interesting. i'll have to try that in the near future.

---

### Post by jordanmthomas on 2008-09-06
> **cosmocrazy said:**
> Well..I wasn't technically logged in as root, I was logged into the "Live session user" of the live CD which is still a passwordless admin but not root :) 

jordanmthomas, that's very interesting. i'll have to try that in the near future.

In case you're interested, you can do all kinds of cool things like that in Linux because everything is a file.  The terminal you were logged in to was just a file that he added text to.  Pretty cool if you ask me.

Your sound card is even just a file.  You can do something like ```
cat /usr/bin/firefox > /dev/dsp
``` and the firefox binary will written to your sound card and you can "listen" to it (if you are man enough)

---

