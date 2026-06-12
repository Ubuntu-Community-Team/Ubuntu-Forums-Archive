---
title: "I hate Evince. Can I kill it?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by screamingturnip on 2008-06-09
Can I delete evince without retarding ubuntu? If not where do I go to change defaults to retard evince as to not be the default .pdf viewer?


edit: and I have strange feeling I've posted in the wrong section.

---

### Post by yesudeep on 2008-06-09
What problems are you facing with Evince?

Cheers,
Yesudeep.

---

### Post by sub2007 on 2008-06-09
Yup you can, just uncheck evince in Synaptic. The only catch is it will ask you to remove ubuntu-desktop but it **won't** remove your whole desktop - Ubuntu desktop is just the name of a metapackage (which isn't a package itself - it's a package that just installs a bunch of other packages). Removing it won't remove ANY of the packages unless you ask it to remove them (like in the case of evince) and you can manage quite safely without the ubuntu-desktop metapackage installed.

If you'd prefer not to remove it then you can change your default PDF reader. Right click on a PDF file in your file browser and choose Properties. Then where it says "Open With" change it to your preferred PDF viewer.

---

### Post by screamingturnip on 2008-06-09
> **yesudeep said:**
> What problems are you facing with Evince?

Cheers,
Yesudeep.

It's default format is so friggin magnified that it freezes before I can change the percentage.Also it just annoys me when an OS shoves software down my throat.

oh and thanks sub. For the life of me I couldn't figure that out. Probably will just retard it.

---

### Post by philinux on 2008-06-09
Just use main menu and uncheck it menu item from the list.

---

### Post by GSZX1337 on 2008-06-09
> **screamingturnip said:**
> It's default format is so friggin magnified that it freezes before I can change the percentage.

oh and thanks sub. For the life of me I couldn't figure that out. Probably will just retard it.

What specs do you have? I use evince all the time and I never had any slow downs or hiccups at all. To me, it's even better than Foxit in Windows. 

> Also it just annoys me when an OS shoves software down my throat.
The Ubuntu devs aren't 'shoving it down your throat', I'm sure there's a good reason why they chose evince over other pdf readers.

---

### Post by stchman on 2008-06-09
> **screamingturnip said:**
> Can I delete evince without retarding ubuntu? If not where do I go to change defaults to retard evince as to not be the default .pdf viewer?


edit: and I have strange feeling I've posted in the wrong section.

What is the big problem with Evince?  I use it to view PDFs and it does a good job.

Evince is a pretty small program so deleting it will be of near zero impact to your system.

You can install Adobe Acrobat via Medibuntu.  I have a tutorial that tells you how.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

I need to update and put in the Hardy Medibuntu repo.  Just make this change if you are using Hardy.

```
 sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Use the same key.

You can then install Acrobat.  To make Acrobat the default PDF viewer right mouse click on a PDF and go to properties and select Acrobat over Evince.

---

### Post by RomeReactor on 2008-06-09
Hi. I think installing Acrobat will be more of a problem than Evince; if screamingturnip is having Evince freeze, it may be due to a lack of RAM or processor speed in his system, and Acrobat is known to be more resource intensive than Evince (and Acrobat not being native only makes matters worse).

A search for 'PDF' in Add/Remove showed some results; maybe Xpdf or ViewPDF would be lighter.

---

### Post by FakeOutdoorsman on 2008-06-09
I prefer epdfview over Evince or Adobe Acrobat.  It's small, lightweight, and in the repos:
```
sudo aptitude install epdfview
```

---

### Post by sub2007 on 2008-06-09
Yeah I like epdfview. Unfortunately it doesn't print so I use epdfview for PDFs that I only need to view and xpdf for printing. kpdf is also well worth checking out if you don't mind using KDE apps.

---

### Post by lazyart on 2008-06-09
I hate evince as well.  Often when I try to print a .pdf instead of printing the document it prints an error message.  I can't think of anything as stupid as printing an error instead of just displaying the error.

I moved to Acrobat myself using the above method.  Once you've installed another .pdf handler, right click on a .pdf and get the properties.  From there you can change which application to open all future files of the same type.

---

### Post by Vivaldi Gloria on 2008-06-09
> **lazyart said:**
> Often when I try to print a .pdf instead of printing the document it prints an error message.

That's really weird.

---

### Post by FakeOutdoorsman on 2008-06-09
> **sub2007 said:**
> Yeah I like epdfview. Unfortunately it doesn't print so I use epdfview for PDFs that I only need to view and xpdf for printing. kpdf is also well worth checking out if you don't mind using KDE apps.
I suppose the version from the repos has been compiled without support for printing on my Ubuntu machine, although Hardy has the latest version (0.1.6).  As of 0.1.5 it should support printing using CUPS.  I have 0.1.6 on Arch Linux and printing is available.

---

### Post by Vivaldi Gloria on 2008-06-09
> **FakeOutdoorsman said:**
> I suppose the version from the repos has been compiled without support for printing on my Ubuntu machine, although Hardy has the latest version (0.1.6).  As of 0.1.5 it should support printing using CUPS.  I have 0.1.6 on Arch Linux and printing is available.

I just installed 0.1.6 on Hardy but it has no printing.

---

### Post by Tomas_IV on 2008-06-12
> **FakeOutdoorsman said:**
> I suppose the version from the repos has been compiled without support for printing on my Ubuntu machine, although Hardy has the latest version (0.1.6).  As of 0.1.5 it should support printing using CUPS.  I have 0.1.6 on Arch Linux and printing is available.

What I'm missing in epdfview is the ability to select text in the document. Do you know if this is also a compilation option? Or would anyone recommend a lightweight PDF viewer which supports text selection and searching very well?
Text selection is crucial for me, because I use Stardict to quickly translate selected word when reading foreign language articles. It is the only reason I'm looking for Evince alternative - Evince has a bug when selecting a text in two-column documents (quite frequent layout of scientific paper articles), which makes the translation unusable.

---

### Post by faust99 on 2008-06-12
evince has a memory leak bug in it somewhere. the result is very slow performance at times. on my computer its intermittent- sometimes it works perfectly, at other times it uses up all memory and effectively freezes my computer until i kill it. from memory this became an issue with gutsy. i'd hoped it would be fixed by now but...

---

### Post by vamsibethapudy on 2008-06-12
evince also cant display highlighted pdf files. i just shows a yellow coloured area instead of the words being on top of the colour. & it sometimes get killed if i try to scroll pages quickly or select text randomly.

---

### Post by screamingturnip on 2008-06-14
Technically, I had never tried on my new configuration (which was a vast improvement) however my philosophy is that if it will work well on a shitty computer, it's generally a better app. A simplification perhaps but more of a guideline than a rule. The reason why I was asking was when I went to delete it, the OS was telling me this great story of how vital the program was for reading .pss. I really actually knew "how" to delete it. I was wondering if it was going to turn out to be a linchpin.
Anyways I unselected it from properties. It now defaults to KPDF, basically the first alternative that I found that ddidn't freeze my system.

---

### Post by screamingturnip on 2008-06-14
> **GSZX1337 said:**
> What specs do you have? I use evince all the time and I never had any slow downs or hiccups at all. To me, it's even better than Foxit in Windows. 

Ibm M50 thinkcentre 8187
Pentium 4 2.4GHz
865 G integrated sound and an appalling 56MB video
512 MB 2700 333 ram
40 GB PATA (deceased and buried in my underwear drawer)
CD/DVD-RW PATA
500 GB SATA (all storage)
160 GB (with a 100 gb linux and 50 left over just in case I dance with the devil again)
It also has an unmounted floppy drive that I can't bring myself to remove.

It's named hodgeman because it's what I imagined his character in those Mac, PC ads looked like. I honestly bought it for the IBM chassis which is a breeze to get in and out of.

edit: I wish I didn't come off so negative but it's my nature. I do like ubuntu. It's just that eVince tried to kill my computer and I don't generally let things do that twice unless its gaming related. 

.... crap. Darn my nature.

---

### Post by Nameless_one on 2008-06-20
Btw, because I didn't see it already answered in the thread, you can just right click on a .pdf, go to the Open With tab, and choose another program to view pdfs.

---

