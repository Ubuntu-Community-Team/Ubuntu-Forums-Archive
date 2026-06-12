---
title: "Should Linux be scared of GNU Hurd?"
date: 2010-04-05
forum: Recurring Discussions
---

### Post by dmaxel on 2010-04-05
I've been wondering this for a while now...I've read up a little on GNU Hurd, and want to know what you guys think: If the Hurd will eventually be mature and stable enough for a productivity environment, will Linux have to be concerned about it? Because personally I want to see Linux stay on top.

---

### Post by Dayofswords on 2010-04-05
not sure

let just remember its **IF** they finish it

its has been 20 years since they started

---

### Post by juancarlospaco on 2010-04-05
no

---

### Post by MooPi on 2010-04-05
FOSS does not control the Linux kernel so HURD exists. Richard Stallman needs a fall back if Linux splits with his wishes entirely. I would suggest that BSD has a greater chance of unseating Linux in the free OS realm. Just my humble opinion.

---

### Post by NightwishFan on 2010-04-05
I for one hope the project becomes successful. In the worst case competition breeds innovation.

Debian is going to create a Hurd port along with Linux:
[http://www.debian.org/ports/hurd/](http://www.debian.org/ports/hurd/)

---

### Post by perham on 2010-04-05
> **dmaxel said:**
> I've been wondering this for a while now...I've read up a little on GNU Hurd, and want to know what you guys think: If the Hurd will eventually be mature and stable enough for a productivity environment, will Linux have to be concerned about it? Because personally I want to see Linux stay on top.

if a free (as in freedom) kernel better than linux is made, I would use it instead of linux any day. it is the idea of freedom that is important. 

fanaticism != freedom

---

### Post by Paqman on 2010-04-05
Not really, Hurd is vapourware. Even if it was released, that's not anything Linux users need to worry about, any more than we should be worried about BSD.

---

### Post by YeOK on 2010-04-05
Linux has some major investment in drivers already included. Even when Hurd is ready for the public its not going to contain everything we have now come to expect from Linux. 

I'd be surprised if Hurd could ever catch Linux up.

---

### Post by ugm6hr on 2010-04-05
I would have that that potential opensource competitors would be OpenSolaris or BSD.

Can't imagine Hurd will ever be an issue.

---

### Post by steev182 on 2010-04-05
> **perham said:**
> if a free (as in freedom) kernel better than linux is made, I would use it instead of linux any day. it is the idea of freedom that is important. 

fanaticism != freedom

But Richard Stallman is the definition of Fanatical. He is basically an Open Source Extremist.

---

### Post by kellemes on 2010-04-05
> **dmaxel said:**
> Because personally I want to see Linux stay on top.

On top of what?

Anyway, without competition Linux won't be on top of anything anytime soon.

---

### Post by Penguin Guy on 2010-04-05
Until they change the name, I'm sticking with Linux.

---

### Post by NoaHall on 2010-04-05
> **Penguin Guy said:**
> Until they change the name, I'm sticking with Linux.

Yeah, cause that's a valid reason to be using a kernel or not.

Anyway, HURD is no good. If it was close to being stable at all, rms would use it. He does not, shows how much it sucks ATM. And yes, I have tried it.

In theory, it would be good, in practice, it's not going to be.

---

### Post by louis--taylor on 2010-04-05
no.
I would like to see how different it would be from Linux, with all of the gnome DE etc. I doubt If many linux users would be able to tell the difference.

---

### Post by blueshiftoverwatch on 2010-04-05
> **louis--taylor said:**
> no.
I would like to see how different it would be from Linux, with all of the gnome DE etc. I doubt If many linux users would be able to tell the difference.
As far as the GUI goes, booting up into Gnome, running GIMP, IMing people with Pidgin, etc. It wouldn't be any different from the GNU/Linux we use now.

But, the Linux kernal has it's finger in a lot of different pies that aren't readily visible. For example, video & sound drivers. Everything that currently uses the Linux kernal as a dependency would have to be radically changed to take advantage of the HURD.

Not only is the HURD a different kernal. It's a completely different kernal design. Linux is a singular towering monolithic monstrosity while HURD is a whole bunch of little applications that communicate to each other. It's like the difference between English and Mandarin.

---

### Post by 3rdalbum on 2010-04-05
> **blueshiftoverwatch said:**
> As far as the GUI goes, booting up into Gnome, running GIMP, IMing people with Pidgin, etc. It wouldn't be any different from the GNU/Linux we use now.

But, the Linux kernal has it's finger in a lot of different pies that aren't readily visible. For example, video & sound drivers. Everything that currently uses the Linux kernal as a dependency would have to be radically changed to take advantage of the HURD.

The interesting thing is that the Linux desktop consists of systems-over-systems. Gnome, KDE and your regular programs can work on a BSD or Solaris system because they've been written to work with multiple backends for tasks, or the systems they use are designed to work with multiple OSes.

I mean, your desktop environment runs on X, which runs on all sorts of OSes. Your sound programs these days use Pulseaudio, which is being ported to BSD and therefore is not reliant on ALSA. Even your iPod connection functionality uses FUSE (Filesystems in User-Space) which could be ported to HURD without requiring the drivers themselves to be modified. You could practically replace the Linux kernel with kFreeBSD and next reboot not notice any difference :-D

The HURD is in no danger of becoming production-ready, and there are enough ways in which HURD is behind Linux to make it non-threatening. But it's good to have options.

---

### Post by ibuclaw on 2010-04-05
> **steev182 said:**
> But Richard Stallman is the definition of Fanatical. He is basically an Open Source Extremist.

If he believed in Open Source... which he doesn't.

---

### Post by gnomeuser on 2010-04-05
HURD is a mere joke, it doesn't have driver support and it's Microkernel implementation makes microkernel experts cry. The number of developers working on the project can be counted on one hand, whereas Linux has thousands of kernel developers.

Being scared of HURD is a bit like mankind being scared that butterflies will overthrow us using secret raygun technology.

It is a pointless project that is at best a hobby.

---

### Post by dmaxel on 2010-04-05
OK, so I guess the Hurd isn't really something to worry about and that although options are nice it probably won't be a good one. And what about kfreeBSD? What makes it so good and what differences are between it and Linux?

---

### Post by mickie.kext on 2010-04-05
> **steev182 said:**
> But Richard Stallman is the definition of Fanatical. He is basically an Open Source Extremist.

No he is not, and no he is NOT.

On topic:

Hurd is very nice project, but Mach sucks. I expect to see lot more development once L4 port is done. In practice, Linux can snatch code from HURD anytime(given that they rework it because architecture differ greatly), while HURD can not take code from Linux if contributor does not sign away copyrights to FSF (because that is the policy of FSF). So having HURD as competitor is few order of a magnitude better for Linux than having OpenSolaris (which is completely license incompatible, both ways) as a competitor. No reason to worry that HURD will stopm Linux. At all. It might turn out to be very good for Linux. 

The reason for fear can be some permissively licensed OS (like BSDs) taking lots of corporate development. If BSD surpass Linux, we might have UNIX wars all over again because there is nothing stopping corporations from changing license and making incompatible proprietary versions. 

RMS is not extremist. He is just wise to see danger before other see it. Bad news is that shortsighted people call him crazy for that.

---

### Post by forrestcupp on 2010-04-05
> **MooPi said:**
> I would suggest that BSD has a greater chance of unseating Linux in the free OS realm. Just my humble opinion.That statement is true.  And since BSD doesn't have a snowball's chance in hell to unseat Linux, what does that tell you about HURD?

> **steev182 said:**
> But Richard Stallman is the definition of Fanatical. He is basically an Open Source Extremist.
Don't tell RMS that, if you want to live to see tomorrow.  He's a Free Software extremist. ;)

---

### Post by gnomeuser on 2010-04-05
> **dmaxel said:**
> OK, so I guess the Hurd isn't really something to worry about and that although options are nice it probably won't be a good one. And what about kfreeBSD? What makes it so good and what differences are between it and Linux?

Largely kfreebsd is a better choice than HURD merely because it is more complete and actually present a working kernel on many systems today. It is the kernel from FreeBSD lovingly fitted into a Linux userspace using an appropriately sized hammer.

It is however slower than the Linux kernel in many respects and has less driver coverage. Again you have the problem that Linux has lots of people working on it and FreeBSD has comparatively few. 

That being said I have run FreeBSD in the past and as a system while not as suitable for a desktop system as Ubuntu is it is a fine system. Their documentation is quite excellent and I wholeheartedly recommend reading the FreeBSD Manual to anyone wanting to learn general UNIX tricks.

---

### Post by donkyhotay on 2010-04-05
Who cares if BSD or HURD push linux out of the way? With FOSS software it's usually pretty easy to port/recompile. If HURD suddenly had a breakthrough, became the best FOSS OS on the planet and there was a mass migration to it, I'd probably just migrate along with everyone else and continue using my favorite programs. FOSS is all about choice, the reason so many different FOSS kernels and distro's exist is because they cooperate with each other and work well together. There is no need for linux to 'fight' with BSD, HURD, plan9 or any of the others. If someone writes an improvement for one it will quickly spread through the others and improve them as well. Same thing with HURD and linux. I don't care what kernel I have running underneath everything, I do care about having an OS that I know will obey me rather then the company that made it.

---

### Post by bapoumba on 2010-04-05
Moved to You-Know-Where.

---

### Post by NoaHall on 2010-04-05
> **bapoumba said:**
> Moved to You-Know-Where.

Linsux.org?

---

### Post by bapoumba on 2010-04-05
> **NoaHall said:**
> Linsux.org?

You guys.. :D

---

### Post by kaldor on 2010-04-05
The Hurd isn't going ANYWHERE if they keep up the current pace. 

It's not that I wouldn't want to see a new free OS, it's just that the Hurd development is a mess.

OpenSolaris, *BSD and Haiku are the main FOSS competitors. I think Linux will always be on top, though. I can, however, see OpenSolaris catching up as a great Desktop OS in years. BSD will always stay with the more technical users/server/etc people; it's pretty much how it is meant to be. Haiku.. I don't know about. Haiku could either flunk totally or it could become really good and make a great media OS.

What would the "worry" be anyway? If Hurd surpassed Linux, wouldn't it be better to use a Hurd distro? It's not like talking about Windows/Mac/Solaris, it's just another *free of charge* OS that anyone can use if they want.

Edit: On that note, I'd like to say that I intend to switch to OpenSolaris in the future if they continue doing things the way Sun did in the past. Oracle is slack with it right now, but if it picks up and catches up with certain things, I will switch quickly. There are certain things in OpenSolaris that I just simply like more than Linux.

---

### Post by forrestcupp on 2010-04-05
> **NoaHall said:**
> Linsux.org?

******.org?

---

### Post by ibuclaw on 2010-04-05
> **forrestcupp said:**
> ******.org?

No, ************.org ;)

---

### Post by dmaxel on 2010-04-05
In case anyone is questioning this, yes, I guess I am feeling somewhat pro-Linux. However, I still love to see advancement in all free OSes. Its just that Linux has been working great for me and is advancing at a record pace. I just wish that Linux stays on top so that distros don't eventually change to a different kernel.

I hope you guys understand what I mean.

---

### Post by Simian Man on 2010-04-05
No.  Linux actually works and has intelligent people working on it.  Hurd, not so much.

---

### Post by MooPi on 2010-04-05
> **ibuclaw said:**
> No, ************.org ;)
Man do I wish I could read asterisk ;)

---

### Post by swoll1980 on 2010-04-05
Why be afraid of it? It would be great if it were finished, and worked, and was better than Linux.

---

### Post by Crunchy the Headcrab on 2010-04-06
Linux shouldn't be afraid of anything.  You should be afraid of Linux!  MWwahahaha.  I mean...no.

---

### Post by forrestcupp on 2010-04-06
> **MooPi said:**
> Man do I wish I could read asterisk ;)It's ubuntuforums.org. ;)

> **Crunchy the Headcrab said:**
> Linux shouldn't be afraid of anything.  You should be afraid of Linux!  MWwahahaha.  I mean...no.
Linux is the reason that Waldo is hiding.
Linux once roundhouse kicked a horse in the chin. Its descendants are giraffes.
Linux can divide by zero.
Linux CAN believe it's not butter.

Ha, ha, ha.  :)

---

### Post by blueshiftoverwatch on 2010-04-06
> **Simian Man said:**
> No.  Linux actually works and has intelligent people working on it.  Hurd, not so much.
*In short: just say NO TO DRUGS, and maybe you won't end up like the Hurd people.*
- Linus Torvalds

---

