---
title: "Ethernet Connection Problem"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by ZiXian on 2012-09-15
Hi, my Ubuntu 12.04LTS desktop PC was built from individual components. However, Ubuntu does not detect my Ethernet cable when it is plugged in while Windows 7 does. My Ethernet poert is the one that comes integrated with the motherboard. How do I go about getting wired internet connection?

---

### Post by critin on 2012-09-15
> **ZiXian said:**
> Hi, my Ubuntu 12.04LTS desktop PC was built from individual components. However, Ubuntu does not detect my Ethernet cable when it is plugged in while Windows 7 does. My Ethernet poert is the one that comes integrated with the motherboard. How do I go about getting wired internet connection?

Just a couple of basic troubleshooting questions that you've probably already checked.  Is your internet modem/router on and working before turning on the computer?    It should be.  Have you tried turning off the comp., the router, and the modem?  Waiting a minute or two and turning them back on in the opposite order, waiting for each box to complete their booting before turning on the next?

Are the appropriate lights blinking after all is on?  Is the light on the ethernet port on the machine lit up?  Does it blink?

You can't check for drivers without the internet, so I won't mention that.  :P    Perhaps someone can suggest the terminal fixes.

That's as far as my knowledge goes on this issue--sorry.

---

### Post by newb85 on 2012-09-16
I'm no expert on this kind of thing, but I'm pretty sure it will help the experts help you if you post the output of

```
$ sudo lshw | grep -i eth
```

(Enter it into the terminal without the $.  When it prompts for a password, it won't give any visual feedback as you enter it.)

---

### Post by varunendra on 2012-09-16
> **newb85 said:**
> it will help the experts help you if you post the output of
```
$ sudo lshw | grep -i eth
```
- not much.. :) A better (and correct) form of the same command would be:
```
sudo lshw -C network
```

However, there may be much more to know before we can start troubleshooting. Just download the "wireless_script" given below in my signature, and run it as indicated in the link- "how to use" against it. Post back the contents of the file "netinfo.txt" it creates (or attach the file itself).

---

### Post by newb85 on 2012-09-16
> **varunendra said:**
> - not much.. :) A better (and correct) form of the same command would be:
```
sudo lshw -C network
```

I'm not trying to argue, I'm trying to learn.  Why was my form incorrect?

---

### Post by NikTh on 2012-09-16
> **newb85 said:**
> I'm not trying to argue, I'm trying to learn.  Why was my form incorrect?

Hi , 

run both commands in terminal and you will figure  out , why 

```
sudo lshw -C network
``` is better. (more informational)

Thanks

---

### Post by varunendra on 2012-09-16
> **newb85 said:**
> I'm not trying to argue, I'm trying to learn.  Why was my form incorrect?
I like your curiosity and would only encourage it.

Apart from other details, it omits some important details like driver in use, link status, bus info and physical ID.

Although sudo is not always important, it is recommended because sometimes some important info is left hidden from lshw due to lack of root access. The -C switch stands for 'Class' in lshw listing (I don't remember since when it became equivalent to -c, but traditionally, capital 'C' was used for that purpose), and provides all the available info about (only) the given class.

Some other useful arguments for -C switch as 'class' are display, sound, multimedia, disk etc. For example, *lshw -C display*. Whereas *lshw -C disk* will only give results when used with sudo. (try only *lshw* or *sudo lshw* and you'll get the idea about 'class' argument).

Some of such stuff you can learn and understand from man pages (e.g. *man lshw*), while some with time and experience.

Hope it answers your curiosity.

---

### Post by newb85 on 2012-09-16
> **NikTh said:**
> Hi , 

run both commands in terminal and you will figure  out , why 

```
sudo lshw -C network
``` is better. (more informational)

Thanks

Yes, I ran my command before I posted it, and ran lshw with the category option before responding to that post.  Obviously, if you ask for all information on hardware in the network category rather than just limiting it to hardware that contains "eth" (as in ethernet, the issue in question), you're going to get more information.

That wasn't my question.  I asked why my command was *incorrect* (as implied by the statement that the alternative was correct).

---

### Post by newb85 on 2012-09-16
Never mind.  I see the problem.  Entries and lines are different in the lshw command.  The grep command stripped lines from the entry of interest because they didn't specifically contain "eth".

---

