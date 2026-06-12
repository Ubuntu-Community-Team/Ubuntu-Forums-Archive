---
title: "Libre Office printing garbage instead of .doc file"
date: 2020-10-17
forum: New to Ubuntu
---

### Post by nginmu on 2020-10-17
Running Lubuntu 20.04 with whatever version of Libre Office came with it by default (sorry, was stupid enough to uninstall Libre Office without making a note)

I wrote a fairly simple 2-page text document in Writer, then saved it as .doc / MS Word 2003 format.

I then emailed the .doc file to someone. They were then able to open the file on their mobile phone and read it just fine. The formatting was ok too.

I then reloaded the .doc file into a fresh instance of Writer, and directed it to print it on my HP Envy printer. Just garbage came out. Mainly a lot of random decimal characters 0 thru 9 scattered over to the right side of the page, but with a more consistent column of more ordered-looking stuff toward the left with many instances of lines like;

0     6  99   6  1     8

.. and a small smattering of non-alphanumeric symbols throughout

Tried printing a text document with featherpad, no problem

In the end in frustration (letter was pressing to send & didn't have the time for really analysing the problem) I completely uninstalled Libre Office and installed Open Office instead, just so I could print the .doc file.

Open Office didn't seem to really understand the formatting, had to edit the document quite heavily to make it right again. OO then printed it just fine.

Just wondering if anyone recognises the issue and can shed any light on how it's arisen.

The only reason I decided to use Word 2003 / .doc format was to be somewhat surer the recipient (pure MS Windows user) might know what to do with it.

---

### Post by guiverc on 2020-10-17
There is an issue with LibreOffice and printing..

I'll point you to [URL="https://discourse.lubuntu.me/t/printing-problems-with-libreoffice-in-lubuntu-20-04-1-and-20-10-beta/1610"]https://discourse.lubuntu.me/t/printing-problems-with-libreoffice-in-lubuntu-20-04-1-and-20-10-beta/1610

I can't provide any insight into what was stored though, I've not used .doc in maybe a decade so have forgotten it's structure.
[/URL]

---

### Post by nginmu on 2020-10-17
Thanks for responding. I followed your link & thought, yes that's worth investigating further..

Thought that first thing to do would be to remove Open Office entirely, then reinstall Libre Office. Then go testing.

Once Libre Office was reinstalled (via metapackage in Muon), decided to check problem was still apparent before starting going through the link.

Opened up my .doc file, unchanged from yesterday. It loaded fine in Libre Office Writer.

Tried printing the document, results were perfect. Must have been something wrong with my installation of Libre Office yesterday, that removal and reinstall has fixed.

Feel cheated out of the detective mission!

---

