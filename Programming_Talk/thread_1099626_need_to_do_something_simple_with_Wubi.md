---
title: "need to do something simple with Wubi"
date: 2009-03-18
forum: Programming Talk
---

### Post by DouglasAWh on 2009-03-18
I'm not really a programmer.  I've done some web dev and took a Java class a while back, but it's not something I've touched in a year and I wasn't doing a lot of it then.

However, Wubi is severely lacking for the corporate environment and I need to fix that because Windows is also severely lacking for the corporate environment.  What I want to be able to do is hard code a username and password.  We want to be able to do that for when a Windows user inevitably gets a virus they can boot into Ubuntu and at least check their e-mail.  Since all of our imaging tools are (sadly) of the Microsoft variety, we need to do the Linux install from Windows.  Enter Wubi.  

I think I can handle the actual code, but I'm not sure where the input fields might be.  There seems to be a lot of files in the source.  If someone could point me to the file where the options for possible OS choice and hard drive size are, I think I would find that very helpful.

Thanks!

---

### Post by shatterblast on 2009-03-18
While not a direct answer, a web-mail interface could act as a secondary solution.  It would allow a user to check his or her immediate e-mail, though it wouldn't resolve a lack of access to mail archives.  The benefit might include allowing e-mail access at home computers for those with out the portable kind.  If I'm understanding correctly, it also might reduce the need to just put in an Ubuntu disk for the purposes of retrieving e-mail on a server.  With out knowing your corporate set-up, a server that controls a domain might suffice for the password and user name as far as e-mail goes.  If you're wanting to password protect the Linux distribution, I think that might be separate altogether.

Also if a system gets a virus and you're concerned it might spread, I would highly suggest booting the computer with something else to fix the solution and let the user borrow a spare computer for checking e-mail or doing work.  I have used Remastersys so far for making LiveCDs, and it has worked quite decently.  There were a couple of applications it didn't include on a non-data software-only version, but I think it also allows for creating a bootable ISO image with everything attached, including data.  Not considering any license issues, you could put an anti-virus like Avast, AVG or Clam with what ever else suits your purposes.  I believe Clam has the ability to tag and clean / eliminate individual e-mails within an archive from my limited experimentation.  Thunderbird and Outlook seemed okay with Clam in that regard.

---

### Post by DouglasAWh on 2009-03-18
> **shatterblast said:**
> While not a direct answer, a web-mail interface could act as a secondary solution.  

You are *totally* missing the point.  If you can't boot into Windows, you can't get into webmail.  We know what we are doing as to Windows viruses.  We have several full-time support staff.  Thanks for your suggestions though.

---

### Post by shatterblast on 2009-03-18
Can't you get Internet access through a LiveCD though?  I suppose I'm introducing something complex when your post says "simple."

---

### Post by DouglasAWh on 2009-03-18
> **shatterblast said:**
> Can't you get Internet access through a LiveCD though?  I suppose I'm introducing something complex when your post says "simple."

Yes, but we have 3400 people in the company.  Are you suggesting we burn them all LiveCDs?  Even if we did this, what's the guarantee they'll have them with them when they travel?  There is a *lot* of travel involved.  This is going *only* on laptops...so I guess the number is less than 3400.  They need something on their laptops.  We could do the repartitioning, but that's not going to really work through Windows scripting.

What we need is for Wubi to do it's thing without us in the IT dept having to touch it.  We hire about 50 people a month, so there's that many images plus however many we need to do because of NTFS file corruption or other Windows bullcrap.  I don't have stats on that, but I could probably get them.  Basically, it not being unattended isn't an option.

EDIT: I got some stats after talking to a couple team members.  We are imaging about 200 computers a month.  Probably about half of those are laptops.

---

### Post by slavik on 2009-03-18
ok, so you have 3400 users and you're a run of the mill windows on the desktop everywhere shop ... This tells me 2 things:

1. You have an Active Directory setup
2. You are running Exchange

Here are my suggestions:

1. Google search: samba, pam_ldap
2. Install OWA and imap on exchange

Last question, where is the CTO/director of IT in all of this?

Edit: for imaging, I presume there is a PXE server with Ghost somewhere? Or am I mistaken?

---

### Post by cabalas on 2009-03-18
Is wubi the right option? granted I don't know a lot about wubi but if you are worrying about viruses that won't even let windows boot - let's assume for the moment that in this particular case they have either messed with the windows boot loader or the ntfs partition windows is installed under - isn't then wubi kinda boned as well? seeing that it relies on the windows boot loader and the ntfs partition wouldn't you be better of dual booting?

---

### Post by slavik on 2009-03-18
> **cabalas said:**
> Is wubi the right option? granted I don't know a lot about wubi but if you are worrying about viruses that won't even let windows boot - let's assume for the moment that in this particular case they have either messed with the windows boot loader or the ntfs partition windows is installed under - isn't then wubi kinda boned as well? seeing that it relies on the windows boot loader and the ntfs partition wouldn't you be better of dual booting?
BTW, very good point as well.

Dual boot the system and make grub boot Windows by default with the standard 3 second timeout, then give your employees a simple instruction on how to switch to ubuntu.

Symantec Ghost 14 supports EXT3 and SWAP.

---

### Post by DouglasAWh on 2009-03-18
> **slavik said:**
> 
2. Install OWA and imap on exchange


OWA is installed.  They'll be using that from Linux.

> **slavik said:**
> 
Last question, where is the CTO/director of IT in all of this?


This doesn't really matter, because the decision has been made.  We don't really have a CTO or CIO in the typical sense.  The IT team makes decisions and they are approved by either the COO or CEO. This is not a decision that needs to go to that level though.  This should be something users never see.  It is only for emergencies.

> **slavik said:**
> 
Edit: for imaging, I presume there is a PXE server with Ghost somewhere? Or am I mistaken?

not Ghost, it's RIS for XP and whatever the equivalent is for Vista.  This would be easy if it were Ghost, because then it'd just be a disk image

---

### Post by DouglasAWh on 2009-03-18
> **cabalas said:**
> Is wubi the right option? granted I don't know a lot about wubi but if you are worrying about viruses that won't even let windows boot - let's assume for the moment that in this particular case they have either messed with the windows boot loader or the ntfs partition windows is installed under - isn't then wubi kinda boned as well? seeing that it relies on the windows boot loader and the ntfs partition wouldn't you be better of dual booting?

You guys aren't listening.  I don't want advice on what the best thing to do is.  We are *not* going to be dual booting.  Get it out of your head.  What I want to do is input passwords into Wubi.  End of story.  If you can't help with that, please don't respond.

There are a few reasons other than viruses to do this. login broken for some reason, networking stack broken for some reason, browser broken, video driver broken, etc.

---

### Post by slavik on 2009-03-18
Then you are wrong here:

> 
You are *totally* missing the point. If you can't boot into Windows, you can't get into webmail.


OWA means you have webmail. From ANY browser.

Have you looked at my suggestion #1?

---

### Post by DouglasAWh on 2009-03-18
> **slavik said:**
> Then you are wrong here:



OWA means you have webmail. From ANY browser.

Have you looked at my suggestion #1?

no, that's right.  If they don't have a functioning computer, how are they supposed to get to a browser?  That's entirely why Linux will work for them.  Thanks for proving my point!

---

### Post by slavik on 2009-03-18
Your logic escapes me ...

But in any case, have you looked into my suggestion #1?

The following would also be of interest to you:
[http://www.gnome.org/](http://www.gnome.org/)

specifically this part:

[http://library.gnome.org/misc/release-notes/2.26/#rnusers.evolution](http://library.gnome.org/misc/release-notes/2.26/#rnusers.evolution)
> 2.3.&#8195;Evolution Evolves its Migration from Windows

GNOME's e-mail and groupware suite, Evolution, has gained two important features for helping users who are migrating to GNOME from Microsoft Windows environments.

First is the ability to import Microsoft Outlook Personal Folders (PST files) directly in Evolution. E-mail, contacts, appointments, tasks and journal entries are supported. Previously, the files had to be imported via a third-party utility, such as Thunderbird on Windows.

Second is support for Microsoft Exchange's MAPI protocol. This is the protocol that Microsoft Outlook uses to communicate with Exchange. Previously, Evolution only supported Exchange's SOAP protocol, which is not available on all Exchange servers. This support significantly improves Evolution's integration with Exchange servers.

---

### Post by DouglasAWh on 2009-03-18
> **slavik said:**
> Your logic escapes me ...

But in any case, have you looked into my suggestion #1?

The following would also be of interest to you:
[http://www.gnome.org/](http://www.gnome.org/)

specifically this part:

[http://library.gnome.org/misc/release-notes/2.26/#rnusers.evolution](http://library.gnome.org/misc/release-notes/2.26/#rnusers.evolution)

Even if we were to use Evolution, they'd still need a second OS.  Firefox in Ubuntu will work just fine.  We just need Wubi to do it.  Dual-booting is not an option with MS deployment tools.  Dual-booting would be ideal, but it's not going to happen (unless you can point me to something that will do the partitioning unattended).  Wubi is *easy* and the only reason we're even doing it.  It *must* be unattended.

These are the options:

1) We get Wubi working.
2) This company never looks at Linux again.

I'm already fighting an uphill battle.  Please don't make it harder for me.  

Is there anybody out there that actually knows anything about Wubi?  Where do I need to go to talk to those people?

---

### Post by cabalas on 2009-03-18
Just had a quick browse through the source code to wubi I would recommend looking in /src/wubi/main_page.nsh there seems to be a bit in there about getting the user name and password hopefully that will set you on the track to do what you want to do.

As for people who know about wubi I would have a look on the wubi site [http://wubi-installer.org](http://wubi-installer.org) and try and find their mailing list or the IRC channel the devs hang out in.

> **DouglasAWh said:**
> no, that's right.  If they don't have a functioning computer, how are they supposed to get to a browser?  That's entirely why Linux will work for them.  Thanks for proving my point!

The reason people (myself included) are suggesting dual booting (or other options) is for the point above if they don't have a functioning computer (like I said in my previous post due to the ntfs partition or the boot loader being broken) you aren't going to be able to boot into wubi which defeats the point of installing it for that reason.

---

### Post by slavik on 2009-03-18
1. Your company never looks at linux again ... it's worked out great for you so far, hasn't it?
2. You answer the question: "Have you looked at my suggestion #1?" instead of ignoring it.

---

### Post by DouglasAWh on 2009-03-18
> **cabalas said:**
> Just had a quick browse through the source code to wubi I would recommend looking in /src/wubi/main_page.nsh there seems to be a bit in there about getting the user name and password hopefully that will set you on the track to do what you want to do.


Ok, this is getting somewhere.  I'm going to have to figure out what these variables in parenthesis mean, but if nothing else at this point I can probably figure it out by trial and error.

---

### Post by DouglasAWh on 2009-03-18
> **slavik said:**
> 
2. You answer the question: "Have you looked at my suggestion #1?" instead of ignoring it.

I am only interested in Wubi, but since you seem to have taken offense to my thread title ("need to do something simple with Wubi"), we have had bad experiences with the pam stack and likewise.  Until Likewise 5.0 gets in the repos, we won't be looking at it.  When it does, we'll revisit it for our Linux only desktop machines, of which there are very few (and which I also maintain).  Until then we'll be using Wubi or something similar to kick off an unattended install.  All of our install scripts are written in Windows only languages, so having a .exe like Wubi gives us the opportunity to use those.  Again, if there is a tool that will do the repartitioning in an unattended install, I'll look at it, but I've already spent more time on this than I really can afford.

---

### Post by slavik on 2009-03-19
My suggestion #1 was to look into samba and pam_ldap ... I think you misread something somewhere.

---

