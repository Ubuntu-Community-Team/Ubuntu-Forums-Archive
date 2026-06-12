---
title: "Ruby can't find Tk..."
date: 2006-03-14
forum: Programming Talk
---

### Post by infidel on 2006-03-14
Hello, all. I recently compiled & installed Ruby 1.8.4 from source (no .debs) on both of my computers-- an old Mandrake box, and my Breezy laptop. The base language appears to work fine on both machines; but under Breezy, Ruby can't find Tk. Once I realized something was amiss I reconfigured and reinstalled with Tk explicitly included as a compile-time option, and made sure I had all dependencies in place beforehand, but "require 'tk'" still throws a "no such file to load" error.

What strikes me as particularly odd is that Ruby's configuration run was able to find everything (with no extra configure options) under a four-year-old Mandrake distro, but evidently not under Breezy. Is there anything unusual about Breezy in relation to this kind of stuff that I ought to know about?

Sorry that the language in this post is so clumsy. You can see that I don't have a lot of know-how. Any and all guidance would be greatly appreciated-- thanks very much in advance.

---

### Post by Dullin on 2006-03-14
The thing is that Ubuntu doesn't carry any compiler of development package in it's default install.

Here's the place to go to know what you need to have before compiling it

[https://wiki.ubuntu.com/InstallingCompilers](https://wiki.ubuntu.com/InstallingCompilers)

---

### Post by infidel on 2006-03-14
Thanks, Dullin. I did what the page describes, and watched to see that make compiled tk (it did...), but I'm still getting the same result-- no Tk in Ruby. :(

Tk's there, I have it, I just can't seem to convince Ruby to see it.

---

