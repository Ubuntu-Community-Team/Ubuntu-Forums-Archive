---
title: "What on earth is a swap file?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by jamieh on 2008-06-06
I can't find this ANYWHERE. What is a swap file?

How big should I make my swap file when I install? I have a LOT of hdd space to spare, I can make it 50GB if needed. What does it do? The more space the better?

I have 768MB of ram (One 512MB stick and one 256MB stick, if that matters)

Thanks for your help!!

jamieh

---

### Post by SunnyRabbiera on 2008-06-06
A swap file or swap partition is extra memory that the system may need.
Linux manages memory a little differently then windows, while windows uses all availible memory linux uses as little memory as possible.
The swap partition is more or less emergency memory, and it helps even with systems with decent memory like mine.

---

### Post by Joeb454 on 2008-06-06
Then make your swap file 1.5GB

Generally your swap is twice the size of you're RAM (unless you have 2GB or more, then it gets a little too big ;))

And do you know what the page file does on Windows? It's basically the same thing

---

### Post by Duck2006 on 2008-06-06
1Gb should be bigger enough, The swap partition is use to dump memory in to when it becomes full, just like a swap file in windoze.

---

### Post by SunnyRabbiera on 2008-06-06
> **Joeb454 said:**
> Then make your swap file 1.5GB

Generally your swap is twice the size of you're RAM (unless you have 2GB or more, then it gets a little too big ;))

And do you know what the page file does on Windows? It's basically the same thing

right, though I dont think that dumps out after reboot unlike linux... thus why XP is a space hog, there is some evidence I have seen backing that up too.

---

### Post by H.Callahan on 2008-06-06
A swap file is used by the operating system (in this case, Ubuntu) as extra virtual RAM when more memory is needed than is being supplied in actual memory.  The cost of this is that the data in the swap file has to be paged into and out of real RAM when it is needed for manipulation or execution (in the case of a program).  This slows the system down.  But, it DOES allow you to do things that you ordinarily would not be able to do.  If you are utilizing swap memory a lot, you should consider more memory for your system.

Generally, the rule-of-thumb that I see most often for the size of the swap file is 1.5 to 2.5 the size of your installed memory.  In your case, it would be about 1152 to 1920 MB.  Making too big of a swap file can actually significantly slow down your system overall (at least in the case of Windows...I'll let someone more versed in Linux correct me if I am wrong WRT Ubuntu).

---

### Post by FuturePilot on 2008-06-06
A swap file or partition is used as virtual RAM. The OS will swap out un-needed things from the RAM to the disk so other things can use more of the RAM.
Linux uses a swap partition instead of a file like Windows does. More doesn't always mean better. After a certain point it won't help anymore and you will just be wasting space. The Ubuntu installer will automatically create a swap partition the appropriate size. I also have 768MB of RAM and Ubuntu automatically created a 1.8GB swap partition. I would recommend the size to be at least equal to the amount of RAM you have especially if you want to use Suspend and Hibernate. If it's less you won't be able to use those features. But it should probably be no more than 2x your RAM. After that it pretty much becomes wasted space.

---

### Post by lisati on 2008-06-06
Think of the swap file or swap partition as an extension to physical memory - it's a way of letting your computer behave as if it has more memory than it really has.

> **FuturePilot said:**
> A swap file or partition is used as virtual RAM. The OS will swap out un-needed things from the RAM to the disk so other things can use more of the RAM.

...and the OS will reload the information from the Swap partition when needed.

---

### Post by Joeb454 on 2008-06-06
> **SunnyRabbiera said:**
> right, though I dont think that dumps out after reboot unlike linux... thus why XP is a space hog, there is some evidence I have seen backing that up too.

Yeah I believe you're right. A Page File just stays at the same size as your RAM - which is kind of annoying :p

---

### Post by philinux on 2008-06-06
If you got 2gig memory swap don't get used.

---

### Post by stchman on 2008-06-06
> **jamieh said:**
> I can't find this ANYWHERE. What is a swap file?

How big should I make my swap file when I install? I have a LOT of hdd space to spare, I can make it 50GB if needed. What does it do? The more space the better?

I have 768MB of ram (One 512MB stick and one 256MB stick, if that matters)

Thanks for your help!!

jamieh

Think of it as reserve memory.

When you run out of memory the OS starts to store data in the swap file.

The swap file will not be used unless you run out of RAM.

---

### Post by Duck2006 on 2008-06-06
> If you got 2gig memory swap don't get used.

I you are using a program that takes a lot of memory, then yes it will, but most people will never use programs that need that much memory.

---

### Post by Joeb454 on 2008-06-06
True - I think video encoding or large image editing may increase the RAM usage a lot, though personally I've never gone over 1GB (unless I'm running a VM)

---

### Post by Sinkingships7 on 2008-06-06
You couldn't find this anywhere?

Did you try a google search for "swap file"? The second result gives you [this]("http://www.computerhope.com/jargon/s/swapfile.htm")...

---

