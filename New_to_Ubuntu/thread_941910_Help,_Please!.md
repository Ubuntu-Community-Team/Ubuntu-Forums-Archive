---
title: "Help, Please!"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Wanderone on 2008-10-08
Have had Happy Heron 8.0-Ubuntu 8.04.1 kernel 2.6.24-19-generic for several months and use it on and off, though not a whole lot.
Installed it off a dvd after downloading it.  Today, I updated everything and restarted.  Now, after logging in, I go to a pure white screen, nothing else.  Restarted half a dozen times with the same results.  Installed as a dual boot with Vista and had no trouble at all until today.
Any suggestions, should I just try to reinstall??

---

### Post by jerome1232 on 2008-10-08
Can you get to a tty? (ctrl+alt+f1 - f6) What video card do you have and what driver are you using? How did you install that driver?

---

### Post by Wanderone on 2008-10-08
> **jerome1232 said:**
> Can you get to a tty? (ctrl+f1 - f6) What video card do you have and what driver are you using? How did you install that driver?

To be honest, I'm not sure.  I followed instructions in adding/installing software.  AS I said, I've had no problems til now.

---

### Post by Christmas on 2008-10-08
try alt+ctrl+f1 to login in command-line mode, then you'll probably have to edit your /etc/X11/xorg.conf file. what hardware are you using?

---

### Post by Wanderone on 2008-10-09
> **Christmas said:**
> try alt+ctrl+f1 to login in command-line mode, then you'll probably have to edit your /etc/X11/xorg.conf file. what hardware are you using?

What hardware are you referring to?  I have no trouble logging in and password.  It's after the password that the screen goes blank and then to pure white.

---

### Post by hyper_ch on 2008-10-09
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by Nxion on 2008-10-09
> **Wanderone said:**
> What hardware are you referring to?  I have no trouble logging in and password.  It's after the password that the screen goes blank and then to pure white.

By hardware they mean what type of video card are you using. It sounds like the xorg.conf file has something it it that is messing it up. I know you mentioned that you are able to log in but we need to find out the video card, the driver that you are using. This will give us a base line to start to troubleshoot the issue.

I too has had this issue before and it turned out to be a bad video card. Now I am not saying that you have one, it might just turn out to be a misconfiguration somewhere. I was just letting you know the possibilities.

With that being said, how old is this machine you have Ubuntu on? What brand is it? Dell? HP? or a clone?

If you don't know what video card you have thats fine, can you get to a command line by doing what jerome1232 stated further up in this thread? 

Then we can find out what card you have by invoking this command once you have reached a command prompt.

```
lspci
```

Please post the output from the above command.

Regards,
Nx

---

### Post by REDace0 on 2008-10-09
If you're able to get to a well-rendered login screen, but it goes to whitescreen after you log in, it's probably something particular to your session. I've had this happen before with compiz. Under Fedora I had to search 'til I found someone who knew the right set of options to have compiz start with in this case.

---

