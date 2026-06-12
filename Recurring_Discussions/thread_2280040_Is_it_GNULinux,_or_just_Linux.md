---
title: "Is it GNU/Linux, or just Linux???"
date: 2015-05-27
forum: Recurring Discussions
---

### Post by benrob0329 on 2015-05-27
[http://www.gnu.org/gnu/gnu-linux-faq.html](http://www.gnu.org/gnu/gnu-linux-faq.html)

But on the Linux Foundation's website, (and Wikipedia) they call Linux an OS, not just the Kernel...

:confused::confused::confused::confused:

---

### Post by mörgæs on 2015-05-27
When such a question is posted we often see a number of not-very-constructive posts bashing Stallman as the response. 
Maintaining a faint hope that people will refrain from that and focus on the topic this time.

---

### Post by QIII on 2015-05-27
The Linux Foundation and Linus call it Linux.

---

### Post by Copper Bezel on 2015-05-27
Which makes sense for them. It still causes unnecessary confusion. I think a lot of people think of Torvalds himself as somehow central in the GNU/Linux world, or "belonging" to it, and yet something like Android and something like Ubuntu each get exactly as much from the "Linux" effort, but only one of them is GNU/Linux. 

Isn't this a "recurring discussion"?

---

### Post by deadflowr on 2015-05-27
I wonder if you install adobe flash, or something like nvidia-current, if it can still be called gnu?
Or would we have to use a 3rd name like mostly-gnu/linux?

---

### Post by PhilGil on 2015-05-27
> **deadflowr said:**
> I wonder if you install adobe flash, or something like nvidia-current, if it can still be called gnu?
Or would we have to use a 3rd name like mostly-gnu/linux?

```
sudo apt-get install vrms
``` ;)

---

### Post by Copper Bezel on 2015-05-27
Well, it doesn't refer to the license, or you wouldn't have to say /Linux, either. I mean, that's also GPL. "GNU" is referring to an amorphous and ill-defined body of code.

---

### Post by benrob0329 on 2015-05-27
So, Linux isn't an OS???

Thats what i've known for the past few weeks, but shouldn't Ubuntu be called a GNU/Linux distro???

---

### Post by QIII on 2015-05-27
No.  It's purveyors call it a Linux distro.  If someone else wants to call their distro a GNU/Linux distro, that's up to them.

Torvalds used GNU tools to develop Linux.

Do you call your home a Hammer/House?

No.

There are a lot of bits of GNU software surrounding Linux.

Do you call your house a Siding/House?

No.

What I think causes the confusion is people going around with red faces, stamping their feet and shouting "It's GNU/Linux! It's GNU/Linux!" just because a GNU/Hammer was used in its construction.  Let them call it GNU/Linux.  It's up to them.  Just so it doesn't come to a scene at a dinner party if someone doesn't say GNU.

The whole "controversy" is silly.  You call it a tomato, I call it a to-mah-to.

---

### Post by Copper Bezel on 2015-05-27
It's complicated. 

"Linux" is used both to refer to the kernel and, less formally, to the operating systems that use it. Linux systems and Linux users definitely exist. We know what is meant by those phrases. The fact that they're *called *Linux systems or Linux users is more historical than anything to do properly with the Linux kernel.

Android and Ubuntu are both systems that use Linux. Ubuntu also uses GNU; GNOME, for instance, is a part of GNU. Debian, from which Ubuntu is packaged, was started by the GNU project. Everything that most users associate with "Linux" systems is more about GNU than it is about the Linux kernel. You could replace the kernel in Ubuntu with something else entirely and never know the difference. 

"Linux" nonetheless tells you a very little bit about the kind of system you're talking about. Most systems you'll ever see in the wild that aren't Mac or Windows really probably *are *running the Linux kernel, whatever else their operating systems contain. So it's a handy label. "GNU" would have been, too, given a different set of historical accidents. The first people to grab both parts, the middleware/shell environment/toolchain (GNU) and the kernel (Linux), and distribute the system, labeled it with the one name instead of the other, probably because it sounds better. 

GNU likes to have their name at least listed in describing the system. Even they acknowledge that there are others who could be on that list (like X11). I go the other way with it, personally - I just say I use Ubuntu (and Android) and avoid the whole trainwreck. 

Note that this is *exactly *correct - Ubuntu and Android are exactly the code they refer to. The label "GNU" doesn't describe the whole system, and neither does GNU / Linux / or GNU / Linux / X11 or whatever - it's still not an exact account of what Ubuntu ships with, nor is it true that Ubuntu uses *all *&#8203;components of those things. (Particularly the Mir blend!)

Edited to clarify.

---

### Post by DuckHook on 2015-05-27
> **Copper Bezel said:**
> It's complicated.I agree with your very complete and well-considered assessment. I don't agree that it's complicated. I've often wanted to make the same point to "GNU/linux" acolytes: that their arguments for "proper" attribution should, by their own logic, be extended to X11, and then onward to the DE and then the distro. This would give us the mouthful: Linux/GNU/X11/Unity/Ubuntu. And their reply&#8213;that a workable system can be assembled sans GUI but not sans GNU&#8213;is disingenuous: the average user does not run a CLI. In fact, a pure CLI is useless to the average user. Without the GUI, it is likely that MS would have completely dominated the computing landscape by now and Linux would have been consigned to the dustbin of history quite some time ago.

However, there is a place (and a use) for a short memorable single word that refers to the guts of the thing. And since it is, after all, the guts that we are talking about, it is perfectly logical to call it by the name of the kernel, since the kernel is its most fundamental and most irreducible unit.

Anyway, I am not about to make a religion out of it. I have no real beef with those who call it "GNU/Linux". If one wants to call it by this ungainly nomenclature, go nuts. My beef is with *their* making a religion out of it... *their* insistence that everyone else call it "GNU/Linux", a phrase that I find not only awkward and contrived, but ugly.

So, trainwreck or not, it's plain "Linux" for me.

---

### Post by Copper Bezel on 2015-05-28
Oh, yeah, it's pretty awkward as a term, and I definitely don't say GNU / Linux myself. I do think both "sides" have a pretty fair claim to being more "fundamental", though, which is where the real fuss is. We could all probably more or less agree that the display server, whether that's X11, Mir, or Wayland, is the next in line for fundamentalness (and half of GNU is on the other side of it, if you count GNOME.) The kernel's definitely and unquestionably the thing that makes the computer go, as it were, the first layer that needs to launch and the closest to the metal. And *because Linux is a monolithic kernel, *it's nearly irreducible. 

But ... yes, you can use GNU and Linux without X11, and deal with a CLI, and yes, you can run Linux without GNU or anything else on top and watch it blink or something. It's like asking which organs of your body are most essential. That's not really the point of the label here. What's more important to say is that you can use Linux without GNU or X11 by buying an Android handset, or that you can use GNU and Linux but not X by buying an Ubuntu one.

Linux is a kernel that's used in all kinds of environments, and embedded and mobile (GNUless, Xless) Linuxes probably outnumber the servers (X11less) and *dwarf* the desktop installs (with all three.) But when we talk about "the Linux user base," we don't mean people with Android handsets, people who use the internet and thus interface with Linux servers, or people who buy routers that invisibly use embedded Linux. We somehow mean a somewhat arbitrarily drawn set of people people running Ubuntu desktops, maintaining Redhat servers, or installing Rasbians that check the amount of Mt. Dew left in the fridge - that is, everything from ordinary desktop users to enterprise server sysadmins to homebrew embedded tinkerers, who are all interacting directly with the operating system that we sort of informally think of as "Linux." And the distinguishing bit of code in all *those* operating systems is still GNU.

---

### Post by sffvba[e0rt on 2015-05-28
*Thread moved to **Recurring Discussions**.*

---

### Post by benrob0329 on 2015-05-28
Ok, here's my $0.02:

First, I probably should have posted it there in the first place,

Second, after taking in everyone's comments, my opinion is that we should call it neither.

:o

The reason:

Ubuntu is an OS which uses the Linux kernel, running the set of tool released  by GNU as GNU OS,

However, Linux takes up considerably less of Ubuntu than GNU, however it is still an essential tool to the OS as a whole.

Neither GNU nor Linux would be considered a "Hammer" in the Ubuntu OS, that would be like saying that you built a hammer into your house, or that you used a piece of your house to built your house....

Still, I think it should be something like this:

**Ubuntu is an OS which uses the Linux Kernel and a set of core tools and libraries known as GNU along with the Unity desktop environment.**

---

### Post by QIII on 2015-05-28
Or ...

Ubuntu is Sheldon Cooper's favorite Linux-based operating system.

---

### Post by ZoiaGuyver on 2015-05-29
> **QIII said:**
> 
Torvalds used GNU tools to develop Linux.


Can we just clear up this, Linus Torvalds did not use any GNU tools to build the Linux Kernel, its written in C, assembly. The GNU tools were altered/hacked to work with the Linux kernel rather than built with it or for it.

The GNU has a clear policy on no binary blobs, as such even the Linux Kernel has to be "cleaned" as they put it for it to fit their GNU mandate. This results in the Libre-Linux kernel. The only true GNU kernel is Hurd and that has only support for i386.

The whole "we should call it GNU/Linux (GNU+Linux)" or whatever else is pushing the limits. The actual meaning of "Operating System" has been twisted and misinterpreted to include the "userland and software applications".

The [Operating System]("http://en.wikipedia.org/wiki/Operating_system") controls hardware and allows access to software resources. The only thing that relates to that as far as software goes is [C Programming Language]("http://en.wikipedia.org/wiki/C_%28programming_language%29"). Now people could argue (and many do) that the kernel is built with GCC (GNU C Compiler) and that Linux is nothing without the GNU tools, this is also a misconception. As stated before Linux can be ran without any GNU tools, it has even been compiled with Clang/LLVM. GNU on the other hand has difficulty running with any other setup bar Hurd (the Debian Kfreebsd which used the FreeBSD kernel and GNU userland is afaik the only project to have tried to port GNU to alternative kernels and has been working on it since before 2005).

People can choose to give GNU credit or not imho as for their part. But I would not feel right calling anything bar a distro that follows GNU policy closely (Trisquel) or was at some point funded by them (Debian) a GNU/Linux release. Ubuntu although being based on Debian is **NOT** a GNU/Linux distribution as it allows and even recommends the use of Proprietary Binary Blobs. Ubuntu is an Open Source project and uses the GPL/LGPL licences from the Free Software Foundation and GNU Project. I don't think this warrants it being called GNU/Linux, unless we are going to call it something really long to cover every other licence used.

Think I've rambled enough this guy does a great breakdown of it [Michael Lustfield I-use-linux-get-it-right]("https://michael.lustfield.net/rambling/i-use-linux-get-it-right")

Oh and take note that even with a "Pure" GNU OS only 13% of that are actually GNU Tools..

---

### Post by QIII on 2015-05-29
GCC?  That's not a GNU tool?  The GNU C Compiler?

He used that under minix (after porting it) in his attempts to compile the kernel while he was working on it.  That's the GNU hammer he used.  That doesn't make the product GNU.

Your point is correct, however.  Linux did not need GNU.  Any other tool set could have been used.  But after 31 years, GNU still does not have a HURD.

---

### Post by ZoiaGuyver on 2015-05-29
I didn't mean to say the GCC wasn't part of the GNU, if it seemed I did I apologise, I just meant that although it was the "first" to be used doesn't make it the only one that could have been used. If I remember correctly Bash and GCC were the first tools to be ported over and others quickly followed suit.

---

### Post by QIII on 2015-05-29
I agree that it was not the only thing he could have used.  Hence, my analogy to a GNU hammer.  It could as easily have been a Craftsman hammer.

It's just a historical accident.

---

### Post by Copper Bezel on 2015-05-30
> **ZoiaGuyver said:**
> Think I've rambled enough this guy does a great breakdown of it [Michael Lustfield I-use-linux-get-it-right]("https://michael.lustfield.net/rambling/i-use-linux-get-it-right") 
That's ... really hard to follow, particularly once he brings in the quotations without any indent or quotation marks to, like, mark them as quotes, and most of what he says is less correct than the statements he is attempting to respond to from the GNU site. 

> The [Operating System]("http://en.wikipedia.org/wiki/Operating_system") controls hardware and allows access to software resources. The only thing that relates to that as far as software goes is [C Programming Language]("http://en.wikipedia.org/wiki/C_%28programming_language%29"). 
Whoa, hold on. That line doesn't mean "access to resources for developing software." A machine doesn't need to be able to compile its own code to have an operating system. The phrase *is *ambiguous, but the most sensible interpretation I can take from it is "allows (application) software to access resources", that is, operates as middleware. 

More importantly, the operating system in the modern sense of the phrase absolutely is the whole mess, from the kernel and shell environment to the libraries and middleware and on up to the desktop interface and basic builtin utilities like file managers and so on. You definitely can't redefine it to something that would include less GNU.

Who used what to build what is also irrelevant. I mean, "X could have used another Y instead" carries little weight when Linux and GNU were the only games in town, but also just misses the point. I mean, that's an argument that the whole project of open source operating systems was set i motion by one and only one of these two groups. If that's the case, then a modern Debian running a (hypothetical) Hurd kernel would still be a "Linux," because that's what we call the operating systems that grew out of these things that happened in the late 80s and early 90s.

It's much less confusing to at least acknowledge that Linux is the name of the kernel and that we're describing operating systems by association - "those sorts of things that tend to use Linux kernels." "Linux-based" does that in a way "a Linux" does not.

---

### Post by benrob0329 on 2015-05-30
In that case, both The Linux Foundation and Wikipedia should be corrected...

---

### Post by Copper Bezel on 2015-05-31
They don't need to be "corrected," because their usage is both commonly understood and not *incorrect *by any particular authority's sayso. (Citing the Linux Foundation is really no better than citing the GNU project's opinions, but Wikipedia, as usual, correctly reflects common usage.) It is still misleading to treat any Linux-based OS as "Linux with some stuff on top" when the stuff on top is what we're really talking about 99% of the time, and equally misleading to call a system that runs a typical Linux-oriented desktop on top of a BSD or Hurd or whatever else kernel a "Linux" because it shares almost all of its most important components with these other things we call Linuxes. So those of us who have reason to should adjust our language to avoid confusion.

And the confusion is *not *hypothetical. My dad recently asked me why he hadn't seen any major Linux news lately on a software site he follows, and then mentioned not hearing anything about Linus Torvalds recently. That's a conflation that really did lead to confusion - I'm sure the site had covered recent developments in Android or Chromebooks to pace, and Torvalds is exactly as relevant to those as to new developments from Ubuntu or Redhat; the two comments are effectively unrelated, but my dad didn't know that. Or people will refer to an application or desktop as having a "Linux feel" - I've seen that lately here at UF. What they're referring to is a set of UI conventions common to GNOME-oriented applications; it's what most users of Linux-based desktop OSes are familiar with, but it's nothing to do with Linux qua the bit of code that handles all the hardware and all the processor scheduling and memory allocation and permissions assignment and so on for very nearly every piece of hardware more complicated than a digital watch that doesn't have an apple or a tetrachromatic flag on it.

---

### Post by benrob0329 on 2015-05-31
I think that both Linux and GNU should get credit in a system that "depends" on both...

---

### Post by Copper Bezel on 2015-06-02
Okay, but when a project is launched by GNU, and is a part of the GNU operating system, but distances itself from the GNU Project, is it still GNU? Is Kubuntu "less GNU" than Ubuntu vanilla? And we still have that question of just how many developers we're trying to "credit." Again, what about X/Wayland/Mir?

When we call Linux-based operating systems "Linux," we're implying a monolithic single identity like that of Windows or OSX. That isn't the case in anything Linux-based, because any Linux-based OS is depending on a number of separate projects with separate goals to keep it running and in development, and two Linux-based operating systems, say, Ubuntu and Fedora, really are different operating systems, even if a lot of the code is shared. Prepending "GNU /" doesn't solve any of that.

You'll never be able to properly credit everyone involved in the massive and multifaceted undertaking that is any particular Linux-based OS (save for cases, perhaps, like Android, where you really could just say Android / Linux and credit the exactly two teams responsible for the OS.) But you can avoid some ambiguity. For the moment, I think I'm sticking with "Linux-based OSes."

---

### Post by benrob0329 on 2015-06-05
The thing is, neither Linux nor GNU is an OS, but they are an essential part of the Ubuntu core. You couldn't have Ubuntu without either of them. (at least, not as we know it today)

Giving X11/Wayland/Mir credit is the responsibility of the DE, not the main OS. Those are also not essential parts of the system, just the DE.

Unity/GNU/Linux is my argument.

---

### Post by Copper Bezel on 2015-06-05
User-facing desktop elements, when present, are certainly considered part of the operating system in anything that *isn't *Linux based. Or conversely, just because they were CLI doesn't mean that many of the original GNU components weren't user-facing. So I'd say I'm using Ubuntu, which I'd describe as a Linux-based operating system using the GNOME desktop interface stack along with some bespoke interface components. I haven't mentioned X or GNU in there, but that's because they're implied in "Linux-based" when we're not talking about Android or embedded systems.

---

### Post by Harry_Riley on 2015-08-22
GNU/Linux

---

