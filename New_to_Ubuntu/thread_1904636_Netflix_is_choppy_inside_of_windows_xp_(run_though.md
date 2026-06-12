---
title: "Netflix is choppy inside of windows xp (run though virtualbox)"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by venom104 on 2012-01-05
I followed the directions on here, [http://ubuntuforums.org/showpost.php?p=9506867&postcount=6](http://ubuntuforums.org/showpost.php?p=9506867&postcount=6).

I have a decent machine, it's running two AMD cores, 3 gigs of memory, and netflix works fine under windows 7 (on it's own partition). 

I've tried running netflix in firefox and chrome under my windows xp install (in virtualbox) and disabling/enabling 2/3d acceleration. I've been googling for a while now and I can't figure out what to do next?

Someone please help me out?

I'm running Ubuntu 10.04 LTS and virtual box 4.1.8

EDIT
I forgot to add I have a 512 mb 9400 GT NVIDIA card, I let virtual box have 128 MB of it. Also, the XP has SP 3 installed

---

### Post by venom104 on 2012-01-06
Awww, come on guys, serously, no one else has this problem?

---

### Post by snowpine on 2012-01-06
I recommend dual-booting (choose between Linux or Windows when you turn on the computer).

---

### Post by venom104 on 2012-01-06
> **snowpine said:**
> I recommend dual-booting (choose between Linux or Windows when you turn on the computer).

As I've said before, I'm running windows 7 on it's own partition on my computer and netflix works fine. I don't want a work around, I want a solution.

---

### Post by robgraves on 2012-01-06
I decided I was gonna hound netflix for native linux support, I called their customer service number and said I want to officially go on record as being a member that wants linux support. As for now I dual boot and use windows for netflix and games, linux for everything else.

---

### Post by snowpine on 2012-01-06
> **venom104 said:**
> As I've said before, I'm running windows 7 on it's own partition on my computer and netflix works fine. I don't want a work around, I want a solution.

Choose a Linux-friendly content provider?

---

### Post by QIII on 2012-01-07
> **venom104 said:**
> 
I forgot to add I have a 512 mb 9400 GT NVIDIA card, I let virtual box have 128 MB of it. Also, the XP has SP 3 installed

You didn't necessarily give your NVIDIA card's memory to Virtualbox exactly.  What you did was assign 128MB of memory to a virtualized VESA card that will *attempt*, through the Guest Additions, to use some of the features of your physical card, like some parts of OpenGL and 2D/3D acceleration.  But there is still a hand off to the physical card.  There's an expense in that communication and handover of duties.  It's faster than trying to do that with software emulation, but there is still some overhead.

This is about gaming performance, but it tells a sad tale:

[http://www.phoronix.com/scan.php?page=article&item=virtualbox_41_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=virtualbox_41_3d&num=1)

Also read here:

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

Until the guys at Virtualbox can give us something better, using Windows natively for some things*** IS*** the solution.  I think they put out a pretty good product.  What we are talking about is a pretty tough nut.

---

### Post by QIII on 2012-01-07
[U]
That was weird
[/U][]("http://www.phoronix.com/scan.php?page=article&item=virtualbox_41_3d&num=1")

---

### Post by wildmanne39 on 2012-01-07
Hi, I used netflix in virtualbox for a while and it did not work as well as I would have liked but my problem was a sound issue and not choppiness.

I like watching movies on my tv so my computer is free for other things so I invested in a roku box and I have never been happier but I agree netflix needs to make it able to be used by linux users.

I use to run a dual core with 4 gigs of ram and the processor was weak for what you are trying to do in my opinion, I now run a quad core and the performance is greatly improved in virtualbox.
Thanks

---

### Post by venom104 on 2012-01-07
I've managed to semi fix the issue and determine what the cause is. Apperently my refresh rate in ubuntu was set to 60 hz, and I upped it 75 hz and that make the vidoes play smoother. 

I wont mark this solved because the issue isn't totally resolved, but I know it has to deal with the framerate.

I don't think it's possible to increase the framerate in the guest OS in virtual box, and I think that is where the problem lies.

Also, changing the guest OS resolution to 800x600 helped a ton.

---

### Post by Paqman on 2012-01-07
> **venom104 said:**
> I don't want a work around, I want a solution.

The problem is that hardware graphics acceleration in VMs is a fairly new feature, and not particularly good. If you want good graphics performance, you need to be running on bare metal, not a VM.

Sorry, but there is no real solution to this. Except maybe wait a couple of years, as graphics performance in VMs is definietly improving.

---

### Post by venom104 on 2012-01-07
I SOLVED THE PROBLEM! Since the lack of information here wasn't acceptable I went to the ubuntu IRC channel and discussed the problem. Installing the guest additions ( [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) ) and enabling 2d acceration fixed the issue, I don't even have to change my guest OS resolution to 800x600 anymore.

WARNING: Sliverlight doesn't play well with 3d acceleration, best to disable it.

---

### Post by QIII on 2012-01-07
You were told about Guest Additions in this thread.

You were also given a link to the Virtualbox manual in this thread.

I'm sorry that you had to go to the IRC to get information you were already given here in a single post.

---

