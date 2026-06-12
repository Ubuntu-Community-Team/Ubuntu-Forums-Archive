---
title: "No simple contact info/label printing software?"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by farna on 2012-02-18
I've been tearing my hair out trying to find a simple all-in-one address/contact manager that will also print sheets of address labels. All I'm getting is how to build a database then use mail-merge to do this. There are literally HUNDREDS of SIMPLE Windows programs to do this, but I can't find EVEN ONE that is native Linux! Surely someone has done this? Anyone have a recommendation (other than making my own database)??

The closest I found to what I want/need is Rubrica ([http://rubrica.berlios.de/index.html](http://rubrica.berlios.de/index.html))...  but it has no printing function at all. Perfect for entering and storing the data. According to the website, "XML is used to store the data". I'm assuming I could use that database and OO word processor to print labels? [B]I'm really looking for a push-button solution though. 
[/B] 
Might just have to reformat the #$%%$^  computer and kill Ubuntu... go back to Windows. It's absolutely frustrating that this one simple task is stalling me so much! I write a small hobby publication and thought that DTP would be the big hurdle, not something that so darned simple!

I bought PageStream STP software because I wasn't sure of the stability of Scribus. I've been following Scribus development for the past couple years, things seem to change more often than I'd like. PageStream is a lot more stable.

---

### Post by Matt__ on 2012-02-19
There are numerous plugins for GIMP that deal with labels.

[This one looks quite comprehensive]("http://blog.worldlabel.com/2009/fast-labels-and-card-layout-with-gimplabels-open-source.html") but you will have to find out as I've not used it myself.

There is also a small list of other options at the bottom of the page.

You could also try [Libreoffice Templates](http://templates.libreoffice.org/template-center?getCategories=Labels&getCompatibility=any&sort_on=positive_ratings&path=%2FLibreOffice-Templates%2Ftemplate-center&portal_type=PSCProject&SearchableText=)

---

### Post by farna on 2012-02-19
Basically what I'm running into is that a combined address/contact information database with label printing capabilities simply DOES NOT EXIST for Linux. All solutions combine using two separate programs, one for collecting/compiling the data and another for printing, usually with the third step of exporting the database to a CSV file (comma delimited data file) between the two. Oh, I could learn scripting and combine the two in a more or less automated fashion though. 

It's not too difficult to do the above, and I might... or I might just use Libre Office Base (or the spread sheet)and try my hand at creating a data base... and will pretty much have to do the same -- use Base (or spread sheet) for data entry then use Writer to print the labels, but shouldn't have to translate the data between. Just a different way of doing things, and totally unexpected. 

What just seems so absurd is that there are literally a hundred or more simple programs to do this for Windows and I can't find even one for Linux! It just seems so simple... and common... for anything but Linux. You'd think that the PIMs and contact managers would be able to print labels!

---

### Post by Zill on 2012-02-19
> **farna said:**
> ...It just seems so simple... and common... for anything but Linux. You'd think that the PIMs and contact managers would be able to print labels!
On the surface your comments seem valid.  However, we must remember that most open-source software is produced by teams of *unpaid* developers who, generally, work on whatever they wish to work on.  This means that, as users, we cannot *demand* that a certain product or function is provided for *our* convenience - after all, we aren't paying for it. ;-)

Personally, I am very grateful to the army of developers who *have* produced all the FOSS that we use today in our Linux distributions.  If you wish to assist in this effort and incorporate your ideas then I am sure the teams will be glad to hear from you.

Finally, returning to your original question, it isn't particularly difficult to use a spreadsheet as a data source for a mail-merged document which prints labels - I do this every Christmas. ;-)

Alternatively, if your address data is already in Evolution then *some* versions of Open/Libre Office can use this directly as a data source.

---

### Post by wolfen69 on 2012-02-19
Glabels is a great label making/business card app, but does not do anything else. Consider it.

---

### Post by JKyleOKC on 2012-02-19
> **farna said:**
> What just seems so absurd is that there are literally a hundred or more simple programs to do this for Windows and I can't find even one for Linux! It just seems so simple... and common... for anything but Linux. You'd think that the PIMs and contact managers would be able to print labels!I suspect you're encountering the "Unix philosophy" for the first time; it's quite different from the approaches taken by "classical" PC software publishers such as Apple and Microsoft, who produce monolithic programs that have all sorts of features included in a single package.

Unix was the ancestor (philosophically at any rate) of Linux, and the Unix philosophy has been part of it from the earliest days. Its guiding principle is to create small programs that do just one thing but do it very well, and then chain such programs together as needed to do any specific task at hand.

For instance, to take a file of data that's in random order and produce a sorted printout with all duplicate lines removed, the Unix approach would be to chain "cat," "sort," "uniq,", and "lpr" together in a "pipeline." The cat program would read the file, pass its content to sort for sorting, then uniq would eliminate the duplicate lines, and finally lpr would send the result to the printer.

If you needed this done fairly often, a one-line script file could handle it, and could be used just as if it were a single program.

This approach is actually quite a bit more efficient for all concerned, when compared to the single large program that does almost everything. The small programs can be refined to do their single jobs exceedingly well, while the big program may well have a few dozen hidden bugs that show up only occasionally. This also makes it possible to create customized arrangements that do exactly what you want them to, rather than being forced to choose from a limited range of choices set by developers elsewhere.

However, it's very different from what most of us were used to seeing before we came to Linux, and it does take a bit of time to become comfortable with it.

---

### Post by farna on 2012-02-20
Jim, you pretty much hit the nail on the head. I came up with other than MS-DOS/Windows based machines -- the little Tandy Color Computer mainly. Did a little BASIC programming on it, enough to even sell a few programs, but that's about my programming limit. I did one big project, a specialized genealogy database with reports printing. Due to the limited memory (128K on a CoCo3), I had to do something similar. There was a menu program that called various programs that did specific tasks, but it appeared pretty seamless to the user.

I realize it's not difficult to use one program for data and another for printing, but it was very frustrating not finding something as one integrated program when I expected to. I mean a label program that doesn't print just doesn't seem logical! Makes a bit more work for me, but I do realize that once I set it all up the process will be pretty easy. Just have to get used to a different way of thinking about things. 

But I still say something this simple should be "fixed"... wish I had the skill to fix it, but I did just enough programming in BASIC (and I know line number BASIC isn't very comparable to anything we have now!) to realize that programming isn't my cup of tea! I struggled for a year writing that genealogy program, and I had an old GW-BASIC program to use as a framework, and it was all text screens! I had originally thought I could port the GW-BASIC program over since the CoCo used a simplified version of MS BASIC, but the code was WAY different and 90% had to be totally re-written. I did give the GW-BASIC author credit... put a line in that said "based on xxx program by xxx". 

Maybe a simple script would work to more or less link Rubrica (for data entry) and GLabels (for printing). Then that would be a THIRD "program" to call! Those two need integrating in a more or less seamless way...  Oh well, it's not going to get done before I need to switch! For the time being I still have my old XP machine running and will print my labels through it until I have time to set everything up in Linux.

---

### Post by Zill on 2012-02-21
> **farna said:**
> ...Maybe a simple script would work to more or less link Rubrica (for data entry) and GLabels (for printing). Then that would be a THIRD "program" to call! Those two need integrating in a more or less seamless way...
You really don't *need* to write scripts to print address labels!

This can be done easily with LibreOffice.  See this [howto]("http://blog.worldlabel.com/2012/mail-merge-address-labels-in-the-excellent-free-libreoffice.html") for more info.

---

