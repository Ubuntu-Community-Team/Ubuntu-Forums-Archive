---
title: "Is there a ISO/DVD shrink program that actually works?"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by sillyboy on 2013-01-20
Let's see...ones that Do Not work -- k9copy, DVD Shrink(in WINE),etc. I've tried so many that I have lost track of the names. :(:(:confused:
All the ones I have used, have froze up after they start processing, the DVD or ISO.

Any suggestions??

Thank You

---

### Post by slickymaster on 2013-01-20
Have you already tried [AcidRip]("http://untrepid.com/acidrip/")?

---

### Post by mapes12 on 2013-01-20
What kind of DVD's are you trying to rip?

What are your hardware specs? ```
sudo lshw
```

---

### Post by squakie on 2013-01-20
Out of curiosity, were any of these disk DL so they were larger than 4.7gb?  I've had trouble with that myself.

As mentioned before me, AcidRip did work for me.  Also, the previous question on the type of DVD is important on 2 fronts:

- the aforementioned question on size

- if they are commercial DVD's, did you install the decryption routines?

---

### Post by sidzen on 2013-01-20
FYI:
[PHP]sudo apt-cache search dvd95[/PHP]
but if using wine, who knows?

---

### Post by speartip on 2013-01-20
dvdrip has always worked fine for me.

---

### Post by greg_ory on 2013-01-20
DVD Shrink has worked perfectly for me in wine and I find it still excellent.

-Greg

---

### Post by sillyboy on 2013-01-20
> **squakie said:**
> Out of curiosity, were any of these disk DL so they were larger than 4.7gb?  I've had trouble with that myself.

As mentioned before me, AcidRip did work for me.  Also, the previous question on the type of DVD is important on 2 fronts:

- the aforementioned question on size

- if they are commercial DVD's, did you install the decryption routines?

Hello

I can make an ISO, 9 or 5 with K3b.  It works great. Trying to shrink the 9 to a 5 is the problem.  These are DVD's I own, and want to back up.

I have installed all (I think) the restricted extras and other packages, and dependencies.  

Thanks

---

### Post by sillyboy on 2013-01-20
> **greg_ory said:**
> DVD Shrink has worked perfectly for me in wine and I find it still excellent.

-Greg
 
Hello,  DVD Shrink, in WINE, used to work for me too.  After an kernel (?) update it quit working.  It starts, then just freezes up.  I tryed purging it and reinstalling it to no avail.

Thanks

---

### Post by sillyboy on 2013-01-20
> **mapes12 said:**
> What kind of DVD's are you trying to rip?

What are your hardware specs? ```
sudo lshw
```

Do you want me to copy all that info and paste it in this window?

thanks

---

### Post by sillyboy on 2013-01-20
> **sidzen said:**
> FYI:
[PHP]sudo apt-cache search dvd95[/PHP]
but if using wine, who knows?

DVD95 freezes up also.  I have purged and reinstalled it a few times.

Thanks

---

### Post by sillyboy on 2013-01-20
> **slickymaster said:**
> Have you already tried [AcidRip]("http://untrepid.com/acidrip/")?

I am going to try Acidrip, as soon as I finish answering these responces.

Thanks

---

