---
title: "How Do I Uninstall Compiz &amp; Emerald ?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-25
I can't boot the computer after adding a 8600gts card so I'm guessing it might be Compiz and/or Emerald that is causing the problem. How do I uninstall COmpIz and Emerald? Thanks ...

---

### Post by Dutch70 on 2008-06-25
until someone with more knowledge than myself comes along, you can disable compiz by typing this in terminal...
```
metacity --replace
```

to re-enable...
```
compiz --replace
```

to uninstall emerald, just use synaptic.

Dutch

---

### Post by forestpixie on 2008-06-25
Compiz and emerald wouldn't be causing the problem as if it's not booting they are not running yet.

If you have added a card have you turned off the onboard video in bios or are you replacing an older card.

Have you tried to fix x from the recovery mode - in hardy there is a little menu to do it, previously you had to run a dpkg reconfigure command.

The command was 

```
dpkg-reconfigure -phigh xserver-xorg
```

But it doesn't do anything for video with hardy I believe.

You certainly need to tell the system that you have a new card.

---

### Post by Dutch70 on 2008-06-25
Thank you forestpixie, I just did my best to answer the direct question!

---

### Post by forestpixie on 2008-06-25
You carry on - it's how I learnt, I didn't know you're answer was there when I started mine :)

You're response would have worked to stop compiz if the pc had started, I don't think there is any need to be uninstalling either though.

I doubt if you saw the other thread asking the same question without the remove compiz/emerald bit.

---

### Post by Dutch70 on 2008-06-26
Ohh, this just aint right. forestpixie is so "not a guest",(info literally changed while I was making this post) unless you call 34 hundred thousand million post a "guest" :lolflag:
 hope the admins get this straightened out soon. kinda killed my testimonial thread too. just being patient. I feel confident that they will do everything they can to get it fixed....til then. :popcorn:

edit: oops, not this post...testimonial post!

samurai penguin, let us know if you have gotten everything taken care of, or just encountered more problems.

---

### Post by Elfy on 2008-06-26
No - I've been a guest since yesterday in my alter ego and if I can't be resurrected then so be it :D

Saumrai penguin has a couple of other threads on the go an dI think this one is kinda redundant at the moment

---

### Post by Dutch70 on 2008-06-26
Well forestpixie2, Welcome to the Ubuntu forums. :lolflag:
sarcasm included! (for anyone that doesn't know) 

 All I can do is scratch my head at this point, maybe "I" should check for bugs!

---

