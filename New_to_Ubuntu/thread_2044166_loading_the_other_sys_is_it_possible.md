---
title: "loading the other sys is it possible"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by amrosama77 on 2012-08-18
Dear All,

I am sorry to post such a question ,but after I saw a lot of great features in ubuntu and also a lot of great tech. answering questions here ,I though why not ... I will ask and see may be some one develop something to do it,

so here is my question, now I have win7 and ubuntu 12 on my pc what I want is to open ubuntu and then by some how open the other system win7 (not talking about new win7 or vitual box solution) which on my pc too :))))))

so any ideas

---

### Post by cariboo on 2012-08-18
No you can't run 2 operating systems at the same time without resorting to something like virtual box.

You can access the files on you Windows partition while running Ubuntu, but you can't access your Ubuntu files when running Windows without installing an extra program

---

### Post by llamabr on 2012-08-18
Really, windows still cannot read ext3/4?

[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

---

### Post by amrosama77 on 2012-08-18
I dont have problem to use VB but to load MY win7 not which is on my hard disk not a fresh new copy of win7 (understand me?)

---

### Post by zombifier25 on 2012-08-18
> **amrosama77 said:**
> I dont have problem to use VB but to load MY win7 not which is on my hard disk not a fresh new copy of win7 (understand me?)

Sorry ut no. You should post in more details what you're trying to achieve. Though I'm pretty sure my response will not be different than cariboo's.

---

### Post by wojox on 2012-08-18
> **llamabr said:**
> Really, windows still cannot read ext3/4?

[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

Apparently not. 

[COLOR="Red"]Important Note:- Use these tools with your own risk if you don't use them properly it will remove your linux partition data[/COLOR]

---

### Post by llamabr on 2012-08-19
> **wojox said:**
> Apparently not. 

[COLOR="Red"][/COLOR]

Geez, what are they doing down there?

---

### Post by BlackoutWorm on 2012-08-19
> **llamabr said:**
> Geez, what are they doing down there?
There are 3rd party software you can install that will allow you to do this.

---

### Post by Mark Phelps on 2012-08-19
> **amrosama77 said:**
> I dont have problem to use VB but to load MY win7 not which is on my hard disk not a fresh new copy of win7 (understand me?)

YES, we understand you but ... you have to INSTALL Win7 to run it in VB. IF you don't have a way to install it, then you can't use it that way.

---

### Post by amrosama77 on 2012-08-19
Thank you,

---

### Post by spjackson on 2012-08-20
The problem you would have with trying to run your existing Windows installation within a Virtual Machine is that the virtual hardware presented by the virtual machine is not identical to the real hardware, and the installed system is configured for the real hardware. You would have similar difficulties if you took the hard drive out and put it in another computer.

In addition, Windows activation is tied to the hardware.

The VirtualBox website has a ["How to"]("https://www.virtualbox.org/wiki/Migrate_Windows"), but it is not straight forward and not without risk.

---

