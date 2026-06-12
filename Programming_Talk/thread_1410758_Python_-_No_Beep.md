---
title: "Python - No Beep"
date: 2010-02-19
forum: Programming Talk
---

### Post by s.fox on 2010-02-19
Hello,

I have been trying to learn more python and have come across a problem getting a system beep.   

I did some searching and everything I have seen indicates that print '\a' will work.   Can someone please assist?  

Below is my simple little script.  It is a timer script which I am trying to get to beep when time up and also display a message.

[PHP]
#!/usr/bin/python
import time
import threading

msg = 'Input Time In Minutes: '
uin = raw_input(msg).strip()
intSecAsMin= int(uin) * 60

class Timer(threading.Thread):
    def __init__(self, seconds):
        self.runTime = seconds
        threading.Thread.__init__(self)
    def run(self):
        time.sleep(self.runTime)
        print '\a'
        print "Time Up!"

t = Timer(intSecAsMin)
t.start()
[/PHP]Any help would be great, thank you :D

**Edit:**

I have also tried chr(7) and that did not work either.  I can also confirm that the package beep is installed

```
Package beep-1.2.2-5.fc12.i686 already installed and latest version
```-Silver Fox

---

### Post by wmcbrine on 2010-02-19
The beep package is not relevant to what you're doing, although supposedly you could use it as an *alternative* to what you're doing. (I haven't used it, just read the description.)

Beeping is a function of the terminal. Often it's mapped to a visual "beep" (flash) instead of audible. Right now, using "echo -e '\a'" in Gnome Terminal as a test under Ubuntu 8.04, I'm not seeing or hearing anything, even though "Terminal Bell" is checked in the profile. So yeah.

Hmm... xterm does nothing, either. Heck, I don't know if I even have an old-style PC speaker device on this machine (Asus Eee PC 900A). Maybe they're just trying to beep something that's not there.

Edit: I just tested on my 9.10 system, and I get a barely-visible flash of the title bar.

---

### Post by s.fox on 2010-02-20
Hello,

Thank you for responding to my query. :)

> **wmcbrine said:**
> The beep package is not relevant to what you're doing, although supposedly you could use it as an *alternative* to what you're doing. (I haven't used it, just read the description.)

Thank you for informing me of this,  I wasn't totally sure.  I just wanted to rule it out :)

> **wmcbrine said:**
> Beeping is a function of the terminal. Often it's mapped to a visual "beep" (flash) instead of audible. Right now, using "echo -e '\a'" in Gnome Terminal as a test under Ubuntu 8.04, I'm not seeing or hearing anything, even though "Terminal Bell" is checked in the profile.

I too get that result.  

> **wmcbrine said:**
> Hmm... xterm does nothing, either. Heck, I don't know if I even have an old-style PC speaker device on this machine (Asus Eee PC 900A). Maybe they're just trying to beep something that's not there.

Thats an interesting point.  Do you mean that our machines may be lacking the hardware to beep in this manner?

Once again thank you for your input on what I am trying to achieve,

-Silver Fox

---

### Post by Bachstelze on 2010-02-20
Make sure the [font=monospace]pcspkr[/font] module is loaded. It is not loaded by default in Ubuntu, maybe Fedora doesn't load it either.

---

### Post by s.fox on 2010-02-20
Hello,

Thank you for replying to my thread.

> **Bachstelze said:**
> *EDIT: never mind, you're on Fedora..*

The code was initially written on Fedora and didn't work.  I have since tested it on Ubuntu 9.10 and #!Crunchbang Linux 9.04 and had the same result.   Instead of beeping all I get is an empty line in terminal. :(

> **Bachstelze said:**
> Make sure the [FONT=monospace]pcspkr[/FONT] module is loaded. It is not loaded by default in Ubuntu, maybe Fedora doesn't load it either.

That sounds like it could be the cause of the problem I am experiencing. I just did a search in synaptic for pcspkr and could not find it listed.  I am pretty green at python but I thought that was how you would install the module.  Am I incorrect?

Thanks again for your time,

-Silver Fox

**Edit**:  Fixed a small typo in the original code.  Somehow during copy and paste I missed off the closing ) on t.start

---

### Post by Bachstelze on 2010-02-20
> **Silver_fox_ said:**
> 
That sounds like it could be the cause of the problem I am experiencing. I just did a search in synaptic for pcspkr and could not find it listed.  I am pretty green at python but I thought that was how you would install the module.  Am I incorrect?

Sorry, I should've been more specific. :p [font=monospace]pcspkr[/font] is the *kernel* module which acts as a driver for the speaker-thingy inside PCs. It is blacklisted in Ubuntu by default:

[quote=/etc/modprobe.d/blacklist.conf]# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr
[/quote]

Just do a

```
sudo modprobe pcspkr
```

and try again. You might also want to try that in a virtual console instead of an xterm.

---

### Post by s.fox on 2010-02-20
> **Bachstelze said:**
> Sorry, I should've been more specific. :p [FONT=monospace]pcspkr[/FONT] is the *kernel* module which acts as a driver for the speaker-thingy inside PCs.

Oh,  I see :D.  Thank you for clearing that up.

```
sudo modprobe pcspkr
```

Tried that and ran in virtual console,  still no joy :(

Thank you for your help :)

-Silver Fox

---

### Post by Bodsda on 2010-02-21
> **Silver_fox_ said:**
> Oh,  I see :D.  Thank you for clearing that up.

```
sudo modprobe pcspkr
```Tried that and ran in virtual console,  still no joy :(

Thank you for your help :)

-Silver Fox

I too have tested this and it does not seem to work anymore. The pcspkr module is blacklisted by default in /etc/modprobe.d/blacklist.conf - commenting that line does not seem to resolve the issue though.

I'd use pygame to load a basic wav file or something.

Bodsda

---

### Post by s.fox on 2010-02-21
> **Bodsda said:**
> I'd use pygame to load a basic wav file or something.

I was thinking about doing that,  but would be nice to get the beep working :)

-Silver Fox

---

