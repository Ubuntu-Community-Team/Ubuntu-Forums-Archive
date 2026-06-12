---
title: "dumb question"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by jeff Odom on 2008-09-25
on my earlier post of need help Somebody gave me this code to see if my windows is still in the system

sudo fdisk-lu when I type this in, it gives me the boot. Somebody else gave me one to put windows back in grub list, but the person put it in 3 
                                                                  different
                                                                  lines
Am I suppose to put these in at the "c" prompt?

---

### Post by lisati on 2008-09-25
Try the following (you can copy it from your browser to the terminal):
```

fdisk -l

```
Caution: it's a little "ell", not a number "1"

---

### Post by vikramaditya on 2008-09-25
there are no dumb questions, only ignorant answers. :)

---

### Post by paultag on 2008-09-25
> **jeff Odom said:**
> on my earlier post of need help Somebody gave me this code to see if my windows is still in the system

sudo fdisk-lu when I type this in, it gives me the boot. Somebody else gave me one to put windows back in grub list, but the person put it in 3 
                                                                  different
                                                                  lines
Am I suppose to put these in at the "c" prompt?

Also, for future knowledge -- 

its the Bash Shell, not C Prompt ( no Microsoft here :) )

You can view this through the GUI through gparted ( System --> Administration --> Synaptic ) search: gparted.

Best of luck!

---

### Post by lisati on 2008-09-25
> **vikramaditya said:**
> there are no dumb questions, only ignorant answers. :)

Are you trying to tell me something? (Smiles!)

aah yes, I see. I blinked and missed something in the question. On Ubuntu the equivalent of the "C:" prompt is the terminal (from the Applications->accessories->terminal menu), this is a common place to type in commands.

---

### Post by vikramaditya on 2008-09-26
> **lisati said:**
> Are you trying to tell me something? (Smiles!)
Good heavens, no!  I'm sure you're an absolute linux guru compared to me.  I'm just saying that no question asked in earnest is stupid, but many answers (mine, for instance :) ) are downright ignorant.

---

### Post by lisati on 2008-09-26
> **vikramaditya said:**
> Good heavens, no!  I'm sure you're an absolute linux guru compared to me.  I'm just saying that no question asked in earnest is stupid, but many answers (mine, for instance :) ) are downright ignorant.

I think you accidentally touched a nerve in me: when I came back to this thread I realised there was information I had missed in the original post.....

Keep on smiling, everyone!

---

### Post by lisati on 2008-09-26
> **jeff Odom said:**
> on my earlier post of need help Somebody gave me this code to see if my windows is still in the system

sudo fdisk-lu when I type this in, it gives me the boot. Somebody else gave me one to put windows back in grub list, but the person put it in 3 
                                                                  different
                                                                  lines
Am I suppose to put these in at the "c" prompt?

I've been a bit side-tracked to follow your original question: how are you getting on?

---

### Post by Sef on 2008-09-26
> sudo fdisk-lu

There should be a space between the k and the -.
```
sudo fdisk -lu
```

---

