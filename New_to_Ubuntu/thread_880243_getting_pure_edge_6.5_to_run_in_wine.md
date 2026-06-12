---
title: "getting pure edge 6.5 to run in wine"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by phirebug on 2008-08-04
having some trouble getting pure edge to run in wine.  i upgraded to 6.5 and it will at least open files now, but it will only let me delete text, and not edit it.  i really, really need this program for work.  any help?

thanks

---

### Post by SunnyRabbiera on 2008-08-04
Hmm, well not all windows applications work under wine, can you give us a link to this application so we can see for ourselves?

---

### Post by phirebug on 2008-08-04
[http://www.af.mil/shared/media/epubs/resource/Viewer_6_5_Download.zip](http://www.af.mil/shared/media/epubs/resource/Viewer_6_5_Download.zip)

are there any other programs similar to wine that might run this?

---

### Post by SunnyRabbiera on 2008-08-04
well hold on a sec and let me see what we are dealing with.
What kind of application is this?
What does it do?
Perhaps we can direct you to a linux alternative.

---

### Post by phirebug on 2008-08-04
it fills out standardized forms in .xfdl format.  it's used by all kinds of government departments/agencies and stuff.  i have hundreds of these forms that i have to maintain.  i can get the blank forms and fill them out by hand, but it's time-consuming and frankly doesn't look very professional.  i also have to file the paper copies.  organization is not really my strong suit.  i like being able to just carry them around on my usb drive, since every computer in the army has pureedge on it.  also, since i can download the blank forms from various sources, i never have to create an original.

---

### Post by SunnyRabbiera on 2008-08-04
Well it does look like you can open the files with gedit the native text editor for ubuntu but its not very graphical...
and it looks like its very complicated.
I dont know what to tell you here, its a shame I know little about this format and such or I could help you better.
I know this is a xml format, but I dont know of any xml editors that do things graphically.

---

### Post by phirebug on 2008-08-04
i hadn't thought of trying to get it to open in another program.  i guess i had just assumed that it was a proprietary file type.  i'll see if i can work some google magic on this.  Thanks for helping me with this.

---

### Post by SunnyRabbiera on 2008-08-04
Well I have looked up the format, but there seems to be no major ownership of the format.
I assume if you find a xml editor for windows or linux you can try it out.
I am just shooting in the dark here.

---

### Post by missilemax on 2009-03-28
I use Lotus Forms/Pure edge viewer a lot at work and I am a 100% ubuntu only user. To get this app to work I did the following.

Step one:
Install wine

Step two:
Go to configure wine. Click the libraries tab. Add "riched20.dll" as native.

Step 3:
Install PureEdge viewer, I haven't got the newer Lotus Forms working yet.

You have to open the viewer first then click open and open the file you would like to edit. 

To open a document on a thumb-drive or cd, goto my computer, then Z:, then media.

Good luck.

---

### Post by Neostar2119 on 2009-03-29
> **missilemax said:**
> I use Lotus Forms/Pure edge viewer a lot at work and I am a 100% ubuntu only user. To get this app to work I did the following.

Step one:
Install wine

Step two:
Go to configure wine. Click the libraries tab. Add "riched20.dll" as native.

Step 3:
Install PureEdge viewer, I haven't got the newer Lotus Forms working yet.

You have to open the viewer first then click open and open the file you would like to edit. 

To open a document on a thumb-drive or cd, goto my computer, then Z:, then media.

Good luck.

Dude, I've been trying to get PureEdge to work ever since I started Ubuntu, and that one simple fix got me squared away.

That was epic.

---

### Post by dementio on 2009-03-30
Thank you so much. I've been trying for way too long as well.

---

### Post by warpasylum on 2009-04-30
Sweet. Thanks alot guys. Gonna try this out tonight. I have to do my counselings in Pure Edge (in the Army). I really appreciate this.

---

### Post by warpasylum on 2009-05-01
Hey guys, just installed PureEdge viewer and it's working flawlessly.  Thanks :)

---

### Post by mcking on 2009-05-16
> **warpasylum said:**
> Hey guys, just installed PureEdge viewer and it's working flawlessly.  Thanks :)

I had PE working on an 8.10 laptop a couple of months ago, but I attempted to install it on my new Dell Mini 9 and it only partially works now.  The single-line input controls (for fields like Name, SSN, Rank) don't work, but the multi-line (richedit??) and multiple choice fields work fine.

I've already enabled the library override for the riched20.dll and the msvcp60.dll, and there are no error message on the console, but those single-input controls just have the cursor centered in the control and it just blinks whenever I type into the control.

Any suggestions?  I'd love to get this working so that I can use my Mini for my Army forms.

---

### Post by arm-c on 2009-08-15
TWO QUESTIONS:

Anyone know about how to get approveit running?

How to use a CAC Card with Pureedge to sign a document?

How to use a CAC Card with ies4linux? (ie6)

---

### Post by arm-c on 2009-08-15
McKing:  I'm not sure... try running latest wine.  Easy to setup using ubuntu tweak.  Add the wine ppa through it and update.  I'm on latest and PureEdge appears to work for all fields.

I just have the riched20.dll override option set.

---

### Post by aatyler on 2010-03-24
Wow, I can't believe getting this to run was so simple. I have been messing with this for months now. Thanks for the help man!

---

### Post by Objekt on 2010-06-15
I'm going to resurrect this thread, because it's still of interest.

I am getting out of the military, but it would be handy to be able to fill one of their .xfd or IMT forms on occasion.

So far, I can't find a way to do it natively in Ubuntu 9.10.  WINE was no help.  The Lotus Form Viewer 3.5 (which replaced PureEdge late last year) installer complained about some kind of missing library or something.  The form viewer would run through WINE, but I couldn't open an .xfd I downloaded from a military e-pubs site.  That was probably due to the problem during installation, or something else missing.

It worked fine on a virtualized Windows XP machine, of course.

I wish .gov would quit screwing around with proprietary document "solutions," and just use fillable .pdf for forms.  At present, it's a crazy quilt of proprietary stuff like .xfd, IMT forms, and non-fillable .pdf's.  By "non-fillable .pdf" I mean the forms allow you to enter data in fields, but will not save the information - thus forcing you to print them out & fill by hand.

---

### Post by arm-c on 2010-06-15
> **Objekt said:**
> I'm going to resurrect this thread, because it's still of interest.

I am getting out of the military, but it would be handy to be able to fill one of their .xfd or IMT forms on occasion.

So far, I can't find a way to do it natively in Ubuntu 9.10.  WINE was no help.  The Lotus Form Viewer 3.5 (which replaced PureEdge late last year) installer complained about some kind of missing library or something.  The form viewer would run through WINE, but I couldn't open an .xfd I downloaded from a military e-pubs site.  That was probably due to the problem during installation, or something else missing.

It worked fine on a virtualized Windows XP machine, of course.

I wish .gov would quit screwing around with proprietary document "solutions," and just use fillable .pdf for forms.  At present, it's a crazy quilt of proprietary stuff like .xfd, IMT forms, and non-fillable .pdf's.  By "non-fillable .pdf" I mean the forms allow you to enter data in fields, but will not save the information - thus forcing you to print them out & fill by hand.

Hello,
  I am many of others are quite frustrated with the pureedge thing.  I have to get it setup to run on my new PC.  I don't believe purredge 6.5 has any issue running in my experience, although you do HAVE to enable to riched dll overrides.

  I can tell you that what DOES NOT work is being able to digitally sign a form.

  You also have to save the form to your computer and then load from within pureedge.

---

### Post by Objekt on 2010-06-17
From what I understand about the Common Access Card (CAC) technology, there's nothing that limits it to Windows platforms.  At least some manufacturers of CAC readers (Schlumberger in particular) have offered Linux versions of the reader middleware.  As recently as 2002, the US Navy succesfully tested Schlumberger's stuff on Red Hat 7.3.  Here's a report I stumbled across: 

[http://www.it-umbrella.navy.mil/contract/middleware-esa/schlumberger/Linux_Report_Card.pdf]("http://www.it-umbrella.navy.mil/contract/middleware-esa/schlumberger/Linux_Report_Card.pdf")

It's the forms software where the problem lies.  As long as the DoD insists on using proprietary document viewers that are Windows-only, we'll have this problem.  I'm sure DoD doesn't consider it a problem, because Windows is their de-facto standard desktop OS.

Same applies to email.  I don't think anyone will ever wean the DoD off the Outlook teat.

---

### Post by eriktheblu on 2010-06-17
The CAC works fine with Ubuntu once Coolkey is properly configured.

PureEdge and it's soon to be replacement Lotus Forms (no hope for a Linux port that I can see) are proprietary, but as far as I can tell the XFDL format is completely open. 

I've been corresponding with a developer who is addressing several XFDL issues. While a form viewer for Linux doesn't seem to be his highest priority, I think he could eventually get there. 

<shameless plug warning>
[http://stayarmyreserve.wordpress.com/2010/06/14/rethinking-army-forms/]("http://stayarmyreserve.wordpress.com/2010/06/14/rethinking-army-forms/")

Oh yeah, this is the guy actually doing the work:
[http://blog.skeltonnetworks.com/]("http://blog.skeltonnetworks.com/")

---

### Post by SkylinesSuck on 2011-04-06
I know this is old, but just for anybody banging their head on the keyboard, you can NOT use the Lotus Forms Viewer in Wine.  Find a legacy copy of the PureEdge 6.5 program like here [http://ncoschool.com/modules/downloads/singlefile.php?cid=22&lid=556](http://ncoschool.com/modules/downloads/singlefile.php?cid=22&lid=556) and install that using the instructions on the first page.  Worked like a champ for me and was the only way for use to get our forms printed at work due to our stupid iMac Airport Extreme garbage router.   :guitar:

---

### Post by torstenaf on 2012-06-08
Ancient thread, but it got me up and running with PureEdge so I could fill out some .xfdl gov't forms.

Thanks!

---

### Post by lisati on 2012-06-08
Back to sleep, old thread.

---

