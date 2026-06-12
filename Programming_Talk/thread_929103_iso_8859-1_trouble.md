---
title: "iso 8859-1 trouble"
date: 2008-09-24
forum: Programming Talk
---

### Post by Moezzie on 2008-09-24
Ive been asked to update quite a few websites lately. Just small stuff like changing some text and pictures. Usually my "clients" send me a word-doc with the information they want edited.

This usually gives me a huge problem.
After copying the text from the document into the html(which usually is coded iso-8859-1) i cant save the file. Gedit tells me there are characters that iso-8859-1 does not support and wants me to save it as utf8. Vim doesn't save it eather. Same thing with Smultron and TextMate on OS X.
I know the reason it doesn't work is that there is a bunch of invisible stuff that is dragged into gedit from the word-document. How do i "clean" that stuff away?

I read an article on how you could copy the text into notepad and from there into your html on windows, but it didn't work for me in gedit.
[http://www.le.ac.uk/webcentre/basicskills/text.html]("http://www.le.ac.uk/webcentre/basicskills/text.html")

The reason im so determined to get this to work with iso-8859-1 is that most of the text on the pages im working on is in Swedish and this character set works pretty well with our languages special characters( åäö ).

Does any of your guys have a good solution for this?
Thanks in advance!

---

### Post by gomputor on 2008-09-24
Open gedit ,go to File Open and when the dialog appears, click down to Character encoding and choose Add/Remove. There select ISO 8859-1, and click on add. Then select it in the encodings and load your file. That's the gedit way of course. :)

[You can also check here for a python solution to a similar problem.[http://gomputor.wordpress.com/2008/09/22/convert-a-file-in-utf-8-or-any-encoding-with-python/]("http://gomputor.wordpress.com/2008/09/22/convert-a-file-in-utf-8-or-any-encoding-with-python/")]

---

