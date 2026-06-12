---
title: "Kernel API changes 2.4.X -&gt; 2.6.X (FS related)"
date: 2006-01-10
forum: Programming Talk
---

### Post by Malakim on 2006-01-10
Hi there,

I don't know if there are many kernel developers hanging around here, but I thought I might as well ask. ;) 

In order to learn a little about the 2.6.X internals, I decided to port a FS module I started to work on for a school project with the 2.4.2X kernel. However, I have run into a small problem. I can't find the bread() function, it seems to be replaced with __bread(). Is this what I should use instead of the old bread(), or would I be better off moving to the new bio API's that I've read about in ["Linux Kernel Development"]("http://www.novell.com/training/books/book.html?book=bookDev&val=5") by Rober Love? Is the bio structure even meant for getting data from the block device, or only to manage data when it's in memory?

Regards,
Markus Svensson

---

