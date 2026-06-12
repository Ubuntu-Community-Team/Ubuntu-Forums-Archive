---
title: "Need to delete all my Shotwell tags"
date: 2016-02-22
forum: New to Ubuntu
---

### Post by stevemid on 2016-02-22
I recently imported 6000 photos from an iphoto export into Shotwell. All my iphoto photos had titles which were used in the export process to create files. Shotwell took the  file name (or title?) and created a tag for each one.  Now I have 6000 tags in Shotwell that I need to get rid of.   In the import process I opted to have Shotwell copy the photos into my home folder so I have that folder structure there that I could re-import from.  Is there a way to delete all the tags in one go?  This question was asked and answered here [http://ubuntuforums.org/archive/index.php/t-1976690.html](http://ubuntuforums.org/archive/index.php/t-1976690.html) but the nabble link is dead and anyway the solution involved sql edit which I wouldn't have any experience with anyway. I would be ok with getting rid of every tag and starting over.

Any help would be much appreciated.

---

### Post by stevemid on 2016-02-24
The analysis and solution to the problem of Shotwell Creating a Massive number of Tags is in three parts: 1. What I did wrong exporting from iPhoto. and 2. What Shotwell does wrong and 3 What I did to recover.

1. Exporting from iPhoto, I ticked the box to use Titles for file names. [ATTACH=CONFIG]267477[/ATTACH] DON'T DO THIS!  This created two instances of the title in the exported images, one of which Shotwell imported as a tag.  So for each image, I ended up with the same field as both a tag and a file name and a forest of 6000 tags!
2. Shotwell imports tags from any of these metadata fields: (Credit for this goes to Toma)
- Iptc.Application2.Keywords
- Xmp.dc.subject
- Xmp.digiKam.TagsList
- Xmp.lr.hierarchicalSubject
- Xmp.MicrosoftPhoto.LastKeywordXMP
All my photos exported from iPhoto had Xmp.dc.title set* as the title of the picture. This caused the import process to create a different tag for every single picture, which created my problems. 
3. To recover, temporarily renamed my home Pictures folder, created a new Pictures folder and also renamed my Shotwell database folder (Home/.local/share/shotwell) Then I re-exported my 6000 photo's in batches of 1000 from iPhoto _without the option to use titles for file names_.  If I knew SQL, apparently I could have deleted all tags in the Shotwell DB, but I don't know SQL.  Shotwell created a new DB folder and imported all the pictures with the Titles but without the duplicate tags.  Once I'm confident in the result, I'll go in and delete the renamed folders.

This little hiccup cost me a week or two in playing around and re-doing the export import took 4 hours.  I never thought moving away from the Apple ecosystem was going to be easy.  This confirmed that.

---

