---
title: "Launchpad vs Sourceforge"
date: 2009-01-21
forum: Programming Talk
---

### Post by Kilon on 2009-01-21
I was wondering which one you prefer and in what areas both overlap. I considering in releasing some open source code and I am very inexperienced with both and wondering what is your experience with them. 

[https://launchpad.net/](https://launchpad.net/)

[https://sourceforge.net/](https://sourceforge.net/)

Are there any other good alternatives. I like how anyone can contribute to your code in launchpad.

---

### Post by bruce89 on 2009-01-21
I like using a less weird DVCS, so I currently use [gitorious]("http://gitorious.org/") for my one (boring) project.

However, if you want to use Bazaar, you need to use Launchpad.

---

### Post by cb951303 on 2009-01-21
> **bruce89 said:**
> I like using a less weird DVCS, so I currently use [gitorious]("http://gitorious.org/") for my one (boring) project.

However, if you want to use Bazaar, you need to use Launchpad.

theres is also mercurial which is really the least weird DVCS I've ever seen :) bitbucket.org gives 150MB repo for free.

---

### Post by Kilon on 2009-01-21
> **bruce89 said:**
> I like using a less weird DVCS, so I currently use [gitorious]("http://gitorious.org/") for my one (boring) project.

However, if you want to use Bazaar, you need to use Launchpad.

what is so weird with launchpad ? Please explain, I have not used any VCS till now.

---

### Post by bruce89 on 2009-01-21
> **Kilon said:**
> what is so weird with launchpad ? Please explain, I have not used any VCS till now.

I was referring to Bazaar. It's just a bit odd (sidestepping comparing it to bizarre) in it having revision numbers. Also, branching is not as good as git.

---

### Post by Kilon on 2009-01-21
> **bruce89 said:**
> I was referring to Bazaar. It's just a bit odd (sidestepping comparing it to bizarre) in it having revision numbers. Also, branching is not as good as git.

Thanks for the clarification and the link

---

### Post by ajackson on 2009-01-21
My two projects live on sourceforge, I find it easy to use and now that they have improved the file upload procedure it is a doddle to release new versions of your applications.

Never tried launchpad for my own projects, did have a look at google code but that was when it first came out and it seemed a bit flaky. What it is like now I don't know.

---

### Post by Kilon on 2009-01-21
> **ajackson said:**
> My two projects live on sourceforge, I find it easy to use and now that they have improved the file upload procedure it is a doddle to release new versions of your applications.

Never tried launchpad for my own projects, did have a look at google code but that was when it first came out and it seemed a bit flaky. What it is like now I don't know.

Oh yeahhhh... i completely forgot about the google code!!!! I have visited it a couple of times , was not impressed. 

Yeah I probably go the old and tested Sourceforge route myself since I am already a registered member there and have been surfing the site for ages . I already made a launchpad account very recently as well, will see how it goes.

Thanks for all the suggestions.

---

### Post by nvteighen on 2009-01-21
The problem with Sourceforge is that in their new TOS they require you to give them permission to redistribute and/or modify your code without any restriction. In other words, anyone visiting your project will have to comply to the GPL/LGPL/BSD/<whatever Free License you use> but the guys at Sourceforge not. Take a look at: [http://alexandria.wiki.sourceforge.net/Terms+of+Use](http://alexandria.wiki.sourceforge.net/Terms+of+Use) (Section 6, Title "Your Rights")

> 
By submitting, posting or displaying Content on or through SourceForge.net, you grant COMPANY a worldwide, non-exclusive, irrevocable, perpetual, fully sublicensable, royalty-free license to use, reproduce, adapt, modify, translate, create derivative works from, publish, perform, display, rent, resell and distribute such Content (in whole or part) on SourceForge.net and incorporate Content in other works, in any form, media, or technology developed by COMPANY, though COMPANY is not required to incorporate Feedback into any COMPANY products or services. COMPANY reserves the right to syndicate Content submitted, posted or displayed by you on or through SourceForge.net and use that Content in connection with any service offered by COMPANY.


---

### Post by snova on 2009-01-21
> **bruce89 said:**
> Also, branching is not as good as git.

Hmm, how so? I tried Git for a while, but I found it weird... maybe it was just the unfamiliarity (being new to DVCS at the time), or maybe it was genuinely queer. ;)

Either way, I figured out Bazaar without hassle, and can do more with it than I ever figured out with Subversion.

> **Kilon said:**
> I was wondering which one you prefer and in what areas both overlap. I considering in releasing some open source code and I am very inexperienced with both and wondering what is your experience with them.

I like Launchpad, though I've little experience with either (and virtually none with Sourceforge). The Bazaar integration is nice, for example; it's trivial to upload some code, and equally easy to grab some.

And, on a side note, I've heard people who use Sourceforge complain about various annoyances. (The project in question seems to be using Launchpad for more and more...)

---

### Post by imdano on 2009-01-21
I've used both, and I prefer the Launchpad/bzr combo for a few reasons:

1) We like to use branches in our project a good amount, and svn/cvs are pretty terrible with branches compared to DVCS like bzr/git/hg. Launchpad also makes it possible for anyone with a Launchpad account to make their own private branch of your code, make changes, and then propose it for merging into the mainline release.  I don't think anything like this is possible through Sourceforge.

2) With bzr you can use a local repository.  So you can make a branch, commit some experimental changes, and then delete the whole branch if you decide its not going to work, all without it ever pushing anything to Launchpad.

3) Launchpad makes it very easy to link bugs to things like milestones, releases, and branches, which is really helpful for organization and identifying when and where things are getting fixed.  The bug tracker itself is also a lot nicer.

4) Built-in translation support, though our project had set up our own system while we were still using Sourceforge that we kept.

5) I like Launchpad's look & feel a lot more.

The one nice thing I miss from SF is that they gave you webspace to use for setting up a site and hosting files/forums/whatever.

---

### Post by Kilon on 2009-01-22
> **nvteighen said:**
> The problem with Sourceforge is that in their new TOS they require you to give them permission to redistribute and/or modify your code without any restriction. In other words, anyone visiting your project will have to comply to the GPL/LGPL/BSD/<whatever Free License you use> but the guys at Sourceforge not. Take a look at: [http://alexandria.wiki.sourceforge.net/Terms+of+Use](http://alexandria.wiki.sourceforge.net/Terms+of+Use) (Section 6, Title "Your Rights")


Do not worry about these pseudo-legal tricks, they have no legal bearing. How my copyright will be treated will be defined by me and me only. Other than that I simple do not care so much about this issue.  

My source code will be free and open as will be the libraries that I will use from other people. 

I see 2 supporters of Launchpad so that means I will have to try Launchpad as well. Thank you imdano for your detailed opinion on the matter.

---

### Post by nvteighen on 2009-01-22
> **Kilon said:**
> Do not worry about these pseudo-legal tricks, they have no legal bearing. How my copyright will be treated will be defined by me and me only. Other than that I simple do not care so much about this issue.  


Actually, I'd worry: by agreeing the TOS, you're giving them a really permisive license which allows them to do almost anything they want with your work. In some sense, you're sharing copyright with Sourceforge and have no control over what they do with it.

Of course, you are free to sign the TOS and it's you who decide to give them that license or not. But, even if you don't care, you should know what the TOS are.

On-topic: Have you seen GNU Savannah? [http://gnu.savannah.org](http://gnu.savannah.org)

---

### Post by Kilon on 2009-01-22
> **nvteighen said:**
> Actually, I'd worry: by agreeing the TOS, you're giving them a really permisive license which allows them to do almost anything they want with your work. In some sense, you're sharing copyright with Sourceforge and have no control over what they do with it.

Of course, you are free to sign the TOS and it's you who decide to give them that license or not. But, even if you don't care, you should know what the TOS are.

On-topic: Have you seen GNU Savannah? [http://gnu.savannah.org](http://gnu.savannah.org)


Agreeing does not mean much legally at least. If they wanted to do it in a way that is meaningfully legaly then they would have to contact me make a private contract with me where I would sign and give my full consent.  

Generally anything that involves copyright is very specific and it has a specific way it is done to be legally valid.  And generally anything you see that has an "I agree" button is invalid. Also GPL and other licences are not so "legal" if you catch my drift ;) But generally internet is a huge legal mess. LOL

But other than that I do not care , as will posting/uploading fun code , nothing that I will take too seriously.


No I have not seen savannah , I am going to visit it right now. Thanks!!! (too bad there is no thanks button any more)

EDIT:

The correct link is [http://savannah.gnu.org/](http://savannah.gnu.org/)

---

### Post by nvteighen on 2009-01-22
> **Kilon said:**
> Agreeing does not mean much legally at least. If they wanted to do it in a way that is meaningfully legaly then they would have to contact me make a private contract with me where I would sign and give my full consent.  

Generally anything that involves copyright is very specific and it has a specific way it is done to be legally valid.  And generally anything you see that has an "I agree" button is invalid. Also GPL and other licences are not so "legal" if you catch my drift ;) But generally internet is a huge legal mess. LOL

But other than that I do not care , as will posting/uploading fun code , nothing that I will take too seriously.

I forgot you're a lawyer :p

Yeah, I see the point now that you mention contractual issues. There's no way to afterwards validate whether you did agreed or not to that "terms", because there's no physical support of your signature. So, you're defense-less against any abuse.

Am I right?

> No I have not seen savannah , I am going to visit it right now. Thanks!!! (too bad there is no thanks button any more)

EDIT:

The correct link is [http://savannah.gnu.org/](http://savannah.gnu.org/)

Yup, that's the link. As you see, it's not the very best, but it has some good features. It all depends on what you want.

---

### Post by Kilon on 2009-01-22
> **nvteighen said:**
> I forgot you're a lawyer :p

Yeah, I see the point now that you mention contractual issues. There's no way to afterwards validate whether you did agreed or not to that "terms", because there's no physical support of your signature. So, you're defense-less against any abuse.

Am I right?




Yes your line of though is correct ...

the problem with the " I Agree " button generally is that people press it just to use the service/software/whatever product not to actually agree. In almost all national laws consent is crucial, without it there is no contract. And establishing consent is not as straightforward as people think. For example pressing the  "I agree" button does not mean you consent to the terms. Maybe because English is not you mother tongue so you do not understand what the terms are saying exactly , or maybe you just do not read them at all cause you do not care . So it is highly unlikely this kind of contract will have any baring. 

But even if the "I agree" button is accepted legally then there is an issue of national law, there is case law that proves that the national of the customer applies and not the national law of the provider. In my national law there is only ONE way to cancel copyright or move copyright from one person to the other. And pretty much the same application is for all other national laws that I studied like UK law and EU law ( i think the same applies to US law as well but I am not certain). This case is actual a contract that you sign not as a freelancer but as an employee of a company where you explicitly say that "I John give my copyright to the Company named ....." , if you are a freelancer then it is almost impossible to give your copyright to another person even if you sign a contract where you say you do!!!! So the issue of copyright per se is highly complex legal area and lot different to how people perceive it. 

That is why GPL and other licences have a very limited legal application. I have read some of them and found them to large part inadequate.

Thanks for the savannah link , I just remembered I have visited before and I will visit it again for a more careful look.

---

### Post by CptPicard on 2009-01-22
Yeah, now that I recall, defending the TOSes on websites in Europe has actually been hard, they don't seem to *really* mean jack as contracts. I was a bit sceptical about the freedom-of-speech issue but yeah I would really like it see enforced that someone steals your code...

---

### Post by nvteighen on 2009-01-22
> **Kilon said:**
> 
the problem with the " I Agree " button generally is that people press it just to use the service/software/whatever product not to actually agree. In almost all national laws consent is crucial, without it there is no contract. And establishing consent is not as straightforward as people think. For example pressing the  "I agree" button does not mean you consent to the terms. Maybe because English is not you mother tongue so you do not understand what the terms are saying exactly , or maybe you just do not read them at all cause you do not care . So it is highly unlikely this kind of contract will have any baring. 

But even if the "I agree" button is accepted legally then there is an issue of national law, there is case law that proves that the national of the customer applies and not the national law of the provider. In my national law there is only ONE way to cancel copyright or move copyright from one person to the other. And pretty much the same application is for all other national laws that I studied like UK law and EU law ( i think the same applies to US law as well but I am not certain). This case is actual a contract that you sign not as a freelancer but as an employee of a company where you explicitly say that "I John give my copyright to the Company named ....." , if you are a freelancer then it is almost impossible to give your copyright to another person even if you sign a contract where you say you do!!!! So the issue of copyright per se is highly complex legal area and lot different to how people perceive it.

I see. Thank you! (I'd have used the Thanks button, but you know...)

---

### Post by FrankT-Qc on 2010-03-03
Just noticed :

Nobody here suggests that maybe you don't need to use a service like launchpad, sourceforge or whatever...

Depending on the size of your project, you can host your code yourself... Especially if you're going the bazaar way, the best bet might be no server at all (bazaar does not require any server...). I have seen quite a few projects going around on usb keys, emails and shared folders...

A shared folder of ftp might be all you need

---

### Post by nvteighen on 2010-03-03
> **FrankT-Qc said:**
> Just noticed :

Nobody here suggests that maybe you don't need to use a service like launchpad, sourceforge or whatever...

Depending on the size of your project, you can host your code yourself... Especially if you're going the bazaar way, the best bet might be no server at all (bazaar does not require any server...). I have seen quite a few projects going around on usb keys, emails and shared folders...

A shared folder of ftp might be all you need

Yeah, but these sites give you a couple of features that are nice for people that don't know/want set a server for that... and administrate that same server.

---

