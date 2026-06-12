---
title: "Printing Tips     Multiple Pages per sheet"
date: 2009-02-21
forum: Outdated Tutorials &amp; Tips
---

### Post by eotakos on 2009-02-21
to complete the title of the thread, of course i mean for printers that don't have extra hardware to do the job.

i was searching tutorials for this issue, and i bumped into a guy who wrote something like "not every printer can print front and back..."
and i thought to myself... every common A4 copier paper has two blank sides... why not print on both of them.
someone will say: "if i'm about to print every single sheet of paper front and back, i'd rather read it right from the screen..."

So, in this thread i give some tips from personal experience on how to print **2 pages per sheet and 4 pages per sheet** (2 pages per side) in a semi-automatic way. That is half driver, half human touch....

For printing i use a deskjet hp 940c printer with the cups drivers & configuration tool that came with ubuntu. This shouldn't matter anyway - it is the human touch that makes the difference.


_**1) printing 2 pages per sheet**_

it may sound easy but there are traps which can lead you into wasting some blank-sheets! (recycle people!)


_step1:_
	[INDENT]have your printer print only the odd pages of the document in reverse order (so that the first page is on top of the pile in the output tray).
	
for cups drivers the options to do this are the following:
	[INDENT]*general tab*: check the reverse option at the bottom right
	*page setup tab*: [INDENT]pages per side: 1
			two sided : one sided !!!
			only print : odd sheets[/INDENT][/INDENT]
	the rest of the options are about the quality of the printing and not the order so we won't bother here.
[/INDENT]

_step2:_
	[INDENT]place the already printed pile of paper into the input tray of the printer, the way that the blank sides get printed this time
	have your printer print only the even pages of the document in the right order.

	cups drivers options:
	[INDENT]*general tab*: uncheck the reverse option
	*page setup tab*:	change only the "only print" option to even sheets[/INDENT]
	hit print![/INDENT]

if everything worked as it should, then you will have a book-printed document nice and easy.

note1 : if you are not printing the entire document but rather a part of it, you should watch this: if the first 	page is an even one (watch out - for PDFs this is the number shown at the toolbar, and not the one shown on each page!) ... then at the first step you should print the even sheets, and at the second the odd ones. All the other options remain with their steps.

note2 : it is highly recommended that you experiment with prints of 4 pages in order not to waste too much paper on trials. the common error is to flip the pages around the wrong edge. So the flip you SHOULD do is ONLY the one around the long edge (for A4). (this is for book-printing - for tablet-printing feel free to experiment yourself and share in this thread - i never used this kind of printing; my guess is that you just have to flip over the short edge instead of the long one)



_**2) printing 4 pages per sheet**_


_step 1:_
	[INDENT]create a dummy pdf-document that has two pages (of the original document) in every page.
	[INDENT]for CUPS:

	*general tab:* select the PDF printer from the main window    / the reverse option should be UNchecked
	*page setup tab*:
		[INDENT] pages per side : 2
		 two sided : one sided
		 only print : all sheets[/INDENT][/INDENT]
	hit print[/INDENT]

note : the orientation and format of the pages at the original document, affects the result of merging two pages in one. the preview at the page setup tab gives you an idea, but it's not the way it is going to show - you have to see the result in order to understand what it really looks like. You can hit print preview so as to know in advance, but even if you don't the pdf file can be deleted and re-created in no time. If you don't like the result, the way to correct the orientation is through the "print setup" or "page setup" options in the file menu.


_step 2:_
	find the pdf-document under /home/user/PDF  and print it using the 2 pages per sheet (book printing) trick i described above

---

### Post by eotakos on 2009-02-22
this is my first thread here, so any comments, positive or negative are very welcome! :-)

---

### Post by binbash on 2009-02-22
Thanks for the tricks  ;)

---

### Post by Jose Catre-Vandis on 2009-02-23
Well done, good to have this all written down somewhere. I like this kind of tip, its much more real world useful - now I am looking at my digital pdf copy of  Ubuntu Unleashed coming in at @ 860 pages.....in a completely different way - 215 sheets of A4 and how much wil need to be recycled? ;)

---

### Post by eotakos on 2009-02-24
Jee!! this is huge! i hope it went well...

in such cases, when you print the front sides of the sheets and something goes wrong, you've probably wasted a couple of pages... no big deal.

but when you print the back sides and somewhere in the middle the printer sucks 2 or 3 pages together... well, this is nerve-racking!  
Because you most probably wont be standing on top of the machine the whole time, and it will continue to print the back-pages at the wrong place. And when you go back to check on "a job well done" you see that half of the pages are recycle material ](*,)

---

### Post by sb73542 on 2009-03-06
Hi there, thanks for the tip.  Can I ask what printer configuration tool you are using?  Mine doesn't have any "only print odd sheets" option.  I am using Gnome on Intrepid.

---

### Post by eotakos on 2009-03-12
first of all sorry for the delay...

i'm using the default printing tools that come with hardy (gnome). As far as i know, CUPS comes with intrepid too.

I've just booted up with intrepid live cd, i tried to print a .pdf document, and the option was there. As soon as you hit print, the second tab has an option (dropdown list) that says "only print". The default value for that is "all sheets" which you can change into odd, or even sheets.

---

