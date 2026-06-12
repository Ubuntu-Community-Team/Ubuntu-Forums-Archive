---
title: "GPL and Copyright"
date: 2009-02-27
forum: Programming Talk
---

### Post by Npl on 2009-02-27
Suppose theres an existing huge GPLed library, and I have my own codebase which I want to use however it pleases me (ie releasing Programs, containing parts of it, closed-source or with less restrictive Licenses than GPL).

Now there is code in the GPLed library, for easier arguing say is a function called "foobar" which I could replace with a better implementation. By doing so however I commit my code under a GPL-License, and as far as I understand I give up my copyright at that point.

Which means that I cant ever use my own "foobar" code again unless I put everything that contains it under GPL aswell. (Id even have to replace it in Programs predating the commit to avoid having to prove prior-art).


Am I right or am I missing something here?

---

### Post by eye208 on 2009-02-27
> **Npl said:**
> Am I right or am I missing something here?
Two things:
[list=1][*]You don't give up copyright by publishing code, even if that code goes into a GPL project. The GPL does not void copyright law. In fact the GPL needs copyright law to work.[*]You can put the same code into your own non-GPL project. However, you can't put *other people's* GPL code into your own non-GPL project.[/list]

---

### Post by Npl on 2009-02-27
> **eye208 said:**
> Two things:
[list=1][*]You don't give up copyright by publishing code, even if that code goes into a GPL project. The GPL does not void copyright law. In fact the GPL needs copyright law to work.[*]You can put the same code into your own non-GPL project. However, you can't put *other people's* GPL code into your own non-GPL project.[/list]So how do I prove its my code?
You can put your stuff under GPL and set your name into the License as autor, but others who add/modify stuff only leave the changed code.
So the only one "owning" anything is the guy/corporation that put the project under GPL in the first place. He/it can then even change the License for the code, including possible modifications/additions from others. See cdrtools which went from GPL to CDDL for example.

---

### Post by eye208 on 2009-02-27
> **Npl said:**
> So how do I prove its my code?
Put your name into the patch.

> He/it can then even change the License for the code, including possible modifications/additions from others. See cdrtools which went from GPL to CDDL for example.
A license change is possible only if all the contributors agree. If a contributor doesn't agree, his contribution must be removed/replaced (see the Java SDK for example). And even then the old GPL version continues to exist and can be forked. That's what happened in the case of cdrtools.

---

### Post by Ferrat on 2009-02-27
First of you never give up copyright unless you sell it, give it away or you are under contract that makes your development fall under someone else (often your employers copyright, and this if they want it). 

Using GPL material does not void copyright or make someone else own your code, what GPL does (last time I checked anyway) is this. 

1. You can not use GPL code directly in a closed source project because of the GPL agreement of sharing code.

2. If your code is based on a GPL code, your code needs to be GPL as well, take the IDsoftware engines for ex. released under GPL you need to put your game engine under GPL if based on one of them. 

3. If you use it as a stand alone module only the module gets "tainted" as some say. So lets say you use the network code from the quake3 engine, is you make code around it you need to put that code under GPL, but if you just write a module around it, then hook it to your engine. As long as you can unhook it without trouble the rest of your code isn't required to be under GPL.

You can never sell someone else's code, you could sell the rest of your engine and ship it with the hooked on module and the source code for that module on your homepage or cd or whatever. 

At least that's how it used to be.


Also your own code can be both under GPL and other licenses at the same time, it's all about what you give people "freedom" to do with your code.

---

### Post by nvteighen on 2009-02-27
> **Ferrat said:**
> 
You can never sell someone else's code, you could sell the rest of your engine and ship it with the hooked on module and the source code for that module on your homepage or cd or whatever. 


Hmm... GPL allows you to sell code or at least that's what I understand from Section 4 (GPLv3). The other GPL "cases" (modified version, object code, whatever) are all based upon Section 4.

---

### Post by Ferrat on 2009-02-27
> **nvteighen said:**
> Hmm... GPL allows you to sell code or at least that's what I understand from Section 4 (GPLv3). The other GPL "cases" (modified version, object code, whatever) are all based upon Section 4.

Took a look at it, yeah you can sell it but have to make it available I think and also include GPL with the software (saying you sold something free:P) and fulfil some other requirements I think (just skimmed it). 
But you are right you can sell it if you do those things. 

Linksys made that mistake with one of their routers around 2003-4?, using GPL software and build their firmware from it but not making the firmware GPL and not making it available, forcing them to make it open source. 

the later released a whole new firmware not based on GPL code.

---

### Post by Npl on 2009-02-27
> **Ferrat said:**
> Also your own code can be both under GPL and other licenses at the same time, it's all about what you give people "freedom" to do with your code.All GPLed software has a sort of owner, so if you publish your code as own GPL-Project and use it somewhere else its fine and dandy.

Problems arise if you add your work to "foreign" GPL Projects.
See, the "owners" are the only ones which can pursue infringments, if someone nicks your code and uses it you cant do anything but contact the "owner" and hope he does anything about it.
Similar your commited code can be modified so its not clear whats technically your code anyway, if theres a revision control system you can refer to your patches - but thats not a given, and old patches can get purged after a while.

---

