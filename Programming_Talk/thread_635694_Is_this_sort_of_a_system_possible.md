---
title: "Is this sort of a system possible?"
date: 2007-12-09
forum: Programming Talk
---

### Post by PmDematagoda on 2007-12-09
Does anyone think it to be possible that a system monitors commands executed when installing applications and using such programs such as Python at the base of it? 

Now that there are ways of disguising those dangerous commands, people who want to issue them for malicious reasons could do so by using them in disguise as said in jdong's announcement and the time a person came on the forums and gave some commands saying that it was a game when it fact it was a disguised "rm -rf /". I think this may be possible since the command executes those codes by "unpacking" them from the "disguise" so that it could make out what it is trying to do. Is this true and can this be done?

Thanks:).

---

### Post by NathanB on 2007-12-09
I do not understand why people want to continue to spread this FUD.
A simple command like...
```

C:>  del *.*

```
...can cause damage on a Windows PC.  Yet, it is not a "disguised" command.  It is a perfectly valid and usable and necessary tool that is shipped as part of the OS.

The actual problem exists with the _user_ who does not take the time to read the manual to discover what the command actually does.  It is simple "social engineering" at work.  In, and of themselves, the 'commands' are not harmful.  In fact, they are quite helpful and often quite necessary for proper system maintainence tasks.  The real malicious code is the "couched" posting that the command appears in.  It only does harm to the easily-deceived reader who follows those instructions.

The best way to fight these types of threats is through education.  Simply 'teach' people what the Linux CLI commands do and how to use them properly.

---

### Post by public_void on 2007-12-09
You can protect root by using the --preserve-root argument.

---

### Post by emergingtechnologies on 2007-12-09
I'm pretty new to actually reading posts here and this is the first time I have heard of people offering malicious and bogus instructions or guides in Ubuntu land... what a drag.

Hopefully the forums are read by enough well intentioned people that a malicious instruction is well flagged before newcomers actually try to implement them.

---

### Post by Nekiruhs on 2007-12-09
> **NathanB said:**
> I do not understand why people want to continue to spread this FUD.
A simple command like...
```

C:>  del *.*

```
...can cause damage on a Windows PC.  Yet, it is not a "disguised" command.  It is a perfectly valid and usable and necessary tool that is shipped as part of the OS.

The actual problem exists with the _user_ who does not take the time to read the manual to discover what the command actually does.  It is simple "social engineering" at work.  In, and of themselves, the 'commands' are not harmful.  In fact, they are quite helpful and often quite necessary for proper system maintainence tasks.  The real malicious code is the "couched" posting that the command appears in.  It only does harm to the easily-deceived reader who follows those instructions.

The best way to fight these types of threats is through education.  Simply 'teach' people what the Linux CLI commands do and how to use them properly.
+1 Agreed. Like the saying, give a man a fish and he'll be fed for a day, teach a man to fish and he'll be fed all his life.

---

### Post by pmasiar on 2007-12-09
> **emergingtechnologies said:**
> I have heard of people offering malicious and bogus instructions or guides in Ubuntu land... what a drag.

Hopefully the forums are read by enough well intentioned people that a malicious instruction is well flagged before newcomers actually try to implement them.

I am around for little longer than you, and I **never** encountered any dangerous instructions personally. Just the opposite, people around are rather passionate about selecting "better" from two "good" suggestions, bad suggestion would be disputed immediately.

I guess when you see one of such, report it immediately and it will be cleaned within minutes.

I do not see point in mentioning it in sigs and all over the place, newcomers might get impression that bad advice is common, and it is not the case. It feels like signing a will every time you step out of your house just in case you get hit by a car.

Better place for such a warning will be IMHO on registration screen: "If you get some advice and you are not sure what it does, wait couple minutes for someone else to evaluate it before running it on your computer. Some strangers are ... strange, and rest of us work hard to not to let them hurt anyone".

---

