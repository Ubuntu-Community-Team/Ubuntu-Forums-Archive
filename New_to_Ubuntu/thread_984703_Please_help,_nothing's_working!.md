---
title: "Please help, nothing's working!"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by the_fury on 2008-11-16
OK, please forgive me if I'm a little short. Here's my problem:

I used to have a Sony Vaio, VGN-240E model, running Vista. Vista crapped out on me, so I switched to Ubuntu. Best thing that ever happened to my computer -- until 2 weeks after the install.

Ubuntu will randomly display problems - here are a few that may be in other threads:

-Google Search : assertion fails
-The screen will go completely black except for a few lines of what look like machine-gun rounds.
-The screen will freeze and all you can hear is a repeating loud "nuh nuh nuh nuh nuh nuh nuh" and I am forced to shut down manually.

Running "fsck" in the emergency terminal fixes it for about a day or two, and then it's back to the stupid problems.

I am at my wit's end! Please tell me - is it due to the computer, perhaps a faulty Ubuntu LiveCD download, or what?

Any help you can give me is appreciated.

---

### Post by 73ckn797 on 2008-11-16
> **the_fury said:**
> OK, please forgive me if I'm a little short. Here's my problem:

I used to have a Sony Vaio, VGN-240E model, running Vista. Vista crapped out on me, so I switched to Ubuntu. Best thing that ever happened to my computer -- until 2 weeks after the install.

Ubuntu will randomly display problems - here are a few that may be in other threads:

-Google Search : assertion fails
-The screen will go completely black except for a few lines of what look like machine-gun rounds.
-The screen will freeze and all you can hear is a repeating loud "nuh nuh nuh nuh nuh nuh nuh" and I am forced to shut down manually.

Running "fsck" in the emergency terminal fixes it for about a day or two, and then it's back to the stupid problems.

I am at my wit's end! Please tell me - is it due to the computer, perhaps a faulty Ubuntu LiveCD download, or what?

Any help you can give me is appreciated.

Try a re-install after verifying the md5checksum of the downloaded iso.

---

### Post by the_fury on 2008-11-16
I did a "Check CD for errors" and it was fine.

Also, I have reinstalled Ubuntu, both Hardy and Intrepid, several times, and the problems recur. Just thought I'd mention that.

---

### Post by chrisod on 2008-11-16
If it works fine for a while then suddenly stops it probably is not a software problem. It sounds like you might have faulty memory, or maybe a hard drive that is starting to fail.

---

### Post by detroit/zero on 2008-11-16
I like how everybody is quick to point to a potential hardware failure when Ubuntu doesn't work right.

It's not that I don't love Ubuntu and use it every day, but come on - this OS has a good share of bugs in it yet, as is evidenced by the hundred and seventy seven million threads in these forums.

How often do you people *see* actual hardware failures, anyway? I mean personally; on something you own. I've owned probably 50 different computers starting in 1986 with a Commodore 64. The only - **only** - hardware failure I ever saw happened when I spilled a big bowl of chicken-noodle soup on my Amiga 500 back in 1990. I'm not saying they never happen, but not every flaw in someone's Ubuntu experience is due to a hardware failure.

Having said that... I don't know, fury, if you've done multiple re-installs and keep coming back to the same problems. Have you tried Kubuntu? Any other distros? It's definitely a compatibility issue... How does the live cd work for you? Are these problems reproducible? That is - is it the same set of problems every time, or is this just what's going wrong this time?

If you're computer's Vista capable, it should darn well run Ubuntu. Since your biggest problems are display related, are you using any proprietary divers? ATI? NVidia? Are you using Compiz fusion?

_**EDIT:**_ I see from some of your other posts that you're using the 64-bit version. Are you sure that's the right version for you? Run this in a terminal:```
cat /proc/cpuinfo
```Near the bottom, in the "flags" section, you're looking for [COLOR=Red]**lm**[/COLOR].

I just found that in a [google search]("http://www.google.pl/search?num=20&hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&q=how+to+tell+if+i+have+64+bit+processor+linux&btnG=Search"), but it seems to hold true. Me, for example:```
zero@zero-laptop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 14
model name    : Genuine Intel(R) CPU           T2080  @ 1.73GHz
stepping    : 12
cpu MHz        : 1733.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon bts pni monitor est tm2 xtpr
bogomips    : 3462.04
clflush size    : 64
```The info is repeated for my second core, but I know I have a 32-bit processor, and my stats are listed without the lm flag. Maybe someone with a definite 64-bit processor can come by and verify this?

---

### Post by handydan918 on 2008-11-16
+1 for a hardware issue. 

Granted, real hardware failures are rare, but they do happen, and I have seen them. Personally. Verifiable.

This one sounds like it could be a hardrive starting to go away, especially since this is the SECOND O/S to fail on this machine....

---

### Post by detroit/zero on 2008-11-16
> **handydan918 said:**
> +1 for a hardware issue. 

Granted, real hardware failures are rare, but they do happen, and I have seen them. Personally. Verifiable.

This one sounds like it could be a hardrive starting to go away, especially since this is the SECOND O/S to fail on this machine....
Yeah, that is a valid point. Hardware failures do happen, true. I've spent some time doing component-level electronic repairs, and I've seen firsthand what can happen.. But come on. When's the last time you junked a computer just because Windows crapped out on you? ( And - can I have the next one you throw away? I'll even pay for shipping :))

[Check his model number on Amazon]("http://www.amazon.com/Sony-VGN-C240E-Laptop-Processor-Premium/dp/B000M5ND4S/ref=cm_cr_pr_product_top/181-2000735-1726209").. That's practically a brand-new laptop. And again, yes, a hardware fizzle is more bound to occur in the first couple weeks off the shelf than in the long run, but I'm assuming OP has been plugging away with Vista for some time now?

Plus, a hard drive dying out is not very likely to cause recurring display problems at two-week intervals.

_**EDIT:**_ Well, after looking at the user reviews on Amazon, I guess that model is going on two years old. One of the reviews even specifies a hard drive that had to be replaced twice because it died.

---

### Post by CatKiller on 2008-11-16
It sounds most like a memory problem to me. The GRUB boot menu has an option for memtest86+. Run that to check your memory. It takes quite a while, so run it overnight or something. Let it run for a few full passes.

If that doesn't show anything amiss, then it might be temperature or power supply related. These would cause your processor or your memory to function differently to how they should. Hard drives are the most likely component to fail early, even in normal use. You'll often get mechanical noises when they're failing. Clicking can be especially bad. The manufacturer of the hard drive should have a diagnostic tool that you can download from their website that will check for errors.

Contrary to detroit/zero's assertion, most lockups are hardware-related in one way or another. Even in Windows. Either through hardware that is faulty or running out of spec, or through drivers that don't function correctly.

Memory or hard drive problems can cause issues in seemingly unrelated systems, since the data that they are working from is inaccurate. Instructions (drivers and applications) as well as user-data like images or sounds.

EDIT: If your hard drive is suspect, then it's probably best to run the version of memtest86 that's on the Ubuntu cd, since the version on the hard drive might give flawed results.

---

### Post by detroit/zero on 2008-11-17
> **CatKiller said:**
> Contrary to detroit/zero's assertion, most lockups are hardware-related in one way or another. Even in Windows. Either through hardware that is faulty or running out of spec, **or through drivers that don't function correctly.**Drivers not functioning correctly would make it a software problem.> **CatKiller said:**
> EDIT: If your hard drive is suspect, then it's probably best to run the version of memtest86 that's on the Ubuntu cd, since the version on the hard drive might give flawed results.OK, ok.. I'll admit it. It could be a hardware problem. The possibility does exist.

Having said that, I'll continue to try and give the guy options that don't include him running out the door and dropping a couple hundred bucks on service/new hardware before it's absolutely necessary.

---

### Post by PierreDeKat on 2008-11-17
> **detroit/zero said:**
> How often do you people *see* actual hardware failures, anyway?

I just replaced my hard drive last week, as a matter of fact. And that's exactly what I think your problem is, as well.

I, too, suspected Ubuntu, and even [filed a bug]("https://bugs.launchpad.net/ubuntu/+source/seamonkey/+bug/290857") about a problem I was having with Seamonkey.

It should have been a big tip-off for me that this supposed bug was so erratic. 

Anywho, after a couple weeks thinking there was a bug in Seamonkey, I was rebooting my computer, and my [BIOS threw up a message]("http://en.wikipedia.org/wiki/S.M.A.R.T.") that I needed to back up any data on my primary drive because it was about to crap out on me.

I dropped in a new hard drive, reinstalled Windows and Ubuntu, temporarily plugged in my old hard drive and dragged over everything I needed from the old drive. Then I reformatted it and dropped it in my trash can.

Guess what. No more quirky error messages in Seamonkey.

The fact that your Windows Vista crapped out on you, and now Ubuntu is crapping out on you should be a big tipoff.

---

### Post by starcannon on 2008-11-17
+1 to hardware failure:

2 different operating systems(Vista and Linux), both fail after a time of use.

HDD is my favorite horse in this race (HDD gets all straightened out after a nice soothing format, then bad sectors start puking again; ram would present itself all the time); that said, it could still be a bad ram chip, but my monies on the hard drive.

---

### Post by philinux on 2008-11-17
Have a look in the file

/var/log/messages

Scroll down and look for any read/write errors. This would indicate failing hard drive. 

If no errors then do the memtest from grub or pull out the memory and reseat it. At the same time clean the inside of the case, could also be overheating.

---

### Post by hyper_ch on 2008-11-17
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by CatKiller on 2008-11-17
> **detroit/zero said:**
> Drivers not functioning correctly would make it a software problem.

Not necessarily. It could be firmware. And it would still be hardware-related, which is what I said.

> Having said that, I'll continue to try and give the guy options that don't include him running out the door and dropping a couple hundred bucks on service/new hardware before it's absolutely necessary.

He doesn't need to buy new hardware yet. He just needs to test the hardware he's got. Replacing hardware without isolating what's wrong is likely to just be a waste of money.

---

### Post by handydan918 on 2008-11-17
> **detroit/zero said:**
> Yeah, that is a valid point. Hardware failures do happen, true. I've spent some time doing component-level electronic repairs, and I've seen firsthand what can happen.. But come on. When's the last time you junked a computer just because Windows crapped out on you?Ummm, let me think....


Never?>  ( And - can I have the next one you throw away? I'll even pay for shipping :))Sure! i have a real nice PII here with 96 megs of pc66sdram....real screamer. It already has a Linux firewall/router disto on it...Shipping should come to about 3 times it's value if you live across the street from me...> 

[Check his model number on Amazon]("http://www.amazon.com/Sony-VGN-C240E-Laptop-Processor-Premium/dp/B000M5ND4S/ref=cm_cr_pr_product_top/181-2000735-1726209").. That's practically a brand-new laptop. And again, yes, a hardware fizzle is more bound to occur in the first couple weeks off the shelf than in the long run, but I'm assuming OP has been plugging away with Vista for some time now?

Plus, a hard drive dying out is not very likely to cause recurring display problems at two-week intervals.

_**EDIT:**_ Well, after looking at the user reviews on Amazon, I guess that model is going on two years old. One of the reviews even specifies a hard drive that had to be replaced twice because it died.

It is important to remember that "Not very likely" or "One in a million" don't mean squat on a forum with this kind of trafiic. The unusual happens every day.


The impossible just takes a little longer...

---

### Post by detroit/zero on 2008-11-17
> **CatKiller said:**
> Not necessarily. It could be firmware. And it would still be hardware-related, which is what I said.
That's not what you said, and by that definition anything that could ever possibly go wrong with any aspect of a computer is hardware related.

Can't read a CD you just burned? CD drives are meant to read CDs.. Must be a hardware problem.

Does your screen flicker when you turn on 3d compositing? Screens aren't supposed to flicker when you do that. Must be a hardware problem.

Can't get your extra mouse buttons to work? Mouse buttons are supposed to work.. The configuration for that mouse is stored in a file that is located *inside a hard drive* - Must be a hardware problem!

Whatever. Since we haven't heard back from OP, I'll go ahead and assume all his faulty memory and that bad hard drive finally went out on him. Hopefully, when he goes out and buys new RAM and a HDD, it'll fix his **intermittent display problem**.

---

### Post by CatKiller on 2008-11-17
> **detroit/zero said:**
> That's not what you said,

That **is** what I said:

> **CatKiller said:**
> Contrary to detroit/zero's assertion, most lockups are hardware-related in one way or another. Even in Windows.

>  and by that definition anything that could ever possibly go wrong with any aspect of a computer is hardware related.

Can't read a CD you just burned? CD drives are meant to read CDs.. Must be a hardware problem.

Does your screen flicker when you turn on 3d compositing? Screens aren't supposed to flicker when you do that. Must be a hardware problem.

Can't get your extra mouse buttons to work? Mouse buttons are supposed to work.. The configuration for that mouse is stored in a file that is located *inside a hard drive* - Must be a hardware problem!

Whatever. Since we haven't heard back from OP, I'll go ahead and assume all his faulty memory and that bad hard drive finally went out on him. Hopefully, when he goes out and buys new RAM and a HDD, it'll fix his **intermittent display problem**.

You know you're being silly now. Hard lock-ups (and this **is** a hard lock-up - see the stuttering sound when it's crashed) are quite distinct from a poorly configured mouse.

As far as I can tell, you aren't that experienced with hardware problems, and you don't seem to like Ubuntu much. Hardware issues can manifest in lots of different ways, and you'll learn to spot them as you get more experience with flaky hardware. Or you'll never experience flaky hardware, in which case you'll be very lucky.

As you say, we haven't had a progress report from the OP, so let's just leave it at that.

---

### Post by egalvan on 2008-11-17
> **detroit/zero said:**
> , and by that definition anything that could ever possibly go wrong with any aspect of a computer is hardware related.

[I]Can't read a CD you just burned? CD drives are meant to read CDs.. Must be a hardware problem.
[/I]
[I]Does your screen flicker when you turn on 3d compositing? Screens aren't supposed to flicker when you do that. Must be a hardware problem.
[/I]
*Can't get your extra mouse buttons to work? Mouse buttons are supposed to work.. The configuration for that mouse is stored in a file that is located [I]inside a hard drive* - Must be a hardware problem!
[/I]
*it'll fix his **intermittent display problem***.

It's hilarious, but I've had these EXACT problems, and they turned out to be HARDWARE problems...:lolflag:

Bad CD burns? caused by a bad RAM stick...

Running text was no problem, but running graphics crashed the machine? bad caps...

Intermittent display problems? Bad hard drive cable.

Even funnier?

"Windows runs fine" (as far as that goes) was a constant on the problem machines...
the problems cropped up under LINUX ONLY :lolflag:

I'm convinced that Windows glosses over hardware problems...which may explain it's lousy performance.
Linux seems to demand properly operating hardware.

I purchased my first computer in 1980, new.
I have not purchased a new one since... only used/abused.
Even almost-new, because the owner was tired of Windows crashes, and decided to buy a new computer. (vicious cycle, that).
Windows ME was a bonanza for me... to a smaller extent Vista.

So I have seen my share of HARDWARE PROBLEMS, SORRY.

Bad hardware gives me unstable Windows.
Good hardware gives me unstable Windows.

Bad hardware gives me unstable Linux.
Good hardware gives me good, stable Linux.

It's a no-brainer for me. I use Linux, and make a fortune supporting Windows "problems".

ErnestG

---

### Post by detroit/zero on 2008-11-17
Yeah, hey, whatever.

I'm not saying it ain't possible.. I'm just saying it isn't my first guess. This guy says his display cuts out, and you people are all saying bad RAM and he needs a new hard disk.

It's not like I've never seen hardware go bad - I'm a 33 year old electrical engineer. I've repaired industrial equipment - including power supplies, PLCs (which are just small computers), and CRT & LCD displays - for over 5 years. I've spent the better part of two doing warranty work for a company that repairs defective Toshiba, Acer, and Sony laptops.

I guess if/when OP comes back and drops us a line, we'll know what it ended up being.

---

### Post by kansasnoob on 2008-11-17
> **detroit/zero said:**
> Yeah, hey, whatever.

I'm not saying it ain't possible.. I'm just saying it isn't my first guess. This guy says his display cuts out, and you people are all saying bad RAM and he needs a new hard disk.

It's not like I've never seen hardware go bad - I'm a 33 year old electrical engineer. I've repaired industrial equipment - including power supplies, PLCs (which are just small computers), and CRT & LCD displays - for over 5 years. I've spent the better part of two doing warranty work for a company that repairs defective Toshiba, Acer, and Sony laptops.

I guess if/when OP comes back and drops us a line, we'll know what it ended up being.

Two things you're leaving out of that DX:

#1: Vista failed!

#2: He reinstalls and things work for a day or two!

I'd be suspect of an overloaded power supply! Yeah, seriously! It's quite common for even high-end computer builders to use a power supply that's barely capable of supporting the pre-installed hardware.

Given that a single GB of RAM eats as much as 70 watts, increasing a 512mb mem system to 2GB can easily push a power supply past it's intended limits!

Then consider adding a higher end graphics card!

Sadly by the time folks find their power supply sucked they've usually killed many more components!

---

### Post by the_fury on 2008-11-17
> **detroit/zero said:**
> I like how everybody is quick to point to a potential hardware failure when Ubuntu doesn't work right.

It's not that I don't love Ubuntu and use it every day, but come on - this OS has a good share of bugs in it yet, as is evidenced by the hundred and seventy seven million threads in these forums.

How often do you people *see* actual hardware failures, anyway? I mean personally; on something you own. I've owned probably 50 different computers starting in 1986 with a Commodore 64. The only - **only** - hardware failure I ever saw happened when I spilled a big bowl of chicken-noodle soup on my Amiga 500 back in 1990. I'm not saying they never happen, but not every flaw in someone's Ubuntu experience is due to a hardware failure.

Having said that... I don't know, fury, if you've done multiple re-installs and keep coming back to the same problems. Have you tried Kubuntu? Any other distros? It's definitely a compatibility issue... How does the live cd work for you? Are these problems reproducible? That is - is it the same set of problems every time, or is this just what's going wrong this time?

If you're computer's Vista capable, it should darn well run Ubuntu. Since your biggest problems are display related, are you using any proprietary divers? ATI? NVidia? Are you using Compiz fusion?

_**EDIT:**_ I see from some of your other posts that you're using the 64-bit version. Are you sure that's the right version for you? Run this in a terminal:```
cat /proc/cpuinfo
```Near the bottom, in the "flags" section, you're looking for [COLOR=Red]**lm**[/COLOR].

I just found that in a [google search]("http://www.google.pl/search?num=20&hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&q=how+to+tell+if+i+have+64+bit+processor+linux&btnG=Search"), but it seems to hold true. Me, for example:```
zero@zero-laptop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 14
model name    : Genuine Intel(R) CPU           T2080  @ 1.73GHz
stepping    : 12
cpu MHz        : 1733.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon bts pni monitor est tm2 xtpr
bogomips    : 3462.04
clflush size    : 64
```The info is repeated for my second core, but I know I have a 32-bit processor, and my stats are listed without the lm flag. Maybe someone with a definite 64-bit processor can come by and verify this?



Thanks a bunch. Yes, I do have "lm":

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arc

I tried to run a 64-bit, and it worked for about a day, then failed. So I switched back to the old 32-bit, and works better [doesn't work, but works better] .

I used to use compiz-fusion, but disabled it because I would just have to install it again next time I installed the OS [average timespan: 3 days]

My graphics driver -- that would be a:

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I don't know why everyone else seems to have "NVIdia" and "ATI" graphics drivers, when this is all I have. =(

Yes, my computer came [and was "designed for"] Vista. However, that was a mistake, as it repeatedly shot me with "explorer not responding", a relaunching of the "explorer" program, and lather, rinse, repeat.

No, I haven't attempted any other distributions - perhaps that will be what I do then I will buy a new hard drive -- I really like my VAIO. =)

---

### Post by the_fury on 2008-11-17
> **PierreDeKat said:**
> I just replaced my hard drive last week, as a matter of fact. And that's exactly what I think your problem is, as well.

I, too, suspected Ubuntu, and even [filed a bug]("https://bugs.launchpad.net/ubuntu/+source/seamonkey/+bug/290857") about a problem I was having with Seamonkey.

It should have been a big tip-off for me that this supposed bug was so erratic. 

Anywho, after a couple weeks thinking there was a bug in Seamonkey, I was rebooting my computer, and my [BIOS threw up a message]("http://en.wikipedia.org/wiki/S.M.A.R.T.") that I needed to back up any data on my primary drive because it was about to crap out on me.

I dropped in a new hard drive, reinstalled Windows and Ubuntu, temporarily plugged in my old hard drive and dragged over everything I needed from the old drive. Then I reformatted it and dropped it in my trash can.

Guess what. No more quirky error messages in Seamonkey.

The fact that your Windows Vista crapped out on you, and now Ubuntu is crapping out on you should be a big tipoff.

Thanks! Know anywhere where you can get hard drives cheap? Preferably 250GB, that's what I have now..

---

### Post by the_fury on 2008-11-17
I disassembled the back [or bottom] of my laptop...

But there is a big tamper-guard across the RAM. So I reseated it however I could. However, if the problems appear one more time, I think I may just take Pierre's advice and get a new hard disk.

That said, does anyone know where to get hard drives cheap? =)

---

### Post by PierreDeKat on 2008-11-18
> **the_fury said:**
> Thanks! Know anywhere where you can get hard drives cheap? Preferably 250GB, that's what I have now..
I've had pretty good luck with [Newegg]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=380&name=Laptop-Hard-Drives"). You can sort things according to brand or price range or whatever. And generally you get your stuff in about a week, depending on their supply.

---

### Post by rubbsdecvik on 2008-11-18
While I too think this sounds like a hardware problem (I've had two harddrives go bad on a laptop before, and I worked as a repair technician at the time, I know how to test for this stuff), I think there are some options that can be tried before the OP goes off and spends a lot of money.

I would see if it is a bug with Ubuntu by trying a different distribution.  Something not based on Debian if possible (like Fedora or OpenSUSE).  If the system works without problems for a few weeks, then we know it's a problem with Ubuntu (or even any Debian based OS).  If it doesn't work, then I would be inclined to say it's a Hardware issue.  If three different OS's don't work, then something is usually up.  Occam's Razor: if there is two possibilities, the simplest one is probably the right one.

That said, you can usually get the hardware tested.  You can try doing this yourself (if you're fairly tech savy there are some Linux LiveCD's that have harddrive testing tools) or go to a repair shop and have them test the hardware( make sure you say test only, if you don't want to buy something right away).

---

### Post by CatKiller on 2008-11-18
> **the_fury said:**
> No, I haven't attempted any other distributions - perhaps that will be what I do then I will buy a new hard drive -- I really like my VAIO. =)

As detroit/zero says, there's no point buying anything until you know that it will fix it. The memory and hard drive tests are free. Power supply tests will be problematic since it's a laptop - normally it's a multimeter job - but I don't know how easy it would be to replace the power supply in a laptop anyway.

Potentially, the memory might just have jiggled loose. There should be instructions somewhere on the Internet for your laptop model that will show how the memory should be seated.

---

### Post by Sorivenul on 2008-11-18
> **CatKiller said:**
> As detroit/zero says, there's no point buying anything until you know that it will fix it. The memory and hard drive tests are free. Power supply tests will be problematic since it's a laptop - normally it's a multimeter job - but I don't know how easy it would be to replace the power supply in a laptop anyway.

Potentially, the memory might just have jiggled loose. There should be instructions somewhere on the Internet for your laptop model that will show how the memory should be seated.

+1 to this.  

I have a VAIO (VGN-FS980) and it had a major HD failure.  I ran a few different diagnostic tests via the Ultimate Boot CD.  Of course, mine was indicated thanks to SMART originally, so I already had a good idea of what the problem was.  Bought a new HD, replaced it, no problems since.  

In short, run your tests, but you're not the only VAIO user with hardware problems.

---

### Post by the_fury on 2008-11-18
All right, newest update:

I am now inclined to think this is a hard drive problem: I've been running Kubuntu for all of 1 1/2 days, and it's already failed once. Sooo... I should probably get a new HD. I don't see any other reason why all these problems would repeat themselves so.

But as 1 FINAL step, please someone give me the link to this "Ultimate Boot CD" that can check my hard drive. 

Thank you all.

---

### Post by metallicamike on 2008-11-18
> You'll often get mechanical noises when they're failing. Clicking can be especially bad.

uh oh, thats not good for me then :(

---

### Post by Sorivenul on 2008-11-18
> **the_fury said:**
> But as 1 FINAL step, please someone give me the link to this "Ultimate Boot CD" that can check my hard drive.

[Ultimate Boot CD]("http://www.ultimatebootcd.com/")

For good measure read the Tutorials and FAQ before using it.  Good luck, and let us know how it goes.

---

### Post by CatKiller on 2008-11-19
> **metallicamike said:**
> uh oh, thats not good for me then :(

To be fair, it **can** sometimes be a sticky arm. In which case, the hard drive is knackered, but the data is safe.

The heads float on an incredibly thin layer of air, a minute distance from the mirror-smooth magnetic surface of the platters. If the power gets interrupted because of dodgy circuitry, or it's become mis-aligned, the heads smack into the platters, destroying any data that might have been there, damaging the surface of the platter, and probably not doing much good to the head. This is the Click of Death. Sometimes you might hear a quiet ascending hum afterwards as the platters spin up again. Often the fact that this has happened once causes it to happen again, so you get an exponential increase in frequency over time.

The fact that random chunks of data are no longer reliable means that all sorts of things can go weird. That chunk of data might have been part of the kernel, or your graphics driver, or your printer driver, or some critical library for your Desktop Environment. Or it might have been one of the files in your music collection, so some of your songs develop glitches that they never had before.

Hard drive failure is **horrible**, and as I mentioned earlier, hard drives are often the first component to break since they are the most fragile and are made so cheaply. Remember, kids, keep your backups current.

---

### Post by the_fury on 2008-11-19
> **Sorivenul said:**
> [Ultimate Boot CD]("http://www.ultimatebootcd.com/")

For good measure read the Tutorials and FAQ before using it.  Good luck, and let us know how it goes.

I ran the memtest86+... and I left it on all night. It went through 62 passes before it told me that there were no errors. So I'm thinking that perhaps the hard drive doesn't know it's damaged, or that it's still not the hard drive [which i find unlikely].

New: I've been trying to find some correlation between these failures, and I thought it had something to do with flash. However, I was in the middle of typing a report and it suddenly shut down. Meaning... it most likely is hard drive failure. I'm browsing Newegg.com as we speak... looks like a nice site.

Anything else that is constructive is appreciated.

---

### Post by philinux on 2008-11-19
See post #12 and have a look in dmesg.
Just type dmesg in a terminal. Scroll back through the message and look for read/write errors.

---

### Post by Sorivenul on 2008-11-19
> **the_fury said:**
> I ran the memtest86+... and I left it on all night. It went through 62 passes before it told me that there were no errors. So I'm thinking that perhaps the hard drive doesn't know it's damaged, or that it's still not the hard drive [which i find unlikely].

New: I've been trying to find some correlation between these failures, and I thought it had something to do with flash. However, I was in the middle of typing a report and it suddenly shut down. Meaning... it most likely is hard drive failure. I'm browsing Newegg.com as we speak... looks like a nice site.

Anything else that is constructive is appreciated.

Follow the advice above and check dmesg for errors.  Also note, memtest86+ tests RAM, not your HD, AFAIK, and correct me if I'm wrong.  Some of the other tools on UBCD may be of more help in the HD diagnostics, pending no progress after reading dmesg.

---

### Post by Zill on 2008-11-19
> **the_fury said:**
> I ran the memtest86+... and I left it on all night. It went through 62 passes before it told me that there were no errors. So I'm thinking that perhaps the hard drive doesn't know it's damaged, or that it's still not the hard drive [which i find unlikely]...

Err, I think you will find that memtest86+ only tests RAM, not hard drives!

[http://en.wikipedia.org/wiki/Memtest86]("http://en.wikipedia.org/wiki/Memtest86")

---

### Post by the_fury on 2008-11-19
> **Sorivenul said:**
> Follow the advice above and check dmesg for errors.  Also note, memtest86+ tests RAM, not your HD, AFAIK, and correct me if I'm wrong.  Some of the other tools on UBCD may be of more help in the HD diagnostics, pending no progress after reading dmesg.

OK, here is the one error I could find:

[   14.793690] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).                                                                          
[   14.793882] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).                                                                          
[   14.793885] uvcvideo: Failed to initialize the device (-5)

And yes, I can see that memtest tests RAM. But all of the diagnostic tests for my hard drive are designed solely for windows, not for linux. Help?

---

### Post by the_fury on 2008-11-19
OK, the situation has become more serious. I was more confident that Ubuntu would work now, but no dice. It took it 5 minutes to die, and the symptoms are the same:

Scroll Lock + Caps Lock + WLAN blinking,
a noise of something repeatedly thud-thud-thud....

I'm browsing for a new hard drive, but where can I get it installed? I've looked inside my computer.... it wouldn't be easy.

Suggestions? I'm desperate now... Thanks.

---

### Post by rubbsdecvik on 2008-11-19
The blinking lights are probably an indicator of some hardware malfunction.  Check your manual for what it means, or check the internet.

---

### Post by Sorivenul on 2008-11-19
> **the_fury said:**
> OK, here is the one error I could find:

[   14.793690] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).                                                                          
[   14.793882] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).                                                                          
[   14.793885] uvcvideo: Failed to initialize the device (-5)
These errors appear to be related to a webcam or like device, not your hard drive. 

Run some of the diagnostic tools from UBCD - they can test for bad sectors, not necessarily filesystem integrity, so running Linux shouldn't matter.  However, with the "thud, thud, thud" you describe, it sounds like it really could be your HD.

---

### Post by alphacrucis2 on 2008-11-19
> **the_fury said:**
> All right, newest update:

I am now inclined to think this is a hard drive problem: I've been running Kubuntu for all of 1 1/2 days, and it's already failed once. Sooo... I should probably get a new HD. I don't see any other reason why all these problems would repeat themselves so.

But as 1 FINAL step, please someone give me the link to this "Ultimate Boot CD" that can check my hard drive. 

Thank you all.

The hd manufacturers often provide a DOS based diagnostic software option that runs from a bootable floppy or CD. The first step is to download a program from their website that creates these bootable DOS based diagnostics. Unfortunately, the download that creates these is probably a Windows program but you could perhaps get a friend to download and create the diagnostic floppy/CD from their Windows machine, which you can then use to boot your laptop and run the hd diagnostics.

---

### Post by the_fury on 2008-12-10
OK, this thread may have been closed, but no longer: After 4 subsequent re-installations of Ubuntu 8.10, I got the blinking lights again. And I thought we were done with them. =(

I am confused as to determining a trigger for this event. For example, these are the number of things I was doing when this happened:

Watching a youtube video
Editing (gedit) in the Terminal
Typing a paper
Opening Firefox
Adjusting Evolution settings
Installing Flash

These don't seem to have any correlation and I don't know why this is happening. Since I've installed Ubuntu, the manufacturer refuses to help me. I'm at a loss as to what I should do, since it only happens once in a while.

---

