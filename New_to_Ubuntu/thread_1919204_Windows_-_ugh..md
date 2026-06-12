---
title: "Windows - ugh."
date: 2012-02-02
forum: New to Ubuntu
---

### Post by Glkanter on 2012-02-02
My system has Ubuntu 11.10 on it. Nothing else.

But twice this week it would have been convenient to have Windows. I've made it almost a full year without Windows.

I have a legit copy of Vista. 

[LIST]
[*]Should I load it?
[*]Is there an easy way?
[*]Is there a better solution?
[/LIST]
Thanks!


Garry

---

### Post by snowpine on 2012-02-02
Not sure we can answer your question unless you expand upon this statement:

> **Glkanter said:**
> But twice this week it would have been convenient to have Windows.

There are millions of people in the world who don't use Windows, ever (Linux users, Mac users, people without computers, etc.) and yet life goes on. :)

---

### Post by Glkanter on 2012-02-02
Well, I guess only *I* can answer the first question.

What about the other two questions?

---

### Post by LinuXofArabiA on 2012-02-02
Come on man, you cant be like that. Now I reallly want to know the two instances you *thought  *you had to use Windows for. Either way, have you tried virtualization? There is an excellent software called VirtualBox by Oracle (available in the the software center) that would allow you to run windows or any other operating system seamlessly from within Ubuntu, without actually having to install the OS on your partition (or however the heck this works). I use it to load XP to use iTunes, since Apple hates open source.

Hope this helps.

---

### Post by arochester on 2012-02-02
VirtualBox +1

See e.g. [http://www.makeuseof.com/tag/installing-windows-7-on-a-virtual-machine/](http://www.makeuseof.com/tag/installing-windows-7-on-a-virtual-machine/)

---

### Post by snowpine on 2012-02-02
> **Glkanter said:**
> Well, I guess only *I* can answer the first question.

What about the other two questions?

They are unanswerable unless you care to answer the first question. :)

---

### Post by Glkanter on 2012-02-02
Can't I tell my story *my* way?

OK.

First was a piece of client contact software called Top Producer. It's typically an online thing, but to import a .csv file requires a separate program download, and it only runs on Windows.

Then, the same software wouldn't let me modify an e-mail template due to: ```
'Sciter: Browser or platform is not supported"       
```Then, I tried to participate in an unrelated webinar. Had to use my tablet. Which had it's *own* issues.

So, the Earth is still spinning, but I'm wondering what, if anything, I ought to do.

You guys are the best, even if you are ballbusters. LOLZ

Garry

---

### Post by Glkanter on 2012-02-02
Downloaded Virtualbox from the Ubuntu Software Center.

I got the disk created. Then 'started', and get this:

```
Failed to open a session for the virtual machine Vista.
AMD-V is disabled in the BIOS. (VERR_SVM_DISABLED).
Unknown error creating VM (VERR_SVM_DISABLED).
Details:
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}
```Please advise.

Thanks,

Garry

---

### Post by snowpine on 2012-02-02
If Windows is necessary to communicate with your coworkers and be productive in your job, then there is no shame in using it. :)

---

### Post by Lars Noodén on 2012-02-02
When you get a VM running with the old OS, be sure to take a snapshot.  A major advantage of VMs is that you can roll back to a known good [snapshot](http://www.virtualbox.org/manual/ch01.html#snapshots).  That's especially important with systems that can get messy.

---

### Post by linuxsyst on 2012-02-02
ahmm you could google any other program or try to install win7 or go dual boot.
ohh and ill link any other program

---

### Post by linuxsyst on 2012-02-02
ahmm you could google any other program or try to install win7 or go dual boot.
ohh and ill link any other program
a and if you could take screen please

---

### Post by QIII on 2012-02-02
OP:

The error you got indicates that you have not enabled the use of virtual machines in your BIOS.  Reboot, enter your BIOS and find a setting somewhere about allowing virtual machines.  I can't be more helpful than that without knowing your BIOS, but your error is a BIOS setting.  I've had to do that with a number of motherboards.

Notice AMD-V.  You need to activate that on your AMD chipset based mobo.

---

### Post by Ms. Daisy on 2012-02-02
My two cents: if you will need to use Windows in a professional capacity any more than once in a while, I would recommend a dual boot (if you've got a decent sized hard drive).  Virtual machines are great but they run a bit slower than a host installation.  There's a wiki guide on how to dual boot Windows after Ubuntu was installed first (I'm sure you can find it if you google it, I don't have the link at the moment).
 
Also, I'm finding that virtualization is deceptively simple. I recommend you read some threads in the [virtualization forum ]("http://ubuntuforums.org/forumdisplay.php?f=308")before you commit to that route. Things like USB ports & sharing folders seem to be easily and widely misconfigured.

---

### Post by Glkanter on 2012-02-02
I have a huge hd and tons of RAM, so my decision can be based solely on what is 'best' for me.

I don't much want a dual boot system, as I probably 'need' Windows less than 1% of my time using PCs, etc.

I don't think performance will be an issue using VirtualBox.

I hope to get VirtualBox working.

As always, thanks!

Garry

---

