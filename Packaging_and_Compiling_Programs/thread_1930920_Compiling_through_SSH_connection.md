---
title: "Compiling through SSH connection"
date: 2012-02-24
forum: Packaging and Compiling Programs
---

### Post by rhinehartg on 2012-02-24
So I have an SSH connection to a computer with a CUDA program I've been working on, and it is on THAT computer the program can actually run on. I have a performance analysis tool that I want to use to look at this program of mine. This tool has its own comiler, too. Once this program compiled and ran, a trace file should be generated (on the computer I have ssh'd to). 
 
More generally speaking, is it possible to use a compiler on your own machine to compile a source file on another machine? If yes, how do I do that?
 
I hope I've explained it all clearly...

---

### Post by roelforg on 2012-02-24
Use scp to copy the src files from your pc to the other.
Now use ssh to run the compiler.
Use scp to copy the finished binary's back.

---

### Post by rhinehartg on 2012-02-24
I should have mentioned, that I'm rather terminal-illiterate... You're going to have to be more clear and explicit than that. 
 
The source files for the program are already on the other computer. 
How do I use ssh to run the compiler?

---

### Post by roelforg on 2012-02-24
The wiki is a real helpful place.

---

