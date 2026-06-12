---
title: "Privacy, data mining on ubuntu?"
date: 2017-07-03
forum: New to Ubuntu
---

### Post by jebi on 2017-07-03
hi

I am going to install ubuntu lts on my pc, i dont like the way windows 10 data mines you and privacy issues..

does ubuntu have any privacy issues like this?

thx

---

### Post by ian-weisser on 2017-07-03
All Operating Systems have 'privacy issues' if you don't take basic precautions.

If your questions is more specific: 'Does Canonical collect and sell personally-identifiable usage history?' the answer is 'No'.

If your question is more general: 'Does Canonical collect data about my install of Ubuntu and limited anonymized usage history?' then answer is 'Yes'. Does any of that data get sold to marketers or otherwise used to generate spam? No. It is used only to improve Ubuntu.

Starting in 2012, Canonical did try to raise revenue by selling data - anonymized search data specifically to protect your privacy. It's the Amazon application in the Dash. Canonical has been thoroughly open about exactly what the program is and what the program is for. Nothing secret or nefarious about it. It is trivial to completely uninstall, if you wish...or simply don't use it.

---

### Post by TheFu on 2017-07-03
Canonical, the company that puts out the different Ubuntu distributions isn't like Microsoft.  They don't hold the license for everything inside the distro. Each package determines their license agreement.

Most projects will use the GPLv2 or GPLv3 or MIT or BSD or Apache licenses. If you really want to know what each of those are, you can find the license files in any number of places on an installed Ubuntu system or online. Some part of the system that have unexpected licensing may prompt you to review and accept a license.  For example, the Microsoft TrueType license.  Don't feel that you **must** accept it. After all, how important are fonts do your needs?  It isn't like there aren't hundreds of fonts that are NOT from Microsoft on the system too.

There are a few packages that specifically capture data and send that data back. You can review all the packages installed and review the summaries for what they do.  There's one called popularity-contest - this package keeps track of which programs you use and reports that data back to the Debian team.  Is that bad?  Maybe it is to you, so just uninstall it.  OTOH, it lets a non-profit organization know which packages are used the most across all sorts of distributions so those teams get the extra love if lots and lots of people use them.  That data is anonymous and public.  If a package is never used, but installed, why bother installing it at all?
[http://popcon.debian.org/](http://popcon.debian.org/) has the data.

Canonical has, in a past distribution, taken search parameters and sent those off to 3rd parties. Those 3rd parties would pay canonical. Canonical decided to enable that searching by default, but users could always disabled it.  It was only enabled in the normal, Unity, Ubuntu Desktop, not the other flavors, like Lubuntu, Xubuntu or Ubuntu-Mate.

Canonical has a privacy policy here: [https://www.ubuntu.com/legal/terms-and-policies/privacy-policy](https://www.ubuntu.com/legal/terms-and-policies/privacy-policy) You should read it, since there are times when actions you take will require them to get information.

> Searching in the dash

When you enter a search term into the dash Ubuntu will search your Ubuntu computer and will record the search terms locally. Depending on whether you have opted in or out (see the &#8220;Online Search&#8221; section below), we may also send your keystrokes as a search term to productsearch.ubuntu.com and selected third parties so that we may complement your search results with online search results from such third parties including: Facebook, Twitter, BBC and Amazon. Canonical and these selected third parties will collect your search terms and use them to provide you with search results while using Ubuntu.
I don't have a "Dash" and clearly don't search with it. I think that is an Unity GUI thing.

You can disable all the privacy impacting things in Ubuntu, however, just be aware that if you don't patch (the act of downloading patches is logged as all HTTP traffic is logged), then your system will quickly be in a highly undesirable state.

By default, the configured time servers are connected to Ubuntu. You can change those to any NTP servers on the internet that you like.  Having the correct time is extremely important for almost all security protocols. Any network service that is hosted by Canonical and you or the systems uses will generate logs.

---

### Post by monkeybrain20122 on 2017-07-04
> **ian-weisser said:**
> 
Starting in 2012, Canonical did try to raise revenue by selling data - anonymized search data specifically to protect your privacy. It's the Amazon application in the Dash. Canonical has been thoroughly open about exactly what the program is and what the program is for. Nothing secret or nefarious about it. It is trivial to completely uninstall, if you wish...or simply don't use it.

Web search which includes the amazon app is disabled by default since 16.04. In earlier Ubuntu it could be disabled easily from System settings

---

