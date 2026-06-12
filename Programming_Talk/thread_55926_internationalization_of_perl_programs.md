---
title: "internationalization of perl programs?"
date: 2005-08-10
forum: Programming Talk
---

### Post by supenguin on 2005-08-10
It looks like I'll soon be involved in internationalizing an application. It seems like its one of the things Ubuntu focuses on, especially from the front page:

> Ubuntu includes the very best in translations and accessibility infrastructure that the Free Software community has to offer, to make Ubuntu usable by as many people as possible.

I've looked for info on how Ubuntu does translation/internationalization and couldn't find any info.

Now, I don't know if this will make a difference or not, but here's a couple constraints on things. This is a web based application using template toolkit and MySQL, and also it looks like the people doing translation usually aren't going to be people with programming skills, so part of the project will probably be doing some kind of content management system so non-programmers can add or modify translations. Anyone have any suggestions?

---

### Post by supenguin on 2005-08-29
This post has been up for a couple weeks and no replies.

Has anyone had any experience with adding internationalization support to a program? What worked? What didn't? Any other advice or comments?

---

### Post by toojays on 2005-08-30
I'm not very familiar with Perl, but I imagine that i18n in Perl is similar to other languages used for Free Software development.

The usual case is that your application will initialise a system which is compatible with GNU gettext. After initialisation, all strings to be translated are passed to gettext() before use. Commonly, the gettext function call is abbreviated to a single underscore, which makes it less obtrustive. So calls like print("foo") become print(_("foo")).

Once you have marked the translatable strings in your source code, you can then use the xgettext program to extract them into a POT (portable template file). The template is used as a basis for a PO (portable object) file, which contains the translations. You will have one PO file for each language. The PO files are then compiled into MO (machine object) files, which makes the gettext system more efficient.

So, the above is more or less how each application handles the translations. Whan it comes to actually writing the PO files (i.e. where non-programmers translate strings into their native languages), Canonical has an in-house system called Rosetta, which is a web-site where translations take place. Rosetta is still a bit buggy, but it looks like it has great potential. For example, [here](https://launchpad.net/products/temptecr/+series/main/+pots/temptecr) you can see the translations which have been made for a program I maintain in my day job.

---

