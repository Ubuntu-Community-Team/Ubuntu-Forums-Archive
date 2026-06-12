---
title: "question about VMware..."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-08-26
So i read the community doc about VMware, but still had a few questions.

1) So is it free or not. i got conflicting messages.

2)I currently am dual booting xp and ubuntu, and saw that there was the workstation version that could let u treat ur windows partition as the VM Is this like how virtualization works with bootcamp on a MAC? i saw a friend who was running bootcamp on his MAC virtualize his Vista partition from with OSX, and then restared and botted from windows, and everything he did from OSX saved over. Is this the version you have to pay for, and if so how do i do it bc this seems to be the way i want to go.

3) is there any other way to run windows prgrams besides wine and VMware? i was fine using wine for small things like winamp, and feeding frenzy, and peggel, but they were stand alone .exe's. I tried to install a program i need for class: ArcGIS, from cd, and it said it could not locate some file from the D:/ drive. For obvious reasons, it didnt work.

4)If i run the VMware, would it recognize all my drives like my cdrom drive. also i have the ext2 driver on my xp partition. so if i ran the xp VM from with ubnuntu, and accessed my ubuntu drive to make changes, would a black hole start to form from my hard drive?

Thanks for clearing things up for me!

-mike c.

---

### Post by aloshbennett on 2008-08-27
Let me see if I can answer few of your questions.

1. VMWare Server is free. VMWare Workstation is not.

2. Using VMWare server, you can make a virtual machine to boot from the XP installation you have on your harddrive. Its cool. Its tricky, and if you screw up you screw up the XP installation. I couldnt get it to boot. Would get the BSOD when I boot into the XP from virtual machine, but one of my friends had managed to get it working.

3. There are other applications like Wine, but none of them would work with every application you throw its way. You need VMWare.

---

### Post by patrickballeux on 2008-08-27
As for virtualisation, there is also VirtualBox that is available in the repositories and is working quite well.

VMWare Server has more options, but VirtualBox is easier to deploy since it is already available.

I think that both are good for a local virtual machine.  If you want more power, then VMWare is the winner...

---

### Post by crispy_420 on 2008-08-27
VMWare does offer a tool to convert your "real" machine into a virtual machine. It is called VMWare Converter and it is free, just have to register.

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

---

### Post by aloshbennett on 2008-08-27
What VMWare converter does is, it creates a huge image out of your c:\windows and other relevant drives you choose. It doesnt let your vmware boot of your existing windows installation.

---

### Post by crispy_420 on 2008-08-27
But it will allow him/her to use the windows apps they need in a familar enviroment.

---

### Post by deathvalleyjoker on 2008-08-27
But will everything i do in the VM version of my partition carry over, and second, my xp partition is way bigger than my ubuntu partition, because i use the xp for gamming. will this present a problem, since i cant create a huge image?

---

### Post by crispy_420 on 2008-08-27
Sorry my idea will not carry over for you. By that you mean persistant changes in the virtual machine will equate to changes to the "real" machine? Also the disc space may be large as well. I just don't know of a solution for your needs.

---

### Post by lazyart on 2008-08-27
VMWare is not going to help you if you're a heavy gamer-- it's doesn't support hardware 3D.  If gaming is your thing, dual boot so you can have a pure Windows experience.

---

### Post by deathvalleyjoker on 2008-08-28
> **lazyart said:**
> VMWare is not going to help you if you're a heavy gamer-- it's doesn't support hardware 3D.  If gaming is your thing, dual boot so you can have a pure Windows experience.

No i relize i wouldn't be able to game. I really just wanted a VM and saw with macs that ur VM links with an actual partition, and thought that would be cooler. I guess ill just have a normal stand-alone VM, as i dont wanna risk hoseing my windows partition. 

One last question: if i am running a VM, it will recognize stuff in my cd/dvd drive right? For installing purposes mainly. Thanks.

---

### Post by J0hnnyBr@v0 on 2008-08-28
When you guys say install VMWare, do you mean server or workstation?  I see the server reference above so I am downloading that now.

The reason I ask is that I downloaded the TAR for desktop and now that I have it unpacked....I don't know what to do to get it installed.  This is my first day being a convert to Linux.

I see a Perl script, tried to run it....but guess I don't know how.

Just downloaded VMWare server as RPM to convert to deb and install package...but so far...no packages I've installed have worked.

Thanks in Advance,
Eric

Never mind...found what I was looking for and installed VMWare a-ok

---

