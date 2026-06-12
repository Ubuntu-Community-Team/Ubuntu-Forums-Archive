---
title: "IBM Thinkpad Issues"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by algorithm786 on 2008-09-04
Hi,
I am having a IBM Thinkpad R60 . I have Ubuntu Ultimate Edition installed on it. I compiled new kernel linux-2.6.26.3, which I downloaded from [http://www.kernel.org](http://www.kernel.org).

Now when I boot into the kernel normally it does not show me the display. It just plays the login sound. and when I type my login name and password. It logs in but still no display.

But when I log in through recovery kernel it runs absolutely fine with display. Can you tell me the cause of this problem and How can I fix it.

And If Have posted my query in the wrong place ... please guide me to the right place.

---

### Post by alpage2 on 2008-09-04
By no display, do you mean that you have a completely blank unresponsive screen?

Or is it a text screen with a command prompt? In which case startx should do it, or if you need root privileges (quite likely), type: sudo startx.

Hope that does the trick.

Alan

---

### Post by ronnieredd on 2008-09-04
After it finishes booting (or about the time it would let you log in), try ctrl-alt-F1
Do you get a screen?

You may also try ctrl-F1 along the boot up - after bios post That shows messages about what's happening as it boots.

Lastly you may want to put the LiveCD in and check the grub menu.list

---

### Post by algorithm786 on 2008-09-05
It was a blank screen but you can not say it an unresponsive screen. I could type my login name and password ... ofcourse which could not see. And when I pressed ENTER I could listen that the system is logging in. Only thing was that I was not able to see anything ... May be some XWindow issue !.
   
By trial and error... I don't know how did it got fixed. But what I did is ... deleted the source code which had compiled and it started working.
Location of the source code was **/home/user_name/src**
And it was working fine recovery mode but not in normal mode..

Any explanation for this kind of problem will be appreciated ... Thanks

---

