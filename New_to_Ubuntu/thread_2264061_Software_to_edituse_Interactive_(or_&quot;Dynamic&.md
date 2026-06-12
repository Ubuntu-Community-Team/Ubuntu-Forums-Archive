---
title: "Software to edit/use Interactive (or &quot;Dynamic&quot;?) PDF"
date: 2015-02-05
forum: New to Ubuntu
---

### Post by harelb on 2015-02-05
Hello,
Until very recently, "Image Viewer" is all I've needed to view PDFs. No Adobe installed on my old machine. It's an older one so probably "WINE" is not the best solution (and not much space to install newer version; I have "Ubuntu 12.04.5 LTS") 

Anyway, solution to what? I need to fill out some kind of interactive PDF. "Interactive" means that, depending on how you answer one question, the next question/fill-in you get, will be different. The contact person for where I got this, thinks (but seems not 100% sure) that this sub-type of the PDF form, is called, **Dynamic PDF**. He wrote,

"As far as the PDF is concerned, I believe it is actually referred to as a Dynamic PDF"

I think (while technically it might be identical) this is more than needing something more than just "annotate" since this is not wanting to let me add any arbitrary notes (though hopefully one part of the form has an open "comments" section) but rather to fill in only those parts that (depending on answers to previous questions) the form "wants" me to fill in...

So, what piece of software do I need to view and to "edit the file" or to view and "fill out the form"?
 Thanks!

---

### Post by Holger_Gehrke on 2015-02-05
It's probably a PDF with embedded XFA-Forms. That's a proprietary extensions by adobe to the pdf-standard (and yes, the pdf format is an  ISO-standard, even though adobe invented it). AFAIK only Acrobat Reader handles those right. There is a version of Acrobat Reader in the repositories. You can install it with 'sudo apt-get install acroread'. Whether it's new enough to handle your file I don't know.

---

### Post by bab1 on 2015-02-05
> **Holger_Gehrke said:**
> It's probably a PDF with embedded XFA-Forms. That's a proprietary extensions by adobe to the pdf-standard (and yes, the pdf format is an  ISO-standard, even though adobe invented it). AFAIK only Acrobat Reader handles those right. There is a version of Acrobat Reader in the repositories. You can install it with 'sudo apt-get install acroread'. Whether it's new enough to handle your file I don't know.
Adobe Acrobat 9.5 (acroread) is no longer available in the latest repos.  Here is what I did to install it anyway.
[http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/]("http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/")

---

### Post by ajgreeny on 2015-02-05
I have had exactly the same problem trying to open two different PDF forms from two different UK banks, and for 14.04 there seems to be no acroread available and therefore no solution for me, other than using an old VM of WinXP that I have kept running in VBox.  I can't comment on the availability of acroread for 12.04 which you are using.

Adobe are extremely annoying in this treatment of we Linux users, but I suppose that's what we get for being a bit different and independent.
I also blame organisations that use the type of PDF files that can not be opened by people who decide not to have the type of operating system that they think "everybody" uses.

EDIT:
Oh, WOW!

Thanks bab1, in spite of looking for a long time, I didn't find that way of doing it when I was looking previously, but I have just installed acroread from that link in a VBox install of Lubuntu 14.04 and it opens those forms that no native Linux application would manage, so I no longer need XP to do that (though I still need it for satnav updates).

EDIT2:
I have just been playing with that version of acroread in my VM install and all seems to work except that I can not print anything.  I will try a hard metal install and report back.
No, it will still not print for some reason, so I have given up on this for now and will see what else I can find.

---

### Post by HermanAB on 2015-02-06
Howdy,

You can annotate PDFs with 'xournal' and move pages around with 'pdfshuffler'.  These two work very well indeed.

---

### Post by tgalati4 on 2015-02-06
Try using the PDF viewer in Google Chrome.  It handles PDF forms.  I know that I have done tax forms that had dynamic content.  I was able to save them and print them when finished.

---

### Post by carl4926 on 2015-02-06
I use Okular for annotations, but only adobe reader correctly reads the additions on remote machines.

It's also been possible to edit .pdf's in LO Draw. Complicated, but possible.

---

### Post by harelb on 2015-02-06
Thank you Holger, **Bab1**, hjgreeny (the last by Herman, tgalati, and carl, were not yet posted while I tried the first ways)

This is addressed especially to you Bab1 since your post and hjgreeny's recommendation, led me to where I am. I went to your link:

LINK-A: [http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/)

But step 1 of the above link pointed me to another link:

LINK-B: [http://ubuntuhandbook.org/index.php/2014/10/install-adobe-reader-ubuntu-14-10/](http://ubuntuhandbook.org/index.php/2014/10/install-adobe-reader-ubuntu-14-10/)

so I followed that. The end text in my terminal was:

> harel@ubuntuhostname:~$ sudo apt-get install acroread    
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  acroread-bin
Suggested packages:
  libldap2 libgnome-speech7
The following NEW packages will be installed:
  acroread acroread-bin
0 upgraded, 2 newly installed, 0 to remove and 14 not upgraded.
Need to get 60.1 MB of archives.
After this operation, 142 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.canonical.com/](http://archive.canonical.com/) precise/partner acroread-bin i386
9.5.5-1precise1 [60.1 MB]
Get:2 [http://archive.canonical.com/](http://archive.canonical.com/) precise/partner acroread i386
9.5.5-1precise1 [16.3 kB]
Fetched 60.1 MB in 9min 16s (108 kB/s)
Preconfiguring packages ...
Selecting previously unselected package acroread-bin.
(Reading database ... 1040244 files and directories currently
installed.)
Unpacking acroread-bin (from
.../acroread-bin_9.5.5-1precise1_i386.deb) ...
Selecting previously unselected package acroread.
Unpacking acroread (from .../acroread_9.5.5-1precise1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up acroread-bin (9.5.5-1precise1) ...
Setting up acroread (9.5.5-1precise1) ...
No LSB modules are available.
No LSB modules are available.

I have no idea what LSB means but hopefully that's not a problem..This completed all the steps in link-B (which included the shell command giving me a DOS (yes I mean windows DOS, I don't know the linux name for the analog?) type screen asking me to press Y or N for making Reader the default, I clicked yes.

This made step 4 of link-B unnecessary. Though I used "sudo gedit" to check anyway, and indeed that part was done (also, one of the comments in link B said the same thing..that it was not necessary to do step 4)

Thus I went to link-A next, since Link-B was just to complete step #1 of Link-A per the directions in link-A.... 

Then step 2 ("sudo apt-get install gdebi") worked fine too.

Then for step 3:

> cd ~/Downloads && sudo gdebi AdbeRdr9.5.5-1_i386linux_enu.deb

I get just this short error:

> gdebi error, file not found: AdbeRdr9.5.5-1_i386linux_enu.deb

Again please keep in mind I have an old (2006 or 2007) machine, with barely over 1GB to spare, and running 12.04LTS, and that my ubuntu knowledge is minimal (this is probably a permanent condition: every time I visit the "new-comers" forums I find about 1,000 things I am not familiar with *smile*)

With that in mind, can you help me find my way to a working version of Acrobat Reader, given the above summary of what I did/what worked, and where I hit a wall? (or speed bump to be more optimistic :-)

**_EDIT:_** [B]Naturally after the error message I had not bothered to check if Adobe Reader was there :-) But Appilcations-->Office does have Reader 9...wow...at least partial success:
[/B]
"Partial success" means now I can actually view the pdf document instead of getting the old error message; it used to just display this when I tried to open/view the dynamic pdf:
> 
Please wait...
If this message is not eventually replaced by the proper contents of the document, your PDF viewer may not be able to display this type of document.

You can upgrade to the latest version of Adobe Reader for Windows®, Mac, or Linux® by visiting [http://www.adobe.com/go/reader_download](http://www.adobe.com/go/reader_download).
For more assistance with Adobe Reader visit [http://www.adobe.com/go/acrreader](http://www.adobe.com/go/acrreader).

Windows is either a registered trademark or a trademark of Microsoft Corporation in the United States and/or other countries. Mac is a trademark of Apple Inc., registered in the United States and other countries. Linux is the registered trademark of Linus Torvalds in the U.S. and other countries


It no longer does that...I am seeing a page. Just one page "1/1" and I know a LOT more is there, hidden, but I have to wait until a better hour when I have time to sit and try to, to see if I have full success - whether it lets me *complete the process interactively* (to fill out the questionnaire) without any problems, that's what remainst to be seen..

Meanwhile thanks again, and if you see any things I should know about, about either:
1. "No LSB..."
or
2. "gdebi error, file not found: AdbeRdr9.5.5-1_i386linux_enu.deb"

if so let me know please, otherwise can I assume all is well? I might need until weekend to fully test drive this (it's a very detailed  questionnaire I'm told) before I know whether I can fill it out fully.

---

### Post by mastablasta on 2015-02-06
check the path to file AdbeRdr9.5.5-1_i386linux_enu.deb or file name

---

### Post by Holger_Gehrke on 2015-02-06
> **harelb said:**
> Meanwhile thanks again, and if you see any things I should know about, about either:
1. "No LSB..."
or
2. "gdebi error, file not found: AdbeRdr9.5.5-1_i386linux_enu.deb"

if so let me know please, otherwise can I assume all is well? I might need until weekend to fully test drive this (it's a very detailed  questionnaire I'm told) before I know whether I can fill it out fully.

You can assume, but you should test. Acrobat Reader is at Version 11.0.10 for Windows, so there's possibly some new things in there which the older version on Linux can't handle.

Regarding your problems:
1. LSB modules are programs to check whether or not a system conforms to certain standards. Some programs (especially closed source ones) like to check that the assumptions made about the system they are going to run on are correct. You could install the LSB modules by doing 'sudo apt-get install lsb-core', but it's not really necessary.

2. You mixed up the two tutorials. The gdebi-step is not needed in one of them. Anyways, since you are -- according to the last bit in the first paragraph of your first post -- still on **12.04** and the tutorials are about making **14.xx** download the packages from the older 12.04 repositories, they are a bit besides the point. A simple 'sudo apt-get install acroread' is all that's needed on 12.04.

Hope it works for you

---

### Post by harelb on 2015-02-07
Holger, thanks for clarifying about 1...

About the rest, Link-A was confusingly worded; the fact that "UPDATE" was put *inside* step 1 (as opposed to putting it before all the steps or after all the steps) made it look like the link "UPDATE" pointed to (Link B) was a replacement for *only* step 1 of Link A...(that's what it normally means when an alternate link is put as a subset of just one single step..that this alternate replaces only that one single step...I guess not here) Luckily for me, this misunderstanding did not cause damage despite this, what a relief :-)

The other part that suprisede me is that it's less steps, for 12.04 than for 14.xx (that's what you seem to be saying) which I guess means I'm doing the right thing (or lucky) for having stayed with 12.04

Now I just have to see this weekend whether I can truly go through editing the whole file...hopefully yes..

Mastablasta, I did not understand your comment but don't worry about it, I will see if what I have now, works...And thanks to your signature I will save the url of this online manual, which might be handy in the future, thanks.

---

### Post by cressrt2 on 2015-02-07
I use a flpsed PDF Annotator, it is basic but works OK.

---

### Post by GrouchyGaijin on 2015-03-13
For what it is worth, I have to scan a lot of files to PDF and fill in several PDFs a month for my job.
I've been using PDF Studio 9 and it works well.  In fact, it is the only software I've found that works with my CanoScan scanner as well as Acrobat does in Windows.
The only time I had a problem was filling in a form from a Swedish government website; PDF Studio 9 choked on it because it was a "Life Cycle" document. (I have no idea what that is, except I guess it is a PDF that Adobe designed to not work with software other than their own.)

The downside is the PDF Studio 9 isn't free.  In my case, however, it is worth the money.

---

