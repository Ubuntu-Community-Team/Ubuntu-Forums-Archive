---
title: "bash script: check for deleted files"
date: 2012-09-27
forum: Programming Talk
---

### Post by Ares Drake on 2012-09-27
Hey folks. I could use some help with a (bash) script, trying to check for deleted files.

Problem background:
[INDENT]I have an extensive video library on disk. All legaly recorded from television with mythtv. I wrote a script to generate an XML file from that library, contaning info on all video files with file size, duration, audio languages, audio- & videocodecs, bitrates, etc.

To update this XML file, the script currently just throws the old version away and generates a new XML file from scratch, iterating through all directories and all files again, and probably only a couple have changed.[/INDENT]

Having only very little programing experience, the best I could come up with a little help of google was the idea to:
[LIST]
[*]Loop through all files with find, put the output of find into an array, store the array into a "storagefile". This file would document all files in the XML at the first run. Then proceed as normal with the first run, generate the XML file.
[*]For the next run, only files newer than the date of the first run would need to be added to the XML.
[*]However old files, that are now deleted would have to be removed from the XML file. To do so, I would reload  the "storagefile" into an array, loop through that array and check if the files are still present on disk. I case a file was in the array, but no longer on disk, it's <video> ... </video> entry would need to be removed from the XML file.
[/LIST]

This however sounds rather complicated to me. Am I missing something? Are there easier options for what I want? Does anyone have some code sniplets for similiar problems, and wants to share with me?

Thanks in advance for any pointers,

best regards
Ares Drake

---

### Post by ofnuts on 2012-09-27
> **Ares Drake said:**
> Hey folks. I could use some help with a (bash) script, trying to check for deleted files.

Problem background:[INDENT]I have an extensive video library on disk. All legaly recorded from television with mythtv. I wrote a script to generate an XML file from that library, contaning info on all video files with file size, duration, audio languages, audio- & videocodecs, bitrates, etc.

To update this XML file, the script currently just throws the old version away and generates a new XML file from scratch, iterating through all directories and all files again, and probably only a couple have changed.[/INDENT]Having only very little programing experience, the best I could come up with a little help of google was the idea to:
[LIST]
[*]Loop through all files with find, put the output of find into an array, store the array into a "storagefile". This file would document all files in the XML at the first run. Then proceed as normal with the first run, generate the XML file.
[*]For the next run, only files newer than the date of the first run would need to be added to the XML.
[*]However old files, that are now deleted would have to be removed from the XML file. To do so, I would reload  the "storagefile" into an array, loop through that array and check if the files are still present on disk. I case a file was in the array, but no longer on disk, it's <video> ... </video> entry would need to be removed from the XML file.
[/LIST]

This however sounds rather complicated to me. Am I missing something? Are there easier options for what I want? Does anyone have some code sniplets for similiar problems, and wants to share with me?

Thanks in advance for any pointers,

best regards
Ares Drake
If I were to do the same, I would keep an XML stub for each file in the same directory of that file (ie foo.mp4 would have a foo.xml) (or in a "shadow" directory structure elsewhere, or in any file structure/naming convention that makes it simple to go from video to xml and vice-versa).

Then to rebuild:
- for each xml, if there is no video, remove the xml
- for each video, if there is no xml or if the xml is older, rebuild the xml
- collect all the xml and build the final xml from them.

---

