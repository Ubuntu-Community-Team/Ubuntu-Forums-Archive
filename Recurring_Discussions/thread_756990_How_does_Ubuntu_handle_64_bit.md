---
title: "How does Ubuntu handle 64 bit?"
date: 2008-04-16
forum: Recurring Discussions
---

### Post by Th3Professor on 2008-04-16
Question in subject line.

---

### Post by phidia on 2008-04-16
By "handle" what specifically do you mean?

---

### Post by Half-Left on 2008-04-16
Just like 32bit but everything is compiled 64bit and it allows for more memory to be addressed, i.e over 4Gb.

---

### Post by Th3Professor on 2008-04-16
Pretty generic... anything that comes to mind.

I'm new to the whole realm of 64 bit and would like to learn more about it.

I plan on building my 1st desktop computer, which will definitely be 64 bit.

---

### Post by schiznik on 2008-04-16
Use the 64bit install CD, after that its pretty much the same as using 32bit now, flash "just works" etc

---

### Post by nasvemos671 on 2008-04-16
It handles it really, well having 8gbs of memory is awesome :) ALthough you have to look out for the packages and debs you install because there almost always have to be a work-around as a 64-bit user.

---

### Post by Th3Professor on 2008-04-16
> **Half-Left said:**
> Just like 32bit but everything is compiled 64bit and it allows for more memory to be addressed, i.e over 4Gb.

Ah you just sent your reply while I was previously replying...

I will definitely start with 4GB RAM on the 64-bit system (dual core).

Though it sounds like more and more people are already moving up to 8GB RAM on those systems.

I believe I can get a Kingston, 4GB RAM, for about $107, though don't know if the 8GB is still "too" high. I'm guessing memory, in general, isn't really "too high" anymore, considering how much all of it - in general - has gone down.

But more memory is always a plus.

So with 64-bit would one have to choose between speed and address space? Or is that only an issue with 32-bit?

---

### Post by Th3Professor on 2008-04-16
> **nasvemos671 said:**
> It handles it really, well having 8gbs of memory is awesome :) ALthough you have to look out for the packages and debs you install because there almost always have to be a work-around as a 64-bit user.

(I'm not really familiar with possible issues with packages/debs & 64-bit...)

What would be an example of there being a work-around as a 64-bit user? How would one work around it?

---

### Post by T-MAN3000 on 2008-04-16
Stickies are there for a reason, especially this one will be very useful for you: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) It actually says "Please read first".
 It's impossible to answer a question like "how does ubuntu handle 64-bit" in a meaningful way. I think we can help you much better when you ask something specific.

---

### Post by Th3Professor on 2008-04-16
> **T-MAN3000 said:**
> Stickies are there for a reason, especially this one will be very useful for you: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) It actually says "Please read first".
 It's impossible to answer a question like "how does ubuntu handle 64-bit" in a meaningful way. I think we can help you much better when you ask something specific.

Okay. who would drop $8,000 on 16 GB RAM? How would 64-bit handle that?

nasvemos671:
What would be an example of there being a work-around as a 64-bit user? How would one work around it?

---

### Post by dabl on 2008-04-16
I've been running 64-bit exclusively for over a year now.  Couple of thoughts:

- Discard your Windows-based assumptions about memory -- they are not applicable.  You'll have to get way deep into video encoding to ever use 4GB, and I don't know how you would ever use 8GB of memory short of some advanced server functions

- Flash works mostly (depending on which OS version and which day I check it)

- Jave Runtime Environment has been on-again off-again over the past 6 months

- There are some proprietary media players that flat out won't work on 64-bit.  For example, the one at Rhapsody.com.

BUT, you can run a 32-bit VM in your VirtualBox or VMWare Player, and use that to run any of the above items, if it's important.


Everything else just works the same as 32-bit, including:

- video drivers and compiz
- VMWare
- Open Office suite
- GoogleEarth
- common browsers and internet apps
- multimedia packages

---

### Post by Th3Professor on 2008-04-16
Awesome. Good to know that.

How does it do with a computer specifically set-up for "music studio" and "music recording/production" type things?

Or even DVD things, ripping/editing/etc., and simple playback?

---

### Post by dabl on 2008-04-16
Early last year, before Ubuntu Studio was released, I installed Feisty and the "low latency" kernel version that was available at that time, and then set up a custom turntable and equalizer and captured a lot of music from a collection of old 78 RPM records.  I used Audacity and GWC to process the files and I'm totally happy with the results.

I'm kind of a piker on the video processing stuff - I did capture some old VHS tapes last year (like 250GB of them), but I've yet to master the process of converting them to DVDs.  But DeVeDe and Kdenlive and Avidemux and all of that stuff is now in the standard 64-bit repos and should run with no problem on the new RT kernel, if that's what you're wanting to do.  :)

---

### Post by Th3Professor on 2008-04-16
Sweet!

Yeah, that's basically what I'm looking to do... though will dive deeper into music, mixer/soundboard (with instrument going in), and the board going - hopefully - to the pc... if it's possible.

btw- where did you get the picture (the avatar/user-icon-thing)?

---

### Post by dabl on 2008-04-16
> **Th3Professor said:**
> 

btw- where did you get the picture (the avatar/user-icon-thing)?



I had scanned an ancient family photo -- my great-grandmother was just a young girl, so it was in the late 1880s or early 1890s.  I used Gimp to outline one of the gents' head and shoulders, and then to copy out the outlined area and make a new image file of it.  Shrank it to avatar size and voila!

On your Linux sound system to-be, I would advise some caution and research on the sound card.  You can plunk down big bucks for one that works great in Windows and find out the Linux driver sucks or some such problem.  There are lots of threads in the Multimedia forum that will probably lead you to a good decision.  If you choose a third party add-on card, then your best bet on a motherboard would be to find one that does not have integrated sound on it, if possible.  FYI, I'm quite pleased with the Intel HDA system on my Intel motherboard, and have never hankered for more, in that regard.  I got an Altec Lansing set of speakers and sub-woofer, and it's a pretty nice rig, for an amateur.  :)

---

### Post by natros on 2008-04-16
> **Half-Left said:**
> Just like 32bit but everything is compiled 64bit and it allows for more memory to be addressed, i.e over 4Gb.

you can address up to 64 gb with 32bit, you have to enable PAE in the kernel

---

### Post by Half-Left on 2008-04-16
> **natros said:**
> you can address up to 64 gb with 32bit, you have to enable PAE in the kernel

If you want to be more specific yes but 64bit can address more at one time making it superior with large memory configs.

---

### Post by Th3Professor on 2008-04-16
> **dabl said:**
> I had scanned an ancient family photo -- my great-grandmother was just a young girl, so it was in the late 1880s or early 1890s.  I used Gimp to outline one of the gents' head and shoulders, and then to copy out the outlined area and make a new image file of it.  Shrank it to avatar size and voila!

On your Linux sound system to-be, I would advise some caution and research on the sound card.  You can plunk down big bucks for one that works great in Windows and find out the Linux driver sucks or some such problem.  There are lots of threads in the Multimedia forum that will probably lead you to a good decision.  If you choose a third party add-on card, then your best bet on a motherboard would be to find one that does not have integrated sound on it, if possible.  FYI, I'm quite pleased with the Intel HDA system on my Intel motherboard, and have never hankered for more, in that regard.  I got an Altec Lansing set of speakers and sub-woofer, and it's a pretty nice rig, for an amateur.  :)

Pretty cool avatar.

That's a good point, re: soundcards, I'll keep that in mind when it comes to building the new system.

> **natros]you can address up to 64 gb with 32bit, you have to enable PAE in the kernel[/quote]
and
[QUOTE=Half-Left said:**
> If you want to be more specific yes but 64bit can address more at one time making it superior with large memory configs.

So is PAE the only option for allowing a 32-bit CPU to address 64GB of memory?

With 32-bit, do you have to make a choice - even with PAE - between speed and address space?

If "Physical Address Extension" (PAE) involves memory addressing, though at a cost of CPU performance, would it be a win-lose situation between "speed" and "address space"?

Is it possible, on a 32-bit system, to optimize both "speed" and "address space" without any sacrifice?

Would it be a win-win situation between "speed" and "address space" on a 64-bit CPU?

---

### Post by Half-Left on 2008-04-17
Yes you can but there is quiet a big overhead with PAE for 32bit. Now the kernel has memory split so no need to enable high memory options for some setups. Basically 64bit is much better on 4Gb above memory configs because it allows the applications to address memory in bigger chunks, something like 3d apps will take advantage of something like that more so.

---

### Post by LaRoza on 2008-04-17
Welcoming to the Recurring Discussions. I believe all technical issues are addressed in the forum from which this came.

---

### Post by jespdj on 2008-04-17
> **Th3Professor said:**
> Okay. who would drop $8,000 on 16 GB RAM? How would 64-bit handle that?
Why would 16 GB cost $8,000 if 8 GB costs less than $200? :confused:

64-bit Ubuntu would handle 16 GB just like it would handle 8, 4 or 2 GB. There's nothing special about 16 GB. You'll just need to make sure you get a motherboard that supports that much memory, if you really want it.

---

### Post by Th3Professor on 2008-04-17
> **jespdj said:**
> Why would 16 GB cost $8,000 if 8 GB costs less than $200? :confused:

64-bit Ubuntu would handle 16 GB just like it would handle 8, 4 or 2 GB. There's nothing special about 16 GB. You'll just need to make sure you get a motherboard that supports that much memory, if you really want it.

oH LOL Yeah.
I came across a website that was selling some type of Kingston memory, it was 16 GB RAM, and had a price tag of something around $8,200. I have no idea what kind it was, I just saw the $ and thought, "woh."

---

