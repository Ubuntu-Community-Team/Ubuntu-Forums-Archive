---
title: "PDF files show no text in 12.10"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Don Bowen on 2013-02-17
I tried to search for this because I'm sure it's been covered, but searching on this board doesn't seem to work... I searched on "PDF no text" and got nothing back that seemed at all related... thus this post...

When I open a PDF in 12.10, I can see the graphics but NOT the text.
How do I fix that?

---

### Post by Don Bowen on 2013-02-17
I did try search... please don't get mad if I ask a question and say "you didn't search on it".
Yes I did.

PDF files display no text in ubuntu 12.10.
Is there a fix for that?
If so, how do I fix it?

---

### Post by schragge on 2013-02-17
Try to open it in another PDF viewer, e.g. install *epdfview*. Does the problem still persist?

---

### Post by Habitual on 2013-02-17
[http://www.google.com/search?q=](http://www.google.com/search?q=)**[COLOR=Red]KeyWord[/COLOR]**+**[COLOR=Red]or[/COLOR]**+**[COLOR=Red]Keywords[/COLOR]**+site:ubuntuforums.org

Examples:
[http://www.google.com/search?q=don+bowen+site:ubuntuforums.org](http://www.google.com/search?q=don+bowen+site:ubuntuforums.org)

[http://www.google.com/search?q=pdf+no+text+site:ubuntuforums.org](http://www.google.com/search?q=pdf+no+text+site:ubuntuforums.org)

---

### Post by Don Bowen on 2013-02-17
Habitual, were you trying to communicate?  

I'm sure it's my fault, but I don't understand your reply.  It looks like gibberish.

Was there a link you wanted me to read? follow?

please explain?

---

### Post by oldos2er on 2013-02-17
Threads merged; please don't start more than one thread per question, it dilutes community effort.

Habitual's showing you the most effective way to search the forums with google's advanced search.

---

### Post by Don Bowen on 2013-02-17
I searched the final link...the other two don't do anything... and I get a lot of questions about converting PDF.

I'm not converting PDF.

I'm just wanting to open a PDF and read the text.  I can't imagine that Ubuntu is unable to do that?
It's also unlikely that I'm the first person to ever have this problem.

If you know the answer/solution, please reply.

I just want to be able to open a PDF file and read it... that's all... nothing fancy.

---

### Post by Don Bowen on 2013-02-17
I'm sorry, i didn't know I had started more than one thread.  I gurantee you I didn't do that on purpose.

I've never used "Google Advanced Search".  I'm sure the advice is well meant, but I don't know how to take advantage of it.

---

### Post by Michael Dooley on 2013-02-17
Don:

What habitual was trying to show you was something like this:

---

### Post by Don Bowen on 2013-02-17
> **Michael Dooley said:**
> Don:

What habitual was trying to show you was something like this:

Well OK... i get that part now, but lets try a different tack with the original question:

Does anyone have a PDF viewer that shows text?  What is its name?

If it's Ubuntu's default pdf viewer, how did you get it to show text?

thanks.

---

### Post by The Cog on 2013-02-17
I use evince, also known as Document Viewer. I haven't seen any problems with that one. I thought it was the default PDF viewer, but maybe Ubuntu is different to Xubuntu (which I use). 

Is this just one PDF you are having trouble with, or is it lots of PDFs?

---

### Post by Impavidus on 2013-02-17
I imagine it could be a pdf without embedded fonts. Most of the time people/programs embed all fonts in the portable document format to make it, wel, portable. Sometimes they don't, assuming the fonts are installed on every computer anyway. Which may not be a save assumption on a non-windows-latest-version machine.

In evince, you can click file->properties and then click the fonts tab to get a list of fonts in the pdf, with an indication on whether it is embedded, partially embedded (only the characters used in the document) or not embedded at all. You may need to install some fonts.

Evince is the default pdf viewer on ubuntu (xubuntu at least, assuming it's the same in ubuntu) and by default it does show text. Would be quite worthless otherwise.

---

### Post by Don Bowen on 2013-02-18
I erased my machine and re-installed 12.10.  Right before I added all the fonts I know and love, the PDF viewer works.  

AFTER... I add the fonts, it stops working.  I can only guess that one of the new fonts is overwriting a "core" font Ubuntu needs to make the PDF viewer work.

Anyone know how to restore that font?

I could go through the 900 I install one at a time to see which one is doing it, but that seems like it would take a while.

---

### Post by Don Bowen on 2013-02-18
the phrase "core" font made me wonder if Ubuntu had such a thing... it does.

In /usr/share/fonts/truetype

I add my own folder called "myfonts" with 900 .TTF files.  When I remove that, the PDF viewer works.... sooo.... I found a folder called "ubuntu-font-family" and copied the contents of that folder to "myfonts" folder overwriting my substitutions with the system originals.  

That worked.

The PDF viewer is working normally now.
Thank you all.

---

### Post by The Cog on 2013-02-18
Thanks for posting the solution. That always helps others who are looking at a similar problem.

You can mark the thread solved with the Thread Tools pull-down at the top.

---

### Post by Don Bowen on 2013-02-18
> **The Cog said:**
> Thanks for posting the solution. That always helps others who are looking at a similar problem.

You can mark the thread solved with the Thread Tools pull-down at the top.

I pronounce thee.... "SOLVED"....

I'm sure that's not what you meant, but in the absence of knowing how to mark a post "solved" it will have to do.

---

### Post by oldos2er on 2013-02-18
> **Don Bowen said:**
> I pronounce thee.... "SOLVED"....

I'm sure that's not what you meant, but in the absence of knowing how to mark a post "solved" it will have to do.

Scroll up to the top of this page, you should see a small triangle next to 'Thread Tools'. Click it, and click icon next to 'Mark this thread as Solved'.

---

