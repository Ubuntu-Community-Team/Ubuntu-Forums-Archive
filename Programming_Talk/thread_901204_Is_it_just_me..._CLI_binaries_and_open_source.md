---
title: "Is it just me... CLI binaries and open source"
date: 2008-08-26
forum: Programming Talk
---

### Post by brianbourke75 on 2008-08-26
Fist I must apologize for the vagueness of this post, but this thought has been stumbling around in my head and I would like to get some feedback to see if I am crazy, stupid or both :)

I have been working with C# in the MS world for a while in my professional life and also have been observing the mono project along side with it.  One of the larger problems with the binaries my company produces is that they totally expose our proprietary stuff and thus need to be obfuscated in some manner.

In doing this I will often think to myself, "Gosh this would be easier if we just open up our source".  So this is my actual question... Does a CLI binary (ie: .NET/MONO) lend itself to open source development in the fact it allows for better functionality sharing?  It would just strike me as really nice to just call Linux.Devices.Sound.ALSA.play(...) in my media player source.

Does this need clarification?  Is it super obvious?  Is this an entirely bad attitude to take?  Any feedback would be nice.


Thanks!
Brian

---

### Post by samjh on 2008-08-26
Please clarify. :)

The CLI bytecode itself does not "lend itself to open source developement".  Open-source development is neither facilitated or constrained by any kind of binary or bytecode produced by a compiler.  The only thing that matters is the **source code**, hence the name "open source".

As for CLI bytecode allowing better functionality sharing, I don't know what you mean.  You can share functionality in languages that compile to native machine code too, like C/C++ with their *.h files and dynamic/statically-linked libraries.

---

### Post by pmasiar on 2008-08-26
"Open source" is deliberately warn and fuzzy term - there are dozens of mutually incompatible "OSF certified" software licenses. Most popular of course is "GPL/LGPL", aka "Free Software".

You IMHO will have little problems to start with any of the licenses, tricky part is 

(1) distribute the code: are you allowed legally to share and link your own code to other CLI libraries
(2) "steal" (reuse) interesting code issued under different license. You can grab any code and re-release it under different (your own) license, if code is BSD and IIUC also Apache, but not GPL.

It's tricky question, that's why everyone just goes with GPL, but it might not be possible for you. There are MSFT-issued OSF-certified licenses (like for NHibernate), you may look at those, and then consult a real lawyer.

---

### Post by brianbourke75 on 2008-08-26
What I am thinking about is not a matter of what *can* be done, but would it make anyone's life easier to not have to deal with header files, linking this that and the other thing and embedded comments.  My mind has been wondering towards the newer developers who may find it easier and more intuitive to use a fancy IDE complete with intellesense (or whatever the non-MS name for it is) and autocomplete.  Not what has to be done, just something to streamline the process and make it more intuitive.

In so far as the licensing issues are concerned, I think that is a little out of scope of what I was really getting at.  At this point I just want to see if the idea has any plausibility to it from a project management point of view. :)

thanks again!
B

---

### Post by pmasiar on 2008-08-26
> **brianbourke75 said:**
> newer developers who may find it easier and more intuitive to use a fancy IDE complete with intellesense (or whatever the non-MS name for it is) and autocomplete.  Not what has to be done, just something to streamline the process and make it more intuitive.

IDE is nice to have, but little trickier for dynamically typed languages, and huge amount of quite boring work which is easier to marshal and deliver by a for a for-profit company than a project run by volunteers. But there are plenty of Free IDE's to chose for any language, and if you want to add any feature, join and do it!

---

