---
title: "Intercepting the algorithm or message?"
date: 2012-01-24
forum: Programming Talk
---

### Post by cowboy.bebop on 2012-01-24
Is it possible to read memory or reserved blocks that have stored information and dump that information to a text file. Kind of like memory dump in windows but more targeted on applications that are already running. I am not asking how to do it, but I can also do the research myself I just want to know the correct terminology to search for.

Basically I was reading online about encryption and if it was possible to intercept the message before its encrypted or somehow intercept the algorithm in memory before that message becomes unreadable.

I have a fair amount of knowledge with vb, c# and c and catch on pretty quick with the rules of programming. 

Targeted languages C#, C or C++

---

### Post by CoffeeRain on 2012-01-24
> **Ubuntwha said:**
> Basically I was reading online about encryption and if it was possible to intercept the message before its encrypted or somehow intercept the algorithm in memory before that message becomes unreadable.

Do you mean that you want to know how to read/steal an encrypted message? I don't exactly think that's a good idea. If you're supposed to know what the message says, there should be no reason to need to find the message before it gets encrypted.

---

### Post by cowboy.bebop on 2012-01-24
> **CoffeeRain said:**
> Do you mean that you want to know how to read/steal an encrypted message? I don't exactly think that's a good idea. If you're supposed to know what the message says, there should be no reason to need to find the message before it gets encrypted.

I wouldn't typify as stealing, anything is possible and it all depends on how you use it, I know its subjective IN your head to think that when I say I never cross the unethical line of behavior but being barred from gaining or acquiring the knowledge and the basis of how it works shouldn't be a problem. I never said I was crossing that line I never asked how to do it, I asked if it was possible and what the terminology is used to describe it.

I am not trying to be rude, but why does everyone assume the everyone has an evil background. I am just here for the knowledge and if I wanted to commit a cyber crime I would have done that a long time ago. Its kids stuff and not worth me time.

---

### Post by lisati on 2012-01-24
> **Ubuntwha said:**
> I wouldn't typify as stealing, anything is possible and it all depends on how you use it, I know its subjective IN your head to think that when I say I never cross the unethical line of behavior but being barred from gaining or acquiring the knowledge and the basis of how it works shouldn't be a problem. I never said I was crossing that line I never asked how to do it, I asked if it was possible and what the terminology is used to describe it.

I am not trying to be rude, but why does everyone assume the everyone has an evil background. I am just here for the knowledge and if I wanted to commit a cyber crime I would have done that a long time ago. Its kids stuff and not worth me time.

Because an answer such as this which evades answering someone's request for clarification on what you're trying to do suggests that you have something to hide.

---

### Post by cowboy.bebop on 2012-01-24
> **lisati said:**
> Because an answer such as this which evades answering someone's request for clarification on what you're trying to do suggests that you have something to hide.

You assume I have something to hide, but of course that is everyone natural response, I can encrypt a message if I please and hide the message as I please, but to gain knowledge and understand of how something works is not hiding anything but more targeted on curiosity and ability to gain knowledge. Then maybe we should punish software developers for having such a creative mind.. or do I have to pay tuition to find the answer im looking for.

---

### Post by lisati on 2012-01-24
To get things back on topic, I think terms you are asking about include "Joe Job" and "man in the middle"

---

### Post by cowboy.bebop on 2012-01-24
To be quite honest the articles online seem a bit cumbersome to understand most of it, I think I would hold off on understanding the rest. I do appreciate the time taken to solute my needs. I will mark this topic resolved ty. sd(^.-)-b

Hmm guess there is no way to mark is solved.

---

### Post by CoffeeRain on 2012-01-24
It's in "Thread Tools" right above your first post. :)

---

### Post by cowboy.bebop on 2012-01-24
Hah, you rock ty sir =)

---

### Post by Bachstelze on 2012-01-24
In general, one process cannot read other processes' memory, the operating system makes sure of that. However, if you are root or if you exploit a bug in the operating system, you might be able to do that. Most often, though, you would just use another method to bypass the operating system completely. the most (in)famous example is the FireWire interface, which lets you do just that: access any area of memory without any intervention by the operating system. So if you can acquire a specially crafted FireWore device (and attach it to the target machine), potentially all its memmory is yours to read. Other methods in general are much more intrusive than that, you have so somehow fiddle with the memory controller, or other things at the heart of the computer. Yet another is to use the fact that data does not disappear instantly from RAM after the machine if powered off, so if the target powers off his computer and instantly leaves, if you are quick you can read the data directly from the RAM chips.

Modern computer architectures, in particular the x86, were not designed with security in mind, so there are a lot of ways to attack them. All of them require some kind of special access to the machine, though, either physical or root.

---

