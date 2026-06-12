---
title: "Application Protection and Trial"
date: 2011-05-31
forum: Programming Talk
---

### Post by jfreak53 on 2011-05-31
My company is looking at porting some of our commercially available software to linux here in the next month or so. In that lies the problem that we have been using for years now, EXECryptor on our windows software to create the hack protection and also trialware software.

This being said I have just spent about an hour looking through google and cannot find a program like EXECryptor for linux. Something that will pack my application file into obfuscated code and also create trialware out of it.

Does anyone know of software like this for the linux platform?

We are programming in Pascal by the way, don't think it matters since I don't really need something inside pascal, but an external app to encapsulate my software like EXECryptor for windows does.

Thanks.

---

### Post by JupiterV2 on 2011-05-31
Therein lies the problem with porting Windows ideas to Linux. While porting between operating systems can be a task in of itself, Linux is based on FOSS (Free and Open Source Software). You will have a hard time finding applications which create a hostile environment for this mindset. Obfuscation of code and locking software is frowned upon by many in the Linux world. I'm not going to say its not possible but you will have a difficult time.

---

### Post by SevenMachines on 2011-05-31
I've heard of stunnix stuff being used on linux, but no idea how good/relevant itll be for you.

---

### Post by Zugzwang on 2011-05-31
@OP: I wonder how much your request makes sense in Linux. While your EXECrypter might make disassembling the executable harder, it's no problem in Linux to create a memory dump of the application at runtime and just disassemble the code found there (where it will not be encrypted), as the root user can just read out the data from the "/proc" filesystem.

Also, as far as evaluation copies go, it's absolutely no problem to create a chroot environment in which your application is running, and just restore it to the original content before every execution of your program. This way, your program will always think that it is executed for the first time. If it is acceptable for you to require your users to have internet connection while running the evaluation copy, you can just have some task done on a server instead and let every evaluation copy of the program connect to it. Then, using user accounts and closed-source server software, you can control how long a copy of the program can be used.

To sum it up: circumventing something like executable encryption is so easy on Linux such that everyone who can read a disassembly is equally able to circumvent your counter-measures such that can just ship the unencrypted executable (strip the debug symbols first, though).

---

### Post by DangerOnTheRanger on 2011-05-31
I'm sorry to say this, OP, but everyone who's posted in this thread is correct: DRM/trial-like software is not well-loved in the Linux world. Besides, it's kinda counter-intuitive to make an open-source executable obfuscation scheme, or an open-source DRM implementation.

---

### Post by jfreak53 on 2011-06-12
Thank you for your input but OUR customers have been asking for our software for linux for quite sometime now, so you must be wrong.  And I wasn't really looking for an Open Source software to do the trial ware with, I am willing to pay.  But again thanks for your input.

---

### Post by juancarlospaco on 2011-06-12
There are methods to make something like that on the code itself, 
so you dont need relevant modifications on the program for any platform.

Like a Watchdog timeout*-er*...  I only know Python, but this is the thingy:

```
try:
  with Watchdog(120):
    MyApp()
except Watchdog:
  print "MyApp() got 120 Seconds Timeout..."
```

---

### Post by slavik on 2011-06-13
why don't you do what people have been doing a long time ago, make a branch of your code and remove functionality so that the only thing left is some basic functionality.

---

### Post by jfreak53 on 2011-06-13
> why don't you do what people have been doing a long time ago, make a branch of your code and remove functionality so that the only thing left is some basic functionality.

I would but most of our software is basic to begin with and cheap.  Not much to take away really.  And some of it there really is nothing at all to take away, it does only one function type thing.  Thanks.

---

### Post by JupiterV2 on 2011-06-13
What about implementing a "call-home" style system? It wouldn't let offline users from using the trial version but I doubt, in this day and age, that that is really a limitation.

Is the software you're developing so novel that code obfuscation is really necessary? Have you developed unique algorithms which would be difficult to duplicate?

---

### Post by DangerOnTheRanger on 2011-06-14
> **jfreak53 said:**
> Thank you for your input but OUR customers have been asking for our software for linux for quite sometime now, so you must be wrong. 

I'm not trying to start a flamewar or anything, but what makes you think that proprietary software is well-loved in the Linux world because *one *company (or group of people) wanted proprietary Linux software? Besides, are you sure they care that your software is proprietary? Given a choice between open-source and proprietary software with identical abilities, any company in the world is going to go with open-source.

> **JupiterV2 said:**
> 
Is the software you're developing so novel that code obfuscation is  really necessary? Have you developed unique algorithms which would be  difficult to duplicate?

Good point. Why not do what Red Hat does: keep the software itself free (and possibly open-source), and charge for installation and support? Red Hat's a *multi-million* dollar company, so they got something right here.

---

### Post by PaulM1985 on 2011-06-14
> **DangerOnTheRanger said:**
> I'm not trying to start a flamewar or anything, but what makes you think that proprietary software is well-loved in the Linux world because *one *company (or group of people) wanted proprietary Linux software?

Ubuntu has added a "For Purchase" section in the software centre.  Someone must want it.

Paul

---

### Post by 3rdalbum on 2011-06-14
DRM is distasteful to Linux users. If you attempt to create copy-prevention for your program, people will probably take pride in pirating it "on principle".

Just don't even try it.

---

### Post by DangerOnTheRanger on 2011-06-14
> **PaulM1985 said:**
> Ubuntu has added a "For Purchase" section in  the software centre.  Someone must want it.

Paul

It seems you're operating under the common misconception that FOSS=no cost. This isn't true. Even the GPL license states you can charge for your software (you can even charge for the source code).

Besides, Ubuntu is a Linux distro that caters in large part to former (non-technical) Windows users. They in all likelihood (at least for now) don't care about having freedom with their software, which is probably why Canonical added that section in the USC.

---

### Post by Thewhistlingwind on 2011-06-14
Lol. You guys....

1. Stop asking him to not put DRM on it, thats him and his company's decision.

2. The Redhat model only works if your program will actually have people call support that often. (An OS is the only thing I can think of that fits that criteria.)

3. I think that DRM poses a very interesting problem for both the user and the content provider. How does one make a DRM that can't be broken, but that the user can still authenticate to get to their content? I'm not really sure this balance is possible to do well.

4. Linux COMES with a disassembler, unfortunately your facing the most DRM hostile platform of them all. (Except the FreeBSD guys.)

5. Someone needs to write some utilities for that sort of thing.

---

### Post by DangerOnTheRanger on 2011-06-14
I never just said he could charge for support. He could charge for installation, as well.
Also, doesn't an open-source DRM implementation seem a little backwards to you?

---

### Post by JupiterV2 on 2011-06-14
Don't get me wrong, closed source/commercial software has its place. I have, and will continue to, purchase software. I don't think everything should be free. If someone feels their work is novel enough for people to pay for it, great! Lets be realistic, when you look at the cost of paying employees, overhead, marketing, etc, you're not going to want to give it away. You want to recuperate costs, and make a little profit, too.

My point was, unless there is a significant trade secret involved, does he really need the tools he's looking for? How much of a threat is reverse engineering to their success? Only he, and his bosses, can be the judge of that.

DRM is another subject. They want it because they want some guarantee they'll get paid. Like it or not, that's what they want. Really, I don't think I can blame them. If I spent a lot of money to make a product I'd like to get some dividends, too. If the tools don't exist on Linux already, they'll either need to create their own or suss out another method of achieving their goals. The Linux community, for the most part, is built on open-source technology. Being built on a premise of transparency, closed-source solutions aren't usually well received in our community. Still, they have their place. As Linux grows, so will the presence of commercial products, don't kid yourself. You will see more and more DRM coming to Linux.

---

### Post by ssam on 2011-06-14
why not talk directly to canonical. they have a system for selling closed source software through the software center. they may have a system that meets you needs.

---

### Post by Thewhistlingwind on 2011-06-14
> **DangerOnTheRanger said:**
> 
Also, doesn't an open-source DRM implementation seem a little backwards to you?

No, not at all. Such a implementation would be crossplatform and able to be used on all platforms in the forseeable future. It'd stop problems like netflix lacking Linux support.

Does DRM work? Hell no, do corporations see it as a necessary measure? Completely.

---

### Post by jfreak53 on 2011-06-15
No, it's not so much I need obfuscation, I need a trial system.  Our users are not savy enough to hack our software, they wouldn't even know where to begin.  That's the point.  Someone who is, would have ZERO use for our software.  That's why I was just looking for something to encapsulate it like EXECryptor does and makes it trial ware.

I think the only way I see of doing it is as you said, a web based trial ware. :(

---

### Post by juancarlospaco on 2011-06-15
You can encapsulate it with a self-extracting bash container

---

### Post by PaulM1985 on 2011-06-16
With your trial version you could install a file alongside that contained an encrypted expiry date.  If the trial program can't find the file or the date has expired then the trial would be expired.

Its a very simple system but since you said your users aren't overly savvy then it might work.

Paul

---

### Post by nvteighen on 2011-06-16
IMO, you should look for a security mechanism that reduces the risks to an acceptable minimum, but do never expect to find a way to completely eliminate all circumvention methods, known or unknown... There's always a weak spot in the execution of any program, which is that any chunk of code will have to be decrypted at some place in order to be executed. In the usual PC architectures, the weak spot is the memory. GNU/Linux just makes it easier to dump the memory, but it is just as possible in Windows or any other OS.

I won't get into the DRM debate, because it's not the point of this thread.

But I want you to realize this: if you want your port to GNU/Linux to be widely adopted (or as widely as possible), then you'll have to go the FOSS route. Here's the issue: the community only adopts a propietary software if and only if there's no other choice... and immediately, people will start developing FOSS clones. As soon as a clone reaches an acceptable state, your closed-source program will have no chance against it. The only way you'd have to stop it is by filing a patent beforehand and then suing the developers of the clone.

In fact, this is happening with Skype. There's an official closed-source Skype port, but there are a couple of clones being developed.

On the contrary, if you just want to port your program for a specific group of people, with no intention of "entering the GNU/Linux market" then go for it.

Yep, operating systems involve a culture or a certain way of things. In GNU/Linux, people want high quality software they can contribute them (no, costs are not the real thing). In Windows, people want easy non-technical solutions.

---

### Post by JupiterV2 on 2011-06-16
> **PaulM1985 said:**
> With your trial version you could install a file alongside that contained an encrypted expiry date.  If the trial program can't find the file or the date has expired then the trial would be expired.

Its a very simple system but since you said your users aren't overly savvy then it might work.

Paul

I was thinking the exact same thing. Place it somewhere, perhaps in /etc or within a user's home directory, and don't remove it if the application is uninstalled. I, personally, HATE it when applications leave garbage behind but its a solution non-the-less.

---

### Post by KdotJ on 2011-06-16
> **JupiterV2 said:**
> I was thinking the exact same thing. Place it somewhere, perhaps in /etc or within a user's home directory, and don't remove it if the application is uninstalled. I, personally, HATE it when applications leave garbage behind but its a solution non-the-less.

I agree with this idea as well, seeing ad you said your users wouldn't be able to "hack" it. If you hide the file, as well as encrypt the date (or the number of times it been run, if you go with a "x amount of runs trial") then your users would have a hard time changing this. However, you'd need to think about what would happen if a user were to reinstall the software, this file would get overwritten and then they have the full trial length again?

---

### Post by jfreak53 on 2011-06-16
> **JupiterV2 said:**
> I was thinking the exact same thing. Place it somewhere, perhaps in /etc or within a user's home directory, and don't remove it if the application is uninstalled. I, personally, HATE it when applications leave garbage behind but its a solution non-the-less.

Yeah it's a good idea, but I HATE it also when software leave CRAP behind in my computer and I WON'T do that to my users, ever.  I personally think it's horrible programming to leave stuff behind, it's not needed really.

So I don't think I want to go down that road.  Hearing all the ideas I think I am looking at a web based trial ware.  The good thing is that my software is used over the web anyways, so it's no use to a local system, so they would have to have internet anyways.

---

