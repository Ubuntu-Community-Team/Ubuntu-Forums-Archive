---
title: "Disc burning with K3b and Brasero"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-21
Hi,
I recently posted re problems with Brasero, which informed me my medium was not writable with the current set of plugins. I'm posting again because the reply I received referred me to K3b without addressing the Brasero problem. I should add that I would prefer to use K3b but that is giving me grief as well, telling me Optimal Power Configuration fails at each attempt to burn. Then, when I try to eject the disc, it seems I don't have the required privileges to do so, and round and round it goes. 
Can someone please help me before I go nuts? I'm running Hardy Heron.
Thanks in advance,
philk949

---

### Post by Morpheun on 2008-07-21
Refering you to K3B was probably a bad idea if you're running gnome. Do you have a link to the previous thread or can you tell me exactly what your brasero error was?

---

### Post by philk949 on 2008-07-21
Hi Morpheun, 
Here is the link to the original post. 
Could you tell me please, if I can't get Brasero going, whether or not it would be a good idea to download PowerISO for Linux?


[URL="http://http://ubuntuforums.org/showthread.php?t=859761"]

---

### Post by Morpheun on 2008-07-21
It looks like you were trying to burn a DVD without a DVD drive. Are you sure your drive supports DVD writing?

---

### Post by krsmit0 on 2008-07-21
i had a similar problem. for me it seemed that nautilas was grabbing control of my blank media before the burn program could.

if using gnome, go to any folder, click edit, then preferences.

last tab is media, check "never prompt..."

close out of everything, and to be safe and also be able to get you disc out of the drive, reboot.

then burn away.  this fixed my problem.

---

### Post by philk949 on 2008-07-21
To morpheun:
No, I wasn't trying to burn a DVD. Am well aware I have no drive to do so. I tried burning a data CD, as I believe the screenshot on my posting shows and I've also tried burning an ISO image

To krsmit0:
Thanks, I'll give that a shot and let you both know how it goes

phil

---

### Post by philk949 on 2008-07-21
Back again.
Changed the preferences, rebooted and fired up Brasero. All was looking good for a while until I received the error message below, which is really annoying because I'm trying to burn 696MB of image onto a 702MB disc, so there should be no overburn.
K3b is still, of course, rubbish.
Anything else I can try?

Phil

---

### Post by alienexplorers on 2008-07-21
> **philk949 said:**
> Back again.
Changed the preferences, rebooted and fired up Brasero. All was looking good for a while until I received the error message below, which is really annoying because I'm trying to burn 696MB of image onto a 702MB disc, so there should be no overburn.
K3b is still, of course, rubbish.
Anything else I can try?

Phil

This is why I don't use Brasero.  I stick with either K3B or gnomebaker.  Errors I would get in Brasero I don't get in the other two.

---

### Post by philk949 on 2008-07-21
Thanks for the input, alienexplorers. 
I would dearly love to be able to work with K3b, but it won't let me. Below is a screenshot of error message and the error log for that attempted burn.

gnomebaker, you say? Could you give me some info please?
I'm running Hardy heron 8.04

---

### Post by editrix on 2008-07-21
A lot of people are getting that "Warning: Cannot raise RLIMIT_MEMLOCK limits" error, and it seems to be a bug--not in K3B but in Wodim--and I have no idea how to fix it or work around it.

If you search RLIMIT_MEMLOCK here, or with google Linux, or uboonto.com, you'll see what's going on.

I'm posting this to give the thread another bump, and in the hope that some genius can tell you (and therefore all of us with the problem) how to solve it.

---

### Post by philk949 on 2008-07-21
Thanks for the bump, editrix.
I researched the error code postings you mentioned. Made me feel less like a demented, solitary soul when I saw the all-too-familiar troubles others were having. Let's hope something turns up, 'cause I'm really over this whole coaster-producing cottage industry thing.
Good luck to all of us.
Phil

---

