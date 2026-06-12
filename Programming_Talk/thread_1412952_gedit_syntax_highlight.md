---
title: "gedit syntax highlight"
date: 2010-02-21
forum: Programming Talk
---

### Post by oviorus on 2010-02-21
Hello, I'm trying to make gedit automatically highlight *.as files when I open them. Here is what I've done so far:

1) I created a custom highlight spec in */usr/share/gtksourceview-2.0/language-specs/actionscript3.lang*. This is the head of the file:

[INDENT]<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE language SYSTEM "language.dtd">
<language id="actionscript3" _name="ActionScript 3" version="1.0" _section="Sources">
  <metadata>
    <property name="mimetypes">text/x-actionscript3</property>
    <property name="globs">*.as</property>
    <property name="line-comment-start">//</property>
    <property name="block-comment-start">/*</property>
    <property name="block-comment-end">*/</property>
  </metadata>  
.
.
.[/INDENT]

Now I can select it inside gedit with View > Highlight Mode > Sources > ActionScript 3 and it works fine.

2) I created a custom mimetype in the following locations with the following data

*~/.mime.types*

    [INDENT]text/x-actionscript3			as

[/INDENT]*/usr/share/mime/packages/freedesktop.org.xml*

 [INDENT] <mime-type type="text/x-actionscript3">
    <comment>AS3 source code</comment>
    <generic-icon name="text-x-generic"/>
    <glob pattern="*.as"/>
    <sub-class-of type="text/plain"/>
  </mime-type>[/INDENT]
    
*~/.local/share/mime/packages/actionscript3.xml*
[INDENT]
  <mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
    <mime-type type="text/x-actionscript3">
      <comment>ActionScript 3 Source</comment>
      <!-- more translated comment elements -->
      <glob pattern="*.as"/>
    </mime-type>
  </mime-info>[/INDENT]

and restarted. Now both nautilus and gedit recognize .as files as text/x-actionscript3. However I still have to manually select ActionScript Highlight from the menu. Is there something else I can try?

Thank you for your time.
Heron Anzures.

---

### Post by delfick on 2010-02-22
hello,

You need to update the mime database

Third part of this [http://ubuntuforums.org/showthread.php?t=742981](http://ubuntuforums.org/showthread.php?t=742981) shows you how to do that

Also, you can find some syntax files here : [http://code.google.com/p/flashbsm/source/browse/testing/language-specs/](http://code.google.com/p/flashbsm/source/browse/testing/language-specs/)

:D

---

### Post by oviorus on 2010-02-22
Thank you delfick. I just updated the mime database as you suggested, but nothing happened. I still have to manually pick the syntax highlight. I believe the mimetype is not the problem, because both nautilus and gedit recognize *.as files as text/x-actionscript3 as expected. The same goes for gnomevfs-info command. I don't know where the problem lies though. But thank you I'll keep looking.

Heron Anzures

---

### Post by delfick on 2010-02-22
hmmm, I'm not sure then........... sorry

---

### Post by oviorus on 2010-02-22
I found the problem!. Looks like there is something wrong in my actionscript3.lang file, maybe some deprecated tags or something, because I tried one of yours and it worked. It's strange though, that I was able to select it from inside gedit and reported no problems. Now I'll just try different highlight specs. 
Thank you.
Heron Anzures.

---

### Post by delfick on 2010-02-23
> **oviorus said:**
> I found the problem!

Awesome :D
> . Looks like there is something wrong in my actionscript3.lang file, maybe some deprecated tags or something, because I tried one of yours and it worked. It's strange though, that I was able to select it from inside gedit and reported no problems.

weird....

> 
Thank you.
Heron Anzures.

no probs :D

---

### Post by matteosistisette on 2012-04-28
Where's the lang definition you downloaded? I can't find it in any of the links mentioned above.

The one at [http://code.google.com/p/flashbsm/source/browse/testing/language-specs/](http://code.google.com/p/flashbsm/source/browse/testing/language-specs/) is 2.0

thanks

---

