---
title: "GPL to proprietary"
date: 2009-11-10
forum: Programming Talk
---

### Post by TheBuzzSaw on 2009-11-10
If I release a project under GPL3, do I still have the right to use a future version in a proprietary project? It is my code, so I would think I have the right to give new direction to my own creation, but at the same time, someone could argue that this later version is a violation of the GPL on the prior versions (since the proprietary version uses GPL code, technically).

---

### Post by Bachstelze on 2009-11-10
> **TheBuzzSaw said:**
> It is my code, so I would think I have the right to give new direction to my own creation,

Aye. It's your code, so the GPL (or any other license) doesn't apply to you.

---

### Post by Simian Man on 2009-11-10
Nope you can't change it.  Once it's GPL'ed it *stays* GPL'ed.

This is a situation in which you'd want to use an MIT-style license.  The work you've done up until the change must remain FOSS, but any new developments of the old code can be under another license.

---

### Post by TheBuzzSaw on 2009-11-10
Wow, right off the bat, I get contradicting answers. LOL!

On one hand, I have heard of external organizations (such as EFF) enforcing the GPL. On the other hand, it was my understanding that it was the copyright holder's job to prosecute (thus exempting myself from using my own GPL code in a proprietary product).

---

### Post by Simian Man on 2009-11-10
> **TheBuzzSaw said:**
> Wow, right off the bat, I get contradicting answers. LOL!
Ha ha yeah.  I'm pretty sure I'm right, but Bachstelze is quite experienced, so hopefully someone can clear this up.

> **TheBuzzSaw said:**
> On one hand, I have heard of external organizations (such as EFF) enforcing the GPL. On the other hand, it was my understanding that it was the copyright holder's job to prosecute (thus exempting myself from using my own GPL code in a proprietary product).

It's a question of sticking to the letter of the law vs. what you can practically do.  If you switch the license of a project nobody hardly uses, nobody will hardly care :).

---

### Post by napsy on 2009-11-10
If your're the copyright holder of the code, you can change the licensing terms for new releases. Old releases must still be GPL.

---

### Post by TheBuzzSaw on 2009-11-10
> **napsy said:**
> If your're the copyright holder of the code, you can change the licensing terms for new releases. Old releases must still be GPL.
Yeah, this was my understanding. As far as I know, I cannot suddenly withdraw the older releases (and I have no problem leaving those available), but I should be free to use my own code in a proprietary project elsewhere.

I'd appreciate any further clarification on the subject. Given the confusion in this thread, it doesn't seem so clear cut. I could see myself running into issues if the code I used included *other people's* contributions, but as long as I use only my portions, I should be OK, right?

---

### Post by Bachstelze on 2009-11-10
> **napsy said:**
> If your're the copyright holder of the code, you can change the licensing terms for new releases. Old releases must still be GPL.

This. If you released an older version under the GPL, someone who dowloads it reads "this code is under GPL", that grants him the rights tu use it ain accordance to the GPL, and there's nothing you can do about it.

---

### Post by SledgeHammer_999 on 2009-11-10
If somebody else contributes to your project after you open it, then I don't think you can change licences(unless that person agrees).

---

### Post by nrs on 2009-11-10
> **SledgeHammer_999 said:**
> If somebody else contributes to your project after you open it, then I don't think you can change licences(unless that person agrees).
Depends on how you do things, some projects have people transfer copyright assignment, though usually for more noble reasons. :P If you don't do that, you could just maintain separate versions or remove the offending code. 

My understanding of this is you just can't retroactively change licenses but as the owner you can give it a .1 version bump and use whichever licensing scheme you want.

---

### Post by badrunner on 2009-11-10
> **TheBuzzSaw said:**
> If I release a project under GPL3, do I still have the right to use a future version in a proprietary project? It is my code, so I would think I have the right to give new direction to my own creation, but at the same time, someone could argue that this later version is a violation of the GPL on the prior versions (since the proprietary version uses GPL code, technically).

You can never revoke the gpl license on code you release. Once someone has it under the terms of the gpl they have those rights forever, you cant take them away (with the exception of them breaching the gpl terms). However any code you own the copyright on you can release under as many different licenses as you like (including both proprietary and more free licenses).

However if you run a project as gpl, and take contributions from other contributors under the gpl, you can't release the contributions under any other license than the gpl (beyond license changes the gpl allows for, usually just changes to a newer version of the gpl, or lgpl -> gpl changes), of course if you get permission from the individual copyright holders, or have all copyrights assigned to you then you can do whatever is agreed.

The best thing to do is actually read the gpl, its fairly easy to understand for non-lawyers if you read it carefully, and if you are still unsure, you really need to consult a lawyer on the matter.

---

### Post by Simian Man on 2009-11-10
> **napsy said:**
> If your're the copyright holder of the code, you can change the licensing terms for new releases. Old releases must still be GPL.

OK I seem to be mistaken then.  As others have said, you do have to be careful about others' contributions to your code.  In any case I'd really recommend using a BSD or MIT style license which will prevent this problem all-together.

---

### Post by TheBuzzSaw on 2009-11-22
So, I've been doing a bit of research. Let me know what you think of this.

I plan on releasing a certain project under GPL. Let us say that it reaches version 2.0 under GPL. If no one else has contributed to that project (in terms of actual code), I can go on to develop 3.0 privately and use it in a proprietary project elsewhere, right? Am I violating the terms of the GPL by "technically including 2.0 code"?

However, if by version 2.0, other developers have contributed code, I will just leave the project open for eternity. That will render this whole hypothetic scenario irrelevant. :P

---

### Post by nvteighen on 2009-11-22
> **TheBuzzSaw said:**
> So, I've been doing a bit of research. Let me know what you think of this.

I plan on releasing a certain project under GPL. Let us say that it reaches version 2.0 under GPL. If no one else has contributed to that project (in terms of actual code), I can go on to develop 3.0 privately and use it in a proprietary project elsewhere, right? Am I violating the terms of the GPL by "technically including 2.0 code"?

However, if by version 2.0, other developers have contributed code, I will just leave the project open for eternity. That will render this whole hypothetic scenario irrelevant. :P

It's very simple: If you own the copyright, you can relicense it as you want. Period.

Licenses affect the receiver of some code, never the author.

---

### Post by TheBuzzSaw on 2009-11-22
Awesome.

OK, I have one more question. :P

I read the GPL word for word. It's a lot to take in, but let me see if I understand this correctly. If I want, I can take existing GPL code, modify/upgrade it, and sell that modification. I simply have to obey the rules that (A) I have to provide source code to those who purchase it, and (B) the buyer is free to distribute that software. Is that right?

---

### Post by Bachstelze on 2009-11-22
> **TheBuzzSaw said:**
> 
I read the GPL word for word. It's a lot to take in, but let me see if I understand this correctly. If I want, I can take existing GPL code, modify/upgrade it, and sell that modification. I simply have to obey the rules that (A) I have to provide source code to those who purchase it, and (B) the buyer is free to distribute that software. Is that right?

Yes.

---

### Post by shadylookin on 2009-11-22
> **TheBuzzSaw said:**
> Awesome.

OK, I have one more question. :P

I read the GPL word for word. It's a lot to take in, but let me see if I understand this correctly. If I want, I can take existing GPL code, modify/upgrade it, and sell that modification. I simply have to obey the rules that (A) I have to provide source code to those who purchase it, and (B) the buyer is free to distribute that software. Is that right?

yes, but once it gets sold the first time the price effectively drops to zero because the person you sold it to can release it for free.

---

### Post by Bachstelze on 2009-11-22
> **shadylookin said:**
> yes, but once it gets sold the first time the price effectively drops to zero because the person you sold it to can release it for free.

Unless there is some added value to your version, like nice packaging, a hardcopy manual, or whatever.

---

### Post by benj1 on 2009-11-22
nobody seems to have mentioned dual licensing.
if you want you can release gpl code you own under another license.

---

### Post by TheBuzzSaw on 2009-11-22
It's a lot to consider, but I think I will consider the path of selling it under GPL. I know that customers can be given plenty of reasons to buy beyond having a "legal license" to avoid being targeted by various lawenforcement entities. Frankly, I'm just tired of the way businesses treat consumers.

---

### Post by koenn on 2009-11-22
> **shadylookin said:**
> yes, but once it gets sold the first time the price effectively drops to zero because the person you sold it to can release it for free.
more precisely: the price **may** drop to zero, *if and when* the person you sold it to releases it for free

---

### Post by Bachstelze on 2009-11-22
> **koenn said:**
> more precisely: the price **may** drop to zero, *if and when* the person you sold it to releases it for free

Aye. The GPL only requires you to ship a copy of the license with your software, not to put a big red banner on your website saying : "you can redistribute it for free!" ;)

And even if someone does redistribute it, it doesn't mean other people will find out.

---

### Post by nvteighen on 2009-11-22
> **TheBuzzSaw said:**
> It's a lot to consider, but I think I will consider the path of selling it under GPL. I know that customers can be given plenty of reasons to buy beyond having a "legal license" to avoid being targeted by various lawenforcement entities. Frankly, I'm just tired of the way businesses treat consumers.

Just a marketing tip. Charge a fee for service; it's what Red Hat has been doing with lots of success. They sell their distribution alongside warranty and support and other advantages others just can't give at the same quality, even though they could redistribute Red Hat for free. In simple words: make the customer have it worth to buy instead of just taking it free.

---

### Post by TheBuzzSaw on 2009-11-24
I am also considering the dual license. If some business really wants to make proprietary use of my code, I suppose I can profit off that too. It is my understanding that MySQL offers proprietary licenses on top of the GPL license.

[quote="GPLv3 5c"]You must license the entire work, as a whole, under this License to anyone who comes into possession of a copy. This License will therefore apply, along with any applicable section 7 additional terms, to the whole of the work, and all its parts, regardless of how they are packaged. This License gives no permission to license the work in any other way, but **it does not invalidate such permission if you have separately received it**.[/quote]

Am I understanding this correctly?

---

### Post by koenn on 2009-11-24
yes

---

### Post by TheBuzzSaw on 2009-11-24
I suppose I need to make it clear that anyone contributing to my branch must release the code to my copyright.

---

### Post by nvteighen on 2009-11-25
> **TheBuzzSaw said:**
> I suppose I need to make it clear that anyone contributing to my branch must release the code to my copyright.
That's optional. In small projects I prefer to have people retain their copyright, but use the same license so we don't get in trouble with eachother. In big projects, I suppose having a "Developer team's copyright" makes much more sense.

---

### Post by TheBuzzSaw on 2009-11-25
Yeah, I have no problem with people forking the code and going another direction with it in a separate project, but I need to be able to license the "official original" in other ways as needed.

---

### Post by earthpigg on 2009-11-25
> **TheBuzzSaw said:**
> Yeah, I have no problem with people forking the code and going another direction with it in a separate project, but I need to be able to license the "official original" in other ways as needed.

dual license from the start.

Release it under the GPL and under "TheBuzzSaw's License" or BSD or something.

make anyone contributing code give the rights of the code directly to you, TheBuzzSaw, to do with ***whatever you please***.

as i understand it, that is how Chrome/Chromium works.

edit:
wiki on Chromium~
License	BSD license, MIT License, LGPL, Ms-PL, MPL/GPL/LGPL tri-license

and, from [here]("http://code.google.com/legal/individual-cla-v1.0.html"):

> ***Google Individual Contributor License Agreement ("Agreement"), v1.0***
...
2. Grant of Copyright License. Subject to the terms and conditions of this Agreement, You hereby grant to Google and to recipients of software distributed by Google a perpetual, worldwide, non-exclusive, no-charge, royalty-free, irrevocable copyright license to reproduce, prepare derivative works of, publicly display, publicly perform, sublicense, and distribute Your Contributions and such derivative works.

---

### Post by TheBuzzSaw on 2009-11-25
Yeah, makes sense. Others can run off and do what they want with the code provided they stay within the confines of the GPL (mainly in sharing the code of their modifications), but if someone wants to license the code for use in a proprietary mode, I'll have the right to do that by requiring the copyright on all contributed code.

Before anyone gets the wrong idea, though, I have absolutely no problem giving those contributors credit. I respect people's hard work. :P

---

