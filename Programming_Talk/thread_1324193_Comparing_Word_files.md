---
title: "Comparing Word files"
date: 2009-11-12
forum: Programming Talk
---

### Post by thunderbirdje on 2009-11-12
Hi Everyone,

I would like to sketch my situation... I am teaching Microsoft Word 2007 (sorry about that... but I refer to open source as well :)). You can imagine that with a a large amount of students (about 200) I have to open 200 times the same Word-file to compare and check if (for example) the applied font is correct. 

I was wondering of there is a possibility to compare Word files on layout to a master file? I would prefer php (if possible) because I developed a small exercise site (multiple choice quiz etc.) in php, so it would be great if I can integrate that into the training site.

I am able to compare the text of the Word file, however it is the layout (formatting) which I don't know if that is able? You can compare files in Word and show the differences... If that would be possible in php, to generate such a difference file (you can with C# .NET access the Word COM object model...) but I do like php more :D I hope some can help me? Maybe there is some open source framework in php which I don't know the existence of it?

Thanks I lot, and I hope I can help others with this question too! I am always prepared to share my experience or if I can find a solution...

---

### Post by myrtle1908 on 2009-11-12
If the compare functionality is exposed by the Word COM server (which you say it is eg. .NET/C#) then any COM aware language can utilize.  PHP can talk COM so you should have no problem eg.

[PHP]
$word = new COM("Word.Application");
# ... and so on ...
[/PHP]

---

