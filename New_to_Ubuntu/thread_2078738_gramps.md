---
title: "gramps?"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by squakie on 2012-10-31
I just started trying to convert my large family history over to gramps.  I assume I must be missing something as I don't see any reporting options.  Also, sometimes when going over the ancestors on the screen, when I go to the next page some of the names are weird on the screen - everything looks fine put the first name is shifted up and cut off by the box.  When I try to go back a page (up the ancestry) then I get a blank tree.

Am I missing something, perhaps some kind of add ons or something.

BTW - I installed the version in synaptic package manager.

---

### Post by lykeion on 2012-10-31
I've never used gramps (must say it's a funny acronym for a genealogy program though), 
however the homepage have a wiki documentation, including a complete manual with a long chapter on reports here:
[http://www.gramps-project.org/wiki/index.php?title=Gramps_3.3_Wiki_Manual_-_Reports](http://www.gramps-project.org/wiki/index.php?title=Gramps_3.3_Wiki_Manual_-_Reports)

---

### Post by Zill on 2012-10-31
squakie:  I have used Gramps for a while now and currently use v3.2.0-1 running on Ubuntu 10.04 Lucid Lynx.  The "Reports" menu at the top has a long list of the different reports (such as graphical and text) available in the sub-menus and these save in either OpenOffice or pdf formats.

My (standard) version was installed from the repos in the usual way and I have no add-ons as the program works fine for me straight out of the box.

If your system runs fine generally it indicates the video drivers etc are OK.  It may be that the problems you have seen with Gramps may be due to importing an existing family tree from another application.

To see if this is the case I would try creating a brand new (test) family tree and enter some dummy data.  If that seems to work OK then your Gramps application must be OK and the problem must be with the imported data.

---

### Post by squakie on 2012-10-31
Thanks everyone!  I feel pretty stupid for not looking at the very top bar - I should know much better than that by now.  I was just going by things on the gramps screen and just became a total air-head. ;)

I think I'm going to take some screen shots of what is going on and ask for help at the gramps site.

Zill - I imported a 20,000+ individuals gedcom from my FTM software.  It seems to have gone ok, but now I'm faced with the monsterous task of getting photos, videos, etc., and back in.  Have all of these things gone fine for you?  It's a lot of work converting, but I'd like something I don't have to pay for each time Windows updated and I needed a new version.  Since I've been running Ubuntu since about 1995 or 1996 in a dual boot, and just made my laptop only ubuntu, I wanted to use a native app and take the huge task of converting everything.  If you could let me know of any "tricks" or "hiccups" you have run into along the way it would be greatly appreciated!

---

### Post by Zill on 2012-11-01
squakie:  I'm glad you found the reports. ;-)

It seems you are a lot keener with your genealogical research than I am!  My database only has 490 individuals and no photos or videos etc - just basic info.  I have always used Gramps and so have never needed to import a gedcom file from another system.

However, I understand this should generally be possible with Gramps but there may be a few "compatibility" problems due to a lack of standards support.  The Gramps documentation ["Import from another program"]("http://www.gramps-project.org/wiki/index.php?title=Import_from_another_program") may help:
> Check your data carefully once imported into GRAMPS. There are many things GEDCOM does not support that may be lost during transfer. In addition, many commercial programs do not create standard GEDCOM files. GRAMPS aims to support the GEDCOM 5.5. standard.

Take special attention that your media files are transferred too, and found by GRAMPS. In the menu Tools -> Utilities, you will find the Media Manager, with which you can change the path of your media objects to the new path if needed.
Although I am usually a great advocate of FOSS solutions, there can be exceptions and, in your case, I suggest a commercial web-based solution (such as [www.myheritage.com]("http://www.myheritage.com")) *could* be worth considering as this should retain your data irrespective of OS or locally installed applications.  However, I would guess this would be very slow if you need to upload/download videos etc. :-(

---

