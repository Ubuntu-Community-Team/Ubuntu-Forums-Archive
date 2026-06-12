---
title: "Best Email Choice Available?"
date: 2011-07-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-07-21
Here's my situation and I'm hoping someone can help...

My job uses Microsoft Exchange 2010 for our corporate email, with OWA enabled, and *will not* enable either POP nor IMAP because they are so "unsafe." MAPI worked previously, but--as I understand it--that's being replaced by Microsoft for yet another proprietary plugin. On Natty, I was using Evolution+evolution-exchange for all my job email needs; however, one cannot install evolution-exchange in Oneiric because of a whole host of dependency issues. One also cannot install evolution-mapi. 

So... here's where I'm stuck. I've played with [DavMail]("http://davmail.sourceforge.net/"), but it won't work in any configuration I've tried. I had hoped that would permit me to use Thunderbird for my needs.

Any ideas? Or input, even. I'm just looking to try and solve this problem as soon as possible.

Thanks, in-advance, for all your ideas!

---

### Post by haqking on 2011-07-21
> **moore.bryan said:**
> Here's my situation and I'm hoping someone can help...

My job uses Microsoft Exchange 2010 for our corporate email, with OWA enabled, and *will not* enable either POP nor IMAP because they are so "unsafe." MAPI worked previously, but--as I understand it--that's being replaced by Microsoft for yet another proprietary plugin. On Natty, I was using Evolution+evolution-exchange for all my job email needs; however, one cannot install evolution-exchange in Oneiric because of a whole host of dependency issues. One also cannot install evolution-mapi. 

So... here's where I'm stuck. I've played with [DavMail]("http://davmail.sourceforge.net/"), but it won't work in any configuration I've tried. I had hoped that would permit me to use Thunderbird for my needs.

Any ideas? Or input, even. I'm just looking to try and solve this problem as soon as possible.

Thanks, in-advance, for all your ideas!

I knoiw it probably doesnt help, but if it is for work then i imagine you have a windows licence, i use a Virtual machine and outlook for all my exchange/work email stuff.

Not perfect but to be honest it suits me real well.

---

### Post by Simian Man on 2011-07-21
Does your company not offer a webmail interface?  The Outlook Web access is actually not half bad.

---

### Post by ajgreeny on 2011-07-21
I could just be a bit controversial and suggest that using Oneiric in a work situation is probably not such a good idea.  I'm sure you like living at the edge, but for work?  Surely not.

Does the mail setup work OK in Natty, or Lucid, and are the dependency problems a result of Oneiric being still in alpha?  If so either wait for the dependency problems to be sorted out, or use a full release version of ubuntu.

---

### Post by haqking on 2011-07-21
> **Simian Man said:**
> Does your company not offer a webmail interface?  The Outlook Web access is actually not half bad.

the OP stated he had OWA enabled.

as for me then yes too, i just prefer local client for offline work.

---

### Post by mrcsparker on 2011-07-21
What problems are you having with DavMail?

What version of Exchange are you using?

---

### Post by haqking on 2011-07-21
> **mrcsparker said:**
> What problems are you having with DavMail?

What version of Exchange are you using?


The OP states exchange 2010

---

### Post by moore.bryan on 2011-07-21
> **haqking said:**
> I knoiw it probably doesnt help, but if it is for work then i imagine you have a windows licence, i use a Virtual machine and outlook for all my exchange/work email stuff.

Not perfect but to be honest it suits me real well.
I'd rather access my email via OWA than run an entire virtual appliance just to do it. ;-)

> **Simian Man said:**
> Does your company not offer a webmail interface?  The Outlook Web access is actually not half bad.
Sorry, Simian Man, but I hate OWA and its functionality is *incredibly* limited.

> **ajgreeny said:**
> I could just be a bit controversial and suggest that using Oneiric in a work situation is probably not such a good idea.  I'm sure you like living at the edge, but for work?  Surely not.
I'm not using Oneiric at work, just was hoping to set-up an email client so I could check my work email.

> **ajgreeny]Does the mail setup work OK in Natty, or Lucid, and are the dependency problems a result of Oneiric being still in alpha?  If so either wait for the dependency problems to be sorted out, or use a full release version of ubuntu.[/QUOTE]
There are any number of version requirement issues with installing evolution-exchange that it won't install, not the least of which deals with libedataserverui-3.0-0 said:**
> the OP stated he had OWA enabled.

as for me then yes too, i just prefer local client for offline work.
Exactly.

> **mrcsparker said:**
> What problems are you having with DavMail?
It doesn't work, in any way, always claiming my ports are closed or being used by another program... which I can confirm, with no doubts whatsoever, is not true.

> **mrcsparker]
What version of Exchange are you using?[/QUOTE]
[QUOTE=haqking said:**
> The OP states exchange 2010

---

### Post by SeijiSensei on 2011-07-21
I think Exchange can be configured to support IMAP (don't know about the 2010 version).  Is that an option at your organization?  If so, you should be able to use Thunderbird or Evolution.

---

### Post by moore.bryan on 2011-07-21
Sorry, SeijiSensei, like I originally posted, my corporation thinks IMAP is insecure and they won't enable it.

---

### Post by BwackNinja on 2011-07-22
Though of all situations this one is probably a pain, you can install a compatible evolution-exchange (because the current one probably ended up not building) by:

1. downloading the most recent source from launchpad as well as the changes
2. unzipping the source and changes
3. cd into the source dir and "patch -p1 < name_of_changes.diff"
4. "dpkg-buildpackage -uc -us" to build the deb(s)
5. "sudo dpkg -i name_of_packages.deb" or double-click and install through software-center

Often it will just have been that the package gained some new dependencies, which you might see if it fails to compile, but after you add them it should work great. Using this method, everything will still update properly after working versions enter the repos.

---

### Post by moore.bryan on 2011-07-22
> **BwackNinja said:**
> Though of all situations this one is probably a pain, you can install a compatible evolution-exchange (because the current one probably ended up not building) by:

1. downloading the most recent source from launchpad as well as the changes
2. unzipping the source and changes
3. cd into the source dir and "patch -p1 < name_of_changes.diff"
4. "dpkg-buildpackage -uc -us" to build the deb(s)
5. "sudo dpkg -i name_of_packages.deb" or double-click and install through software-center

Often it will just have been that the package gained some new dependencies, which you might see if it fails to compile, but after you add them it should work great. Using this method, everything will still update properly after working versions enter the repos.
I've used this process for other packages in the past and had to build by-hand all necessary dependencies... wouldn't I just have to go through that headache again?

---

