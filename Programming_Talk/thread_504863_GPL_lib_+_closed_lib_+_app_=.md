---
title: "GPL lib + closed lib + app = ?"
date: 2007-07-19
forum: Programming Talk
---

### Post by kung fu buntu on 2007-07-19
From my understanding from GPL when you link (either statically or dynamically) a GPL'ed library to a program the source code of that program must be made available.

Now suppose this:
I code both an application and a library, which I keep closed source. A week latter I decide to link my application to a GPL'ed library (so the program now uses a GPL'ed lib and a closed source lib), as such I have to release the application source code under GPL.
What about my library? Can I keep my library code secret? Does dynamic linking change this?

Another thing I do no understand is GPL v3... I remember reading something that if the application is used for services (e.g. webserver) you do not have to disclose the source code (e.g. changes made to GPL'ed code). Am I wrong?

Thanks!

---

### Post by AusIV4 on 2007-07-19
I can't address your first question, but as far as web based software, that is addressed [here]("http://www.gnu.org/licenses/gpl-faq.html#UnreleasedMods").

Software that is not publicly distributed (software used personally or internally within a company), does not have to be released. Web sites and servers are generally considered internal use, and the content delivered to users is no more covered by the GPL than a document created with openoffice.

---

### Post by smartbei on 2007-07-19
A Quote from the [GPLv2]("http://www.fsf.org/licensing/licenses/info/GPLv2.html"):
> 0. This License applies to any program or other work which contains
a notice placed by the copyright holder saying it may be distributed
under the terms of this General Public License.  The "Program", below,
refers to any such program or work, and a "work based on the Program"
means either the Program or any derivative work under copyright law:
that is to say, a work **containing the Program or a portion of it,**
either verbatim or with modifications and/or translated into another
language.  (Hereinafter, translation is included without limitation in
the term "modification".)  Each licensee is addressed as "you".

Therefore, if the library that you coded does not contain or link to a GPLv2-ed library, it may remain close-sourced. However, the program must be opened if I understand correctly.

---

### Post by pmasiar on 2007-07-19
> **kung fu buntu said:**
> Another thing I do no understand is GPL v3... I remember reading something that if the application is used for services (e.g. webserver) you do not have to disclose the source code (e.g. changes made to GPL'ed code).

You don't have to disclose code for web based apps. IIRC (and IANAL)  the only limit is, if anyone released GPLv3 app which discloses code, you cannot make changes to remove this functionality (but you do not have to add it if not present).

Linking to GPL is tricky. It depends on if your work is derivative or not. Again IANAL, but if you wrote program which uses GPL library is a substantial way, you have to disclose. If you wrote your code to link to proprietary library, and later add wrapper module which converts those calls to GPL library, you are fine. If you want to do something commercial, plan to use real lawyer, not just programmers with little clue in law. Try groklaw.

---

