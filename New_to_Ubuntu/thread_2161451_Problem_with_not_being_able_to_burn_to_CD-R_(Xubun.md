---
title: "Problem with not being able to burn to CD-R (Xubuntu 13.04)"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2013-07-10
I'm not sure I'll get anywhere with this, but I'll give it a try: I don't seem to be able to burn to CD-R disks. I've tried using Brasero, xburn and K3b *and* they all throw up random errors. (Probably doesn't like medium, unknown error, etc.)

Yet I can burn to CD-RW and DVDs just fine. 

Here are a few things it's not. 

1. My CD burner isn't knackered. I triple boot, and I can burn to CD-R in Windows 7 and also Manjaro Linux without any issues. 
2. My understanding is that different lenses are utilised for burning CDs and DVDs, but since I can burn to CD-RW, this doesn't seem to be the answer (Plus, I wouldn't be able to burn CD-R using other OSes.) 
3. Nor is it the CD-R medium. I've tried various quality CD-Rs, from cheap to expensive, and all fail at some point in the process. 
4. I tried researching the problem online, and someone suggested it might be a kernel issue, so I updated my kernel from 3.8.0-25 to 3.8.0-26, with no change in result.

So I'm a bit stumped. Any suggestions would be welcome. I'm running Xubuntu 13.04 (x64)

---

### Post by 4Foot on 2013-08-01
SBSP: I have been having the same issue with burning DVD's (Haven't tried CD's) in 13.04. I was using Mint 15 until yesterday when I switched to Ubu 13.04 in hopes of solving this problem. I use a PLextor Burner and it has been working just fine for years. Both Mint and Ubu always throw up a "cannot mount ..." error no matter what you insert but it mounts anyway, they have always done that. However, a few weeks ago, nothing I tried would successfully burn a DVD. The blanks mount, I start the burning process and then it spits out the blank and gives a message that changes from "Power Adjustment problem" , to "may be your media" to "cannot burn to this device", or "try using TAO",etc.. 

Strange thing is that it does this with K3b, my goto burn prog, Brasero and with Xfburn. I ran across a thread which blamed Wodim and advised installing cdrecord and mkisofs which I did in Mint, (Ubu would not let me install the older version over the newer Wodim). However, even though K3b used cdrecord after the install it did not change anything. Nothing will burn. 

Since the same problem appears in both Mint and Ubu I have to assume that it is not platform specific but must be related to a recent update. I use my Linux box almost exclusively for media creation and burning so this is a big problem for me. I hope someone can point us towards a solution.

Cheers

4Foot

---

### Post by gordintoronto on 2013-08-01
Spongebob: have you tried specifying a slower burn speed in K3B, such as 4x?

---

