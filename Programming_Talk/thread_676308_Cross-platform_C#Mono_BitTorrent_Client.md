---
title: "Cross-platform C#/Mono BitTorrent Client"
date: 2008-01-23
forum: Programming Talk
---

### Post by Stratrix on 2008-01-23
Hi,

I am a programmer that is writing a specialized bit torrent client to do more specific tasks that the clients out there can't offer.  I've been programming in C# for the last few months and found it enjoyable.  I then found out about mono and how it's able to run on linux without too much hassle (supposedly).  But then the problem hits...

My C# application runs fine on Windows. I am able to compile my client on ubuntu using monodevelop. It compiles fine and starts up fine, but when I run my client, it doesn't seem to be able to do much. It seems as if the tracker isn't returning any peers, or as if it never starts communicating to the tracker. What makes this more difficult to debug is that there is no debugger that I can use! I've looked at monodevelop-debugger - the add-in is broken, and I'm having issues even just trying to build the broken version from source. I've also looked at mono-debugger (mdb) - this doesn't work because although it supports 1.1 and 2.0 applications, it does not support the use of generics.

I was wondering if anybody could point me in the right direction as to what I should be doing as my next steps. Should I continue to try looking for other debuggers that are able to run in the *nix environment? Should I use another programming language? Are there special procedures I need to do before I run the code on mono in linux?

Thanks in advance.

---

### Post by LaRoza on 2008-01-23
> **Stratrix said:**
> 
I was wondering if anybody could point me in the right direction as to what I should be doing as my next steps. Should I continue to try looking for other debuggers that are able to run in the *nix environment? Should I use another programming language? Are there special procedures I need to do before I run the code on mono in linux?

Thanks in advance.

I have never used Mono or C#. It is a great language, I hear, and a Java improvement. However, it seems to be best used with Windows, although it can be used with Linux.

You might want to look into the following: Java, Python, or Perl. These languages are better for cross platform development, and they usually work fine on any OS. Java is similar to C#, so you'll likely find it easy to learn, Python might be something you'll like. It can be learned very quickly. See my wiki.

---

