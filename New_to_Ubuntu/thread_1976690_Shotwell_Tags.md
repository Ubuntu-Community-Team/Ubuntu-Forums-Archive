---
title: "Shotwell Tags"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by expatCM on 2012-05-09
Does anyone know if there is an easy way to edit the list of tags in shotwell.  The gui seems to let you edit only one at a time and you are prompted for each deletion which makes it a really slow painful operation.  What I was looking for was a txt file I can quickly edit ....

---

### Post by eric-yorba on 2012-05-09
What are you trying to do, exactly?

---

### Post by expatCM on 2012-05-09
When you install Shotwell it is pre-populated with a range of tags.  Those tags are simply not relevant to my needs.  

They may be removed incrementally but since there are say 100 tags I would like to remove them as a batch.  You cannot use Control to select more than one tag so I am now looking for a file to go and edit.  However ...  it looks like everything is held in a database which may mean that incremental removal is the only solution.

---

### Post by Preserved Killick on 2012-05-13
Hi.  I have the same problem with removing tags from the list.  I can't remove more than one at a time.  I'd be glad to see answer posted here.  (Shotwell came with my 12.04 distro and it had no tags in it when I first launched it.  I'm still playing with it-- adding a folder of pictures, then removing them to test behavior, so that's when I noticed you have to remove tags individually).

But I do wonder about removing tags from the list-- if you remove a tag from the list, will Shotwell also remove it from all of the photos in the library that had that tag?  Would that be a good thing?

killick

---

### Post by Preserved Killick on 2012-05-13
OK, I found this:

[http://shotwell.3510.www.nabble.com/Shotwell-massive-automatic-tag-creation-with-import-how-to-delete-them-all-td56005.html]("http://shotwell.3510.www.nabble.com/Shotwell-massive-automatic-tag-creation-with-import-how-to-delete-them-all-td56005.html")

But I have no experience with sql databases.

---

### Post by eric-yorba on 2012-05-14
> **Preserved Killick said:**
> But I do wonder about removing tags from the list-- if you remove a tag from the list, will Shotwell also remove it from all of the photos in the library that had that tag?  Would that be a good thing?

Yes, but let me explain a bit. By default, tags are only stored in Shotwell's database for performance reasons.  If you've enabled the "write metadata to files" option, then Shotwell will also remove the tag from all your files -- note that this may take some time if you have a large photo collection.

---

