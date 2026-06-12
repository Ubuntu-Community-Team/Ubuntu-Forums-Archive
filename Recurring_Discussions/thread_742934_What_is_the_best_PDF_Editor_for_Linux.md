---
title: "What is the best PDF Editor for Linux?"
date: 2008-04-02
forum: Recurring Discussions
---

### Post by Hutom on 2008-04-02
I need to make corrections on Latex generated papers for proof reading. Earlier I used Adobe editor. That was fine. i am looking for something that can substitute it.
I used PDFedit. It is not good. Breaks too often.

---

### Post by 23meg on 2008-04-02
Inkscape 0.46 works.

---

### Post by ComputerHermit on 2008-04-02
I had a app for work to fill out and I had no ink in the printer so I google 
and this is what I used worked great
[http://sourceforge.net/projects/pdfedit]("http://sourceforge.net/projects/pdfedit")

---

### Post by Hutom on 2008-04-02
> **23meg said:**
> Inkscape 0.46 works.

hmm. Heard about it never used though. But is it not more of a drawing tool? I need to make corrections on Latex generated papers for proof reading. Earlier I used Adobe editor. That was fine. i am looking for something that can substitute it.

---

### Post by aeiah on 2008-04-02
inkscape is akin to adobe illustrator yea. its for vector art, but it has other functionality. the newest version (probably not in the repos) does offer pdf editing apparently. when i have time im gonna test it and hope to roll out a version here. adobe editor costs far too much

---

### Post by rubinstein on 2008-04-02
Inkscape repository for Gutsy (newest version):

deb [http://ppa.launchpad.net/inkscape.testers/ubuntu](http://ppa.launchpad.net/inkscape.testers/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/inkscape.testers/ubuntu](http://ppa.launchpad.net/inkscape.testers/ubuntu) gutsy main

---

### Post by Hutom on 2008-04-02
If I get some name then I can try them. By the way, what about kword? How is it?
Thanks.

---

### Post by hugmenot on 2008-04-03
How do you make corrections in a PDF file with Acrobat? Do you edit the text, oder do you make annotations?

---

### Post by Hutom on 2008-04-23
> **hugmenot said:**
> How do you make corrections in a PDF file with Acrobat? Do you edit the text, oder do you make annotations?

Annotations. There are quite a few options to put a comment with acrobat and those are really handy. I am looking for a pdf editor for Ubuntu which allows me put similar kind of comments.

---

### Post by hugmenot on 2008-04-23
Something is scheduled for next Evince release:
[http://live.gnome.org/Evince/Roadmap](http://live.gnome.org/Evince/Roadmap)

---

### Post by Atreus12 on 2008-04-23
If you're just doing something really easy like clipping pages out or reordering pages, pdftk is great. It's a command line tool.

For example, to remove page 4 of an 8 page pdf (example.pdf), use the following:
```
pdftk example.pdf cat 1-3 5-end output new_pdf_file.pdf
```

To combine pdf's first_file.pdf and second_file.pdf into first_and_second_file.pdf, so the following:
```
pdftk first.pdf second.pdf cat output first_and_second.pdf
```

Easy as pie, and I find it really useful.

Andrew

---

### Post by jrusso2 on 2008-04-23
I am surprised no one has mentioned pdfedit

---

### Post by p_quarles on 2008-04-23
> **jrusso2 said:**
> I am surprised no one has mentioned pdfedit
3rd post . . .

---

### Post by eddin on 2008-04-23
I use Foxit in Windows. It has a linux version too. The reader is free. Extra functions like editing and annotation cost money. You can still use these extra functions, but foxit watermark your document with a reminder.

---

### Post by Hutom on 2008-04-24
Thanks to all of you for responding. I'll try these softwares and come back with my experience.

---

### Post by linuxlr on 2009-02-24
PDF Studio is a very complete PDF editor for Linux. But you have to pay for the developers as it is commercial software, costs $60 or $48 for academia / non-profit. 

[http://www.qoppa.com/psindex.html]("http://www.qoppa.com/psindex.html")

---

### Post by Simian Man on 2009-02-24
LaTeX, though it has a bit of a learning curve.

---

### Post by john_spiral on 2009-02-24
Scribus might be useful for complex visual edits.

---

### Post by paulchinnz on 2009-02-27
I want to be able to highlight and leave comments on pdf documents. Have found both PDFedit and Kword substandard. Maybe just not using it right.

With PDFedit the highlight tool just wouldn't work (click with highlight on and the entire line would highlight briefly before disappearing, and anyway I only wanted to highlight two words).

Kword did a poor job opening/converting my pdfs, multiple different fonts in one sentence in any particular paragraph (okay slight exaggeration but you get the idea).

I don't see anything else that's free in Linux for this (I guess that's no worse than with Windows).  Anyone with any other suggestions?

---

### Post by odda on 2009-02-27
> **Hutom said:**
> Breaks too often.

I once tried running PDFedit in Gnome, later found out it was a KDE app

---

### Post by paulchinnz on 2009-02-27
Hmm I'm running Ubuntu/Gnome ... how can I get PDFedit to run properly with it?

---

### Post by vpraveen84 on 2009-09-18
You can try xournal. Its available in the ubuntu repo, but its most useful if you have a tablet pc or atleast a wacom. You can delete pages, annotate & highlight pages, and import/export as pdf.

---

### Post by ve4cib on 2009-09-18
For simple annotations/filling in forms (when the PDF is designed to be printed and filled in by hand) Xournal is pretty good.  I use it all the time for RPG character sheets.

For anything more complicated than simple annotations I'm pretty sure Xournal would be insufficient though.  You can check it out though.

---

### Post by paulchinnz on 2009-09-18
Thanks for the Xournal suggestion. Highlighting is 'freestyle', but hey it's free, can't complain.

---

### Post by Yeti can't ski on 2009-09-19
If the idea is not changing the text of the file but simply adding, removing or rotating pages of a pdf document then Pdf-Shuffler is just perfect, even simpler and more user friendly than Adobe tools [http://ubuntuforums.org/archive/index.php/t-1105927.html]("http://ubuntuforums.org/archive/index.php/t-1105927.html") 

Two thumbs up!

---

### Post by Viva on 2009-09-19
In addition to those already mentioned, the latest openoffice can edit/create pdf files too.

---

### Post by mmix on 2009-09-19
web-browser + one of web pdf editor(below)

[quote="[wikipedia](http://en.wikipedia.org/wiki/List_of_PDF_software)"]   

    * DocQ – free online application to store, view, edit and share PDFs
    * PDFescape – a free web service which views and edits PDF documents in the browser
    * PDFFiller – a web-based program that allows the user to read, edit or fill out PDF forms from within the browser.
    * PDFVue – a free web application that allows the user to view PDF's, comment and fill PDF forms from a web browser.
[/quote]

---

### Post by paulchinnz on 2009-09-19
OOo 3 can edit PDFs? All I get opening a PDF with OOo is a mess of characters. How do you edit PDFs with OOo?

---

### Post by dragos240 on 2009-09-19
Openoffice?

---

### Post by moodle on 2009-09-22
[Mendeley]("http://www.mendeley.com") is the best linux pdf editor for academics.

With it you can:

- Create a library of .pdf files
- Export libraries or bibliographies to .bibtex for use in latex
- Highlight text in .pdf files
- Insert notes in .pdf files

Best of all, it's completely free.

To install on Ubuntu 9.04, open the terminal and type:

```
sudo gedit  /etc/apt/sources.list

```You might need to enter your password.

At the bottom of the sources.list file that opens in gedit, type:
```
deb http://www.mendeley.com/repositories/xUbuntu_9.04 /
```Save the file. Then go back to your terminal and type:

```
sudo apt-get update
```    ```
sudo apt-get install mendeleydesktop
```To launch Mendley, open the terminal and type:
```
mendeleydesktop
```

---

### Post by paulchinnz on 2009-09-22
Mendeley looks very impressive at first glance, almost as if all my birthdays had come at once. Thanks moodle!

If this works out, all I need for full Ubuntu integration is a mature GUI-enabled equivalent to GraphPad Prism, SPSS and Matlab, but that's a topic for another day...

---

### Post by sdowney717 on 2009-09-22
to use pdf with open office, you need the pdf extension installed

[http://wiki.services.openoffice.org/wiki/Pdf_Import_Extension](http://wiki.services.openoffice.org/wiki/Pdf_Import_Extension)

---

### Post by meho_r on 2009-09-22
I tried all that is available for Linux regarding pdf editing and none solution was satisfactory. It is true that one can make a .pdf file from any app, but the problem here is how to edit already created document. Inkscape is good, but limited. OpenOffice addon have serious problems with importing .pdf (I didn't expected it'll work). Scribus often crashes when opening .pdf or import trash... Couple of days ago I was about to perform a trivial task: changing header and footer in a .pdf file and the best solution among all tools available was manually changing it for every page in pdfedit! There were 500 pages :(

However, recently I discovered an application, [**Infix**]("http://www.iceni.com/infix.htm") (actually the first app for which I'm willing to pay since using Ubuntu and FLOSS, because it is worth it to the last cent). Apart from "standard" small editing of text, adding comments, annotations etc. one can actually work with text (believe it or not) as in a word editor! Amazing! Think of changing text, moving it around, setting indents, changing spacings, alignment, rearranging text boxes, linking them etc. A particular feature that I like so much is merging boxes. I would dare to say, Scribus or even OpenOffice for pdf editing :D I worked with Adobe Acrobat, but this little guy beats it almost at every front ;) So, if you're in need and want to make extensive changes in .pdf files, I strongly recommend to check it out. There is a short demonstration on the webpage and demo version is available for download.

P.S. Although intended for Windows, works perfectly through Wine.

---

### Post by Antiqua amans on 2009-09-22
Hello, I tried to install Mendeley with the notes posted in this thread, but I it didn't work at all ... what am I doing wrong? :confused:

---

### Post by hugmenot on 2009-09-22
> **meho_r said:**
> ... Couple of days ago I was about to perform a trivial task: changing header and footer in a .pdf file and the best solution among all tools available was manually changing it for every page in pdfedit! There were 500 pages :(

However, recently I discovered an application, [**Infix**]("http://www.iceni.com/infix.htm") (actually the first app for which I'm willing to pay since using Ubuntu and FLOSS, because it is worth it to the last cent). Apart from "standard" small editing of text, adding comments, annotations etc. one can actually work with text (believe it or not) as in a word editor! Amazing! Think of changing text, moving it around, setting indents, changing spacings, alignment, rearranging text boxes, linking them etc. A particular feature that I like so much is merging boxes. 

Dude, if you are doing all that to a PDF you&#8217;re doing it wrong. PDF isn&#8217;t meant to be edited, you know that, do you?

---

### Post by meho_r on 2009-09-22
> **hugmenot said:**
> Dude, if you are doing all that to a PDF you&#8217;re doing it wrong. PDF isn&#8217;t meant to be edited, you know that, do you?

Actually, sometimes you don't have a choice. When you get huge documentation which need to have some correction and you don't have source, what else you can do? Not to mention material created with some "exotic" apps and styles and fonts that cannot be resembled or obtained. I mentioned a simple example of changing headers, what will you do?

---

### Post by thesuhail on 2009-09-23
A Good PDF Editor in market now...

I had been looking for a good PDF editor in linux for a long time. In addition to a bunch of my favorite features, I was searching for a product that is stable, fast and is easy to use. Among the host of features, I was particular about highlighting, graphical annotations, comments and baloon notes insertion capabilities so I can very easily highlight, mark and add review comments to tons of research papers that I read and review regularly. 

The first tool that I tried was "pdfedit" obviously because it was free. I commend the pdfedit development team for taking initiative and creating the pdfedit software. pdfedit offers many features but falls short in satisfying my top three criteria. 

I then started searching for commercial solutions. After downloading trial versions and trying out many, I finally homed in on pdfstudio from  Qoppa Software([http://www.qoppa.com](http://www.qoppa.com)). The very first run of the trial version caught my attention. Easy to use and yet, it offered many powerful PDF editing features. It has remained stable and has won me so far. I learned that it is targetted to work on hosts of operating systems - linux, mac and windows.

Hopefully, others in the market will catch up soon to understand customer's needs and meet expectations as pdfstudio does. I am certainly looking forward to seeing that come from others(including pdfedit folks).

Suhail

---

### Post by vpraveen84 on 2009-09-24
Mendeley is awesome. Best part, it seems stable and well developed, and does what we want - highlight and add notes. For other manipulation (adding, removing pages), I can use pdftk !

I've used jabref before, but this seems like the best reference database + pdf editor I've seen till now for linux.

Thx !

> **moodle said:**
> [Mendeley]("http://www.mendeley.com") is the best linux pdf editor for academics.

With it you can:

- Create a library of .pdf files
- Export libraries or bibliographies to .bibtex for use in latex
- Highlight text in .pdf files
- Insert notes in .pdf files

Best of all, it's completely free.

To install on Ubuntu 9.04, open the terminal and type:

```
sudo gedit  /etc/apt/sources.list

```You might need to enter your

At the bottom of the sources.list file that opens in gedit, type:
```
deb http://www.mendeley.com/repositories/xUbuntu_9.04 /
```Save the file. Then go back to your terminal and type:

```
sudo apt-get update
```    ```
sudo apt-get install mendeleydesktop
```To launch Mendley, open the terminal and type:
```
mendeleydesktop
```

---

### Post by meho_r on 2009-09-24
> **vpraveen84 said:**
> Mendeley is awesome. Best part, it seems stable and well developed, and does what we want - highlight and add notes. For other manipulation (adding, removing pages), I can use pdftk !

I've used jabref before, but this seems like the best reference database + pdf editor I've seen till now for linux.

Thx !

You guys completely missed the point/thread. Mendeley is NOT a pdf editor but reference database/manager. Adding notes and comments (which is available only from that very application /its database, not .pdf file itself/ and invisible for any other -- try seing that note in Adobe Reader or Evince) cannot make an app editor. You can add notes and highlights in Okular too, but it is still just a pdf viewer. Pdfedit, pdfstudio, Infix... are pdf editors.

---

### Post by Chronon on 2009-09-24
> **meho_r said:**
> Actually, sometimes you don't have a choice. When you get huge documentation which need to have some correction and you don't have source, what else you can do? Not to mention material created with some "exotic" apps and styles and fonts that cannot be resembled or obtained. I mentioned a simple example of changing headers, what will you do?

If I was charged with maintaining documentation and didn't have the source, I would extract the plain text and apply an appropriate LaTeX style sheet to allow me to properly maintain it.  Editing PDFs is not a viable long term strategy for maintaining documentation.

On the other hand, I do understand that sometimes doing things "the right way" isn't viable due to time or other practical constraints.  However, tools like this are a sort of kluge, in my view.

---

### Post by meho_r on 2009-09-24
> **Chronon said:**
> If I was charged with maintaining documentation and didn't have the source, I would extract the plain text and apply an appropriate LaTeX style sheet to allow me to properly maintain it.  Editing PDFs is not a viable long term strategy for maintaining documentation.

On the other hand, I do understand that sometimes doing things "the right way" isn't viable due to time or other practical constraints.  However, tools like this are a sort of kluge, in my view.

Agreed. I often use pdfpages with LaTeX for some editing and retaining pages that do not need any changes. Exporting plain text isn't such a nice solution in many cases. When a document has full-blown headers and footers and different scripts than latin, it is in most cases mess of a text when exported. All gets mixed up, text, headers, footers, page numbers... This is where pdf editors have an advantage. And I don't think of them as kludge since they (Infix mostly) saved me countless hours of unnecessary work.

BTW, in my case, it's one-time-editing in most cases so no need for long-term strategy about maintaining.

---

### Post by paulchinnz on 2009-09-24
> **meho_r said:**
> You guys completely missed the point/thread. Mendeley is NOT a pdf editor but reference database/manager. Adding notes and comments (which is available only from that very application /its database, not .pdf file itself/ and invisible for any other -- try seing that note in Adobe Reader or Evince) cannot make an app editor. You can add notes and highlights in Okular too, but it is still just a pdf viewer. Pdfedit, pdfstudio, Infix... are pdf editors.

Strictly speaking I agree with you meho_r, but for practical purposes _for me[U]_[/U] it highlights and adds notes. It's not quite there yet e.g. 1) when at the bottom or top of a page, depending on how one is viewing the section, the highlight tool doesn't work 2) the word search 'crashed' on me 3) the naming of files leaves much to be desired. But it's a beta, it's free, so not complaining!

---

### Post by Chronon on 2009-09-24
> **meho_r said:**
> 
BTW, in my case, it's one-time-editing in most cases so no need for long-term strategy about maintaining.

I can understand the logic in this case.

---

### Post by moodle on 2009-09-24
> **Antiqua amans said:**
> Hello, I tried to install Mendeley with the notes posted in this thread, but I it didn't work at all ... what am I doing wrong? :confused:

I'm not sure exactly.

You can also add 
deb [http://www.mendeley.com/repositories/xUbuntu_9.04](http://www.mendeley.com/repositories/xUbuntu_9.04) / 
to the Third Party Repositories list in Synaptic Package Manager, then install in the terminal as I explain in the rest of my post.

Instructions are also available on Mendeley.com.

---

### Post by moodle on 2009-09-24
> **meho_r said:**
> You guys completely missed the point/thread. Mendeley is NOT a pdf editor but reference database/manager. Adding notes and comments (which is available only from that very application /its database, not .pdf file itself/ and invisible for any other -- try seing that note in Adobe Reader or Evince) cannot make an app editor. You can add notes and highlights in Okular too, but it is still just a pdf viewer. Pdfedit, pdfstudio, Infix... are pdf editors.

I agree, we partly missed the point.  But I said Mendeley is the best .pdf editor for academics, not the best overall .pdf editor.  Most academics are simply looking to highlight .pdf documents and add notes.

Mendeley would be better if the notes and highlights were added directly to the .pdf file.  But until Linux catches up with Windows options such as Adode Reader and FoxIt Reader (I was shocked to find evince doesn't have highlight or notes functions), Mendeley is the best option.

---

### Post by meho_r on 2009-09-24
> **moodle said:**
> I agree, we partly missed the point.  But I said Mendeley is the best .pdf editor for academics, not the best overall .pdf editor.  Most academics are simply looking to highlight .pdf documents and add notes.

Mendeley would be better if the notes and highlights were added directly to the .pdf file.  But until Linux catches up with Windows options such as Adode Reader and FoxIt Reader (I was shocked to find evince doesn't have highlight or notes functions), Mendeley is the best option.

Okular actually has an option to export .pdf file together with all metadata (i.e. notes, highlights etc.) so it can be shared with others. The caveat is that only Okular understands it, so the other party must use Okular too.

---

### Post by vpraveen84 on 2009-09-24
It doesn't matter if it is a reference manager, it can still export as pdf, and does the job pretty well too. There are hardly any "good" free pdf editors for linux; I might as well use this. 

> **meho_r said:**
> You guys completely missed the point/thread. Mendeley is NOT a pdf editor but reference database/manager. Adding notes and comments (which is available only from that very application /its database, not .pdf file itself/ and invisible for any other -- try seing that note in Adobe Reader or Evince) cannot make an app editor. You can add notes and highlights in Okular too, but it is still just a pdf viewer. Pdfedit, pdfstudio, Infix... are pdf editors.

---

### Post by rifak on 2009-09-25
Mendeley was exactly what i was looking for. a simple, straight forward highlighter and annotator/notes. it works really well

---

### Post by mustaqil.ali on 2009-09-25
> **moodle said:**
> 
Mendeley would be better if the notes and highlights were added directly to the .pdf file.  But until Linux catches up with Windows options such as Adode Reader and FoxIt Reader (I was shocked to find evince doesn't have highlight or notes functions), Mendeley is the best option.
The option to actually save the notes and highlights you make to a PDF file already exists within Mendeley. Open the annotated PDF, and then go to the File menu, and click on "Export with Annotations".

---

### Post by meho_r on 2009-09-26
There is a big difference between **editing** tools and **reviewing** tools. Mendeley Desktop is a great app (I've been using it for some time now and I'm very satisfied with it), but it does NOT **edit** .pdf documents but only does some markup/adding notes, highlights etc. In fact, the only thing that can be considered as editing in Mendeley Desktop is rotating pages. If you consider these things as editing, you're wrong. When you **edit** a .pdf document that means that you do some kind of manipulation of its key elements (text, pictures etc.) and its structure (and, of course, do that in .pdf itself, not just editor's database). Because of that, I still think that mentioning Mendeley here is totally off-topic. You should start a thread about best reference managers for Linux.

---

### Post by paulchinnz on 2009-09-26
> **meho_r said:**
> There is a big difference between **editing** tools and **reviewing** tools. Mendeley Desktop is a great app (I've been using it for some time now and I'm very satisfied with it), but it does NOT **edit** .pdf documents but only does some markup/adding notes, highlights etc. In fact, the only thing that can be considered as editing in Mendeley Desktop is rotating pages. If you consider these things as editing, you're wrong. When you **edit** a .pdf document that means that you do some kind of manipulation of its key elements (text, pictures etc.) and its structure (and, of course, do that in .pdf itself, not just editor's database). Because of that, I still think that mentioning Mendeley here is totally off-topic. You should start a thread about best reference managers for Linux.

I know where you're coming from but actually for me and it seems at least a few others the inaccuracy in suggesting Mendeley on this forum was fine; all I'm after is something that will do highlighting and note-taking personally for me. Completely on-topic in my opinion. However, a _debate of what exactly is a PDF editor_ threatens to become the off-topic topic.

---

### Post by meho_r on 2009-09-27
> **paulchinnz said:**
> I know where you're coming from...

Hmmm... Care to explain what exactly you have in mind?

> ...but actually for me and it seems at least a few others the inaccuracy in suggesting Mendeley on this forum was fine; all I'm after is something that will do highlighting and note-taking personally for me. Completely on-topic in my opinion.

If it is what OP had in mind when started this thread, then it's OK. Mentioning Mendeley here is useful, of course. Off-topics actually can be useful in many cases.

> However, a _debate of what exactly is a PDF editor_ threatens to become the off-topic topic.

That was a clarification, not beginning/looking for a debate, don't worry :)

---

### Post by paulchinnz on 2009-09-27
> **meho_r said:**
> Hmmm... Care to explain what exactly you have in mind?
I believe you've indicated that Mendeley is more a PDF organiser and doesn't actually edit (in the strictest sense) the PDF. In this respect you've made some more accurate and useful suggestions.

> **meho_r said:**
> If it is what OP had in mind when started this thread, then it's OK. Mentioning Mendeley here is useful, of course. Off-topics actually can be useful in many cases.
Perhaps we should refer back to Hutom. It seems unlikely that the Hutom meant highlighting and note-making for him/herself, but I don't feel the post is not specific enoguh to exclude these tasks. We return to the question of whether mentioning a program that does these tasks without actually changing the document is actually on or off-topic.

> **meho_r said:**
> That was a clarification, not beginning/looking for a debate, don't worry :)
No worries, I was using debate in the loosest manner, perhaps discussion is a better term. Anyway, I'll leave it at that, we probably should start another thread if we want to continue this.

---

### Post by Poyntz on 2009-11-25
You mentioned PDFViewer - as far as I know, this doesn't edit per se, but does what Okular does (unless you have the full version). and Okular is native to linux! (so you needent worry about wine's incompatibilities)

For annotation: Okular (and you can highlight in different colours, make comments, etc)
For creation: OpenOffice.org3 Writer, and export to PDF

Not sure why you'd want to edit a PDF per se (I've never needed to do it myself, and you run the risk of plagiarising others' content). I'd recommend you compile from scratch in OpenOffice.org3, your material, and reference material from PDF's if need be. With Okular you can bookmark pages and keep a tab of any highlights/comments that require tabulation.

Good luck! :o

---

### Post by gnomeuser on 2009-11-25
[PdfMod](http://live.gnome.org/PdfMod) might be an app to watch in this arena.

---

### Post by irate.turtle on 2009-11-27
We really need a good pdf editor within linux.

I tried **mendeley** and when I exported the pdf (with annotations) and viewed it from evince, *_the highlights were above the text instead of below it_*. 

**ooffice** *_doesn't open half the files and if it does hardly does what you need_*.

the closest came **PDFescape** online and free. But being *online* it is cumbersome. It has *_no highlighting_* and *_the whiteout option (which is very cool) is only free flowing_*. (*free flowing is useful many times but cumbersome for text*)

so in the end we really need a good pdf editor which opens the pdf files does editing (highlight, comment, whiteout at the least) and produces pdf which consistently look the same on any other pdf viewer.

---

### Post by HermanAB on 2009-11-27
I've used the OpenOffice PDF edit plugin lately and it works pretty good.  Another option is to edit PDFs with The Gimp.

---

### Post by Poyntz on 2009-11-30
> **irate.turtle said:**
> We really need a good pdf editor within linux.
why? 


> **irate.turtle said:**
> **ooffice** *_doesn't open half the files and if it does hardly does what you need_*.
that's why you should get okular ;)

> **irate.turtle said:**
> the closest came **PDFescape** online and free. But being *online* it is cumbersome. It has *_no highlighting_* and *_the whiteout option (which is very cool) is only free flowing_*. (*free flowing is useful many times but cumbersome for text*)
i don't get why you don't just create a file through ooffice. take Windows 7 for example. its main security vulnerability is PDF files. why do you need to produce documents in a format that most people can't edit?

> **irate.turtle said:**
> and produces pdf which consistently look the same on any other pdf viewer.
I definitely agree here

---

### Post by Gendor on 2009-11-30
I've just tried out Xournal, and it seems to get the job done with regards to highlighting and annotations. Annotations and highlights saved to pdf opens correctly in other PDF viewers.

---

### Post by theDaveTheRave on 2009-12-18
> **paulchinnz said:**
> Mendeley looks very impressive at first glance, almost as if all my birthdays had come at once. Thanks moodle!

If this works out, all I need for full Ubuntu integration is a mature GUI-enabled equivalent to GraphPad Prism, SPSS and Matlab, but that's a topic for another day...

That would be really nice!

I know that R is a great stats tool, but being 100% command can be hard work. sorry a little off topic...!

My first linux for my desktop had a PDF editor included, that seemed to work really well (can't remember if it was on Caldera or Suse 7.0 ??)

I seem to recall it was related to "GhostView" in some way (If I remember correctly it was called "GhostWriter"??) but it seems not to exist anymore ??

However I normally use the GIMP for adding details... don't know how it handles opening multiple pages though (ie moving from one page to the next).

I guess you could save each page as an image, edit the image, import back into OO writer and then export from there back to a PDF (but just thinking about that method makes my head hurt!).

Must try Xournal and / or Mendelay at some point....

David

---

### Post by zerubbabel on 2009-12-23
The pdf-XChange Viewer ([http://www.docu-track.com/](http://www.docu-track.com/)) is an excellent pdf editor, better than Adobe Acrobat Pro in my view. The free version allows annotations, and the "pro" version ($34.50) supports extensive editing. It runs very well under Wine, and is much easier to use than all of the other suggested pdf editing tools I've seen referenced in the various forum threads on this topic. I've tried them all, and I keep going back to pdf-XChange. It's the only Windows application I still regularly use.

---

### Post by paulchinnz on 2009-12-23
> **zerubbabel said:**
> The pdf-XChange Viewer ([http://www.docu-track.com/](http://www.docu-track.com/)) is an excellent pdf editor, better than Adobe Acrobat Pro in my view. The free version allows annotations, and the "pro" version ($34.50) supports extensive editing. It runs very well under Wine, and is much easier to use than all of the other suggested pdf editing tools I've seen referenced in the various forum threads on this topic. I've tried them all, and I keep going back to pdf-XChange. It's the only Windows application I still regularly use.

Having trialed Mendeley for a couple of months now, one can understand it's 0.x status. At first glance PDF-XChange seems good - great speedy rendering (still one of Mendeley's great weaknesses in my opinion), lots of tools even for a free version, small hard drive footprint. Great suggestion, great Christmas present!

---

### Post by psrivats on 2010-01-18
> **Atreus12 said:**
> If you're just doing something really easy like clipping pages out or reordering pages, pdftk is great. It's a command line tool.



pdftk is probably the easiest way to add/remove pages or concatenate multiple pdf files. I've been using it for years. Here is a bigger set of examples:

[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

However, you can't annotate/highlight etc.

---

### Post by milia on 2010-03-07
Xournal and pdftk.

Thankfully I could safely import a 100 paged pdf to Xournal, 
delete page by page the most of them, and export the remained document to a pdf.

Thus, Xournal was the best for this job, but pdftk for merging lots of pdf's into one.

ps: pdfeditor crashed while I tried to delete a page. Total Fail !

---

### Post by dragos240 on 2010-03-07
oowriter

---

### Post by CoolRat33 on 2010-04-03
I've used Qoppa's PDF Studio for 2 years and am very pleased with its abilities. Its not free or open source, nor is it inexpensive. But it really is full-featured and runs well on my Linux system and on Windows 7 too. 

I needed a PDF application that would allow me to annotate, highlight text, and make comments on documents. This is the only application that I found that can do this on Linux.

---

### Post by pakki on 2010-04-19
i use foxit pdf editor 2.0 & pdf xchange viewer pro under wine works awesome pm me if u want to have this applications

---

### Post by Charlotte18 on 2010-04-24
Flpsed will let you type on a PDF. Pdfedit is probably the best though.

Btw, besides reordering and rotating pages, what can PDF Mod do? I have a hard time seeing the purpose of this app.

---

### Post by meho_r on 2010-04-24
> **pakki said:**
> i use foxit pdf editor 2.0 & pdf xchange viewer pro under wine works awesome pm me if u want to have this applications

You do know that you aren't allowed to pass these apps to another party, do you? Read terms you agreed with when purchased them. Since your signature contains a citation by Iqbal, here's a hint for you regarding this: Q. 5:1 ;) Of course, if you haven't obtain these apps through any legal means, then think about Q. 5:38.

> **Charlotte18 said:**
> ...
Btw, besides reordering and rotating pages, what can PDF Mod do? I have a hard time seeing the purpose of this app.

Well, it seems the purpose of PDF Mod is just that: reorder, rotate, and remove pages, export images from a document, edit the title, subject, author, and keywords, and combine documents via drag and drop.

I don't think we should expect a decent pdf editor for Linux until [GNU PDF](http://www.gnupdf.org/Main_Page) project stands on its feet.

---

### Post by HermanAB on 2010-04-24
Hmm, I don't think there is a 'Best PDF Editor' for Linux - only a less worst one...

---

### Post by Chromagnum on 2010-04-24
**1st scenario:** _creating pdf document from ground zero._
[INDENT]If I want to create a pdf document, I just do it with OpenOffice. Of course I'd save the document in odt (native OpenOffice file) as well for future editing.[/INDENT] 
**2nd scenario:** _edit existing pdf document (source originally from somewhere else)_
[INDENT]I just simply convert the pdf to rtf using calibre, open the rtf file in OpenOffice, do a little editing (change font, add some lines, insert image, delete page, etc), and then create a pdf out of it. And for the future editing (if necessary) save the change to rtf as well, or odt. [/INDENT]

---

### Post by meho_r on 2010-04-24
> **Chromagnum said:**
> ...
**2nd scenario:** _edit existing pdf document (source originally from somewhere else)_
[INDENT]I just simply convert the pdf to rtf using calibre, open the rtf file in OpenOffice, do a little editing (change font, add some lines, insert image, delete page, etc), and then create a pdf out of it. And for the future editing (if necessary) save the change to rtf as well, or odt. [/INDENT]

As mentioned before, this works OK only for simple .pdf documents which can be converted without significant loss and/or mess ups. But for complex documents this won't work. Conversion isn't an option for many people.

---

### Post by lindude on 2010-08-01
> **jrusso2 said:**
> I am surprised no one has mentioned pdfedit

The person who started this thread, "I used PDFedit. It is not good. Breaks too often."

---

### Post by drfox on 2010-09-22
I too have been looking for the perfect pdf editor. OOo import doesn't work for me, flpsed is hard to work with, and pdfedit uses 100% of my cpu and often crashes. 
I've had good luck with inkscape, but I can only edit one page at a time. Xournal (in the repositories) is almost perfect...you have to use File>Annotate PDF to import the pdf, and then File>Export to PDF to save it, but it works fast and well. The one deficiency is that you can't import images (signatures), nor does it allow you to add additional pages or rearrange your document.
The only application I've been able to find that does what I want it to is a commercial product, Qoppa's PDF Studio which does it all (and does it well), but it's not free software...it costs $60, worth it if you don't want to deal with multiple programs or command lines and if you spend a lot of your time working with pdfs.

Larry

---

### Post by ngcoop on 2010-10-08
I started using PDFStudio recently.  Its easy to install and has a much cleaner feel than some of the other native editors.  The demo version is free, just stamps 'demo' on the pages.  It seems to work well for highlighting and adding text in group projects or drafts of technical reports.  Before that I wine'd PDFxchange.  Both work well, I like PDFStudio a little better.

---

### Post by jaycee23 on 2010-10-10
> **drfox said:**
> I too have been looking for the perfect pdf editor. OOo import doesn't work for me, flpsed is hard to work with, and pdfedit uses 100% of my cpu and often crashes. 
I've had good luck with inkscape, but I can only edit one page at a time. Xournal (in the repositories) is almost perfect...you have to use File>Annotate PDF to import the pdf, and then File>Export to PDF to save it, but it works fast and well. The one deficiency is that you can't import images (signatures), nor does it allow you to add additional pages or rearrange your document.
The only application I've been able to find that does what I want it to is a commercial product, Qoppa's PDF Studio which does it all (and does it well), but it's not free software...it costs $60, worth it if you don't want to deal with multiple programs or command lines and if you spend a lot of your time working with pdfs.

Larry

 Thanks
 This works for me!

---

### Post by 5hiy4Marlo on 2010-10-18
It's good, the previous post turned out to be useful for you. I'd also like to recommend you to have a look at another PDF editor, which serves the same purposes. You'll find it at [http://www.iceni.com/infix.htm](http://www.iceni.com/infix.htm).

---

### Post by buntu_bd on 2010-10-20
> **paulchinnz said:**
> I want to be able to highlight and leave comments on pdf documents. Have found both PDFedit and Kword substandard. Maybe just not using it right.

With PDFedit the highlight tool just wouldn't work (click with highlight on and the entire line would highlight briefly before disappearing, and anyway I only wanted to highlight two words).

Kword did a poor job opening/converting my pdfs, multiple different fonts in one sentence in any particular paragraph (okay slight exaggeration but you get the idea).

I don't see anything else that's free in Linux for this (I guess that's no worse than with Windows).  Anyone with any other suggestions?

Foxit's applications (.exe) such as Foxit Phantom([http://www.foxitsoftware.com/downloads/index.php](http://www.foxitsoftware.com/downloads/index.php)) under wine will satisfy you for sure.

---

### Post by XubuRoxMySox on 2010-10-20
I discovered Xournal and wrote a little kinda-sorta tutorial on it [here]("http://www.linux.com/community/blogs/edit-pdfs-the-easy-way-with-xournal.html") (my first attempt at anything like a "tutorial"). Simple and fun!

-Robin

---

### Post by csolomon on 2010-12-17
Go to PDFEscape.com, upload the pdf file, add sticky note, type text, highlight, white-out, use arrow symbol, fill forms, insert pages, rotate pages, etc., and then download the file to save your edits.  Adobe Acrobat can do more than this free program does but this one does all the basic essentials that you need.  There is also a Firefox add-on for capturing web-based files, including forms.  

I have looked for a solution to this need since abandoning Windows 18 months ago and finally found the solution.  This is what former Acrobat users like me have been trying to find for years.  (I have no connection to this web site and never even heard of it till Gizmo published a note on it yesterday.)

---

### Post by CoolRat33 on 2011-03-27
Several years ago, I found PDF Studio worked well for editing PDFs in Linux and allowed me to add highlighting and notes to PDF documents. 

I’ve used it in Linux for 3 years now, and although I’ve been hoping for an open source solution that supasses it, I’ve not been able to find anything yet. The latest verion has significant improvements and now finally displays Chinese fonts properly. Its Java based, but its quite responsive. 

If you can't find an open source solution, this application might help out. Its not cheap, but it saved me enough headaches and stress and gave me a pdf editor that works in Linux.

---

### Post by farrokh81 on 2011-06-12
> **Hutom said:**
> I need to make corrections on Latex generated papers for proof reading. Earlier I used Adobe editor. That was fine. i am looking for something that can substitute it.
I used PDFedit. It is not good. Breaks too often.

I kinda had the same problem, nothing worked as good as windows tools. The best solution i came around was to wine pdfxchange ([http://www.tracker-software.com/product/pdf-xchange-viewer](http://www.tracker-software.com/product/pdf-xchange-viewer)) in ubuntu which works perfect. free pdfxchange version comes with highlighting and commenting tools and is super fast compared to acrobat lousy tools.

---

### Post by dreamcarrior on 2011-06-15
I had tried to look for PDF Studio, but the website has been down for months. [http://www.qoppa.com/pdfstudio/](http://www.qoppa.com/pdfstudio/)  I cannot access their webpage. Are there any other commercial or open source alternatives?  I simply want to add/remove/rearrange the pages in PDF files (from scanned copies). What is the best way?  Thanks!

---

### Post by Eruaran on 2011-06-23
> **dreamcarrior said:**
> I had tried to look for PDF Studio, but the website has been down for months. [http://www.qoppa.com/pdfstudio/](http://www.qoppa.com/pdfstudio/)  I cannot access their webpage. Are there any other commercial or open source alternatives?  I simply want to add/remove/rearrange the pages in PDF files (from scanned copies). What is the best way?  Thanks!

The site seems to be up. I have just downloaded it. I haven't used it much yet but the reviews that I can find about it are quite positive.

---

### Post by rbowen1 on 2011-07-15
[QUOTE=dixiedancer;10003667]I discovered Xournal and wrote a little kinda-sorta tutorial on it [here]("http://www.linux.com/community/blogs/edit-pdfs-the-easy-way-with-xournal.html") (my first attempt at anything like a "tutorial"). Simple and fun!

Thanks for the tip and tutorial.   Worked for me.

---

### Post by Sef on 2011-07-15
Moved to recurring discussions: another what's the best X for Linux.

---

### Post by fyslab on 2011-08-04
We have got same request by one of senior people in the lab about having same kind of tool like Acrobat Professional under Windows for reviewing/making notes in PDFs. So far my favorite is PDF Studio, and of free tools we tried (pdfedit. mendeley, ooffice, scribus, inkscape) we ended up to xournal.

Though PDF Studio is still more like Acrobat, if one wants simply read the document and comment and keep the comments for other reader.

PDFedit worth being installed, but much less intuitive, rather like an editor, rather than a light reviewer.

---

### Post by fyslab on 2011-08-04
PS. We did not try any of the Windows version under Wine, but the Linux native soft only.

---

### Post by makeni on 2011-08-09
Does anyone knows how to convert PDF to MS word or excel? I already tried KDE and other programs but I want something as easy as online conversion.

---

### Post by fonsi2099 on 2011-08-10
After I moved to 11.04, I've the following problem a big one, because I can not open or see my old files, my backup

"File type unknown (application/octet-stream) is not supported"  

I thank you for any help !!!

:o

---

### Post by edcompsci on 2012-08-23
> **fyslab said:**
> We have got same request by one of senior people in the lab about having same kind of tool like Acrobat Professional under Windows for reviewing/making notes in PDFs. So far my favorite is PDF Studio, and of free tools we tried (pdfedit. mendeley, ooffice, scribus, inkscape) we ended up to xournal.

Though PDF Studio is still more like Acrobat, if one wants simply read the document and comment and keep the comments for other reader.

PDFedit worth being installed, but much less intuitive, rather like an editor, rather than a light reviewer.


I like pdfedit a lot because I can put a text box anywhere on the page and fill out a non-filout-form without needing an electric typewriter, but it's wayy too sow. Is there any way to speed it up?

---

### Post by oliverjames on 2013-04-25
While checking for developments re pdf editors, found this thread. I'm currently using Foxit (with Wine wrapper). It's free and very good, I've not found any lack of editing facility, drawing, etc. Just wondered if a fully integrated Linux solution yet existed. Seems not.

---

### Post by Eyalak on 2013-06-17
For those of you that need a good relaible pdf editor, I found PDF Studio to be the only option. This solution is the only fully capable pdf editor that runs on Ubuntu without the need of wine or Virtual box.

---

### Post by drfox on 2013-06-18
> **drfox said:**
> I too have been looking for the perfect pdf editor. OOo import doesn't work for me, flpsed is hard to work with, and pdfedit uses 100% of my cpu and often crashes. 
I've had good luck with inkscape, but I can only edit one page at a time. Xournal (in the repositories) is almost perfect...you have to use File>Annotate PDF to import the pdf, and then File>Export to PDF to save it, but it works fast and well. The one deficiency is that you can't import images (signatures), nor does it allow you to add additional pages or rearrange your document.
The only application I've been able to find that does what I want it to is a commercial product, Qoppa's PDF Studio which does it all (and does it well), but it's not free software...it costs $60, worth it if you don't want to deal with multiple programs or command lines and if you spend a lot of your time working with pdfs.

Larry

3 years later, and I still haven't found anything nearly as good as PDF Studio. They keep improving it, and I keep updating. The current version is 8, and version 9 is due out this fall.

Larry

---

### Post by Copper Bezel on 2013-06-18
It still seems clunky to me, but it's certainly an impressive feature set in comparison to what most PDF software on Linux comes with (which is admittedly not saying enough, given what those other software packages look like; to give proper credit, PDF Studio seems to have a reasonably complete feature set.) I use PDF Mod for basic concatenation and rearranging, but that's a very small part of a full PDF editor's feature set. For making comments on PDFs, I still just use PDF X-Change viewer. = /

---

### Post by monkeybrain2012 on 2013-06-18
Just saw this, free as beer but not as freedom
[http://www.iloveubuntu.net/master-pdf-editor-available-ubuntu-software-center-ubuntu-1210-and-ubuntu-1304](http://www.iloveubuntu.net/master-pdf-editor-available-ubuntu-software-center-ubuntu-1210-and-ubuntu-1304)

---

