---
title: "OCR program?"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by nifty542 on 2012-02-17
Hi, all

I'm almsot there! There, as in ready to ditch Windows altogether.
I have a very specific problem- as a teacher, I sometimes need to scan in documents for editing.
So far, I haven't been able to get an OCR program to work in Linux, or at least, not accurately enough.
Could anyone please recommend one? I am quite happy to use the command line, but can't find a detailed "how to" for an OCR program.
Regards, and thanks in advance

Nifty

---

### Post by Matt__ on 2012-02-17
Abbeyyocr seems to do a good job if [this blog]("http://www.splitbrain.org/blog/2010-06/15-linux_ocr_software_comparison") is to believed, but it is a commercial product.
10 Euros/9 GB pounds.  There is a free 15 day trial [here]("https://store.abbyyeu.com/cgi-bin/dlreg/ml=EN?ID=SSR1MLT").

---

### Post by nifty542 on 2012-02-17
Hi

Thanks for the reply. I don't mind paying, provided the product works. I'm still wondering about a "how to", though. Do you start with Simple Scan?
Regards
Nifty

PS. What have they done to the thanks button?

---

### Post by Matt__ on 2012-02-17
[ischool tutorials](https://tutorials.ischool.utexas.edu/index.php?title=Introduction_to_ABBYY_Finereader_10)

---

### Post by nifty542 on 2012-02-17
Hi, Matt

Thanks for that. I shall give this a try now.

Your halp is much appreciated.

Regards

Nifty

---

### Post by ajgreeny on 2012-02-17
I use tesseract v3 in Lucid 10.04, which can be added from a number of ppa repositories and is a big jump forward in accuracy terms, in my opinion.

I can get it to use other image formats than the black and white image.tif images that are required for tesseract v2, so I suggest you at least have a look at that before spending any money, as you may find that it is good enough for what you want.

I use xsane for the scan process when needed, though I see no reason why simple scan would not work just as well;  it's just that I've never tried it but will now do so.

Yes, just tried and a full page of Times New Roman, 12 point text, scanned with Simple-scan at 300dpi and saved as an image.png or an image.jpg file has just OCR'd with only a tiny error of an added ' at one point where the page was slightly mucky.  Both jpg and png files worked with no problem.

---

### Post by forrestcupp on 2012-02-17
There's no reason to go beyond the free software included in the repos. Open up Ubuntu Software Center and search for **gscan2pdf**. You can scan multiple pages and save as a pdf or tif or something, and it seems to have decent OCR capabilities.

It's the best scanning/OCR software I've seen on here yet.

---

### Post by ajgreeny on 2012-02-17
> **forrestcupp said:**
> There's no reason to go beyond the free software included in the repos. Open up Ubuntu Software Center and search for **gscan2pdf**. You can scan multiple pages and save as a pdf or tif or something, and it seems to have decent OCR capabilities.

It's the best scanning/OCR software I've seen on here yet.
Not much help if you want to get a text document that you can edit to change the text, surely?  Or does it allow you to select text from the pdf it makes and then copy/paste that to a document?

When I use OCR it is almost always because there is a need to make considerable edits to all the text; to make a pdf out of the sheet of text does not seem to help much, or have I totally misunderstood what gscan2pdf does?

---

### Post by forrestcupp on 2012-02-17
> **ajgreeny said:**
> Not much help if you want to get a text document that you can edit to change the text, surely?  Or does it allow you to select text from the pdf it makes and then copy/paste that to a document?

When I use OCR it is almost always because there is a need to make considerable edits to all the text; to make a pdf out of the sheet of text does not seem to help much, or have I totally misunderstood what gscan2pdf does?

For the OCR feature, you copy the text and paste it into LibreOffice or something.

Edit: I just tried out the OCR on a screen shot I took of a Word document. You can't get a much better source than that. The OCR output royally sucked. Even the best OCR engine out of the 3 only got 2 words right. So this software is great for scanning multi-page documents, but not so great for OCR. The document *was* all in italics, but a decent OCR should be able to read a perfect image with italics.

---

### Post by ajgreeny on 2012-02-18
A screenshot will only be at a max of 96dpi, not the 300dpi needed for good OCR.  Did you also use tesseract 3, or the v2 from the repos, as v3 is a lot better than v2.

I must try an italic page of print to see if I can do better than you managed.  I'll report back asap.

---

### Post by HermanAB on 2012-02-18
On a slightly different topic, I use Xournal to edit and mark up PDFs.  It works like a charm.

---

### Post by forrestcupp on 2012-02-18
> **ajgreeny said:**
> A screenshot will only be at a max of 96dpi, not the 300dpi needed for good OCR.
Hey, that's good to know. That makes me feel a little better about this program. I'll have to check it out.

---

### Post by ajgreeny on 2012-02-18
I've just tried a full page of italic 12 pt text to test out forrestcupp's thoughts, and in this case, scanned at 300dpi, I managed an almost perfect OCR; just one or two extra spaces between letters, usually after an upper case at the start of a sentence.  It was still perfectly acceptable using tesseract 3, and a lot better than gocr or tesseract 2 ever was for me.  Once again both jpg and png worked exactly the same as tif image format.

---

### Post by forrestcupp on 2012-02-18
> **ajgreeny said:**
> I've just tried a full page of italic 12 pt text to test out forrestcupp's thoughts, and in this case, scanned at 300dpi, I managed an almost perfect OCR; just one or two extra spaces between letters, usually after an upper case at the start of a sentence.  It was still perfectly acceptable using tesseract 3, and a lot better than gocr or tesseract 2 ever was for me.  Once again both jpg and png worked exactly the same as tif image format.

Cool! thanks.

Edit: You're right about v.2 not being too good. How did you install version 3?

---

### Post by ajgreeny on 2012-02-18
From a ppa at [https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp)

Try it; I think you'll like it!  As I say, it is not even necessary to always use a b/w image.tif scanned image as a jpg or png seem to work just as well.

I installed tesseract 3, plus dependencies, from this repository then disabled it, rather than update the other package it offers me which is **screen** which I never use.

---

### Post by forrestcupp on 2012-02-18
> **ajgreeny said:**
> From a ppa at [https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp)

Try it; I think you'll like it!  As I say, it is not even necessary to always use a b/w image.tif scanned image as a jpg or png seem to work just as well.

I installed tesseract 3, plus dependencies, from this repository then disabled it, rather than update the other package it offers me which is **screen** which I never use.

It only goes up to Natty. Have you tried it with Oneiric?

---

### Post by ajgreeny on 2012-02-18
> **forrestcupp said:**
> It only goes up to Natty. Have you tried it with Oneiric?
No, but I will tomorrow!

---

### Post by lkraemer on 2012-02-18
nifty542,
There is another option that may work for you.  I purchased Crossover by Codeweavers and that allows me to use TextBridge Classic 2.0 (Windows Software) in Debian 6.0.  TextBridge is installed in a Bottle (Win Enviro) and you can do multi-pages, etc.

Of all the OCR software I've tried TextBridge worked the best.  I have not tried Version 3 of Tesseract.  TextBridge out performed Tesseract Ver 2.

If you are converting lots of Scanned images to another format be sure to install Irfanview 4.30 (or the current version) in WINE.  It has a batch convert feature.  There are also Plugins (OCR) that you can install.  The OCR works descent but is SLOW.

lk

---

### Post by ajgreeny on 2012-02-19
> **ajgreeny said:**
> No, but I will tomorrow!
And I have now done so, on Lubuntu I admit, but 11.10, and tesseract 3 still works beautifully on that.

As an example, here is a jpg (300dpi colour) and the txt file which I OCR'd from it using Tesseract 3 to give you a clue to its accuracy.

What do you think?  The jpg is not even particularly good quality as the play script I scanned is quite dirty, slightly out of alignment, and only 8 or 9 pt font.

---

### Post by forrestcupp on 2012-02-19
Nice. So when you add the PPA, you just change "natty" to "oneiric" and it works, right?

---

### Post by ajgreeny on 2012-02-19
> **forrestcupp said:**
> Nice. So when you add the PPA, you just change "natty" to "oneiric" and it works, right?
Not quite; I changed nothing in the repo address, as the ppa site I linked to is for "Any series" in the dropdown box at the top.

I simply ran ```
sudo add-apt-repository ppa:alex-p/notesalexp
``` and everything worked fine once I had installed the tesseract it provided.  The system itself added the correct ubuntu version (oneiric) to the repo address in software-sources, I simply used synaptic, which I prefer to anything else, to install the application.

---

### Post by forrestcupp on 2012-02-19
> **ajgreeny said:**
> Not quite; I changed nothing in the repo address, as the ppa site I linked to is for "Any series" in the dropdown box at the top.

I simply ran ```
sudo add-apt-repository ppa:alex-p/notesalexp
``` and everything worked fine once I had installed the tesseract it provided.  The system itself added the correct ubuntu version (oneiric) to the repo address in software-sources, I simply used synaptic, which I prefer to anything else, to install the application.

Thank you.

---

### Post by nifty542 on 2012-03-03
Hi, all

The only link I can find to Abby costs over £100.
I have googled Linux OCR, but all the posts I have found involve pages of code which I don't understand at all.
Tesseract v3 is mentioned earlier in this thread, but again, I can't find a clear explanation of how to use it- or even, install it.
I would appreciate any help.
Regards
Nifty

---

### Post by nifty542 on 2012-03-03
Hi, all

By the way, whilst I appreciate people taking the time to reply, I'm afraid I understand almost nothing of the preceding posts.
Regards
Nifty

---

### Post by TheFu on 2012-03-03
I've been using F/LOSS **gscan2pdf **fora few years with my sheet feed scanner.
Installation and use are easy. 
No special instructions required, asuming you get the permissions for the scanner device correct.I like that the original image is displayed and the OCR text placed under it inside a PDF.  Of course you don't need to output PDF unless you like.If you just want the text and not the image, you can dump it out using a pdftotext tool.

---

### Post by nifty542 on 2012-03-03
Hi

Thanks for the reply.
Sorry, but maybe I should stick to Windows. I have no idea what to do with this program, although I have tried to use the OCR option, it just gives hieroglyphics.
I just don't understand or know what most of these posts are saying to me.
Regards
Nifty

---

### Post by nifty542 on 2012-03-03
Hi
What PDF to text tool, please?
I am growing increasingly frustrated at my inability.
People who put "I simply" followed by lots of code just make me feel like giving up.
I tried Gscan2pdf and got gobbledegook.
Of course I am doing something wrong, but answers are assuming I have A level knowledge, when I'm actually at the learning the alphabet stage.
Sorry, folks, don't know what to do next
Regards
Nifty

---

### Post by TheFu on 2012-03-03
I could be mistaken, but usually when something seems misspelled in these forums, we are probably telling you a specific program name. [https://en.wikipedia.org/wiki/Pdftotext](https://en.wikipedia.org/wiki/Pdftotext)  I know I was with "pdftotext" - that is a program that converts non-image PDF files (i.e. those with text) into ASCII text. 

As to your gobbledegook - that is common for images that do not have recognized text - photos of people - not words. Sometimes scrolling down in the bottom pane where the OCR'd text is displayed will let you see the words.  Obviously, good quality source material and a good scan that doesn't need much cleanup is important.  I've scanned utility bills and got over 90% accuracy even with all the tables screwing up the text. For me, just a few keywords and the date were sufficient. Having the original page stored as an image meant a human would never be confused, and having the text "underneath" the image meant my searching would find the bill I need.

I fear if you are trying to scan a book and need 100% accuracy, then the amount of effort needed for manual corrections is beyond your current skills.  I've scripted the most common corrections in perl for my needs (the OCR confuses o, O, 0, and 1, l, I constantly). Basically, I have an ever growing dictionary of misspelled words that are corrected.  If I need even better corrections, I'll run ispell on the text or pull every page over into a word processor and go to town with manual corrections.

I get that you are becoming frustrated.  I don't know anyone who learned UNIX/Linux as a 2nd OS who doesn't at some point. I can only promise that it gets better and that once you understand the different philosophy that Linux has when compared to any non-Linux/UNIX OS, then you'll see the genius of the design and why it works the way it does.  For the first few months, it is a steep learning curve.  I'm a pretty long time user myself and there are still some things I can't make it do ... just like there are thousands of things I can't make _other OSes_ do either.

---

### Post by nifty542 on 2012-03-04
Hi, all

Thanks for the replies.
My gobbledegook was from a plain page of text.
Not sure what to do next. Earlier in this thread there was a mention of Abbby for about £10. Can anyone enlighten me on this?

Regards

Nifty

---

### Post by TheFu on 2012-03-04
I looked for a few easy-to-follow gscan2pdf articles, since that was how I learned about this tool.
* [https://www.linux.com/learn/tutorials/426566:weekend-project-create-a-paperless-linux-office](https://www.linux.com/learn/tutorials/426566:weekend-project-create-a-paperless-linux-office)
* [https://www.youtube.com/watch?v=UjjogfWfWsQ](https://www.youtube.com/watch?v=UjjogfWfWsQ) - a video how-to

It is possible that you don't have the correct OCR language pack installed for tesseract-ocr?  The video goes into that a little.

---

### Post by nifty542 on 2012-03-04
Hi
Many thanks for the reply. I shall look into that, and follow carefully. Tutorials are really useful.
If I don't post again here for a little while, it's because I'm going to be more than a bit busy. I learned last week that I am to be made redundant, so I'm frantically making job applications. So, I'm not ignoring the above post if that happens,
Many thanks.
Regards
Nifty

---

### Post by azmyth on 2012-03-04
Which OCR engine did you use in gscan2pdf. I use OCRopus and it works very well for me but you do have to scan at 300dpi. I like OCRopus since it saves the position of the text with the location in the image. Under gscan2pdf, I save the text and image as a PDF or DJvu file and then I can search against the text. I even setup a folder for all my scans then used recoll to build a searchable db just on my scans and I can find anything quickly.

---

### Post by Kevin McCready on 2012-11-05
I followed the advice above to try to install tesseract 3 but it didn't work. Any advice appreciated. Here is what I did:

~$ sudo add-apt-repository ppa:alex-p/notesalexp
You are about to add the following PPA to your system:
 notesalexp
 tag:launchpad.net:2008:redacted
 More info: [https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpnmk51T/secring.gpg' created
gpg: keyring `/tmp/tmpnmk51T/pubring.gpg' created
gpg: "tag:launchpad.net:2008:redacted" not a key ID: skipping
recv failed

---

### Post by vasa1 on 2012-11-05
With **Lubuntu 12.10**, this is what I see when I search the Lubuntu Software Center  for *tesseract*. I get one hit for *yagf*. Adding that to the basket shows the image attached ...

---

### Post by kalehrl on 2012-11-05
Try searching it in Synaptic package manager.
LSC obviously doesn't offer it.

---

### Post by vasa1 on 2012-11-05
> **kalehrl said:**
> Try searching it in Synaptic package manager.
LSC obviously doesn't offer it.
I'm not going to install yagf to see if it indeed offers a functional tesseract via a GUI but my feeling is that LSC (**12.10**) obviously does offer it.

---

