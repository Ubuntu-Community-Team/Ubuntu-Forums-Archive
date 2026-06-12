---
title: "GPL'd software and CLOSED betas"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by mevets on 2008-08-02
Is it legal to start a new project based on GPL'd software and then only make it available to a select few through an application process? I thought that if you made it available to one person you have to make it available to everyone. Am I wrong?

I dont want to malign the project so I didnt mention its name.

---

### Post by schnauzer93 on 2008-08-02
The way I understand it, is that you COULD theoretically do this, but your selected beta testers would also need access to your source code, and they, in turn, could legally distribute the code or the binaries, if he/she chooses.

---

### Post by northern lights on 2008-08-02
[QUOTE=GPL2]These requirements apply to the modified work as a whole.  If
identifiable sections of that work are not derived from the Program,
and can be reasonably considered independent and separate works in
themselves, then this License, and its terms, do not apply to those
sections when you distribute them as separate works.  But when you
distribute the same sections as part of a whole which is a work based
on the Program, the distribution of the whole must be on the terms of
this License, whose permissions for other licensees extend to the
entire whole, and thus to each and every part regardless of who wrote it.[/QUOTE]This practice is illegal.

---

### Post by mevets on 2008-08-02
Hmm, Im going to email them asking for the source. I can understand not making binaries available, but making the source available at least allows geeks to run it.

---

### Post by northern lights on 2008-08-03
> **mevets said:**
> Hmm, Im going to email them asking for the source. I can understand not making binaries available, but making the source available at least allows geeks to run it.

From the GPL2, section 2b:

You must cause any work that you distribute or publish, that in whole or in part contains or is derived from the Program or any part thereof, to be licensed as a whole at no charge to all third parties under the terms of this License.

--> You can ask for the binaries also.

You might want to contact [http://gpl-violations.org/]("http://gpl-violations.org/")

---

### Post by mevets on 2008-08-03
Oh even better. I emailed them and waiting for their response. They dont seem like a particularly vicious company, so I expect them to comply.

---

### Post by cariboo on 2008-08-03
I participated in a closed beta of Xandros. If the software is not generally available for download load, there is no problem with the gpl, it is once the software is avialable to the public you have to provide the source software.

During the Xandros beta testing period, the software was only distributed via cd-rom, every couple of weeks a new cd would would appear in the mail, there were no update servers, and every once in a while a patch would appear in the closed news group. Once the distribution was released the repositories went on line, and everything was availabe except for one or two closed source applications.

Jim

---

### Post by northern lights on 2008-08-03
> **northern lights said:**
> any work that you distributeWhere does "distribution" start? I guess that's a grey area.

---

### Post by mevets on 2008-08-03
I got a response from their support and apparently they make it available only upon request, which is a little inconvenient. But at least they send you an invite if you request the code.

The project is Boxee and its based on XBMC. They claim they contribute upstream and I figure they do. There binary repo line reads like
```

deb http://apt.boxee.tv hardy main

```
They have a gutsy one too.

No src repo, they offer an archive which I think you can only download if you login, which you need to be included in the beta for. So I uploaded it to [http://mevets.com/boxee-alpha-src.0.9.2335.tar.bz2]("http://mevets.com/boxee-alpha-src.0.9.2335.tar.bz2") (too big to attach)

I figure you can't use Boxee w/o an account but I dont know because it freezes the second I launch it. I can send an invites to anyone that wants one.

---

### Post by crhylove on 2008-08-03
It can be (mis)construed as a "gray area", but it is technically illegal, and definitely immoral, as GPL'd software was clearly intended to be easy to get by all parties.  That's the point after all.  What closed beta are you talking about?  You have to be careful, people can be really touchy about this subject, even though, if they are not freely distributing GPL software as much as possible, they are definitely in the wrong.  Here's a word on secrecy from JFK, if you needed a better moral understanding of the issue:

[http://video.google.com/videoplay?docid=1710662559138481080](http://video.google.com/videoplay?docid=1710662559138481080) (NSFW) (or kids)

---

### Post by hums07 on 2008-08-03
AFAIK, they dont have to make the binary available and if they wish they can disclose the source only upon request. Once requested, they must provide the source to the one who asks for it.

---

### Post by mevets on 2008-08-03
> **crhylove said:**
> What closed beta are you talking about?
Boxee (boxee.tv). You probably were writing your reply when I posted so hopefully this post sends an instant notification to you.

---

### Post by t0p on 2008-08-03
> **hums07 said:**
> AFAIK, they dont have to make the binary available and if they wish they can disclose the source only upon request. Once requested, they must provide the source to the one who asks for it.

Yeah right, seems to me some people misunderstand the GPL.

I can create software, license it under the GPL, then choose to distribute it to 1 person, 100 people, or 0 people.  My choice.  Sure, the people I distribute to can give it to who they like... but I don't have to.

Furthermore, I can take a piece of pre-existing GPL'd software, modify it, then keep it all to myself if I like.  Perfectly legal. I don't *have* to distribute.

---

### Post by northern lights on 2008-08-03
Sure you may keep it to yourself.

However, if you do distribute, I'd interpret the following (section 2, GPL version 2) > You may modify your copy or copies of the Program or any portion
of it, thus forming a work based on the Program, and copy and
distribute such modifications or work under the terms of Section 1
above, provided that you also meet all of these conditions:

    a) You must cause the modified files to carry prominent notices
    stating that you changed the files and the date of any change.
[I]
    b) You must cause any work that you distribute or publish, that in
    whole or in part contains or is derived from the Program or any
    part thereof, to be licensed as a whole [COLOR="Red"]at no charge to all third
    parties[/COLOR] under the terms of this License.[/I]

    c) If the modified program normally reads commands interactively
    when run, you must cause it, when started running for such
    interactive use in the most ordinary way, to print or display an
    announcement including an appropriate copyright notice and a
    notice that there is no warranty (or else, saying that you provide
    a warranty) and that users may redistribute the program under
    these conditions, and telling the user how to view a copy of this
    License.  (Exception: if the Program itself is interactive but
    does not normally print such an announcement, your work based on
    the Program is not required to print an announcement.)

These requirements apply to the modified work as a whole.  If
identifiable sections of that work are not derived from the Program,
and can be reasonably considered independent and separate works in
themselves, then this License, and its terms, do not apply to those
sections when you distribute them as separate works.  But when you
distribute the same sections as part of a whole which is a work based
on the Program, the distribution of the whole must be on the terms of
this License, whose permissions for other licensees extend to the
entire whole, and thus to each and every part regardless of who wrote it.

such that you have to make at least the source, if not binaries also, accessible to the entire public. If you're certain that's not the case, could you please explain your interpretation? Thank you in advance.

It is indeed questionable how many people have to receive the code/executables and in what function or for what reasons before transfer of code/executables is considerd "distribution"

---

### Post by txcrackers on 2008-08-03
"at no charge" != "publicly accessible to any and all via web-site"

It simply means that you cannot charge for the *code*. It does not specify **how** the code is to be distributed. Plus, you have to remember that the GPL actually pre-dates the WWW.

---

### Post by northern lights on 2008-08-03
> **txcrackers said:**
> "at no charge" != "publicly accessible to any and all via web-site"
True. Now this projects members complied to the request to share code. If that hypothetically wouldn't have been the case though that'd be a violation to me.

> **txcrackers said:**
> Plus, you have to remember that the GPL actually pre-dates the WWW.This particular revision indeed does. But the same section exists in version 3.

---

