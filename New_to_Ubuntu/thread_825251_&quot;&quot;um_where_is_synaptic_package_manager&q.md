---
title: "&quot;&quot;um where is synaptic package manager?&quot;&quot;"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-10
how do I use the synaptic package manager to reinstall the package manager when the package manager is not there?  when I hit ctrl +f2 It opens but doesn't give me administrator priveleges.  Also and I don't know if this relates  but I just tried to open amarok and it's not to be found either even though I just had it open 5 minutes ago.

---

### Post by gr4nf on 2008-06-10
The package manager isnt there?
try:
```

sudo apt-get update

```
if this succeeds, you have the package manager.

---

### Post by adamogardner on 2008-06-10
no that doesn't work.   my terminal made updates though which was nice.  only 3-10.  now I also have an icon on my top panel for 12 updates but the last two days it was taking a seemingly long time and I never let it finish because I just had to go. 
 Whoa!  I just went to install those updates  now it's 39 of them.

---

### Post by wannadumpwindows on 2008-06-10
Sounds like it's there. Did you just happen to delete it from the menu? Can you launch it from a terminal? 

```
sudo synaptic
```

---

### Post by Joeb454 on 2008-06-10
I'm not sure I understand your problem :confused:

Can you explain what Synaptic is (or isn't) doing in a little more detail? Thanks :)

---

### Post by -grubby on 2008-06-10
When pressing Alt-F2 enter in ```
gksudo synaptic
```. It sounds like your menus got screwed up or something...but I haven't used GNOME for months so I wouldn't know how to fix it. Also, the updates are normal.

---

### Post by adamogardner on 2008-06-10
when I sudo synaptic it worked.   thanks for the tip But It is also in my menu under administration  when I click on it nothing comes up.  And the same is happening to amarok  and who knows what else?

---

### Post by Joeb454 on 2008-06-10
Check that the menu's are linking to the correct application.

I think you can remove and re-add the menu's to your panel too :) Not 100% sure how though (I've done it a while back, but it's 2am)

---

### Post by aysiu on 2008-06-10
Paste the command ```
gksudo synaptic
``` into the terminal. If you get an error message, post it back here.

---

### Post by markbuntu on 2008-06-10
Update manager uses synaptic and if it is running you cannot open synaptic

---

### Post by Joeb454 on 2008-06-10
> **markbuntu said:**
> Update manager uses synaptic and if it is running you cannot open synaptic

I think you can open it, it'll most likely just give you an error and close again though ;) That's 2 different things

(I'm probably just being picky and pedantic - if so, sorry :))

---

### Post by adamogardner on 2008-06-10
I gksudo synaptic exactly as described ut all the cursor did was go to the next line with no prompt.

---

### Post by Joeb454 on 2008-06-10
> **adamogardner said:**
> I gksudo synaptic exactly as described ut all the cursor did was go to the next line with no prompt.

It should bring up a graphical password prompt. Try running ```
sudo -k
``` first, then running ```
gksudo synaptic
``` as Aysiu suggested :)

Does the prompt appear then?

---

### Post by mdsmedia on 2008-06-10
> **Joeb454 said:**
> I think you can open it, it'll most likely just give you an error and close again though ;) That's 2 different things

(I'm probably just being picky and pedantic - if so, sorry :))Not pedantic, I don't think...I was thinking the same thing, as they potentially mean 2 different problems/situations.

---

### Post by adamogardner on 2008-06-10
I did "sudo -k"    is it supposed to say "unable to resolve host CRONUS" ?  because thats what it keeps say everytime I sudo anything.  ThiS IS MY ComputeR ToO.  So I do have admin priveleges.

---

### Post by Joeb454 on 2008-06-10
Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=723361") will provide a solution?

---

### Post by adamogardner on 2008-06-10
I don't get it.  but I noticed some similarities like downloading these updates is not happening  it's just sitting there and the updates are increasing in number over time.  synaptic doesnt open from the menu but does from the terminal.  reading this aformentioned thread is like reading a conversation in another language.  I'm reading though  but it's confusing.

---

### Post by adamogardner on 2008-06-10
ok  no wonder  I was reading from back to front.  makes a lot more sense the other way.  here's what my terminal puts out after:

adamogardner@CRONUS:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	CRONOS

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

what should I do with this?

---

