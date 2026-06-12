---
title: "how can I increase my Ununtu partition?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-06-12
my Ubuntu hardy partition is very small( 7 gigs) and I want to increase it to 150 gigs  and there is nothing else but Ubuntu hardy on my 320gb hard drive  how can I do this?

---

### Post by gr4nf on 2008-06-12
Use GPartEd. Run:
```

sudo apt-get install gparted
sudo gparted

```

---

### Post by powerpleb on 2008-06-12
> **gr4nf said:**
> Use GPartEd. Run:
```

sudo apt-get install gparted
sudo gparted

```

But I don't think you can resize a partition when it's mounted.
You're better booting off a live CD and doing it.
I recommend [SystemRescueCD]("http://www.sysresccd.org/Main_Page") as it already has gparted installed and boots quickly.

---

### Post by Shadowmeph on 2008-06-12
> **gr4nf said:**
> Use GPartEd. Run:
```

sudo apt-get install gparted
sudo gparted

```

I already have that installed but I don't know how to increase the partition I am on ( the Ubuntu partition)

---

### Post by sam_delta on 2008-06-12
youll need to do it from the live-cd as the partitin has to be un-mounted, insert the ubuntu cd, and boot from it, once you are int the live envoroment, type ALT-F2 then type```
gksudo gparted
``` then select your ubuntu partition and click on resize, and resize it.

sam

---

### Post by Shadowmeph on 2008-06-12
> **sam_delta said:**
> youll need to do it from the live-cd as the partitin has to be un-mounted, insert the ubuntu cd, and boot from it, once you are int the live envoroment, type ALT-F2 then type```
gksudo gparted
``` then select your ubuntu partition and click on resize, and resize it.

sam

Ahh that makes allot of sense thanks

---

### Post by sam_delta on 2008-06-12
no problem, anything else, we'll be around
enjoy ubuntu :)
sam

---

