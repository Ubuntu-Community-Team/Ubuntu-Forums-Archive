---
title: "open source IDEs and licenses"
date: 2008-05-23
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-05-23
I have a question regarding licenses and open source IDEs. Let's say I use an open source IDE to develop my project. Let's say the IDE uses GPLv3 license and I want to use for my project GPLv2. Is this possible? Can I even close-source my project?

---

### Post by dwhitney67 on 2008-05-23
Why would you think this would be an issue?  You are not delivering the IDE with your closed-source project are you?

You are free to use any GPL 2/3 products you wish to develop your product.  Just don't package the IDE up into something "different" and try to sell/distribute.

---

### Post by JupiterV2 on 2008-05-23
The license of the IDE you are using has little to no bearing on the software you create with it. 

The definition of FREE software, truly free software, is that you may use it for whatever means you desire. The only caveat is that you are NOT free to attempt to profit from a GPL project directly by modifying and reselling it (and thereby modifying the license from GPL to private copyright).

---

### Post by SledgeHammer_999 on 2008-05-23
A loooong time ago I had read GPLv2(quite fast). And I think it said something like this "if you use the GPLv2 program to make somework that somework must be GPLv2 too".

I'll try to read the license again, as soon as I can.

---

### Post by dwhitney67 on 2008-05-23
I could understand if you use GPL2 work "within" another piece of work, but not in the context of developing a piece of work.

---

### Post by LaRoza on 2008-05-23
> **SledgeHammer_999 said:**
> A loooong time ago I had read GPLv2(quite fast). And I think it said something like this "if you use the GPLv2 program to make somework that somework must be GPLv2 too".

I'll try to read the license again, as soon as I can.

That means libraries and such. If one wanted to use say libpurple (which is GPL I think) the app would have to be GPL (I think). Using Pidgin (which uses libpurple) to talk to other developers doesn't count as using it.

---

### Post by slavik on 2008-05-23
you can link against libpurple and not distribute your code under GPL if you don't compile libpurple in (if you link against the shared object, not the static library one) and if you happen to distribute libpurple (as a shared object) you also give people the source code to that particular compilation of libpurple (and any code that extends it, since that code would have to be under GPL, too).

This is what NVIDIA and AMD do for graphic drivers. :)

---

### Post by dempl_dempl on 2008-05-23
Actually , if Linus decides to put Gpl3 on the kernel, I believe we all gonna have to write GPL3 software . 

There was a real debate between Linus and RMS some time ago ( I believe 7-8 months ago ) .

On Linus' observation that GPL3 is too restrictive , RMS answered :

"It's not my fault if Linus doesn't like his job" :)  .


**SledgeHammer_999**:

I've been working for couple of U.S. companies 
the country in which you would expect to see people to read  License Agreement , after all ,in U.S. they have all those patent laws :).
Well, they don't! :)   Everyone takes as much GPL libraries as they can, and put it inside their own commercial software. 
Everyone wants to go as cheap as possible. I really hate it , but that's the way it is. 

[ btw, having German or American for a boss is one the worst things on Earth, because they want to make me to actually do some work! :)  preposterous !  ] 


Therefore , while it's nice to talk about the philosophy ,  in real life, no one will harass you for whatever you do :) ( i meant in programming , not in the other aspects of life :)  )
Only People who actually might be thinking of suing you ( your competition, if they exist ) , are using GPL-free stuff as much as you do.

Cheers!

---

