---
title: "Need Testers for NoStaples: A PyGtk Scan-to-PDF Application"
date: 2008-10-21
forum: Programming Talk
---

### Post by staringmonkey on 2008-10-21
Good evening everyone,

  I'm looking for a few people willing to test a 0.1.0 alpha release of a program I have been working on off-and-on for a few months, entitled NoStaples.

[IMG]http://www.etlafins.com/wordpress/wp-content/uploads/nostaples.png[/IMG]

  As described in the subject line it is a Python/GTK-based scanning application with a focus on producing PDFs for permanent archival.  The primary motivation behind the project is to have a HIG-compatible scanning application that caters to the need of home-office users.  Extensive details are available on the project homepage at:

[http://www.etlafins.com/nostaples]("http://www.etlafins.com/nostaples")

  Though I've been in developing for a long while now, I'm a novice to releasing applications publicly and a complete newb to packaging.  I have produced a .deb according to the guidelines esposed [here]("https://wiki.ubuntu.com/PackagingGuide/Python").  It is available at:

[http://www.etlafins.com/files/nostaples_0.1.0-0ubuntu1_all.deb]("http://www.etlafins.com/files/nostaples_0.1.0-0ubuntu1_all.deb")

  I have tested this build to the extent possible for such a early version and most of the oblique features work fine on my machine.  However, I have not been able to have even a single other person test it.  If anyone can spare ten minutes to just let me know if it installs correctly, launches correctly, and runs through a simple scan/save batch without crashing, I would be incredibly appreciative.  If it does crash a debug log will be output to ~/.nostaples/nostaples.log and a copy of that would be very useful to me.

  As a final note, I can't (of course) guarantee that this code won't eat your baby, but I give you my word that it was not intended to.  I have been using this code as a crucial component in my home office for several months now and all my babies (and hard drives) are fine.

Thank you,
staringmonkey

---

### Post by kavon89 on 2008-10-22
I guess a scanner is required to actually test it?

---

### Post by staringmonkey on 2008-10-22
Well, yes.  In theory a web-cam may work as well, if its supported by a proper SANE backend.  Mine was recognized, but I couldn't pull stills from it.

---

### Post by staringmonkey on 2009-01-18
So my first attempt at looking for testers fell totally flat, but for the sake of consistency I am upgrading this thread to say that a second release of this project is now available.  All information (including a .deb) can be found here:

[http://www.etlafins.com/nostaples](http://www.etlafins.com/nostaples)

---

### Post by staringmonkey on 2009-02-16
A third release is now available.  As in the previous posts, the download can be found at:

[http://www.etlafins.com/nostaples](http://www.etlafins.com/nostaples)

This version also requires the SaneMe library, which is available at:

[http://www.etlafins.com/saneme](http://www.etlafins.com/saneme)

This project is now posted on Ohloh, GnomeFiles, and Freshmeat, so hopefully someone will believe it stable enough to give it a try this go-round.

Thanks,
Chris

---

### Post by Olav on 2009-02-21
> **staringmonkey said:**
> [http://www.etlafins,com/saneme](http://www.etlafins,com/saneme)
That link has a comma where a dot is required...

Anyway, I felt sorry that no one responded to your thread, so I went ahead and installed your library and application. I tried to run the program but it wouldn't start twice. Attached is the nostaples.log file.

My scanner is an old parallel port scanner, but it still works in Sane and [gscan2pdf]("http://gscan2pdf.sourceforge.net/"). How is your application different from gscan2pdf?

Ubuntu 8.10, Dutch localisation, but it also crashes when I start it with ```
LANG=C nostaples
```

Whether I click "Close" or "Quit" (is there a difference?) does not matter either, the program just hangs. Have to let Gnome kill the application.

Good luck!

---

### Post by Vadi on 2009-02-21
This isn't exactly a very visited forum, I guess that's why people missed it. Glad you posted it on Gnomefiles & co though. You should also post in the general topics, and the "cool apps" thread.

---

### Post by staringmonkey on 2009-02-21
Thanks for the replies guys.  That comma is a bit upsetting after having copied/pasted that URL all over... I don't see that it is wrong anywhere else though, so I must have just inexplicably retyped it there.  Thanks for letting me know it was wrong.

@Olav:

I haven't gotten localization support in there yet, so I can verify that won't work.  As to the other crash you got (thank you for attaching the log) it looks like something has gone wrong with the parsing the options available for your scanner.  (Or more accurately, something I had assumed has been proven false.)  I've actually spent the last two days overhauling the exception handling for these routines so that I can more easily resolve problems like this.

If you would be willing to give me a couple pieces of information I might be able to resolve this for the next version.

First of all, do you by chance know what version of SANE you have installed?  If you have the "sane-utils" package installed then you can get it from the command line using:

```
scanimage --version
```

If possible could you also get the name of your device by running:

```
scanimage --list-devices
```

It will be the value between the backticks (such as "lexmark:libusb:003:003").  And then if you feed that device name into the following command, like so:

```
scanimage --help --d lexmark:libusb:003:003
```

The output of that command will give me the details of all the options on your scanner.  If I had that information I might be able to debug the exact device option which is causing the problem (I hope).

Scanner hardware is unfortunately a difficult thing to debug since I only have physical access to a single device, but if you could help me with that information I will make my very best effort to figure out why it isn't working for you.

@Vadi:

Thanks for the advice, I'll be sure to do that for the next version.

bouvard

---

### Post by Vadi on 2009-02-21
Some feedback.

- your server is serving the .debs as "text/plain", this making "open with" fail. .debs should be served as the "application/x-debian-package" MIME type
- don't make me scroll all the way down to download :( include some links on the top that point to sections further down the page
- 
> GNOME Document Scanning Application
NoStaples aims to be a HIG compliant desktop scanning application with an emphasis on low-volume document archival for small businesses and home offices. It is written in Python using PyGTK and Glade with an eye to clear, intelligible code. 

Near-perfect description really. Just replace "HIG compliant" to "human-friendly" or "user-friendly", because HIG complaincy is a designer term, and it's meant just that for normal users ;)

- I got an unhandled exception at start - don't have a scanner connected, maybe that's why (although it should tell me so). Pressing "close" made it freeze too. here is the log: [http://paste.pocoo.org/show/104859/](http://paste.pocoo.org/show/104859/) (and sorry, proper way would be to report, but I don't want to register for yet another bugtracker)

- use a bulleted list for the features!

---

### Post by staringmonkey on 2009-02-21
Thanks Vadi!  Looking at your log file it looks like something is connected which SANE "thinks" is a scanner.  Do you have a webcam by chance?  That causes the same problem on my laptop.  I'm about 80% done implementing a feature that will let you blacklist devices like those so that they don't cause problems.  Also, that hanging/crashing bug that struck you and Olav is fixed for the next version as well.  It was a threading problem that has been resolved.

Thanks for the other comments on the site, you make good points!  I'm going to be moving the downloads and such over to GitHub so I will make these other changes at the same time.

Thanks again!
Bouvard

---

### Post by Vadi on 2009-02-21
Yeah, I do have a webcam.

(github though is feh).

---

### Post by staringmonkey on 2009-02-21
Glad I was right about the webcam.  I haven't found a decent way of separating them from other devices other than having the user manually filter them out.  I don't want to blanket filter them by name ("*webcam*", etc), because its possible that some webcams actually can be used as a valid scanning device (although highly I doubt it).  This is one area where I need to review how other SANE-based scanning applications handle such things.

> **Vadi said:**
> 
(github though is feh).


Not a fan, huh?  I have found that of the options it best suits my needs and their source browser (really the feature I care the most about) is great.  I may keep the project page on my local site just for the sake of maintaining control, but I'd rather have all the downloads and such hosted on their bandwidth than mine.  Also that keeps the source and the releases close together, which I find useful and aesthetically pleasing.

---

### Post by Vadi on 2009-02-21
I prefer Launchpad. Better, more clean interface, no commercial fees or signups in your face, normal-sized buttons, no flash widgets for copying text to a clipboard, rss feeds on everything, integration with a good bugtracker, blueprints... you name it. Plus you get announcements, a downloads area, a Ubuntu repository (for multiple ubuntu versions even), and so on associated with project hosting - along with the best translation solution about.

But it's not that big of a deal ;)

---

### Post by Olav on 2009-02-22
Hi Staringmonkey, attached is the list of options for my scanner that you requested. But like I said, this is a prehistoric parallel port scanner. If there is a truly trivial fix that you can do to make it work with your program, or if any fix you implement will also benefit users with different scanners: great. But don't waste more than 5 minutes of your time just for my scanner ;)

Recently I took it from the attic and it will probably end up in the trash in a few weeks. It still gives decent results but it is terribly, unbearably slow.

I need to scan hundreds of documents so I am looking to buy something more suitable for that (I have yet to decide how much I am willing to spend). I trust your program will support ADF?

You are probably aware of [gscan2pdf]("http://gscan2pdf.sourceforge.net/"). I rather like it. I suppose your program is not a clone; could you say a few words about the differences between both programs?

Thank you.

Edit: the version of Sane is 1.0.19, the stock that comes with Ubuntu 8.10.

---

### Post by staringmonkey on 2009-02-22
Hey Olav, thanks for the information.  I just got a hit on my bug-tracker from another user with an issue almost identical to yours (this time a networked scanner).  Somewhere one of my assumptions about how these devices are named internally is incorrect.  Anyway, anything that works with those other applications should work with NoStaples, so I do take the issue serioulsy.  There is no particular reason that they wouldn't work other than that I haven't been working on it as long. :)  If you have a second could you give me the output of just:

```
scanimage --list-devices
```

I am planning on supporting ADF, although its probably a few minor versions away.  I don't currently have an ADF scanner to test with, so I'm going to have to dig one up on Craigslist before I can really begin hacking on that in earnest.

I am aware of gscan2pdf, it was one of the applications I looked at when I was looking for a scanning application for home office.  Its certainly not a bad scanning application.  The primary differences that I'm focusing on with NoStaples could be best summarized as simplicity, ease-of-use, and speed.  I'm not going to support every obscure option in NoStaples, just the ones that cover 90% of the use cases.  Instead I am going to focus on being able to scan many documents quickly, even if you do not have an ADF scanner.  Eventually I would also like to develop a parallel application for indexing and retrieval of these documents.  (For this reason I am thoroughly supporting PDF metadata in NoStaples.)

As an aside, my motivation for starting NoStaples comes from spending my day job working with production imaging systems.  I am very tired of having to hack my own front-end onto production software in order to reach a reasonable level of efficiency.  With NoStaples I want those benefits to be available to casual users right out of the proverbial box.

I hope that answers your question.  Thanks for your interest.

EDIT:  I should have mentioned that I am using NoStaples to scan hundreds of my own documents, so that sort of capacity is absolutely possible.  Unfortunately cleaning up these bugs with devices that I don't have in front of me is rather obscure.  Hopefully once they are resolved it will be as useful to you and others.

---

### Post by Vadi on 2009-02-23
Hmm... should make a big call for testers or somesuch :)

---

### Post by Olav on 2009-02-23
> **staringmonkey said:**
> If you have a second could you give me the output of just:

```
scanimage --list-devices
```

Sure thing:

```
device `mustek_pp:mustek-cis600' is a Mustek 600CP flatbed scanner
```

Thank you for your other comments as well. I will keep following your application with interest. As they say, release often ;)

---

### Post by staringmonkey on 2009-02-23
Thanks for the additional feedback.  I think I have a pretty good idea how to fix this problem with devices such as yours.  I've also done a tremendous amount of work this last week on exception handling and intelligent device support.  There are now automatic and optional device blacklists.  So at the *very least* the next version shouldn't crash/hang. :)

As you say, release early/often is very important to me.  This is my first 'public' open-source project an I'm taking pains to do it the "right way".  (Thus the new bug-tracker, release announcements, etc.)  I will absolutely be doing a wider call for testers once I get the application to the point where it isn't crashing for everyone but me. :)

I'm very glad I've managed to maintain your interest with this first (buggy) release!  I will hopefully be able to push out a new deb in the next 2-3 weeks.

Thanks again for the debug logs!

---

### Post by staringmonkey on 2009-03-07
Hello again!

Version 0.4 is now available for your testing pleasure.  This release should fix all outstanding issues that have been discussed in *this* thread.  (Though not *all* outstanding issues, by any means.)

If anyone has a minute to test the new release and file tickets (or just respond here) regarding any issues that they find that would be hugely appreciated. :-)

This version has a debugging script built in that should help me troubleshoot problems with particular devices, so if you your device fails, please attach the output of `nostaples --debugdevices` to your bug report.

As always the release is available here:
[http://www.etlafins.com/nostaples]("http://www.etlafins.com/nostaples")

(Or: via [direct-link]("http://cloud.github.com/downloads/bouvard/nostaples/nostaples_0.4.0-0ubuntu1_all.deb") to the Intrepid deb.)

Bug-tracking is here:
[http://bouvard.lighthouseapp.com/projects/19416-nostaples/overview]("http://bouvard.lighthouseapp.com/projects/19416-nostaples/overview")

And the source is here:
[http://github.com/bouvard/nostaples/tree/master]("http://github.com/bouvard/nostaples/tree/master")

Thank you for all your help :-)
Bouvard

---

### Post by Vadi on 2009-03-07
Your server is still misconfigured and 'open with' doesn't work for the .deb :(

It needs to server .deb packages as the *application/x-debian-package* MIME type.

---

### Post by staringmonkey on 2009-03-07
I actually had fixed this on my site, but now the deb's are being hosted at GitHub so I unfortunately I don't have control over the MIME type. :(

---

### Post by Vadi on 2009-03-07
Starts great now without any scanners.

Some interface feedback though:

- View tab in preferences should have the combo boxes aligned by width (see [Window Layout]("http://library.gnome.org/devel/hig-book/stable/design-window.html.en") in gnome hig)

- You can click on the add/remove blacklist buttons without having anything selected. It doesn't hurt, but makes no sense either - the buttons should be disabled

- NoStaples toolbar doesn't obey my system preference - it uses "small icons, no text" while my default is "big icons and text". It's understandable though why would you want it different from the system default, but offer an option in preferences for changing it (and follow system by default - you can't decide what is better for a user than he can)

- will let you know more when I plug in the scanner...

---

### Post by staringmonkey on 2009-03-07
Great feedback as usual, Vadi. :)  I will put all these items on my TODO list.  Let me know how it goes when you get your scanner up and running.  I will be keeping my fingers crossed.

---

### Post by Olav on 2009-03-08
> **staringmonkey said:**
> Hello again!

Version 0.4 is now available for your testing pleasure.

Hello again as well, good to see you are still motivated.

First I should say that I am now able to start the program and make some scans with it. So this is indeed progress ;)

I have not tested very thoroughly, yet I did find another crash situation. It happens whenever I choose to scan in "Lineart" mode. Colour scans work with no problem. I have attached a screen shot and a log file.

Again I must emphasise that you should not lose any sleep over this if it is a failure that is unique to my prehistoric scanner. I can't imagine anyone else still using this dinosaur, and in a few days I will also receive the new Epson scanner that I have ordered.

Some other remarks:

[LIST]
[*] In the Options menu, under resolution, I find numbers like 3276800, 6882180, 10485760, 14090240, et cetera. These probably have some technical meaning, but no "real world" meaning that is obvious to me. I would expect to see DPI values (like 75x75, 100x100, 300x300 and so on).

[*] After saving a document it is cleared from the application. If you realise after saving that you wanted to add another page, you have to start scanning again from page one. I think you can see how this could become quite annoying, quite quickly.

[*] Being able to set the page size is important. I see you have already marked it as TODO which is good. In most parts of the world we do not use "Letter" at all, only A4 and its family. So if you care about world wide popularity, you should perhaps try to make this a bit of a priority ;)
[/LIST]

In the spirit of full disclosure I should mention that I will almost certainly stick with gscan2pdf for my personal scanning. It has all the features I need and has been unproblematic for me. Only "unpaper" can't always be trusted. But as far as I can see it is a problem in that program, not in gscan2pdf itself.

I will certainly keep an eye on your progress though, because I just like it when people are ambitious and doing projects like these!

In fact, I was just thinking of a little project of my own, where people would be able to store PDFs in a database for easy search and retrieval. Something like a *very* lightweight EDMS. Still dreaming though, and unfortunately I suck at Python.

---

### Post by Olav on 2009-03-08
> **Olav said:**
> I have attached a screen shot and a log file.

Well, I thought I did. So here:

---

### Post by staringmonkey on 2009-03-08
Olav, I am very glad to hear from you again! :) And I am happy to have more specific answers to each of your concerns/bugs this time around. :)

> **Olav said:**
> 
I have not tested very thoroughly, yet I did find another crash situation. It happens whenever I choose to scan in "Lineart" mode. Colour scans work with no problem. I have attached a screen shot and a log file.


I am amazed that everyone tests the Lineart functionality. :P Amazingly, I have already had this reported in three separate places.  Its [Ticket #23]("http://bouvard.lighthouseapp.com/projects/19416/tickets/24-scanning-in-lineart-mode-causes-a-buffer-overflow-in-pil").

> **Olav said:**
> 
[*] In the Options menu, under resolution, I find numbers like 3276800, 6882180, 10485760, 14090240, et cetera. These probably have some technical meaning, but no "real world" meaning that is obvious to me. I would expect to see DPI values (like 75x75, 100x100, 300x300 and so on).


It looks your "old dinosaur" specifies its resolution in some unit other than DPI.  (I'm guessing bits.)  I was aware this would be an issue for some devices, but I did not actually have a ticket for it.  I do now: [#37]("http://bouvard.lighthouseapp.com/projects/19416/tickets/37-handle-resolutions-specified-in-non-dpi-units").

> **Olav said:**
> 
[*] After saving a document it is cleared from the application. If you realise after saving that you wanted to add another page, you have to start scanning again from page one. I think you can see how this could become quite annoying, quite quickly.


Yes, eventually I would like to include an "import PDF" option, as well as an "insert from image file" option, but both of those are a version or two away as I continue to establish core functionality.  Still, I'm glad you brought it up so I could document it. :)  [Ticket #38]("http://bouvard.lighthouseapp.com/projects/19416-nostaples/tickets/38-add-ability-to-re-import-pdf-for-scanning-additional-pages").

> **Olav said:**
> 
[*] Being able to set the page size is important. I see you have already marked it as TODO which is good. In most parts of the world we do not use "Letter" at all, only A4 and its family. So if you care about world wide popularity, you should perhaps try to make this a bit of a priority ;)


It is! :)  This is actually Priority #1 for the [0.5 release milestone]("http://bouvard.lighthouseapp.com/projects/19416/milestones/32866-alpha-05").  The real fun bit is going to be setting it up so that it outputs a PDF whose resolution exactly matches the scan resolution.  Its a tricky business getting those two things to line up, but it absolutely will be the focus of 0.5, now that I have some of the most glaring device support issues resolved.

You may also be interested to note that Priority #2 for the next release is translation/localization support, which I know you had expressed interest in. :)

> **Olav said:**
> 
In the spirit of full disclosure I should mention that I will almost certainly stick with gscan2pdf for my personal scanning. It has all the features I need and has been unproblematic for me. Only "unpaper" can't always be trusted. But as far as I can see it is a problem in that program, not in gscan2pdf itself.


I certainly can't begrudge you that, and that makes me appreciate your testing all the more.  My goal with this application is not necessarily to displace gscan2pdf, but to offer a similar application with a more refined/constrained/accommodating design.  Hopefully, I am making headway in that direction.  (Also see following paragraph for more long-term thinking.)

> **Olav said:**
> 
In fact, I was just thinking of a little project of my own, where people would be able to store PDFs in a database for easy search and retrieval. Something like a *very* lightweight EDMS. Still dreaming though, and unfortunately I suck at Python.


It is funny that you should mention that, as my long-term goal is to have a companion application that does *exactly* this.  This is why I have already put so much effort into PDF metadata support.  As I use this in my home office I am very carefully tagging all my documents so that some day when NoStaples is fairly well established I can move on to *drum roll* "NoStacks", which I intend to be a lightweight document management system.  Of course, this is pretty far in the future, but I don't think its too far-fetched.  I already have an array of sketches and notes (including ideas for integrating the two applications).  If you would be interested in hacking on something like that or just discussing what you would like to see in such an application, I would be more than happy to receive the input. :)

Cheers!
Bouvard

---

### Post by Olav on 2009-03-09
Hi, thanks for making all the tickets.

As promised, my response:

> **staringmonkey said:**
> I am amazed that everyone tests the Lineart functionality. :P

It shouldn't have to surprise you. "Line art" seems to be best in terms of speed, storage efficiency, printing and OCR (if that ever becomes viable on Linux...). I scan almost everything in line art, 300 DPI. Except photos of course.

> It looks your "old dinosaur" specifies its resolution in some unit other than DPI.  (I'm guessing bits.)  I was aware this would be an issue for some devices,

Now I am surprised. I would have expected Sane, as the layer between the scanner and the application, to solve such problems and provide a uniform interface to talk to the scanner. Oh well, what do I know.

> Yes, eventually I would like to include an "import PDF" option, as well as an "insert from image file" option,
That would be good, gscan2pdf does it too...

> but both of those are a version or two away as I continue to establish core functionality.

If you don't just clear the document immediately after scanning, you can perhaps even skip three versions before you implement your import function. Also, I really think it should be a user's *choice* whether they want to continue, or start a new document. Even better if it were a configurable preference!



About paper sizes...

> The real fun bit is going to be setting it up so that it outputs a PDF whose resolution exactly matches the scan resolution.  Its a tricky business getting those two things to line up,

Sorry if I am stating what is already obvious to you. But I was under the impression that PDF doesn't really have resolution, or if it does, that it doesn't have much to do with the scanning resolution. After all, there can be pages scanned with different resolutions (but the same paper size) in a single PDF file. Scanned pages can also be upscaled or downscaled to fit the PDF paper size. 

Yes, I could see how this is going to be fun ;)

> You may also be interested to note that Priority #2 for the next release is translation/localization support, which I know you had expressed interest in. :)

I may perhaps contribute a translation then, as I have done for several other open source programs. 

> It is funny that you should mention that, as my long-term goal is to have a companion application that does *exactly* this.  This is why I have already put so much effort into PDF metadata support.  As I use this in my home office I am very carefully tagging all my documents so that some day when NoStaples is fairly well established I can move on to *drum roll* "NoStacks", which I intend to be a lightweight document management system.  Of course, this is pretty far in the future, but I don't think its too far-fetched.  I already have an array of sketches and notes (including ideas for integrating the two applications).  If you would be interested in hacking on something like that or just discussing what you would like to see in such an application, I would be more than happy to receive the input. :)

I have to think about it some more. My current thinking is it needs to be a web application, so you can access your documents wherever you are. My PHP skills are slightly less crappy than my Python skills, so I may end up hacking something together. Not tomorrow though, but... later ;)

---

### Post by staringmonkey on 2009-03-09
Hey again Olav,

> **Olav said:**
> 
It shouldn't have to surprise you. "Line art" seems to be best in terms of speed, storage efficiency, printing and OCR (if that ever becomes viable on Linux...). I scan almost everything in line art, 300 DPI. Except photos of course.


I suppose that's true, especially since you can apply post-process smoothing to the lineart image when you view it.  Although I tend to prefer the fidelity of grayscale, especially since disc space is a essentially non-factor.  Still, I'm glad to have it working now, especially if others are actively using it. :)  

> **Olav said:**
> 
Now I am surprised. I would have expected Sane, as the layer between the scanner and the application, to solve such problems and provide a uniform interface to talk to the scanner. Oh well, what do I know.


SANE enumerates six or seven valid units of measure.  Included in these are "bit", "dpi", "percent", etc.  I will be unifying these for NoStaples, but its going to be a non-trivial effort, as some of them are not literally translatable (percent to dpi, for instance, requires another variable).

> **Olav said:**
> 
If you don't just clear the document immediately after scanning, you can perhaps even skip three versions before you implement your import function. Also, I really think it should be a user's *choice* whether they want to continue, or start a new document. Even better if it were a configurable preference!


Now I'm a bit confused... it should only be clearing the document after scanning if you click "Quick Save"... if you just click "Close" in the scan progress window then you should have an opportunity to manipulate the pages, reorder them, scan additional pages, etc.  Are you referring to clearing the pages  immediately after *saving*?  I suppose that would make sense, although I might need to rethink some other design decisions.

> **Olav said:**
> 
Sorry if I am stating what is already obvious to you. But I was under the impression that PDF doesn't really have resolution, or if it does, that it doesn't have much to do with the scanning resolution. After all, there can be pages scanned with different resolutions (but the same paper size) in a single PDF file. Scanned pages can also be upscaled or downscaled to fit the PDF paper size. 


Well, it does and it doesn't.  PDF has a concept of "page size", which is important to set so that "single click" printing of a PDF document works as expected.  The size of the page is the size of a "physical" copy, which is to say, independent of DPI.  The scanned image can, of course, be scaled to fit the target PDF page size, providing that the aspect ratio of the image can be maintained.  The path of least resistance is to specify up-front that the device scans at a size which precisely matches the PDF that you want to output.  This then dove-tails into the issue of how resolutions are specified.  I think you will see that it can be a little be tricky to match input and output resolution when the device is specifying its resolution in "bits". :)  Still, I'm sure I can get there.

> **Olav said:**
> 
I may perhaps contribute a translation then, as I have done for several other open source programs. 


That would be great, I've had another offer to do an Arabic translation.  I would be very grateful to have those when the support is in place. :)

> **Olav said:**
> 
I have to think about it some more. My current thinking is it needs to be a web application, so you can access your documents wherever you are. My PHP skills are slightly less crappy than my Python skills, so I may end up hacking something together. Not tomorrow though, but... later ;)


I agree from a purely utilitarian perspective that having it be a web-based app is a no-brainer, but I do not have much interest in creating that sort of application.  My experience with web-based document systems is that they tend to be lowest-common-denominator systems with very poor user interfaces.  I much prefer having a highly efficient desktop experience, even if it does constrain where I can use it.  Also, I think the web-constraints are less relevant in the days of remote-mountable filesystems.  Perhaps, I just don't want to touch PHP. :D

---

### Post by Olav on 2009-03-09
> **staringmonkey said:**
>  Are you referring to clearing the pages  immediately after *saving*?
Yes, saving. Sorry for the confusion.

---

### Post by RainKap on 2009-04-02
> **staringmonkey said:**
> Hello again!

Version 0.4 is now available for your testing pleasure.  This release should fix all outstanding issues that have been discussed in *this* thread.  (Though not *all* outstanding issues, by any means.)

If anyone has a minute to test the new release and file tickets (or just respond here) regarding any issues that they find that would be hugely appreciated. :-)

This version has a debugging script built in that should help me troubleshoot problems with particular devices, so if you your device fails, please attach the output of `nostaples --debugdevices` to your bug report.

As always the release is available here:
[http://www.etlafins.com/nostaples]("http://www.etlafins.com/nostaples")

(Or: via [direct-link]("http://cloud.github.com/downloads/bouvard/nostaples/nostaples_0.4.0-0ubuntu1_all.deb") to the Intrepid deb.)

Bug-tracking is here:
[http://bouvard.lighthouseapp.com/projects/19416-nostaples/overview]("http://bouvard.lighthouseapp.com/projects/19416-nostaples/overview")

And the source is here:
[http://github.com/bouvard/nostaples/tree/master]("http://github.com/bouvard/nostaples/tree/master")

Thank you for all your help :-)
Bouvard

Hi there - I read about NoStaples in the latest issue of Linux Format. I'm running Ubuntu Hardy Heron (AMD64 version) on my dual Opteron desktop, with an HP Scanjet 3530c attached via a USB port. I downloaded and installed the .deb for version 0.4.0 of NoStaples and started it, but it didn't see the scanner.

scanimage --list-devices gave me:
device `hp3500:libusb:001:003' is a Hewlett-Packard ScanJet 3500 scanner

XSane sees it and scans OK; I can also run the HP-supplied Windoze software in a Windoze VM running in VirtualBox. Any suggestions please?

Output of 'nostaples --debugdevices' follows.

Device 1

Name:	hp3500:libusb:001:003
Vendor:	Hewlett-Packard
Model:	ScanJet 3500
Type:	scanner

	Option 1

	Name:	filler
	Title:	Scan Mode Group
	Desc:	Scan Mode Group
	Type:	5
	Unit:	0
	Size:	4
	Cap:	0
	Constraint Type:	0
	Constraint:	None
	**Failed to get current value for option.**

	Option 2

	Name:	tl-y
	Title:	Top-left y
	Desc:	Top-left y position of scan area.
	Type:	2
	Unit:	3
	Size:	4
	Cap:	0
	Constraint Type:	1
	Constraint:	(0, 19575603, 1387)
	Value:	0

	Option 3

	Name:	tl-x
	Title:	Top-left x
	Desc:	Top-left x position of scan area.
	Type:	2
	Unit:	3
	Size:	4
	Cap:	0
	Constraint Type:	1
	Constraint:	(0, 14149222, 1387)
	Value:	0

	Option 4

	Name:	br-y
	Title:	Bottom-right y
	Desc:	Bottom-right y position of scan area.
	Type:	2
	Unit:	3
	Size:	4
	Cap:	0
	Constraint Type:	1
	Constraint:	(0, 19575603, 1387)
	Value:	19559219

	Option 5

	Name:	br-x
	Title:	Bottom-right x
	Desc:	Bottom-right x position of scan area.
	Type:	2
	Unit:	3
	Size:	4
	Cap:	0
	Constraint Type:	1
	Constraint:	(0, 14149222, 1387)
	Value:	14149222

	Option 6

	Name:	resolution
	Title:	Scan resolution
	Desc:	Sets the resolution of the scanned image.
	Type:	1
	Unit:	4
	Size:	4
	Cap:	0
	Constraint Type:	2
	Constraint:	[50, 75, 100, 150, 200, 300, 400, 600]
	Value:	200

Ian Park

---

### Post by staringmonkey on 2009-04-02
Hey Ian,

  Thanks for the bug report.  I can see straight away that your device is being marked as unsupported by v0.4 because it does not have a 'mode' option.  I knew that this would be a case for some devices, but this is the first concrete example I've seen of a device not supporting it--which is good, because I really need to see the logs to know how best to compensate for these sorts of situations.  I have opened a ticket ([#43]("http://bouvard.lighthouseapp.com/projects/19416-nostaples/tickets/43-devices-that-do-not-specify-a-mode-are-not-supported#ticket-43-2")) for this issue and scheduled it for the next release (it *should* be a pretty easy fix).

  If you care to track the ticket I will mark there when the fix is in or just keep an eye on this thread for the 0.5 announce (hopefully in the third or fourth week of this month).

  On a totally unrelated note, how was NoStaples mentioned in Linux Format?  I'm both gratified and terrified to find out about it. :)

Thanks again,
Bouvard

---

### Post by RainKap on 2009-04-03
> **staringmonkey said:**
> Hey Ian,

  Thanks for the bug report.  I can see straight away that your device is being marked as unsupported by v0.4 because it does not have a 'mode' option.  I knew that this would be a case for some devices, but this is the first concrete example I've seen of a device not supporting it--which is good, because I really need to see the logs to know how best to compensate for these sorts of situations.  I have opened a ticket ([#43]("http://bouvard.lighthouseapp.com/projects/19416-nostaples/tickets/43-devices-that-do-not-specify-a-mode-are-not-supported#ticket-43-2")) for this issue and scheduled it for the next release (it *should* be a pretty easy fix).

  If you care to track the ticket I will mark there when the fix is in or just keep an eye on this thread for the 0.5 announce (hopefully in the third or fourth week of this month).

  On a totally unrelated note, how was NoStaples mentioned in Linux Format?  I'm both gratified and terrified to find out about it. :)

Thanks again,
Bouvard
Hi Bouvard

Linux Format was enthusiastic about Nostaples; they put it on their cover DVD (which I mislaid, so I downloaded it). The review was: "Also in the Desktop section we have /Nostaples/, a simple but cleanly designed scanning program built on /PyGTK/ and /Glade/. It's targeted towards "medium volume document archival for small businesses and home offices", so if you've had endless hassles wrestling with other scanning tools, give it a whirl".

All the best

Ian

---

### Post by staringmonkey on 2009-04-03
Ian,

    That's great, I had no idea.  I'm sorry your first experience did not quite live up to the hype, but I'll work to ensure the next version resolves the issues with your device.

Thanks again,
Bouvard

---

### Post by RainKap on 2009-04-03
> **staringmonkey said:**
> Ian,

    That's great, I had no idea.  I'm sorry your first experience did not quite live up to the hype, but I'll work to ensure the next version resolves the issues with your device.

Thanks again,
Bouvard
Thanks Bouvard. I'll look out for version 0.5 later this month.

Cheers

Ian

---

### Post by towb on 2010-05-06
> **staringmonkey said:**
> I can see straight away that your device is being marked as unsupported by v0.4 because it does not have a 'mode' option.

Nostaples has a bug that causes it to ignore some options, maybe that's related. I made a fork on Github and fixed it. Hopefully that doesn't just pertain to my scanner ;)

---

