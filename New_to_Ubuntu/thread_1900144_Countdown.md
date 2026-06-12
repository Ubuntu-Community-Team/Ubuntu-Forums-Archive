---
title: "Countdown"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-12-25
I'm dual booting Lucid and Windows 7 in a Toshiba laptop. More often than not, when I turn the laptop on, I forget to switch from Lucid to W7, which means, after a few seconds, the computer automatically boots up in Lucid (which is still not working properly), and I end up having to restart it, to go to W7.
Is there a way for me to deactivate that boot up countdown, and have the computer wait for me to manually select the OS I want to run?

Thanks in advance. :)

---

### Post by benpack101 on 2011-12-25
To edit grub run /etc/default/grub as root. You can change the default OS as well as set the time infinitely long. I'm not sure how to just turn it off, but "100000000000000000000000000000" (seconds) should be enough.

Hope this helps!

---

### Post by hakermania on 2011-12-25
Yes, I agree, a large timeout should be enough, although I would nto recommend such a large countdown (because I don't know as what variable this value is being stored, some values cannot take so big values and results could be unexpected). A timeout of 5 hours (18000) would be more than enough.

---

### Post by benpack101 on 2011-12-25
Well yes of course, I was just being a bit sarcastic. Guess I should have pointed that out.

---

### Post by grahammechanical on 2011-12-25
Can you remember to just press any key? That will stop the count down.

Here is a link:

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Regards.

---

### Post by Inodoro Pereyra on 2011-12-25
Thank you all for the replies.
I guess I should've specified I don't have a clue on pretty much anything, when it comes to Linux in general. 

Can anybody explain how should I do this:

> **benpack101 said:**
> To edit grub run /etc/default/grub as root. 

pretty much like you were talking to a 5 year old?:confused:

Thanks again...

---

### Post by benpack101 on 2011-12-25
My apologies... (but you should beware of saying that on such a forum, linux users tend to hate newbies...but we all were one at somepoint, or still are, so I try to help when I can)

1. open the terminal (ctrl-t)

2. type "sudo gedit /etc/default/grub" : This runs gedit (your text editor) as a root user (administrator) and opens the file at such a location

3. type in your password when asked (it will not show you your password, hit enter when you are done)

4. A text document will now open up.

GRUB_DEFAULT = signifies default OS. The first listed in the GRUB menu (when you boot up) is '0'. The next one is '1', '2' etc.  

GRUB_TIMEOUT = is how long the menu will be showed. Set this to a couple of hours or long enough for you. As mentioned earlier, you probably don't want to set the time too high, I would think an hour would be sufficient.

When you are done, save and exit.

Upon restart you will see your changes.

Feel free to ask if you have any questions!

---

### Post by Inodoro Pereyra on 2011-12-25
Thank you benpack101, you're the man!:D
Gonna do it right now.

---

### Post by benpack101 on 2011-12-25
No problem, there is no greater joy than teaching/sharing knowledge!

Let me know if you need any other help! (or have more questions!)

---

### Post by Inodoro Pereyra on 2011-12-25
Just did it. Everything worked like a charm.:D

Just as a tip, in case another newbie has the same problem, once I edited the GRUB_TIMEOUT line and saved it (and closed gedit), I had to run "sudo update-grub" in the terminal, for the changes to take effect.

Thanks again. With any luck, soon enough I'll have the money to get a few books, and stop being completely ignorant on all this stuff...

---

### Post by jerome1232 on 2011-12-25
I just wanted to note if you set it to -1 you get an indefinite wait.

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR="Red"]GRUB_TIMEOUT=-1[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by benpack101 on 2011-12-26
Hmmm...interesting to note jerome1232. Thanks!

Inodoro Pereyra, I would say if you really want to start learning about "all of this stuff", experience is the best teacher. Just go ahead and run Ubuntu as often as you can, and use the internet for any questions you run across. You wish your computer ran a certain way, look it up!

---

### Post by Inodoro Pereyra on 2011-12-27
Thank you Jerome1232. I'll try that.

Benpack101: I already tried that. Been a member of this forum for the last 2 years, and I have to say that, even when most everybody has been really helpful (I never experienced that "hate for the newbie" you mentioned earlier), I'm not any closer to understand Ubuntu than I was when I joined. 
Either way, I enjoy reading, and I hope to get a job very soon. Once I do, books about Linux and C are one of my priorities.

---

### Post by benpack101 on 2011-12-27
Alright, good luck with your job hunt!

---

### Post by Inodoro Pereyra on 2011-12-29
Thank you. :D

---

