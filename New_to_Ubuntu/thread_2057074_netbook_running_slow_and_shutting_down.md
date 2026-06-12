---
title: "netbook running slow and shutting down"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by saintkai on 2012-09-12
I just installed ubuntu on my Acer Aspire One  netbook. (model # nav50) because windows 7 starter was messed up.

Ever since i installed ubuntu, everything seems to lag. And while trying to figure out what was wrong, i recieved an error message but i don't know why...

This is my first time trying Linux. I'm hoping to expand my knowledge because I've always heard Linux is one of the best OS around.

Any help with this current problem and advice on how to utilize properly would be great! 

thanks!

---

### Post by eylisian on 2012-09-12
No one here will ever know why either if you don't post the error message. =)

---

### Post by 2F4U on 2012-09-13
I would also suggest you post your hardware specs. Since it is a netbook, Ubuntu with Unity may be too heavy. Is your machine getting hot? That may be an explanation for the slowdown because Ubuntu tries to protect the hardware components and in emergency case would even shutdown the machine to prevent any damage.

---

### Post by mcduck on 2012-09-13
Aspire Ones also quite often have hard drive problems, thanks to the way how the drives are mounted in the machine that was originally designed to use a SSD drive, so you might want to check the SMART status of the drive in case there are any bad sectors. Broken drive could also explain the problems you had with Windows...

---

### Post by audiomick on 2012-09-13
> **saintkai said:**
> Ever since i installed ubuntu, everything seems to lag. 

But you say Win7 was messed up. Were the symptoms in Win7 possibly in any way similar to the lagginess in Ubuntu? The reason for asking this is to try and determine whether you have a hardware problem, which would have also affected Win7. I am inclined to think this is the case. Either a heat problem, as suggested by 2F4U, or a drive problem as suggested by mcduck. 

You can find the SMART values that mcduck refers to by using the Disk Drive Utility. There is a button in there to the right of the window that shows you them.

A clue to whether your machine is getting hot is that the fan runs flat out the whole time. It will also, of course, be hot to touch. You could install a temperature monitor. There is, for instance, a thing called Xsensors available in the software centre of this 10.10 install that looks like it would do the trick. Try searching "temperature" in the software centre.

Do try and post the error message you got, It could well indicate that something else altogehter is the problem.

One other thing you might like to try is to boot into the live environment from a USB stick. I assume, since your machine is a netbook, that it has no CD drive, and that you installed from a USB stick. Boot to that and go into the "try without installing" option. If the machine behaves in a similar way, there may be a heat problem or something else that has to do with the hardware generally. If not, then maybe the drive has an issue, or maybe the install has an issue.

---

