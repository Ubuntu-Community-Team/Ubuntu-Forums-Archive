---
title: "No offense, but is the &quot;full Ubuntu entreprise&quot; really viable?"
date: 2011-03-09
forum: Recurring Discussions
---

### Post by Jean-Michel C. on 2011-03-09
Hi there,
I am currently in a professional break (read "I lost my job and have not found a new one yet") and I thought I would use the opportunity to do a bit of research and learn "things"...

I have been working in IT & software development for more than 20 years and in manager positions for more than 10 years.

My previous company (ASP/SaaS software provider) was heavily using Linux for the hosting platform and development technologies (LAMP stack) but though all the techies were pretty much Open Source advocates, Linux never made it to desktop and general entreprise IT... Microsoft still ruled here and we had the full suite (AD, Exchange, everything desktop, etc.). I was running the whole technical department there (software development, IT & support, etc.).

Though, with the idea of teaching something to myself, I started to put together my own Ubuntu network at home in order to evaluate if the full Ubuntu entreprise was something viable and something I would recommend (in my next job for example).

The firt bit went like a charm and I had a small server  with LAMP, Tomcat, DHCP and DNS up and running with hardly any headacke... I already had a netbook with Ubuntu and I converted one of my desktops to Ubuntu dual boot... All of that went OK and was really looking promising.

It is when I started to look further into what enterprises need that I was somewhat disapointed.

From my experience, it is not the availability of a "specialised" software (verticals?) that is likely to be the show stopper for a deployment, it is rather "everything else" around it.

What I mean is that it is fairly easy for a company who specialises in selling/manufacturing x, y and z to know if the software they need to sell/manufacture x, y or z will be available and will run in an Ubuntu environment, and they are likely to find this information themselves with their current software providers.
On the other hand, as soon as company reaches a certain size (say above 50 PCs), some questions generaly arise about the management of the IT estate, on a technical point of view, but as well on an organisation point of view (how do you translate organisational choices and rules within the IT estate) or with compliance regulations (PCI DSS, SOAX, ISO2700x, you name it).

If I may here are the questions and topics where I still have unanswered questions...
[U][B]
Set-up and maintenance[/B][/U] (where there are more than a dozen of desktops)
Here I have found a few options, though I have not been able to test them myself, in order to automize deployments in a replicable fashion.
Unfortunately, when it is about maintaining an estate and making it evolve, it is a bit less shiny...
I only found "puppet", but it does not really look easy to use and is rather unfriendly.

Any other options?
[U][B]
The "groupware" (Exchange replacement)[/B][/U]
Here I have found 3 options that look more or less viable. Unfortunately, as I do not want to jeopardize my server instalation yet, I cannot test them for "real"...
There is Zarafa but it seems that it becomes payware fairly quickly.
Then there is eGroupWare but I must say that I read quite a few negative reviews and it does not look like a neat "all integrated" package and is rather a collection of tools...
Finally, Zimbra ticks all the functional boxes but can look a bit scary for a SMB with a fairly significant learning curve.

Here as well, are there any other options? Something simpler that works (email, calendar, contacts, notes) would be great.


_**User management and control**_
I must say that this is the area where I am the most disapointed.
Granted that we have LDAP, and that OpenLDAP is readily available, but how to easily manage the users with a friendly frontend still is an open question...
I have tried "lat" and "Luma", but both packages are buggy and seems unsupported and abandonned.
I read about a PHP frontend as well, but I have not tried it.
I am really surprised that there is not an included "standard" package for that.

And when it is down to control what users can and cannot do, it starts to be fairly "hairy" and hazzy...
Just to put things in perspective, beyond IT self preservation policies, "compliance" certifications (PCI DSS, ISO2700x, SOAX) often impose a tight control on users (what they can, cannot do, can, cannot access).

I read about PolicyKit, but it does not seem to be intergrated with LDAP or be mangeable at the network level...

It is to note though that although Zimbra looks complicated it seems that it integrates the LDAP/user management front end.



In a nutshell, I think that if Ubuntu/Linux really wants to enter the enterprise world beyond servers, a better management suite is required. We can think whatever we want about Microsoft, but almost any averadgely savvy IT person is able to set up a Windows 2008 server with the full shebang running (AD, mail, calendar, etc.)...
I think this is a big gap.

OK, so here are my current findings and open questions, I am really keen to get you comments and inputs, and though it academic for me now, I think it is a discussion that has some mileage.
If there are any helpful resources that I have missed (white papers, case studies, etc.) please feel free to point me in the right direction.


PS: the Zentyal package might be an interesting option, but I am not too sure it is not a bit too basic and as well the fact that it is one package might be an issue (some companies will not want SMB, most will have their own routers/gateways), but it is certainly viable foe very small companies.

Best regards,
JM

---

### Post by howefield on 2011-03-09
Moved to "*Recurring Discussions*" in order that the discourse you want can be had.

If you want to ask specific support related questions, please post in the relevant support forums.

---

### Post by Jean-Michel C. on 2011-03-09
Thanks for that.

---

### Post by bouncingwilf on 2011-03-09
Hmmm.....  20 year software development professional with some spare time on his hands. Needs an integrated management package. While I know nothing of these needs, I do know that the best people to develop such packages are those that intimately understand those needs.  Perhaps you'd consider some input into this process with the "best candidate" What can you lose? ( and if it worked out it's not a bad thing to have on a CV.  Just a silly thought!.


Bouncingwilf

---

### Post by Grenage on 2011-03-09
> **Jean-Michel C. said:**
> _**User management and control**_
I must say that this is the area where I am the most disapointed.
Granted that we have LDAP, and that OpenLDAP is readily available, but how to easily manage the users with a friendly frontend still is an open question...
I have tried "lat" and "Luma", but both packages are buggy and seems unsupported and abandonned.
I read about a PHP frontend as well, but I have not tried it.
I am really surprised that there is not an included "standard" package for that.

And when it is down to control what users can and cannot do, it starts to be fairly "hairy" and hazzy...
Just to put things in perspective, beyond IT self preservation policies, "compliance" certifications (PCI DSS, ISO2700x, SOAX) often impose a tight control on users (what they can, cannot do, can, cannot access).

Yes, this is one of the areas that I believe Linux is lacking.  If there's a good alternative to AD, I haven't seen it.  I've never used Red Hat, so I wonder what their offerings are like.

---

### Post by tlcstat on 2011-03-09
Greetings,
Canonical, Redhat, Oracle, are probably a good starting point for the solution to your questions. Since a business uses a server as a tool to make money it only makes sense that there is a cost. Many of the commercial enterprise solutions have a downloadable product that you can use for testing. They will charge for support. When I was in business I didn't mind paying for the computer products that I used, and I was in the computer business. 
tlcstat

---

### Post by uRock on 2011-03-09
If you have any ideas for engineering software that will fill this gap(s), then maybe you can contact Canonical. You never know, you might not be unemployed as long as you expected.

---

### Post by beniwtv on 2011-03-09
From my personal experience, Ubuntu is not lacking in any of these features. I myself have been researching and developing in those areas for the past two years, however, my actual job does not allow me the time for now, so it's on hold.

The truth is, Ubuntu and / or Linux is an OS you need to do things on your own. I have often searched for one-click (or rather one-command) installs of those things, and found nothing.

However, many little pieces of the puzzle are there, you just have to get your hands dirty and get them to play together in a way it makes sense for your particular situation. 

I personally find that very appealing, because I can tweak the system to my liking, unless other solutions that "force" me into a preset way of work.

Example: A customer that used Windows and the built-in tools was not able to integrate our solution because he could not configure his IAS server the way they needed to. Customers on Linux and Unix has no problems whatsoever.

My conclusion: It can be done, it's just a lot of work.

---

### Post by dionysius on 2011-03-09
Er, Novell Groupwise, Novell Identity Manager, Novell Compliance Manager, and tons of other products that do exactly what you need. 

[http://www.novell.com](http://www.novell.com) 

[BBC mode] Other Linux Enterprise and Business solutions are available. [/BBC mode]


If I'm not mistaken [http://www.linux.com/](http://www.linux.com/) carries news, whitepapers and case studies on linux in enterprise/corp environments too. 


I was involved in some marketing for Novell last year and especially Identity Manager was of great interest to companies trying to make do with Windows solutions. Novell had a bad rep in the corporate world for poor customer service, but those issues seem to have been resolved.


I've no experience and little knowledge of Ubuntu's offerings in this area, but personally I wouldn't care much whether it's brand A or brand B in business. Horses for courses.

---

### Post by Jean-Michel C. on 2011-03-11
> **beniwtv said:**
> From my personal experience, Ubuntu is not lacking in any of these features. I myself have been researching and developing in those areas for the past two years...

Those two sentences do conflict together a bit aren't they? ;)


> **beniwtv said:**
> 
The truth is, Ubuntu and / or Linux is an OS you need to do things on your own. I have often searched for one-click (or rather one-command) installs of those things, and found nothing.

However, many little pieces of the puzzle are there, you just have to get your hands dirty and get them to play together in a way it makes sense for your particular situation. 


Granted, but though we techies like it and can chose to livre with that, IMHO, this is a significant roadblock to a more general Linux adoption in the enterprise world (I not talking about a hosting stack, I am talking about Linux being used in non-IT companies.

There are a few solution that are fairly neatly packaged for groupware (sometimes too packaged) and all the underlying technology is there for the other requirements, but it sems that no-one in the Linux community really wants to glue everything together in a way that the average IT professional in a building company with 50 desktop users can safely say that they are going to deploy Ubuntu on server and desktops and survive the day (or the week)...

Anyway, maybe I am expecting too much...

---

### Post by Jean-Michel C. on 2011-03-11
> **dionysius said:**
> Er, Novell Groupwise, Novell Identity Manager, Novell Compliance Manager, and tons of other products that do exactly what you need. 

[http://www.novell.com](http://www.novell.com) 



Well, I am not really sure this does fly, but maybe it does...
What I mean is that a company who is coming to Linux will moste likely expect a level of compliance with open standards.

Though less expensive than Microsoft (and as with a much musch smaller user base and adoption) these Novell technologies all look very proprietary to me. I am not sure there is a point in trading Microsoft against Novell, but maybe it is just me.

> **dionysius said:**
> 
If I'm not mistaken [http://www.linux.com/](http://www.linux.com/) carries news, whitepapers and case studies on linux in enterprise/corp environments too. 

I few interesting articles and links there indeed (though I keaw about most already)..
[http://www.linuxplanet.com/linuxplanet/reviews/7289/1/](http://www.linuxplanet.com/linuxplanet/reviews/7289/1/)
[http://www.linux.com/learn/tutorials/338482-microsoft-exchange-alternatives-for-linux-](http://www.linux.com/learn/tutorials/338482-microsoft-exchange-alternatives-for-linux-)

I have not found anything regarding user control though (LADP integrated PolicyKit).

Still looking, but thanks.

---

### Post by dionysius on 2011-03-12
> **Jean-Michel C. said:**
> Well, I am not really sure this does fly, but maybe it does...
What I mean is that a company who is coming to Linux will moste likely expect a level of compliance with open standards.

Though less expensive than Microsoft (and as with a much musch smaller user base and adoption) these Novell technologies all look very proprietary to me. I am not sure there is a point in trading Microsoft against Novell, but maybe it is just me.


The point would be scalability and stability. I'm sure companies would like their IT infrastructure to come with a pricetag of £0.00, and compliance with open standards is very nice, but I personally don't see the problem with high quality proprietary products if essential services depend on them.

---

### Post by beniwtv on 2011-04-01
> **Jean-Michel C. said:**
> Those two sentences do conflict together a bit aren't they? ;)

No, not really :)

All the pieces I need are there, I am just developing ways to install/configure them in a way that makes my life easier.

> **Jean-Michel C. said:**
> 
Granted, but though we techies like it and can chose to livre with that, IMHO, this is a significant roadblock to a more general Linux adoption in the enterprise world (I not talking about a hosting stack, I am talking about Linux being used in non-IT companies.

Yes, it is a roadblock. Then again, I have yet to see a small non-IT company using business class software, other than basic Microsoft Office and Windows. Even print servers are rare in my experience.

Windows Server, Exchange, etc... are rarely used in those. And for companies big enough to have more than a couple employees, which means there needs to be a controlled and reliable IT infrastructure, a competent IT technician is a requirement (I do not mean here the "I can use Word"-technicians).

Mind you, the companies you are referring to will not be able to configure Linux to their needs, but then again they won't be able to configure Windows Server either (Windows Server requires a lot of knowledge to configure, so much in fact that I prefer the simplicity of Ubuntu).

> **Jean-Michel C. said:**
> 
Anyway, maybe I am expecting too much...

No, I do not think you are expecting too much. However, keep in mind that simplicity also hides configurability.

I needed to work with several big customers (enterprises) to get them started on our platform. I can tell you, the enterprises using Linux had no trouble at all, but the Windows shops could not get their software configured in a way that met *their* expectations, because their "configuration dialogs" didn't offer what they wanted.

I am not saying that for simple requirements there shouldn't be a off-the-shelf solution, but for more complex scenarios, or if your company plans to evolve, no off-the-shelf solution will do, neither in Linux nor in Windows.

---

