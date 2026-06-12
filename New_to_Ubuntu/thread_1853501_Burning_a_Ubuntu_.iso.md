---
title: "Burning a Ubuntu .iso"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by Johnny3 on 2011-10-02
When ever I burn a Ubuntu .iso using Brasero I have to use a CD. If I burn it to a DVD it will give me errors. Tried different speeds. On my other PC windows 7 I can burn Ubuntu .iso to a DVD or CD and they are fine. Do you think maybe my Ubuntu 11.04 CD/DVD burner reader is going bad? This is the only problem I have with the DVD/CD it burns other things fine.

---

### Post by Rubykuby on 2011-10-02
Brasero isn't the best software tool for burning out there, if you ask me. I can't name an alternative as I haven't burnt CDs in ages, but it's definitely worth looking around for an alternative to see if it works.

---

### Post by sarwiz on 2011-10-02
get infrarecorder, it works great for me, and use the slowest speed

---

### Post by jmszr on 2011-10-02
Johnny3,

I suggest that you try k3b. I have found it to be the best burning app available. You can find it in the Ubuntu Software Center or in the terminal:  "sudo apt-get install k3b" (without the quotation marks).

Hope that helps.

---

### Post by VanR on 2011-10-02
Never had a bad burn with K3B. I suggest you get it from the software center and give it a try.

---

### Post by Sef on 2011-10-02
I like GnomeBaker that is available from the repositories.

---

### Post by Johnny3 on 2011-10-02
> **jmszr said:**
> Johnny3,

I suggest that you try k3b. I have found it to be the best burning app available. You can find it in the Ubuntu Software Center or in the terminal:  "sudo apt-get install k3b" (without the quotation marks).

Hope that helps.

Thanks k3b worked like a champ. I am a software center first, then Synaptic Package Manager old man most of the time. Use terminal just to set up firewall and maybe one game place. But then it is copy and paste. Used it more but they put in the Xsensors in software center and it works great.
Thanks and God Bless Johnny3 65++
Gainesville Fl

---

### Post by mibart on 2011-10-02
It always a good idea to remember a console-way of burning CDs and DVDs. It is as simple as write:
```

$ wodim myfile.iso

```
and hit Enter. Maybe not so candy-look as K3b, but reliable and available on almost all modern Linux environments.

---

