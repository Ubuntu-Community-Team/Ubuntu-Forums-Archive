---
title: "I have 6gb ram. Do I really need any swap?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by malathion on 2008-04-24
As the subject says. Ram prices are so low and I got these sticks of DDR-800 for $35/2gb. Why not go all out I said, and I got 6gb. With this much ram I never come close to using it all in ubuntu. Do I really need any swap?

---

### Post by articpenguin on 2008-04-24
id still have at 512MB swap just incase although it will proably never be used.

---

### Post by Lord Xeb on 2008-04-24
It is recommended. Swap is made by default when you install Ubuntu.

---

### Post by tamoneya on 2008-04-24
as far as i know you should be okay without the swap file as long as you arent using it as a server or something.  I am running with 4GB of ram and have never seen my swap file utilized.  I am running some servers for personal use and using the computer as a desktop.

---

### Post by overdrank on 2008-04-24
> **malathion said:**
> As the subject says. Ram prices are so low and I got these sticks of DDR-800 for $35/2gb. Why not go all out I said, and I got 6gb. With this much ram I never come close to using it all in ubuntu. Do I really need any swap?

HI and I believe you do not but you can always add swap later.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by nicedude on 2008-04-24
Uh I believe you do most certainly. Like in Windows how you could lower your swap size and I always did but no swap never worked correctly. Why risk trouble for a couple GB of HDD space, if you have 6 GB of ram im sure you don't have a 10GB drive in that :-)

---

### Post by phidia on 2008-04-24
You probably don't need it but I think most installers still will require it. You can check the community docs and look at the install procedures there to see if there is some way to do an install without a swap partition.

---

### Post by articpenguin on 2008-04-24
if you want to hibernate you will need a swap partition. With 6Gbs of ram you would need at least 7GB of swap if you want to hibernate.

---

### Post by malathion on 2008-04-24
> **phidia said:**
> You probably don't need it but I think most installers still will require it. You can check the community docs and look at the install procedures there to see if there is some way to do an install without a swap partition.

I installed ubuntu without a swap partition by going into the editor and manually removing it. :)

> **Lord Xeb said:**
> It is recommended. Swap is made by default when you install Ubuntu.

It is recommended, but is there a reason to recommend it in my particular case? 

It never occurred to me what actually happens when the system runs out of memory. I have a basic understanding of how RAM and swap works, but what happens if I ran out of ram? 512mb swap isn't that much, and so if I ran out of 6gb ram I would probably fill that 512 swap too. What happens then?

---

### Post by Kingsley on 2008-04-24
> **phidia said:**
> You probably don't need it but I think most installers still will require it. You can check the community docs and look at the install procedures there to see if there is some way to do an install without a swap partition.
I'm very sure it's possible in Ubuntu. I did it on Feisty and Gutsy and no problems came up.

PS - I had 2 GB ram.

---

### Post by 3rdalbum on 2008-04-24
I don't have any swap on my computer at home; that's just got 2 gigabytes of RAM. But if you want to hibernate, that's when you'd need a swap partition. From what I hear, hibernation doesn't work with a swap file.

---

### Post by Paqman on 2008-04-24
No, I don't think you'll need it, unless you want to hibernate.

Still, you say memory is cheap. Well storage is even cheaper. A meg of swap space that you never use costs you less than a meg of memory that you never use. So it makes sense to play safe and have a small swap space available.

Unless you've already got truckloads of memory (which you do) in which case swap becomes pretty pointless. Personally I wouldn't even know how to use up 6GB of memory in Ubuntu. Maybe open several dozen instances of Firefox?

---

### Post by thisiam on 2008-04-24
I have on a 300GB harddrive 1gb of memory and 2gb swap and never use it,i don't even notice it gone but i know its there if i was to ever need it.

---

### Post by niteshifter on 2008-04-24
Hi,

As others have mentioned if you're going to hibernate the machine, you need a swap partition. No, a swap file will not work: When resuming initially there is no file system, hence no way to access a file. The file system becomes available later in the resume process.

Just wanted to clear that up a bit :)

Now, there's one thing that bothers me whenever this topic of "do I need swap" comes up and that's the responses along the line of "I've never needed it" - with the strong implication the other person doesn't either.

Er ... ahhh ... horsepuckey. Not everyone's usage habits, patterns and needs are the same! On a 2GB RAM install of Edgy (and now Gutsy) I've routinely hit 1GB+ of swap usage. Easy is: just fire up sage (or equivalent) and do some heavy-duty math work. Now you might say (and you'd be quite correct) that not that many folks will do mathematics as a hobby ;)

But consider this: I've also used 100's of MB of swap just playing with Blender, and video edits. Granted there was a lot of "stuff" opened - but that's the point isn't it? To not have to manage application loading ala Windows?

So, to the OP: Even if you currently think that you'll never do anything that needs swap, why not go ahead and plan like you will? The future is awful hard to foretell so I've heard. It's not like allocating a few GB of disk space will cramp you, is it? Figure out what the maximum RAM your machine can accommodate (2GB, 4GB are common sizes) multiply that by 1.2, round up to the next 0.25 GB size over that and call it done.

---

### Post by diplomat.x on 2008-04-24
I think space on hard-drive is cheaper than ram so i would have no questions about assigning even 1 GB to swap if its a must.

---

### Post by Saint Angeles on 2008-04-24
i have 2 GB RAM and ive never seen ubuntu use more than 40% of it... and thats while using a BUNCH of programs at once. (ff3b5, gimp, compiz, mplayer...)

but i got a swap partition just in case.

---

### Post by mozetti on 2008-04-24
> **nicedude said:**
> Uh I believe you do most certainly. Like in Windows how you could lower your swap size and I always did but no swap never worked correctly. Why risk trouble for a couple GB of HDD space, if you have 6 GB of ram im sure you don't have a 10GB drive in that :-)

This isn't windows. Linux runs fine without swap if you don't need it.

I have 3 GB of RAM and my swap is hardly ever touched.

---

### Post by Donskov on 2008-04-24
I do believe that when your ram and swap are full, depending on system settings an attempt to clear some is made. Your ram and hard drive are first come first serve basis(Not always the case as with some newer hardware). And since most memory controllers have been moved to the cpu. Usage should be very dynamic as most queries and requests are done on the external data bus EDB (A direct connection from the cpu/devices.)

I'm sure there is a more technical and correct explanation but this is fairly close I believe.

---

### Post by natirips on 2008-04-24
I once witnessed my swap being used in Ubuntu! It was when I force installed some stupid adobe flash plugin for Firefox (64-bit version), and than opened a .swf file to test it, although the file was half a meg in size, when I opened it took all of my RAM and swap. 
i thought it would crash the system, but Ubuntu proved to be better than that.

---

### Post by Sugz on 2008-04-24
6Gb, what the heck would you need that much for? Ubuntu doesnt run many games so it cant be for that reason. You dont need any more than 3 but hey i suppose your PC's ram is future proof which in computing is always a very good thing :)

---

### Post by Canis familiaris on 2008-04-24
> **articpenguin said:**
> if you want to hibernate you will need a swap partition. With 6Gbs of ram you would need at least 7GB of swap if you want to hibernate.

Exactly. Though I think 6GB + 256MB would just be enough.

And do you use AMD64 version of Ubuntu. I don't think you would be able to use more than 3.2GB RAM in 32bit.

---

### Post by Canis familiaris on 2008-04-24
> **Sugz said:**
> 6Gb, what the heck would you need that much for? Ubuntu doesnt run many games so it cant be for that reason. You dont need any more than 3 but hey i suppose your PC's ram is future proof which in computing is always a very good thing :)

What are DOOM, Quake, TORCS, Tremulous, Unreal Tournament then?
And what about Windows Games you can run with Cedega?

---

### Post by christianxxx on 2008-04-24
I wouldn't even know where to begin to fill 6Gb of RAM. Unless I was running Vista. But that's a different discussion. 

Anyways, as so many before has pointed out, why all the fuss? A small swap space doesn't do any harm.

---

### Post by Canis familiaris on 2008-04-24
> **christianxxx said:**
> I wouldn't even know where to begin to fill 6Gb of RAM. Unless I was running Vista. But that's a different discussion. 

Anyways, as so many before has pointed out, why all the fuss? A small swap space doesn't do any harm.

Yeah. Unless you do not wish to hibernate you need to have atleast more SWAP space than RAM.

Here I have to say if he can spend extra for RAM, he should definitely be able to afford 6GB of Hard Disk space.

---

### Post by duckville on 2008-04-24
christianxxx is right, having the swap is not gonna hurt.
you can even make a swap file rather than a partition if you so desire.

it's like having a 160gb ipod, you may not fill it with music, but it's nice to know you've got the extra capacity if you require it someday.

---

### Post by Canis familiaris on 2008-04-24
> **duckville said:**
> christianxxx is right, having the swap is not gonna hurt.
you can even make a swap file rather than a partition if you so desire.

it's like having a 160gb ipod, you may not fill it with music, but it's nice to know you've got the extra capacity if you require it someday.

Yeah but one cannot hibernate using SWAP file. Right, isn't it?
And I cannot see the point of a SWAPFILE if you can have unlimited logical drives.
After all space used will be the same.

---

### Post by Canis familiaris on 2008-04-24
Wrong Post
Sorry! My mistake

---

### Post by sloggerkhan on 2008-04-24
I think that there are a handful of situations where swap might be useful, and I see no harm in having it. Could you go without it? Yes.

---

### Post by natirips on 2008-04-24
> **sloggerkhan said:**
> I think that there are a handful of situations where swap might be useful, and I see no harm in having it. Could you go without it? Yes.

I do see harm in it, as insane as I might sound , sometimes a buggy application (I don't know why I just remembered the name of [BETTER BE CENSORED]) might be devouring your memory, after it's done with memory, it devours swap, thus slowing down your computer quite a lot.

---

### Post by malathion on 2008-04-24
> **natirips said:**
> I do see harm in it, as insane as I might sound , sometimes a buggy application (I don't know why I just remembered the name of [BETTER BE CENSORED]) might be devouring your memory, after it's done with memory, it devours swap, thus slowing down your computer quite a lot.

Here's my problem with this reasoning. If an insane program is devouring my memory, all the way up to 6gb of it(!) then wont it burn through the remaining 1gb of swap no problem anyway? How can I plan for every future scenario? I can't.

I never hibernate my system, but the "why not?" arguments are somewhat persuasive too. Thanks for all the comments so far! :)

---

### Post by Golem XIV on 2008-04-24
I'm a bit out of touch with the latest tech, but I remember that DDR RAM should be installed in pairs in order to make use of the DDR feature.  So if you used 3x2 GB sticks, wouldn't that mean that the RAM would default to single data rate?

---

### Post by nanotube on 2008-04-24
> **Paqman said:**
> No, I don't think you'll need it, unless you want to hibernate.

Still, you say memory is cheap. Well storage is even cheaper. A meg of swap space that you never use costs you less than a meg of memory that you never use. So it makes sense to play safe and have a small swap space available.

Unless you've already got truckloads of memory (which you do) in which case swap becomes pretty pointless. Personally I wouldn't even know how to use up 6GB of memory in Ubuntu. Maybe open several dozen instances of Firefox?

easy: load up a few 3-gb datasets into R, and there goes your 6 gb of ram :)

---

### Post by OffAxis on 2008-04-24
> It never occurred to me what actually happens when the system runs out of memory. I have a basic understanding of how RAM and swap works, but what happens if I ran out of ram? 512mb swap isn't that much, and so if I ran out of 6gb ram I would probably fill that 512 swap too. What happens then?
There's an easy way to find out. Since you don't have a Swap partition, just pull most of your memory (down to 512 or 1 GB), boot, and start loading programs...

---

### Post by Donskov on 2008-04-24
You only need two identical sticks for dual-channel. DDR stands for double data rate. DDR works very similarly to the old EDO where information can be transfered at the Rise and fall of each clock cycle. Thus your 400Mhz is really running at 200Mhz. But since the rise and fall are used to send or receive info its considered to be doubled. Dual-channel works by basically assigning one address to two physical address. essentially doubling throughput. Like adding more checkouts in a store.

---

### Post by swoll1980 on 2008-04-24
I think you need it for hibernation if you use it

---

### Post by malathion on 2008-04-24
> **Golem XIV said:**
> I'm a bit out of touch with the latest tech, but I remember that DDR RAM should be installed in pairs in order to make use of the DDR feature.  So if you used 3x2 GB sticks, wouldn't that mean that the RAM would default to single data rate?

I have 2x2gb in dual channel and 2x1gb in dual channel.

---

### Post by Joeb454 on 2008-04-24
I usually have 256 MB Swap. 2GB RAM in the PC :)

---

### Post by funrider on 2008-04-24
i have 8gb of ram and never see my swap being used.

---

### Post by tyblu on 2008-04-24
I routinely crash my fancy new MacBook with 2GB RAM and equal swap with grubby Matlab scripts eating up memory and OSX not being able to shut it off in time. (Yeah, I know -- write better scripts, douche.) I imagine Octave could do the same to Ubuntu, though it has much less overhead...

---

### Post by Paqman on 2008-04-24
> **malathion said:**
> Here's my problem with this reasoning. If an insane program is devouring my memory, all the way up to 6gb of it(!) then wont it burn through the remaining 1gb of swap no problem anyway?


AFAIK, once you run out of memory and swap non-system processes start to get killed off first. So your runaway process would most likely die. Which is a comforting thought, really.

---

