---
title: "Will we see LibreOffice in Ubuntu in the future?"
date: 2010-09-29
forum: Recurring Discussions
---

### Post by victorche on 2010-09-29
As many of you already know ... Oracle is the owner of Sun Microsystems and now they own OpenOffice.org too. There were some thoughts in the web that the future of OOo is not so clear. And some fears about making it a paid product.

So the good news is that the developers of OOo already made a fork of the code. For now the package name is LibreOffice and it is released under GPL3 license.

As some articles explain, this project is already supported by big companies like Google, Novell, Red Hat. Maybe Ubuntu also has an opinion about this and if I missed it, sorry...

More info about the project here:
[http://www.documentfoundation.org/](http://www.documentfoundation.org/)

---

### Post by VMC on 2010-09-29
Although this may be exciting news, its not related to Maverick issues.

---

### Post by cascade9 on 2010-09-29
According to this, yes- 

> Mark Shuttleworth, founder of Canonical, the makers of Ubuntu, said, "The Ubuntu Project will be pleased to ship LibreOffice from The Document Foundation in future releases of Ubuntu. The Document Foundation's stewardship of LibreOffice provides Ubuntu developers an effective forum for collaboration around the code that makes Ubuntu an effective solution for the desktop in office environments."

[http://blogs.computerworld.com/17045/openoffice_goes_its_own_way?source=rss_blogs](http://blogs.computerworld.com/17045/openoffice_goes_its_own_way?source=rss_blogs)

---

### Post by victorche on 2010-09-29
> **VMC said:**
> Although this may be exciting news, its not related to Maverick issues.

If this is the wrong forum, then excuse me. My point was, will we see it in a ppa for testing or something. That's why I decided to post in here. Would like to test it, actually.

---

### Post by Simian Man on 2010-09-29
> **victorche said:**
> If this is the wrong forum, then excuse me. My point was, will we see it in a ppa for testing or something. That's why I decided to post in here. Would like to test it, actually.

They *just* forked it.  I very much doubt there is anything new yet.  Maybe they did a search and replace to change the name.

---

### Post by 23meg on 2010-09-29
[QUOTE=http://www.documentfoundation.org/contact/tdf_release.html]
Mark Shuttleworth, founder and major shareholder of Canonical, the makers of Ubuntu, has declared: "Office productivity software is a critical component of the free software desktop, and the Ubuntu Project will be pleased to ship LibreOffice from The Document Foundation in future releases of Ubuntu. The Document Foundation's stewardship of LibreOffice provides Ubuntu developers an effective forum for collaboration around the code that makes Ubuntu an effective solution for the desktop in office environments".
[/QUOTE]

Such says the press release, but I haven't seen anything specific in the UDS-N planning talk or the blueprints so far.

---

### Post by coffeecat on 2010-09-29
> **victorche said:**
> My point was, will we see it in a ppa for testing or something. That's why I decided to post in here. Would like to test it, actually.

If you want to test the beta, you can download it directly and use dpkg to install it. Here:

[http://download.documentfoundation.org/libreoffice/testing/](http://download.documentfoundation.org/libreoffice/testing/)

Click on the details link for the architecture you want to get a mirror list.

Unpack the tarball and the use 'sudo dpkg -i *deb' first in the DEBS folder and then in the DEBS/desktop-integration folder.

---

### Post by VMC on 2010-09-29
> **victorche said:**
> If this is the wrong forum, then excuse me. My point was, will we see it in a ppa for testing or something. That's why I decided to post in here. Would like to test it, actually.

Read [Future Ubuntu Releases Will be Shipped With LibreOffice, Says Mark Shuttleworth]("http://www.techdrivein.com/2010/09/future-ubuntu-releases-will-be-shipped.html") article.

---

### Post by victorche on 2010-09-29
> **Simian Man said:**
> They *just* forked it.  I very much doubt there is anything new yet.  Maybe they did a search and replace to change the name.

You're completely right. But my small experience tells me that it is always good when some piece of software is included in the distro at the beginning of its development. I mean it is somehow easy to implement nicely. Like Ubuntu did with Empathy. They replaced Pidgin with it and there were a lots of opinions that it was too risky, not ready for use. But they took Empathy from the beginning and managed to integrate it.

So an early testing is not so bad idea maybe. Just my 2 cents.

---

### Post by Artemis3 on 2010-09-29
> **Simian Man said:**
> They *just* forked it.  I very much doubt there is anything new yet.  Maybe they did a search and replace to change the name.

Have you tried [http://go-oo.org/](http://go-oo.org/) ? Because they merged their code in, meaning faster performance... And they are [already fixing neglected years old bugs](http://lists.freedesktop.org/archives/libreoffice/2010-September/000003.html).

---

### Post by Tibuda on 2010-09-29
> **Artemis3 said:**
> Have you tried [http://go-oo.org/](http://go-oo.org/) ? Because they merged their code in, meaning faster performance... And they are [already fixing neglected years old bugs](http://lists.freedesktop.org/archives/libreoffice/2010-September/000003.html).

But Go-OO is already the version used in Ubuntu.

---

### Post by Slug71 on 2010-09-30
> **For now** the package name is LibreOffice and it is released under GPL3 license


That says to me that the name isnt final. Until it becomes official and all other things get worked out, i dont think we will see it in Ubuntu or any other Distro for a while. My guess, at least 11.10.

---

### Post by dino99 on 2010-09-30
suse packages ready  :P

---

### Post by Starks on 2010-09-30
Don't know if this has been posted, but there's a PPA by gericom.

[http://gericom.wordpress.com/2010/09/28/libre-office-openoffice-fork-sponsored-by-canonical-novell-google/](http://gericom.wordpress.com/2010/09/28/libre-office-openoffice-fork-sponsored-by-canonical-novell-google/)

BTW, change the curly quotes to regular quotes and use sudo tee instead of just tee.

---

### Post by dino99 on 2010-09-30
> **Starks said:**
> Don't know if this has been posted, but there's a PPA by gericom.

[http://gericom.wordpress.com/2010/09/28/libre-office-openoffice-fork-sponsored-by-canonical-novell-google/](http://gericom.wordpress.com/2010/09/28/libre-office-openoffice-fork-sponsored-by-canonical-novell-google/)

lets go to test it :P

---

### Post by recluce on 2010-09-30
> **Slug71 said:**
> That says to me that the name isnt final. Until it becomes official and all other things get worked out, i dont think we will see it in Ubuntu or any other Distro for a while. My guess, at least 11.10.

Of course the name isn't final. For a project of this size that involves big companies, they will want and need to trademark the name. In my experience, this takes about a year - from the first inquiry into conflicting usage of the name until having the trademark registred. And that would only be the process for Canada and the USA. Worldwide, it may take even longer.

Until that point in time, any name wouldn't be final. Also, the name "LibreOffice" does sound a bit awkward in comparison to "OpenOffice", so they might actually want to find something better.

---

### Post by danbuter on 2010-09-30
Until and unless Oracle charges for OO, I see no reason for this. These devs would be better off submitting stuff to Oracle or working on another project.

---

### Post by seeker5528 on 2010-09-30
> **danbuter said:**
> Until and unless Oracle charges for OO, I see no reason for this. These devs would be better off submitting stuff to Oracle or working on another project.

Seems to me some devs were not happy about the way Sun handled OO to begin with, whether it was process, management, not getting patches in or whatever leading to the previous fork [Go-oo](http://en.wikipedia.org/wiki/Go-oo).

The OO Wikipedia page indicates the Go-oo stuff will be included in LibreOffice.

[http://en.wikipedia.org/wiki/OpenOffice.org#Go-oo](http://en.wikipedia.org/wiki/OpenOffice.org#Go-oo)

Later, Seeker

---

### Post by nanog on 2010-10-01
This is great news! We have not been able to rely on open office in an enterprise setting due to unaddressed bugs and cross platform corruption of files. Instead, we use the oasis odf format in ms office 2007 (so bloody ironic).

---

### Post by randomizer101 on 2010-10-01
> **victorche said:**
> And some fears about making it a paid product.

That would mean Oracle would have two commercial products using the same code base. It's more likely that OOo would go the way of OpenSolaris and leave Oracle to develop Oracle Open Office (formerly StarOffice) in-house.

---

### Post by Elfy on 2010-10-01
moved to recurring

---

### Post by beew on 2010-10-03
> **Starks said:**
> Don't know if this has been posted, but there's a PPA by gericom.

[http://gericom.wordpress.com/2010/09/28/libre-office-openoffice-fork-sponsored-by-canonical-novell-google/](http://gericom.wordpress.com/2010/09/28/libre-office-openoffice-fork-sponsored-by-canonical-novell-google/)

BTW, change the curly quotes to regular quotes and use sudo tee instead of just tee.

I added the PPA but whenever I try to install all packages are 404 not found??!!:confused:

---

