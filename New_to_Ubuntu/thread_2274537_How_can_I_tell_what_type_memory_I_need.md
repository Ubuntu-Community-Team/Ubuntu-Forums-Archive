---
title: "How can I tell what type memory I need?"
date: 2015-04-20
forum: New to Ubuntu
---

### Post by Southron on 2015-04-20
I went to crucial.com to download their program but it was blocked by Dansguardian that came with ubuntu and I dont know how to change those settings to allow that program or if that program would have even worked on ubuntu.

I dont have my computer documentation so don't know my model version. Its a Lenovo

---

### Post by RobGoss on 2015-04-20
I'm confused to what your question is. If your asking about identifying the type of RAM you and not sure just take your Laptop to any computer electronic store I'm sure they won't mind helping you out with it.

---

### Post by deadflowr on 2015-04-20
You can try the command
```
sudo dmidecode | grep Product
```
should show the model version.
Then do a quick search for that model number.
Lenovo should have a manual for it, which should tell you the types of ram that are usable.

There are probably easier commands, but that one was off the top of my head.

---

### Post by mcduck on 2015-04-21
[Kingston's web site]("http://www.kingston.com/us/memory/search/options/") has a good search, no need to install anything, as long as you know your computer's model it'll tell you which memory you need for it. (And then you can just look for RAM modules with same specs from other manufacturers if you prefer).

---

### Post by gordintoronto on 2015-04-21
From the command line, run this command: sudo lshw -html > config.htm

That will create a file called config.htm in your home directory. If you double-click on it, it will open in your browser, displaying a nicely formatted blow-by-blow description of your computer. In the first page or two will be a detailed description of the memory. If you have an empty memory slot, you can just buy more memory like what you have.

---

### Post by sandyd on 2015-04-22
```

sudo lshw -C memory
```

should show you everything you need about your memory

---

### Post by newb85 on 2015-04-23
> **Southron said:**
> I went to crucial.com to download their program but it was blocked by Dansguardian that came with ubuntu and I dont know how to change those settings to allow that program or if that program would have even worked on ubuntu.

I dont have my computer documentation so don't know my model version. Its a Lenovo

The scanner program at crucial.com is a .exe.  Natively, .exe's don't work on Ubuntu.  Sometimes they can be made to work in WINE, but given that the purpose of this one is to scan your system, I doubt that would work, either.  Simply put, the program was written to run on Windows and interact with Windows.  In general, Windows utilities won't work on Ubuntu.  Best to look for Linux tools and methods.  (And sandyd has just told you what you need to know about gathering info on your memory.)

Secondly, to say that Dansguardian "came with ubuntu" isn't quite accurate.  It's not part of the default Ubuntu installation.  (The only exception I know is Ubuntu CE, which isn't an official variant.)  Moreover, it's in the universe repository, meaning that it is a community-maintained project, not supported by Canonical.  But that's not to say you can't have questions answered here.  It's still in the repos.  Just be aware that not everything in the repos is widely used, and for that matter, neither is everything installed by default on Ubuntu CE.

I realize I haven't said anything to your actual objective in this thread, but I thought those things should be pointed out.

---

### Post by grahammechanical on 2015-04-23
Thsi command will produce an HTML file called hardwareprofile in the home folder that will be opened in a web browser when clicked.

```
sudo lshw -html >hardwareprofile.html
```

It is easier to read than a printout in the terminal.

Regards.

---

### Post by Mopar1973Man on 2015-04-23
Best answer right here. That will provide the full listing of what RAM you have on your motherboard right now. Then all you have to do is see if there is open slots or just purchase larger memory.

---

