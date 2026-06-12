---
title: "Manage file/dir emblems"
date: 2009-05-09
forum: Programming Talk
---

### Post by KaLPo on 2009-05-09
Hi!

I want to manage file's and dir's emblems using command line, C, python or java but I cant find how.

I am trying to do a nautilus script for subversion which works like [SCPlugin]("http://scplugin.tigris.org/") for Mac (I have attached some screenshots, [Link]("http://www.blogcdn.com/www.tuaw.com/media/2007/08/scplugin082807.jpg")). It add an emblem with a green tic for saying that the file is synchronized and a red cross for non synchronized. That is what I dont know how to do.

Does anyone know about this?

NOTE: I have been searching in google and in the forum but I have found nothing.

Thank you!!

---

### Post by Arndt on 2009-05-09
> **KaLPo said:**
> Hi!

I want to manage file's and dir's emblems using command line, C, python or java but I cant find how.

I am trying to do a nautilus script for subversion which works like SCPlugin for Mac (I have attached some screenshots). It add an emblem with a green tic for saying that the file is synchronized and a red cross for non synchronized. That is what I dont know how to do.

Does anyone know about this?

NOTE: I have been searching in google and in the forum but I have found nothing.

Thank you!!

I don't see any attachment. Did you forget it?

---

### Post by KaLPo on 2009-05-09
Yes... I forgot to press Upload. I've just done it so now there are. This is one of it anyway:
[IMG]http://www.blogcdn.com/www.tuaw.com/media/2007/08/scplugin082807.jpg[/IMG]
URL: [http://www.blogcdn.com/www.tuaw.com/media/2007/08/scplugin082807.jpg](http://www.blogcdn.com/www.tuaw.com/media/2007/08/scplugin082807.jpg)

Thank you for the answer!

---

### Post by geirha on 2009-05-09
If you look into ~/.nautilus/metafiles/ you should see some xml files with urlencoded filenames. E.g. file:%2F%2F%2Ftmp.xml corresponds to /tmp .

Find the file for a folder you've changed emblems in, and open it in an editor and see how the entries for those files look. Editing those xml-files from your program/script might work. Haven't tried it though.

---

### Post by KaLPo on 2009-05-09
Wow, you are absolutely right!

I have understood how it works and looks really simple.

I am going to do some testing.

Thank you very much!!!!

---

### Post by KaLPo on 2009-05-10
Ok, I have tried to modify the files in the metafiles folder without any successes. This is one of the files in my metafiles folder:

```
<?xml version="1.0"?>
<directory><file name="Webcam" timestamp="1241955656"><keyword name="cool"/></file></directory>
```
The keyword tag represents an emblem named with the variable name.

The timestamp variable is, as far as I have know, the time stamp of the change. :???:.

Well, I have done a simple python script which overwrites this file changing the timestamp and the name of the keyword/emblem:

```
#!/usr/bin/python
import time
 
try: 
    # The addres has to be changed obviously. Change 'kalpo' for your username
    f = open("home/kalpo/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fkalpo%2FPictures.xml", "w")
    try:
	f.write("<?xml version=\"1.0\"?>\n<directory><file name=\"Webcam\" timestamp=\"" + str(long(time.time())) + "\"><keyword name=\"OK\"/></file></directory>")
    finally:
        f.close()
except IOError:
    pass
```

My problem is that this has no effect, so the folder I am trying to change the emblem still has the same emblem.

I have change the emblem manually using the nautilus dialog and after that I have compared both files, the one created by nautilus and the other one which was created by my script by both looks like the same but for the timestamp... 

I guess there must be something else, like any kind of notice to nautilus or similar because if you remove any of the xml files, the effects cant be seen and it is a waste of resources to be permanently watching this files for changes. In the man page of nautilus there is no such option btw.

Does anyone know about this??

Thank you!!!

---

### Post by geirha on 2009-05-10
Hm. Yes. The change only takes effect after restarting nautilus it seems (killall nautilus). There might be a way to tell nautilus to re-read the metafiles through dbus. I don't know much about dbus, but it should be worth a google search I think.

---

### Post by KaLPo on 2009-05-10
Well, I havem't found the way to do it, but I have found that there is an amazing project which does everything I was planning to program

[http://code.google.com/p/nautilussvn/](http://code.google.com/p/nautilussvn/)

Really impressive.

If there was any interested in how to do that we where speaking about, check out the source code or [this]("http://wiki.creativecommons.org/Liblicense_tutorial#Command-line_Interface") can probably help you.

Thank you for your interest!!!

---

