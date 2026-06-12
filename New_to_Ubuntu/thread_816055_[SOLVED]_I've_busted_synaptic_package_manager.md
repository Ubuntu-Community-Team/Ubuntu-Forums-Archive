---
title: "[SOLVED] I've busted synaptic package manager????"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Kalonosaur on 2008-06-02
I'm very new to Ubuntu and in an uneducated attempt to get dansguardian working I seam to have busted synaptic package manager!

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is followed by...

dpkg: requested operation requires superuser privilege

                .... in the terminal.

I was also playing with tinyproxy and firehol.

Any help would be greatly appreciated

---

### Post by rraj.be on 2008-06-02
just open terminal and type the following

```
sudo dpkg --configure -a 
```

this will ask for your pasword.

enter it

now your cache will be cleared and every thing will be ok,

---

### Post by rraj.be on 2008-06-02
System commands can be run only insupre user or root.

to get into root account just get into terminal and type

```
sudo -i
```

This will ask for Your user password.

Just enter it.

now your shell ie. terminal will be provided with root account.

you can use this sudo along with installation directly like

```
sudo apt-get install partimage
```

this will automatically ask for your password and starts installing the specified application

---

### Post by Kalonosaur on 2008-06-02
I've done what you suggested 
       
kalon@KAL:~$ sudo -i
root@KAL:~# sudo apt-get install partimage
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@KAL:~# sudo dpkg --configure -a
Setting up dansguardian (2.8.0.6-antivirus-6.4.4.1-2) ...
 * Starting DansGuardian dansguardian 

but I still get

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by ChameleonDave on 2008-06-02
Type this into a terminal:

```
sudo dpkg --configure -a
```

Edit: someone got in ahead of me.

---

### Post by Kalonosaur on 2008-06-02
These are my results,

kalon@KAL:~$ sudo dpkg --configure -a
Setting up dansguardian (2.8.0.6-antivirus-6.4.4.1-2) ...
 * Starting DansGuardian dansguardian  

Nothing further seams to happen from here. Is this to be expected?
I still get the same error as before on 'manager'.

---

### Post by ChameleonDave on 2008-06-02
> **Kalonosaur said:**
> These are my results,

kalon@KAL:~$ sudo dpkg --configure -a
Setting up dansguardian (2.8.0.6-antivirus-6.4.4.1-2) ...
 * Starting DansGuardian dansguardian  

Nothing further seams to happen from here. Is this to be expected?
I still get the same error as before on 'manager'.
Hmm.  Seems pretty screwed.  Maybe you should force dansguardian to uninstall, since it seems to be clogging the system.

```
sudo dpkg --force-all --purge dansguardian
```

---

### Post by Joeb454 on 2008-06-02
I've got to agree with ChameleonDave on this one - it does look like dansguardian isn't installing correctly. So you should try and remove it with the command above :)

If it does remove correctly - you should note that, in general you don't need AntiVirus, unless you're concerned about passing stuff on to Windows machines on your network of course :)

---

### Post by Kalonosaur on 2008-06-02
Champian. Thankyou, that solved it. now to reinstall...
My problem has been that I don't know run dansguardian or firehol so as to set them up. If you could point me towards a 'HOW TO' for beginners to get these going it would be very kind.

---

### Post by Kalonosaur on 2008-06-02
Thanks Joeb454. All I'm after is parental control for my eight year old. Any recommendations?

---

### Post by rraj.be on 2008-06-02
Yes...you dont need antivirus.....

but to solve this you can remove the specific package but be carefull while removing.

If you are doing any system oriented thing do it completlely and more carefully.
else that may cause you system to be unstable.

---

### Post by Kalonosaur on 2008-06-02
rraj.be  Unstable/unhealthy systems are what I'm trying to escape...

---

### Post by rraj.be on 2008-06-02
Dont be afraid.

Nothing will happen.

But my advice for any one who is experimenting with computers should back up their entire data.

But ubuntu is 1000 times stable than Window.

If something goes unstable only that set of environment will be affected and you can replace packages to reconstruct your system.

---

### Post by Joeb454 on 2008-06-02
I see you have solved your issue (according to the thread title).

May I ask how you managed to do it?

---

### Post by Kalonosaur on 2008-06-03
As recommended by ChameleonDave I uninstalled dansguardian.

sudo dpkg --force-all --purge dansguardian

After this synaptic manager worked again.

---

### Post by ChameleonDave on 2008-06-03
> **Kalonosaur said:**
> As recommended by ChameleonDave I uninstalled dansguardian.

sudo dpkg --force-all --purge dansguardian

After this synaptic manager worked again.
Click on the medal icon on my post then.  ;-)

By the way, "sudo dpkg --force-all --purge *package*" would normally be considered a heavy-handed way of doing things.  For normal uninstallation, just use "sudo apt-get remove *package*" or Synaptic.

---

### Post by Joeb454 on 2008-06-03
> **ChameleonDave said:**
> Click on the medal icon on my post then.  ;-)

Now there's no need to go asking for thanks ;) If the OP thinks it's worth it they'll give it :p

---

### Post by Kalonosaur on 2008-06-03
It's not that I'm not thankful. I just don't know how/what all these icons mean. 
Also, are their any parental control programs that don't require a course to install and use? This is my only negative with ubuntu so far but when you have young children and your computer skills are superficial it's a big one.
Thanks again and I'll look into that medal stuff.

---

### Post by Joeb454 on 2008-06-03
The medal is on the bottom right of every post (in most of the sub-forums here) and you click that to "thank" people :)

---

### Post by ChameleonDave on 2008-06-03
> **Kalonosaur said:**
> 
Also, are their any parental control programs that don't require a course to install and use? 
Yes, but that's a question for another thread.  Use "Search".

---

