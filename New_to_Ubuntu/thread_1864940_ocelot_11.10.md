---
title: "ocelot 11.10"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by Karlof on 2011-10-19
hi forum
I have today downloaded ubuntu ocelot 11.10
The download worked okay and I have booted it twice okay

But now I get the message
1,waiting for network configuration
2,waiting up to 60 seconds for network configuration
3,Booting without full network configuration


Then nothing happens- help-

I have reloaded narwhal 11.04 on the same machine and that is good

Cheers karlof

---

### Post by peperomia on 2011-10-19
I had your symptoms when I upgraded. 

When I upgraded, my computer fell asleep part way through and so everything didn't get installed. I booted into recovery mode by holding down shift during start up. Then I ran 

```
dpkg --configure -a
```

This took a looong time.

And then I restarted

```
shutdown -r now
```

and I was able to boot properly into 11.10. 

Then I did an update from the update manager and it installed some more stuff and now everything is hunky dory.

I'm kind of a n00b and I don't really know _why_ that worked - there might be a better solution.

---

### Post by Karlof on 2011-10-20
Hi it did not work for me
All I got was event failed 

Thanks anyway anybody  got other ideas 
Cheers

Karlof

---

### Post by mörgæs on 2011-10-20
Did you have wired internet connection while installing 11.10?

---

### Post by Karlof on 2011-10-21
Hi
I have tried a few distros but for me ubuntu is the best

I have a wired connection to the net

As stated  I booted Ocelot 11.10  Twice after upgrading and it worked fine
On the third time I had the problems

Cheers Karlof

---

