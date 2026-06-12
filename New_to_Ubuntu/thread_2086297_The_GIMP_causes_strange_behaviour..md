---
title: "The GIMP causes strange behaviour."
date: 2012-11-20
forum: New to Ubuntu
---

### Post by Kev261266 on 2012-11-20
Hi,

I've noticed a bit of an odd quirk when I try to open PSD files in the GIMP. Some files open no problem, whereas other files display the following message when I try to open them:

Unable to run plug-in "file-psd-load"
(/usr/lib/gimp/2.0/plug-ins/file-psd-load)

Failed to fork (Cannot allocate memory)

Is this something to do with Ubuntu memory allocation? or is it the GIMP's doing. And, can it be put right?

Thanks in advance.

Kev

---

### Post by mikechant on 2012-11-21
Looks as if some of the psd files require more memory to convert than you have. Is it actually the largest files that fail in this way? How much RAM have you got? How much swap space?
If this is the case there are three solutions I can think of:
[LIST=1]
[*]Close all other applications when trying to open a psd.
[*]Add more RAM.
[*]Add more swap (increase size of current swap partition or add another swap partition).
[/LIST]
Using swap might be very slow but if this is going to be a one-off conversion you might not mind.

---

### Post by Kev261266 on 2012-11-21
Hi Thanks for the feedback,

It is the bigger files that seem to cause the error. I tried closing other applications, but still got the same error. I used to open them in Photoshop (on the same machine) with no problems.

I was thinking of getting some more RAM fitted so maybe that is the best way to go.

When you say "add more swap" I did look at the preferences>environment>tile cache size

And that's set at 1007 Meg, is it just as simple as changing that number to a bigger one? or is there a different way that I should be looking at?

---

### Post by mikechant on 2012-11-22
> When you say "add more swap" I did look at the preferences>environment>tile cache size...

Actually I wasn't referring to this (presumably a gimp option?), I was referring to the Linux swap partition, which acts as a (slow) extension to your RAM and is not application specific.

Here are a couple of useful links. The first one tells you how to find out how much swap you have already:
[http://unix.stackexchange.com/questions/23072/how-can-i-check-if-swap-is-active-from-the-command-line](http://unix.stackexchange.com/questions/23072/how-can-i-check-if-swap-is-active-from-the-command-line)

The second link is a general explanation of swap space and includes details of how to increase it
[http://unix.stackexchange.com/questions/23072/how-can-i-check-if-swap-is-active-from-the-command-line](http://unix.stackexchange.com/questions/23072/how-can-i-check-if-swap-is-active-from-the-command-line)

I suggest you look at these and then if you decide to increase swap, post what you are planning to do for us to check before doing it (unless you're already confident with partition changes etc.). However, more RAM is likely to be a more satisfactory solution.

Also note I could be barking up the wrong tree here, this might turn out to be some internal GIMP issue instead.

---

### Post by Kev261266 on 2012-11-22
Thanks again for the help,

I do need to read up on the swap space, as per the links you gave me. As this particular area is all new to me (from a Linux point of view)

In the meantime I doubled the amount in The Gimp preferences>environment>tile cache size  to 2014M and that seems to have solved the issue. I opened even my biggest .psd files no problem.

I will go ahead and get more RAM, and if I want to have a tinker with the swap space I'll defo post my intentions on here first, just to make sure I'm doing it right.

Thanks again.

Kev.

---

