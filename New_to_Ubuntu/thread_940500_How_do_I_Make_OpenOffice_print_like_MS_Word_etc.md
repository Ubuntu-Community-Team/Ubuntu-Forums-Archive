---
title: "How do I Make OpenOffice print like MS Word etc?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Rorke on 2008-10-07
When I download files of a tutor group homepage and print them, often the font changes slightly, the table sizes change and consequestly the pagination is all different (single lines on pages - different number of pages.) Is there a good way of emulating final printed output of esp Word 2007?
(Otherwise my girlfriend will bin Ubuntu and go to PC world and spend about 500 on software)

---

### Post by techstop on 2008-10-07
So you're really asking if OOo has 100% formatting compatibility with Word 2007?

Then the answer is no.

EDIT: You could ask the university to provide material in truly portable format, eg PDF.

[http://www.goldmark.org/netrants/no-word/attach.html](http://www.goldmark.org/netrants/no-word/attach.html)

---

### Post by Idefix82 on 2008-10-07
To help the situation a little bit you could install fonts that are as close to Windows fonts as possible. But apart from that, I agree that you really have to make the university provide you material in a universal format. Otherwise they are forcing their students to spend a lot of money on rubbish software.

---

### Post by techstop on 2008-10-07
Here's how to install Word 2007 fonts;

[http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html](http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html)

...but the legality is questionable.

---

### Post by PierreDeKat on 2008-10-07
> **Rorke said:**
> (Otherwise my girlfriend will bin Ubuntu and go to PC world and spend about 500 on software)
Well, don't let her do *that*.

First, this solution will only work if you're trying to emulate the way that "True Type" fonts are displayed in a Windows type setup on the same computer.

But try this:

1) Open Nautilus
2) Browse over to the Windows partition she's/you're trying to emulate
3) Go to /WINDOWS/Fonts
4) Copy all of the .ttf files you want
5) Paste them into a folder in your /home directory (example: /home/yournamehere/Fonts or ~/.Fonts if you want to hide the font folder from Nautilus)

(Alternatively, you can download a font pack from Microsoft that they, in all their generosity, have made available to the public sphere so that folks living outside the Microsoft sphere can see things the way that Microsoft users think they're being seen by folks living outside the Microsoft sphere.)

6) Install msttcorefonts via Synaptic
7) Restart (I find this the easiest way)

At that point, msttcorefonts should find all of those fonts and make them available to all of your X-based applications, including Openoffice.

The first time I went through this process, I had to follow a procedure in OpenOffice's "Help" manual on how to set up the new fonts. But the second time I did it, OpenOffice seemed to find and install the fonts automatically. So your mileage may vary.

Then, once you have the fonts set up, you will just have to tweak the margins for printing, maybe tweak a table, or whatever.

---

### Post by halitech on 2008-10-07
I could be wrong but I believe the folder has to .fonts (lowercase f) and has to be hidden in order for it to work. If someone can prove me wrong I won't take offense :)

---

### Post by PierreDeKat on 2008-10-07
> **halitech said:**
> I could be wrong but I believe the folder has to .fonts (lowercase f) and has to be hidden in order for it to work. If someone can prove me wrong I won't take offense :)
You know, that might explain why I didn't have to have OpenOffice find the fonts the second time, because that time, I called it ~/.fonts instead of ~/Fonts

So yeah, go with /home/yournamehere/.fonts

---

### Post by Kellemora on 2008-10-07
Hi Rorke

I hate to say this, but whoever it is creating these documents at your college is an IDIOT...............

One of the most BASIC things when Using msWORD is to EMBED the fonts in ALL Portable Documents................

No one using any non-standard font should EVER submit a document for use on other machines, printers or viewers WITHOUT making that Document Portable.......  We have our machines set as EMBED FONT as the DEFAULT setting so it NEVER gets overlooked by mistake.

It's SO SIMPLE to set-up the program to.

Go to Tools - Options - Save Tab, then select EMBED TT FONTS, then save the document.  This will preserve whatever Fonts were used to create the document so that ANYONE who opens it, will SEE the FONTS you intended them to see........

Due to the many variations in printers, it's also a good idea to EMBED the page margins, page breaks, section breaks, etc. as well.

I've NOT had a problem printing from Open Office in Ubuntu with any Documents that started out as msWORD documents, because we EMBED the fonts as standard practice.  We DO use a font for 90% of our work that most folks wouldn't have anyhow, it's NOT a freebee font, but with so many using it, you do find it on a lot of machines that have been in use for a long time.

The solution is to tell the college to PROPERLY PREPARE the Documents for PORTABILITY, since they are Distributing them as Portable!
Or at the very least provide a copy of the fonts they use in their documents to every student receiving those documents.

Embedding fonts is COMMON business practice!

TTUL
Gary

---

