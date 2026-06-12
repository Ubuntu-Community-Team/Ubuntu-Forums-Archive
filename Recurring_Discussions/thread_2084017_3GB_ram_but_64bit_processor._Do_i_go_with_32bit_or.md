---
title: "3GB ram but 64bit processor. Do i go with 32bit or 64bit OS?"
date: 2012-11-14
forum: Recurring Discussions
---

### Post by JohneG on 2012-11-14
I have a quad core 64bit processor, however, i only have 3 gb ram. I do plan on getting more ram but things are tight with cash at the moment. Are there any real benefits to be had from installing 64 bit Ubuntu on my computer? I use Ardour, the digital audio workstation, a lot and i'm wondering would i get any better performance out of a programme that needs the power if i installed 64bit? Not that i'm running low on power, i get by without any problems but i'm just curious.

---

### Post by Abhinav Kumar on 2012-11-14
> **JohneG said:**
> I have a quad core 64bit processor, however, i only have 3 gb ram. I do plan on getting more ram but things are tight with cash at the moment. Are there any real benefits to be had from installing 64 bit Ubuntu on my computer? I use Ardour, the digital audio workstation, a lot and i'm wondering would i get any better performance out of a programme that needs the power if i installed 64bit? Not that i'm running low on power, i get by without any problems but i'm just curious.
Hi

Go for 64 bit version.

Regards,
Abhinav

---

### Post by JohneG on 2012-11-14
> **Abhinav Kumar said:**
> Hi

Go for 64 bit version.

Regards,
Abhinav

What benefits would i have? I know the selling point of 64bit is the access to more ram but do i understand correct that for programmes that need more processing power, that 64 bit will give them an advantage?

---

### Post by Paqman on 2012-11-14
> **JohneG said:**
> Are there any real benefits to be had from installing 64 bit Ubuntu on my computer?

Yes.

[Long version]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1").

Short version:
> The 64-bit version of Ubuntu Linux is generally much faster, all modern x86 hardware supports 64-bit instructions, and previous major limitations of 64-bit Linux have all since been addressed.
(Quoted from the conclusion of the above article.)

---

### Post by drmrgd on 2012-11-14
Also to add to all of this, when you do have some extra cash laying around and want to upgrade the RAM, you won't have to reinstall your OS to take advantage of it.  You'll already be ready to handle more.  These days, I don't think there's really any reason not to install a 64-bit OS if given the opportunity.

---

### Post by Artemis3 on 2012-11-14
Please don't use odd numbers of ram, you are probably getting a performance hit because of single channel mode. Stick to 2, 4, 6, 8, etc. 3 is bad, and you usually need to use at least 2 sticks. So 2g x2 is better than 4g x1 (and use different banks when installing).

Besides memory addressing, 64bits assume certain optimization options available the compiler uses, even if you don't have much memory. That is why there is an x32 proposal, but it came too late. x32 would remove the mild extra memory 64bits program take, while taking complete advantage of the latest processors.

But people is using 4g+ these days, so its no longer meaningful.

Since you will buy memory, stick to 64 bits.

---

### Post by Paqman on 2012-11-14
> **Artemis3 said:**
> Please don't use odd numbers of ram, you are probably getting a performance hit because of single channel mode. Stick to 2, 4, 6, 8, etc. 3 is bad, and you usually need to use at least 2 sticks. So 2g x2 is better than 4g x1 (and use different banks when installing).


Of course, if you have four slots then dual-channel 3GB is possible:

2x1GB
2x512MB

All nicely dual channel. Some boards are also triple channel, so obviously you'd want to have sticks in threes in those.

---

### Post by mips on 2012-11-14
Just go for 64-bit.

There are many threads in the recurring discussions section with all the reasons listed if you are keen to go there ;) [http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by forrestcupp on 2012-11-14
Being able to access more RAM is just one benefit that comes from a 64-bit OS. 64-bit means that your OS can run 64-bit instructions.

One bit is a storage of information that can either have a value of 1 or 0. So 32-bits is a single packet of information that has a string of 32 1's and 0's. 64-bits is a packet of information that has a string of 64 1's and 0's. So you can look at it as a pipeline allowing information to flow, and a 64-bit pipeline is twice as wide as a 32-bit pipeline. That allows for much more complicated instructions in each process cycle, as well as access to bigger chunks of memory at a time. With 32-bit, you'll see more bottlenecks than 64-bit.

But apps have to be programmed to take advantage of it. You'll see the biggest difference in things that are processor intensive that require complex calculations, like file compression, 3D rendering, compiling code, maybe some audio processing and video and photo editing.

So being able to access more RAM is just one of the benefits.

---

### Post by philinux on 2012-11-14
Moved to Recurring.

This is a bit old now but still interesting.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by wheeze on 2012-11-14
> **Paqman said:**
> Of course, if you have four slots then dual-channel 3GB is possible:

2x1GB
2x512MB

All nicely dual channel.

This is how my old Abit motherboard is configured.

I run a single-core Athlon 64 with 3 GB dual-channel RAM and use the 64-bit OS. For such an old machines, it'll run anything I put on it acceptably.

---

### Post by deadflowr on 2012-11-14
> Being able to access more RAM is just one benefit that comes from a 64-bit OS. 64-bit means that your OS can run 64-bit instructions.

+1

The more information you can send at once the speedier your system can become.

I've run 64-bit systems with 1, 2, 3, and 4GB of ram. Unless you're planning on doing extensive work, running a whole bunch of programs at once RAM shouldn't be an issue.
And running 3GB isn't as much a problem as mismatched RAM speeds, ie 2GB @533MHZ and 1GB @667MHZ. The system will always run at the lowest speed RAM available.

---

