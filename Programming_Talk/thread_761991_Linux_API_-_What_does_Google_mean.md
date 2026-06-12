---
title: "Linux API - What does Google mean?"
date: 2008-04-21
forum: Programming Talk
---

### Post by mattgaunt on 2008-04-21
Heya everyone

I'm looking into Google internships, and for their requirements they want people with knowledge of the Unix/Linux API or Windows API.

Now I have hardly any interest in programming for the Windows API, but I dont actually know what Google are looking for, does anyone here know what they mean and could they explain it for me?

Also if anyone has any ideas on how to learn the Linux API that would be great

Thanks alot

Gaunt

---

### Post by jnorthr on 2008-04-21
Good evening Gaunt :

The linux API is really several hundred API's rolled into one operating system known by the generic name of linux. Frankly, if you do not know what an API is, and generally only programmer bods do, then you might not have 'the right stuff' for google. You will need to gain some credentials in order to impress Google, as they only take the best candidates.

---

### Post by ruy_lopez on 2008-04-21
> **mattgaunt said:**
> 
I'm looking into Google internships, and for their requirements they want people with knowledge of the Unix/Linux API or Windows API.

I dont actually know what Google are looking for, does anyone here know what they mean and could they explain it for me?

Also if anyone has any ideas on how to learn the Linux API that would be great


By Linux API, they could mean an awful lot. It could mean C development libraries. It could mean Graphical User Interface frameworks. Or it could mean Python development, which Google use a lot.

I'd say at a minimum they are looking for someone with experience programming in C, maybe more.

Linux doesn't really have an integrated API. (Using Linux to refer to a distribution as a whole) Linux comprises many layers of abstraction. Any one of these layers can have many libraries and frameworks that fulfil a similar role, depending on the distribution. Taken together these constitute a Linux API.

Try contacting Google to find out more. Ask them what particular aspects of the Linux API they regard as important for a candidate. 

If they respond to you, post the response here (or a summary). You've got my curiosity piqued.

---

### Post by mattgaunt on 2008-04-21
I know that I API is just a set of classes that you can use for programming in what ever way you want. But Like u guys have kinda said, that seems pretty vague, I was wondering if I was just missing something or not.

I mean I've programmed in C for the past 2 years and started using API's in program developments for certain Libraries.

Unfortunately it is stupidly difficult to get hold of anyone in Google, I have one e-mail but its to someone not on the technical side of Google, but I'll keep trying.

Im looking into python over the summer since Google do ask of that for a candidate so if I do find out anything I'll post back.

Gaunt

---

### Post by ruy_lopez on 2008-04-21
> **mattgaunt said:**
> 
Unfortunately it is stupidly difficult to get hold of anyone in Google, I have one e-mail but its to someone not on the technical side of Google, but I'll keep trying.


Tell me about it. Google BrowserSync mangled my bookmarks last week. All I got for a reply was an automated response.

---

### Post by CptPicard on 2008-04-21
> **mattgaunt said:**
> I know that I API is just a set of classes that you can use for programming in what ever way you want.

An API is just a sort of contract; the description of the interface of some particular piece of software that is going to be called and used from the outside. It doesn't really have much to do with classes (necessarily), and ... it tends to tell you how it wants to be programmed in, so you can't do whatever :p

---

### Post by mattgaunt on 2008-04-27
Just for anyone who is interested, the contact in Google said that they jsut require you have knowledge of the environment.

"We simply require that you have experience of working with Unix/Linux and Windows. The way it is written is something of a tautology."

Gaunt

---

### Post by samjh on 2008-04-27
> **mattgaunt said:**
> I'm looking into Google internships, and for their requirements they want people with knowledge of the Unix/Linux API or Windows API.

Now I have hardly any interest in programming for the Windows API, but I dont actually know what Google are looking for, does anyone here know what they mean and could they explain it for me?

The Windows API will be the Win32 (or Win64) libraries, which are encyclopaedic in size.  It's complex stuff that will easily take months to become familiar with, if not years.

The "Linux API" is more vague.  Most likely they mean a combination of knowledge of the [C POSIX Library as embodied in the GNU C Library](http://www.gnu.org/software/libc/) and the [Linux Kernel API](http://www.gnugeneration.com/books/linux/2.6.20/kernel-api/).  The former is reasonably small, but the latter is highly complex.  As for Win32, they can both take many months of learning to be comfortable with.

> Just for anyone who is interested, the contact in Google said that they jsut require you have knowledge of the environment.

"We simply require that you have experience of working with Unix/Linux and Windows. The way it is written is something of a tautology."A lot of companies will inflate the job requirements of the positions they're advertising.  It attracts better-qualified candidates.

---

### Post by pmasiar on 2008-04-27
> **samjh said:**
> A lot of companies will inflate the job requirements of the positions they're advertising.  It attracts better-qualified candidates.

Not necessarily. It is because they have hiring managers in Human Resources department, who are liberal arts graduates and have no clue what IT department is doing.

---

