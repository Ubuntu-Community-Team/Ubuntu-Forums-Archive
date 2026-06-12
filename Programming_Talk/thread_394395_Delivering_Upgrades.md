---
title: "Delivering Upgrades"
date: 2007-03-26
forum: Programming Talk
---

### Post by SuperMike on 2007-03-26
I'm working on a project to release this year or next as free and open source, and then charge for media+manual packaged versions of it (minimally), pre-installed rack servers, pre-installed memory sticks (minimally), a programmer book for it, and customization consulting. The project is kind of like a CRM-lite and is designed on purpose to be something you start with and customize from there.

**The topic on my mind lately is -- how would developers prefer that I package the upgrades for it?**

For instance, it's a PHP/PostgreSQL web app. However, there will be cosmetic changes, business logic changes, security changes, and additional features. Some of these will be critical and highly recommended, and others will not. However, if developers have already invested half a year customizing it and integrating it in with another system they've written, then how can I get these upgrades to them? It's not going to be easy.

I also realize that uncool people may want to fork the project and steal my potential source of revenue. One way to counter that is to ensure that my version of the project remains more fluid, active, and receptive to customers than the competition. Therefore, by producing a piece of software that has as its primary goal to be a starting point, an SDK, that people can customize -- it runs the risk of being forked.

I feel that these two issues are also the problem with phpBB, vBulletin, and other derivatives. It's also the problem of SugarCRM and vTiger.

My real goals are to make money through the extra stuff besides the FOSS, and for gaining marketshare in a niche in the CRM-lite part of the market. So how do we in the FOSS community for these kinds of projects not only deliver critical updates but also try to prevent so much forking?

---

### Post by cwaldbieser on 2007-03-28
> **SuperMike said:**
> I'm working on a project to release this year or next as free and open source, and then charge for media+manual packaged versions of it (minimally), pre-installed rack servers, pre-installed memory sticks (minimally), a programmer book for it, and customization consulting. The project is kind of like a CRM-lite and is designed on purpose to be something you start with and customize from there.

**The topic on my mind lately is -- how would developers prefer that I package the upgrades for it?**

For instance, it's a PHP/PostgreSQL web app. However, there will be cosmetic changes, business logic changes, security changes, and additional features. Some of these will be critical and highly recommended, and others will not. However, if developers have already invested half a year customizing it and integrating it in with another system they've written, then how can I get these upgrades to them? It's not going to be easy.

I also realize that uncool people may want to fork the project and steal my potential source of revenue. One way to counter that is to ensure that my version of the project remains more fluid, active, and receptive to customers than the competition. Therefore, by producing a piece of software that has as its primary goal to be a starting point, an SDK, that people can customize -- it runs the risk of being forked.

I feel that these two issues are also the problem with phpBB, vBulletin, and other derivatives. It's also the problem of SugarCRM and vTiger.

My real goals are to make money through the extra stuff besides the FOSS, and for gaining marketshare in a niche in the CRM-lite part of the market. So how do we in the FOSS community for these kinds of projects not only deliver critical updates but also try to prevent so much forking?
It is true that under an open source model, someone can take your code base and modify it to make competing software.  However, you are not really selling the software in the first place.  You are selling services you mentioned above (e.g. pre-installation) along with auxilliary materials (printed manuals).

It is true someone could fork your software, make their own changes and try to offer the same kind of services and extras, but under a license like the GPL, they would be obligated to make their changes available, and you could incorporate any desireable changes back into your own source.

I am not actually familiar with CRM, but from what you describe, it sounds like the real money to be made would be in providing the customization services themselves.  Presumably, some degree of technical and analytical skill will be required to do the customization.  It may be cheaper for a business to hire you to customize the system the way they want it and ship it to them pre-installed that way.  If they want it to receive upgrades from the base software, you could charge for ongoing support and retrofitting contracts.

---

### Post by pmasiar on 2007-03-28
> **cwaldbieser said:**
> It is true that under an open source model, someone can take your code base and modify it to make competing software.  (...)
the real money to be made would be in providing the customization services themselves.  (...) If they want it to receive upgrades from the base software, you could charge for ongoing support and retrofitting contracts.

AND: you, as copyright owner, can relicense your own code with different (non-GPL) license, so if business makes some custom changes (or you do it for them), they don't have to release those changes, but keep them as proprietary comparative advantage.

One trick to keep in mind: when accepting any changes from fork, either ask for copyright attributon to you, or keep changes from fork separate (because you cannot relicense code copyrighted by someone else).

---

### Post by SuperMike on 2007-03-28
Thanks for the input on this. Okay, let me put this forward more simply and get to the heart my largest question about this.

How does a FOSS company best deliver critical updates to users who may have already downloaded its code and customized it?

I mean, with Drupal, you can customize it and then update it and I think it supposedly would not affect your customizations. But in a CRM or CRM-lite package, where you may see heavy customization, a critical update would clobber your customization in most cases. Some CRM packages don't want you to access the code, and, instead, use the GUI to customize everything. However, in my case, I made it such that I *expect* that developers will customize it to integrate it with their backend system. Companies may want the logins and groups to come from LDAP or MS Active Directory. They may want the ability to integrate it in with their email system. They may want to integrate it with their online billing system. And so on.

---

### Post by Tomosaur on 2007-03-28
Extreme modularity coupled with very good documentation and a grace-period for deprecation, I would suggest. I'm thinking along the following lines:

Document absolutely everything that is available for developers to utilise. Provide a tool which can ease the documentation of their own projects (similar to javadoc), and possibly access documentation for the code they're using. You could write a parsing script which takes in their source files, links their use of the given libraries with the official documentation, then produces a reference manual with links back to YOUR documentation, but based around THEIR implementation.

Decide on a regular release cycle. When it comes to release time, apply the new SDK, but keep support for the older SDK (with the now-deprecated features). Write another tool which scans their source for now-deprecated code and points them to the new libs/functions which provide this functionality. Give them time to upgrade their code before the deprecated features are officially removed (which I would suggest should be in the NEXT release, so that you don't end up with a big messy API, but it's entirely up to you). This again relies on you documenting EVERYTHING fully. When you deprecate something, be sure to document what new feature is replacing it.

Provide a service which allows developers to get exposure for their projects. Allow them to register their projects with you, and you can run a 'featured projects' website or something similar. If you plan on releasing other tools, you could provide drop-in modules to your customer's/user's own projects.

You may also want to provide an automatic update tool, to ensure that the majority of your customers are kept notified and updated with the latest version. Don't force updates though. Some of your users may prefer an older version and wish to remain on that, they shouldn't be forced to upgrade. An updater tool would allow you to signify which updates are critical, which are optional, etc etc. You can also link updates together if they depend on one another. Basically you'll need a package management system, but tailored specifically to your SDK.

---

### Post by s1ightcrazed on 2007-03-28
I think what you are really looking for is modularity. If possible, you want to keep the application pieces that will need to be upgraded separate from the customizable pieces, possible by using a modular or 'plug-in' approach. That is the way that I would most want to see things, as a developer: a core which can be upgraded without affecting my customization. 

That's my 2 cents. Keep the core separate from the pieces to be customized. 

:-)

---

### Post by SuperMike on 2007-03-28
This is great advice, guys. I needed to know what developers want and you've made me do some thinking here.

I guess I'm disappointed because I was 2 bugs away from finishing the first beta, but now I think I need to go back and make it even more modular than it already is.

Lesson learned on your new FOSS company projects -- make certain to think about how people are going to receive your patches and apply them, especially the security and critical business logic ones. I'm having to learn this the hard way.

---

### Post by pmasiar on 2007-03-28
Do think about architecture, but don't overdo it: be wary about [Architecture Astronauts](http://www.joelonsoftware.com/articles/fog0000000018.html).

Rule of thumb is, don't ry to make generic solution until you have 3 customized cases. It might mean to work closely with early adopters, to see what exactly they customize, and how exactly you can help them.

[Portland Pattern Repository's Wiki](http://www.c2.com/cgi/wiki?WelcomeVisitors) is great reading on design patterns.

---

### Post by SuperMike on 2007-03-28
Hey, thanks for that pmasiar.

---

