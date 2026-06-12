---
title: "Acrobat Reader 9 and childsplay not working after upgrade to 13.10"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2013-11-20
After I upgraded to Ubuntu 13.10 from version 13.04 some of already installed programs have stopped working. One of them is Acrobat Reader 9. When I click on acrobat reader 9 icon in dash nothing happen. If I try to run it through command line I get output

"/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory"

I believe it has something to do with ia32-libs package. As the package has become obsolete. I have installed newer alternate package but that is not working.

Second such program which has stopped working is childsplay. Same like Acrobat Reader 9, nothing happens when I clicked it's icon in dash. Below here is output when I try to run it in terminal

"Traceback (most recent call last):
  File "/usr/games/childsplay", line 118, in <module>
    import childsplay_sp.SPMainCore as SPMainCore
  File "/usr/lib/python2.7/dist-packages/childsplay_sp/SPMainCore.py", line 64, in <module>
    from sqlalchemy import exceptions as sqla_exceptions
ImportError: cannot import name exceptions"


Please help as both these software are important for me.

---

### Post by philinux on 2013-11-20
See this  
[http://ubuntuforums.org/showthread.php?t=2181100&p=12850933&viewfull=1#post12850933](http://ubuntuforums.org/showthread.php?t=2181100&p=12850933&viewfull=1#post12850933)

---

### Post by sujitrjadhav on 2013-11-21
Thanks a lot. It helped. Acrobat Reader 9 is now working. Can you help with second part as well? I am waiting for answer from some one for second part before I mark this thread solved.

---

### Post by philinux on 2013-11-21
```
sudo apt-get purge childsplay
```

Then reinstall it.

```
sudo apt-get install childsplay
```

Any user settings will be preserved.

---

### Post by monkeybrain20122 on 2013-11-21
Why even use Acroread? It is monstrous resource hog. The default document viewer works much better. Even in Windows I didn't use Acrobat's PDF reader.

---

### Post by philinux on 2013-11-21
> **monkeybrain20122 said:**
> Why even use Acroread? It is monstrous resource hog. The default document viewer works much better. Even in Windows I didn't use Acrobat's PDF reader.

Very simple.  Some complex pdfs will not display correctly in evince. No way no how. Formatting gets completely mangled.

---

### Post by Irihapeti on 2013-11-21
I've yet to find another Linux pdf viewer that will handle editable form fields as well as Acroread does. qpdf isn't bad, but it makes the text in some fields HUGE if there are only two or three words needed.

---

### Post by DuckHook on 2013-11-21
*monkeybrain* still has a point though. Until you run into such issues, I would recommend against Acroread too. I haven't needed to fill in editable form fields in forever. Have used Evince for years now, with perfect satisfaction. Acroread also has a history of getting compromised. So not only is it a pig, it easily passes swine flu. If it must be used, I would set Evince as the default and invoke Acroread only for the most swinish PDFs.

---

### Post by monkeybrain20122 on 2013-11-22
> **Irihapeti said:**
> I've yet to find another Linux pdf viewer that will handle editable form fields as well as Acroread does. qpdf isn't bad, but it makes the text in some fields HUGE if there are only two or three words needed.

I can fill some forms with okular, but you are right that there is no good pdf form filler on Linux (it is a shame) especially forms with scripts (some tax forms, e.g)  To my mind a still better solution is to use PDF-Xchange-viewer in Wine (they claim that they have tested it on wine so there is no need for a Linux version. :)) It works perfectly and is very light and fast, unlike acroread. I use it only to fill forms maybe a couple of times in a year, otherwise I use the default reader (or Okular)

Besides, with Adobe dropping everything Linux who knows how long you will even have Acroread. I wouldn't put any egg in the Adobe basket. :)

---

### Post by sujitrjadhav on 2013-12-06
I tried purging and then reinstalling it. Here is output:

childsplay 
Traceback (most recent call last):
  File "/usr/games/childsplay", line 118, in <module>
    import childsplay_sp.SPMainCore as SPMainCore
  File "/usr/lib/python2.7/dist-packages/childsplay_sp/SPMainCore.py", line 64, in <module>
    from sqlalchemy import exceptions as sqla_exceptions
ImportError: cannot import name exceptions

---

### Post by josefg2 on 2014-05-10
I have the same problem, running Mint 16.
From what I can see on [this page]("https://bugs.launchpad.net/ubuntu/+source/childsplay/+bug/1247442") the problem is that the Childpslay package has not been updated in Ubuntu's repository for three years. Installing the latest version from source will supposedly solve the problem.

---

