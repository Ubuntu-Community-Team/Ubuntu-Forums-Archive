---
title: "What's going on when shutting down..?"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by jabbarZA on 2012-08-28
How do you check what is going on during shutdown? One of my machines occasionally "hangs" at the purple ubuntu screen when shutting down. Is there a way to see what's going on or check a log file of sorts to see if there is a process that isn't terminating properly?

---

### Post by d4m1r on 2012-08-28
My first place to check would be /var/log/syslog.

---

### Post by Bashing-om on 2012-08-28
jabbarZA ;

  Hi !
     For your info, I have a way to enable the text termination messages and to scroll them ... I run 10.04 and I do not know if this method applies to other versions.(edit grub file and use scroll lock key to pause the messages)


[INDENT]regards <==BDQ
[/INDENT]

---

### Post by jabbarZA on 2012-08-29
Thanks d4m1r, will have a look, hope i can see what is going on there..

If no luck that route, Bashing-om, what command do you use? 

I am willing to try anything in the hopes of fixing the problem. It isn't something that happens everytime i shut down, but it has happened enough for me to take notice.

---

### Post by Bashing-om on 2012-08-29
Like I said I run 10,04 ,,, do not know if this will work on later versions.

all you have to do is edit /etc/default/grub after you make a backup copy ...on the boot line of the file delete
quiet, splash and $vt_handoff... leave other customizations on this line.
(I found if I used "text or "text=verbose" as  boot options my machine was unstable for undetermined reason).
  Dont forget to update grub:
```
sudo update-grub

```

  anywho, I boot up with bootlog messages and terminate with the shutdown messages. To pause the screen output hit the scroll lock button (some say the escape button works) //Only have a 3 second window to put this in effect.  Then I get the normal login splash greeter screen.

[INDENT]hope this helps <==BDQ
[/INDENT]

---

