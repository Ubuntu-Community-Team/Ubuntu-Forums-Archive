---
title: "I've made a claim and now I have to prove it-Xp Vs Linux"
date: 2010-07-15
forum: Recurring Discussions
---

### Post by Ceiber Boy on 2010-07-15
I made the claim that I could get xp to run faster in virtual box on ubuntu than running it natively. 

I've disabled the unnecessary services and graphics in xp, but is their anything I could to virtual box or ubuntu to optimise the performance? Or any obey performance tweaks to xp that you could seggest!

The speed test will be on a CAD program that is very CPU intensive so anything I could do to keep ubuntu out of the way so that xp in virtual box can have as much power as possible.

If Linux wins I will gain respect in the sight of my work mates who are resisting a move to Linux.

---

### Post by bodhi.zazen on 2010-07-15
Welcome to recurring discussions ...

---

### Post by Ceiber Boy on 2010-07-15
> **bodhi.zazen said:**
> Welcome to recurring discussions ...

If this is a recurring discussion I would be happy to read them, just point me in the right direction

---

### Post by KiwiNZ on 2010-07-15
> **Ceiber Boy said:**
> If this is a recurring discussion I would be happy to read them, just point me in the right direction

From the COC... 

" Respect the forum staff. We provide a service in our free time to keep the forums running efficiently. We will occasionally ask for input, but in some cases we will not, please respect our decisions. Also, we do edit for content, if you have an issue with our moderation, please open a request in the forum resolution center."

---

### Post by Ceiber Boy on 2010-07-15
> **KiwiNZ said:**
> From the COC... 

" Respect the forum staff. We provide a service in our free time to keep the forums running efficiently. We will occasionally ask for input, but in some cases we will not, please respect our decisions. Also, we do edit for content, if you have an issue with our moderation, please open a request in the forum resolution center."

I just asked to be pointed to a thread that could be of assistance to me!

---

### Post by bodhi.zazen on 2010-07-15
You will find lots of threads here, in recurring discussions, on Windows vs Linux.

Just because you are using a VM or are out to "prove" something does not make your thread somehow unique.

---

### Post by Tibuda on 2010-07-15
> **Ceiber Boy said:**
> I've disabled the unnecessary services and graphics in xp, but is their anything I could to virtual box or ubuntu to optimise the performance? Or any obey performance tweaks to xp that you could seggest!
remember to do the same tweaks in the native xp machine.

---

### Post by aysiu on 2010-07-15
That's easy.

Run XP natively on a machine that has 128 MB of RAM.

Then run XP in VirtualBox with 2 GB of RAM allocated to its virtual machine in Ubuntu.

---

### Post by tgm4883 on 2010-07-15
I fail to see how this is going to work better in a virtual machine. Clearly you will have the overhead of Linux running on the machine as well.

---

### Post by Legendary_Bibo on 2010-07-15
Not to mention that you won't have certain things working right. A stripped down  XP on a virtual box versus an old and bloated XP might work. Although if your friend doesn't have a powerful computer then he wouldn't gain anything by using linux and then using xp in a Vbox.

---

### Post by linux18 on 2010-07-15
Use that pirated copy of xp that is so stripped down it only runs in virtualbox ( its called micro or performance edition -- anything along those lines ) i used it back in '06 to prove linux superiority. I believe at its core it was reactOS with windows server 2003 bolted on and countless tweaks. If you have a legal copy ( someone, somewhere has to ) you can perform the tweaks yourself. 

One thing you NEED to know: virtualization is not even 90% efficient so linux + windows(times 1.10) has to have less cpu usage than regular windows xp in order to win any cpu test. Lubuntu + really tweaked XP is probably not even close enough. What you need to do is cheat instead of a cpu test do a defrag or hard disk benchmark because virtualbox loads part of the virtual disk image into ram so throughput can be 400MB/s easy. Also *those *copies of windows are very small ( i think it was 66MB ) so boot time tests are a walk in the park ( under 10 seconds easily ).  any 3D or cpu test will result in failure, instead focus on maintenance ( virus scans, defrag, disk clean up, etc ) and HDD benchmarks those will convert your friends.

Last thought, pirating is bad and dual booting will probably be a better approach for win-win than emulation/virtualization.

good luck!

---

### Post by shazbut on 2010-07-15
Make sure you use AMD-V/VT in VBox or you will have no chance.
Also, you could cheat and put WinXP pre-SP1 on the VM, and WinXP SP4 on the real hardware.  The first release of XP worked ok on 233MHz machines with just 64MB when it was released, and ran quite well on ones upgraded to 128MB.  SP4 is quite a different beast to the original release.  Just make sure you don't connect that pre-SP1 machine to the network, or it might get 'sasser'ed in a few minutes ;)

---

### Post by Diluted on 2010-07-16
> **Ceiber Boy said:**
> I made the claim that I could get xp to run faster in virtual box on ubuntu than running it natively. 

I've disabled the unnecessary services and graphics in xp, but is their anything I could to virtual box or ubuntu to optimise the performance? Or any obey performance tweaks to xp that you could seggest!
Given the same physical hardware and XP installation, I don't think it's possible to make a virtual machine run faster than a physical installation. The best you could do is to make it run as fast as a physical installation, but not faster.

> **Ceiber Boy said:**
> If Linux wins I will gain respect in the sight of my work mates who are resisting a move to Linux.
You don't gain respect by proving "my X is faster than your X", you gain it by working well with your workmates.

---

### Post by Giant Speck on 2010-07-16
Learn to make claims that are easier to prove?

---

### Post by alexan on 2010-07-16
> **shazbut said:**
> Make sure you use AMD-V/VT in VBox or you will have no chance.
Also, you could cheat and put WinXP pre-SP1 on the VM, and WinXP SP4 on the real hardware.  The first release of XP worked ok on 233MHz machines with just 64MB when it was released, and ran quite well on ones upgraded to 128MB.  SP4 is quite a different beast to the original release.  Just make sure you don't connect that pre-SP1 machine to the network, or it might get 'sasser'ed in a few minutes ;)

There's no such things like SP4 for XP, the SP4 for XP will be released when microsoft will be sure Windows XP won't menace the selling of Seven updates.


Back IT: there's no fly if you before of anything don't equip your hardware with an Intel VT-x or AMD-V.
another thing you can try.. is puppy linux: if you manage to make vbox or vmware run into it.
of puppy linux there are some derivative which completely load in only 10MiB ram (turbopup).
Sometime ago, I read someone claim that run a wine game in puppylinux ran even more faster than in windows native (same machine): probably it was a bug of ... notemulation? But you never know, if you want to see some effect... give it a try!

---

### Post by alexan on 2010-07-16
> **Giant Speck said:**
> Learn to make claims that are easier to prove?

Columbus started this way :p



[COLOR="Silver"]he got jailed too[/COLOR]

---

