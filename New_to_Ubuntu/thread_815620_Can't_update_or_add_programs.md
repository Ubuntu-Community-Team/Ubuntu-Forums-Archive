---
title: "Can't update or add programs"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by treeclimber on 2008-06-01
I tried to add some programs and then tried to update.  Nothing works!  I keep getting this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do I have to do to get it to work?  I figure I have to open the terminal, but I don't know what I'm suppose to do.  Can you help?

---

### Post by Xiong Chiamiov on 2008-06-01
It amazes me when people post this question (fairly regularly), when that is the most helpful error message I've ever seen!

Open a terminal window and do as it says:
```

sudo dpkg --configure -a

```

---

### Post by JoshuaRL on 2008-06-01
Yep, he's right.  If the system says to try something, go ahead and try it.  It's almost always right.  And try the following too:
```

sudo apt-get install -f

```
That should help fix any broken packages dpkg may miss, however few there may be.

Hope that helps and fixes your problem.  Welcome to Ubuntu!

---

### Post by SunnyRabbiera on 2008-06-01
> **Xiong Chiamiov said:**
> It amazes me when people post this question (fairly regularly), when that is the most helpful error message I've ever seen!

Open a terminal window and do as it says:
```

sudo dpkg --configure -a

```

well the error does take one of guard, especially if you are a newcommer to linux.
I was taken aback the first time I saw it, though my first encounter with it was after some time with linux so I knew what to do...
still it does take you aback the first time.

---

### Post by JoshuaRL on 2008-06-01
> **SunnyRabbiera said:**
> well the error does take one of guard, especially if you are a newcommer to linux.
I was taken aback the first time I saw it, though my first encounter with it was after some time with linux so I knew what to do...
still it does take you aback the first time.

Agreed.  And the same can be said for any error, especially if you're just learning a new OS.

---

### Post by Xiong Chiamiov on 2008-06-01
I suppose I've lost a lot of that feeling since I was really suited for Linux before having it.  A friend of mine used my computer (with bbLean for a shell and xplorer2 for a file manager) and commented, "Why the hell aren't you using Linux yet?", which began my exploration into Kubuntu.

Apologies if I seemed a bit rude.  In general, reading error messages is good, and even if you don't understand them, obscure errors can be quite helpful when pasting into Google.

---

### Post by g45model21 on 2008-06-01
when I try to install, it still will not install any updates.

---

### Post by treeclimber on 2008-06-01
Thanks, it worked that time.  I don't know what I did wrong the first time.  Maybe didn't enter something correctly, I don't know.  It's been one of those days!  Actually weeks since I still can't get Hardy to connect to the Internet on my computer.  I have posted a lot questions, but all I have got back is answers from people who tell me it just worked on theirs.  Well, it didn't on mine!  Anyhow, thanks!

---

### Post by JoshuaRL on 2008-06-01
What error do you show when you try now?

---

### Post by Joeb454 on 2008-06-01
> **Xiong Chiamiov said:**
> It amazes me when people post this question (fairly regularly), when that is the most helpful error message I've ever seen!

Open a terminal window and do as it says:
```

sudo dpkg --configure -a

```
Actually it's not all *that* helpful, because it doesn't actually tell you it needs to be run as Root (or with 'sudo')

> **treeclimber said:**
> Thanks, it worked that time.  I don't know what I did wrong the first time.  Maybe didn't enter something correctly, I don't know.  It's been one of those days!  Actually weeks since I still can't get Hardy to connect to the Internet on my computer.  I have posted a lot questions, but all I have got back is answers from people who tell me it just worked on theirs.  Well, it didn't on mine!  Anyhow, thanks!

I'm guessing you interrupted an install of some sort :)

---

### Post by Xiong Chiamiov on 2008-06-01
> **Joeb454 said:**
> Actually it's not all *that* helpful, because it doesn't actually tell you it needs to be run as Root (or with 'sudo')

Very true.  Many people get caught up on things until they learn that errors about permissions can usually be solved by adding sudo to the front of the command (or using sudo !!, which sudo-s the last command <-- really nifty!)

---

### Post by SunnyRabbiera on 2008-06-01
> **g45model21 said:**
> when I try to install, it still will not install any updates.

Did you try a restart?
sometimes that helps


> **treeclimber said:**
> Thanks, it worked that time.  I don't know what I did wrong the first time.  Maybe didn't enter something correctly, I don't know.  It's been one of those days!  Actually weeks since I still can't get Hardy to connect to the Internet on my computer.  I have posted a lot questions, but all I have got back is answers from people who tell me it just worked on theirs.  Well, it didn't on mine!  Anyhow, thanks!

well sometimes its win some or loose some, even on windows its like that.
I had to install a new wireless driver on my husbands computer once, the previous driver worked right away with windows XP, but the updated driver didnt work... it turned out that there was a bug in the updated driver so we just downgraded.
Same thing with applications, when I used windows I swore by spybot search and destroy and add aware, on my husbands computer I installed both applications but only addaware worked... spybot froze up and kept on crashing on his machine, despite it using the same processor and memory type I had on mine.
We have two toshiba laptops, both with the same ram, same processor, they are the same model too... on laptop 1 both spybot and addaware worked but on laptop 2 it didnt.
Both with XP, both up to the same specs...

---

### Post by Joeb454 on 2008-06-01
I've seen many threads which are "I ran **dpkg --configure -a** but got this error"

Also I'd advise against the use of **sudo -s** instead I prefer to use ```
sudo -i
```

If you want to find out, run **pwd** after running each (sudo -s and sudo -i)

---

