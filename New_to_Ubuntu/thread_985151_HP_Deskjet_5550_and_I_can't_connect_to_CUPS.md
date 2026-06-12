---
title: "HP Deskjet 5550 and I can't connect to CUPS"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by hmich176 on 2008-11-17
Hi, I have Ubuntu 8.04 with a Deskjet 5550 connected to my HP Pavilion laptop.  

Wasn't sure where to post this, so here it goes.  

I printed a document from Blackboard off Firefox 3.  It printed one page and then it called it quits because it was out of color ink.  First, how can I switch from color to black and white only?  

Secondly, when I went to the printer options under administration, it told me that there was a "problem connecting to the CUPS server."  Until just now, I had never heard of this.  

I need some help, big time, because I need to be able to have this printer working because it's for school.  Given there's only a couple of weeks left, this is a bad time for this to happen.

---

### Post by vgots on 2008-11-17
> **hmich176 said:**
> Hi, I have Ubuntu 8.04 with a Deskjet 5550 connected to my HP Pavilion laptop.  

Wasn't sure where to post this, so here it goes.  

I printed a document from Blackboard off Firefox 3.  It printed one page and then it called it quits because it was out of color ink.  First, how can I switch from color to black and white only?  

Secondly, when I went to the printer options under administration, it told me that there was a "problem connecting to the CUPS server."  Until just now, I had never heard of this.  

I need some help, big time, because I need to be able to have this printer working because it's for school.  Given there's only a couple of weeks left, this is a bad time for this to happen.

Well, you can install Windows and print from it after all ^^
For Linux there's an awesome software called "turbo print", get it [here]("http://www.turboprint.info/download.html")

---

### Post by phidia on 2008-11-17
Open the package manager (System > Admin > Synaptic) and search for hplip and hplip-gui. Install those packages and you should be able to set up your printer and also select features and access maintenance items.

Look at the [printer wiki]("https://help.ubuntu.com/community/Printers") if you continue to have problems

---

### Post by scorp123 on 2008-11-17
> **vgots said:**
>  Well, you can install Windows and print from it after all ^^  Hint: if OP had wanted to use Windows he would not have bothered to post the problem here. Thus your "advice" is not very helpful at all.

> **vgots said:**
>  For Linux there's an awesome software called "turbo print", get it [here]("http://www.turboprint.info/download.html") "turbo print" won't solve OP's problem. "hplip" is what he needs and that one can be installed for free via Ubuntu's package manager ;)

---

### Post by Peter09 on 2008-11-17
to get up the cups utility open a browser and go to

[http://localhost:631](http://localhost:631)

---

