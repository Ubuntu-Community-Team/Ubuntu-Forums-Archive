---
title: "Programming Firmware"
date: 2008-10-05
forum: Programming Talk
---

### Post by computer_freak_8 on 2008-10-05
Hello,

I was wanting to program custom firmware, but I have a couple of questions:

1. Does it matter what language? (I was thinking about using C or C++.)
2. Once I program it, how do I put it on the device? (Using "dd" comes to mind, but this doesn't seem quite right for some reason.)


Thanks,
computer_freak_8

---

### Post by snova on 2008-10-05
Choice of language means a lot. C would probably be the easiest as it can be meshed with assembly (which you *will* be using) fairly easily. C++ is mostly compatible, but you have to disable most of the extra features (leaving you with classes and templates as the only remaining features), and name mangling is a pain.

As for copying it to the device, it depends on what it is. dd probably won't help, you'll need specialized tools for that part of the job.

Out of curiosity, what are you programming?

---

### Post by computer_freak_8 on 2008-10-05
> **snova said:**
> As for copying it to the device, it depends on what it is. dd probably won't help, you'll need specialized tools for that part of the job.

Out of curiosity, what are you programming?

In reverse order:
I'm trying to achieve what I mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=938103"), among a few other things. My goal is to be able to have a flash drive that I can make look like different devices, depending on which firmware I load on, or I could just have it look like several devices at the same time. 
One (different) example (of many): Say I have friend that is really into digital photography. They have their camera's upload/management software on their computer. They get pictures from others on a flash drive of theirs. Instead of loading pictures from the flash drive onto the computer, and then (manually) importing them into their camera's management software, I could write a special firmware so that, when plugged into a computer that did not have the management software (running), it acted as a normal flash drive, easily allowing pictures to be put on it. But when it was plugged into my friend's computer, (with the camera's photo management software running,) it would act *as though it _were_* the camera, thus allowing the pictures on it to be *automatically* imported.

So, what kind of "specialized tools" would I need to "mess around with" firmware?
Do you know of any good guides on writing firmware that you could give me links to?


Thank you much,
computer_freak_8

****Edit: The example I gave, I now realize, is far more advanced than what I have in mind for near-future projects. It is an example that will probably quite a bit farther into the future than what I need to know right now. For now, I should be content with the "two separate devices" thing. (See mentioned thread via link.)****

---

### Post by snova on 2008-10-05
That would be difficult. You'd have to know a lot about the interface that the camera uses, in your example, to be able to emulate it well enough to fool the software.

On the other hand, if it was something like a USB drive, it might be as easy as providing two different USB interfaces and having an option (no idea how you would manipulate the option from the computer, though) to switch between available interfaces. USB, after all, has a standard way to report the type of device. Interfaces for specific device classes are also standard (I think... maybe not).

As for special tools, you'd need something for whatever device you were reprogramming. I don't think there are standardized interfaces for this sort of thing, or even widely accepted ones.

I'm know very little in this area of programming, so I can't help much. But know what you're getting into- you could easily destroy your test hardware.

---

### Post by computer_freak_8 on 2008-10-05
Okay, thanks. (Also see my edit.)

About this:
> **snova said:**
> But know what you're getting into- you could easily destroy your test hardware.

Thank you for the warning! Yes, I was/am aware of this; I've got plenty of flash drives; I'd be willing to sacrifice a handful of them if need be to accomplish what I'm trying to do.

---

### Post by pmasiar on 2008-10-05
Another language **optimizeed** for this task is Forth. Very flexible, but gives you even more ways to shoot your foot (or head) off than C++. But it gives you easier control to any hardware, and from interactive shell, unlike C++.

---

### Post by computer_freak_8 on 2008-10-05
> **pmasiar said:**
> But it gives you easier control to any hardware, and from interactive shell, unlike C++.

So where can I download the compiler and shell? (For Ubuntu, of course. I'm running version 8.04.1 LTS 64-bit, if it matters.)

I looked on Google, but I couldn't find any links that seemed relevant to me (id est, interactive shell/compiler for Linux).

---

### Post by pmasiar on 2008-10-05
Try wikipedia for links about how to learn Forth, and synaptic for binaries to install 8-)

Be careful: Forth has simple syntax but is very non-trivial and demanding: you have to know what are you doing, being rather experienced programmer before you try. Everything is on the stack, you have direct access to everything, so  mistakes in your code will kill you: Forth trusts you absolutely, no syntax help like in C or C++.

Forth should not be your first, or even second language.

---

### Post by Zugzwang on 2008-10-06
Something that hasn't been explicitly stated so far is: The firmware needs to run on the device itself, therefore you also need the *whole compiling chain* for this platform as it's normally not x86 (and they all have custom boot-loaders and that stuff which is also of importance).

Then, (as however already been stated) you will need to know the exact information about interfacing.

For Canon digital cameras, there's the CHDK project (google it) which is a custom firmware for some of these cameras. Drawback: The firmware needs to be adapted for *all cameras individually*. And a lot of the information they use is gathered by decompiling&debugging the firmware of the device which is extremly tedious and quite hard to do.

---

### Post by computer_freak_8 on 2008-10-06
So are there any tools for Linux that have the ability to dump/flash the firmware on various devices? If so, what would these be? 

Okay, this Forth thing sounds cool, but it also sounds like it might not be the way to go. From what I have read about Forth, it is designed for the BIOS firmware - not that of external hot-pluggable devices such as cameras and flash drives. Is this accurate? 

Maybe firmware isn't quite the right term... My main, short(er)-term goal is to have a device, plug it in, and have the computer believe it is a different device. 

Maybe there are firmware "editors" I could try my luck with? It's okay with me if I brick something because I entered an incorrect command or such; I'm aware of the dangers of messing with firmware. Heck, even dd can be extremely dangerous!

Thanks so much,
computer_freak_8

---

