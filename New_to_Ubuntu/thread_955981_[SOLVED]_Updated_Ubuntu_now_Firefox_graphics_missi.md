---
title: "[SOLVED] Updated Ubuntu now Firefox graphics missing."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Statik on 2008-10-22
My Ubuntu (Hardy) install on my laptop has been running fine for two months until the most recent update. I'm not sure what I updated, but now things are missing in firefox, graphically. I've attached screenshot. I'm thinking it might be nvidia related, but that's as far as I've gotten. Any ideas?

Statik

[IMG]http://www.statikonline.com/Slides/Firefox-Screenshot.png[/IMG]

---

### Post by Pro-reason on 2008-10-22
I can see that several graphics are loaded on that screen.  What's missing is some styling.  Could you have accidentally blocked the CSS file in AdBlock?

---

### Post by Statik on 2008-10-22
No, the css isn't blocked, but it seems like it might be a standards thing. Other sites, that display correctly, are in Quirks mode. This one is in standards mode and the error console has a bunch of warnings like :
```

Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-3828c0fa-00098.css
Line: 793
--------------------------------------------------------------------------
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-3828c0fa-00098.css
Line: 798
----------------------------------------------------------------------------
Warning: Expected color but found '#'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-3828c0fa-00098.css
Line: 1023
----------------------------------------------------------------------------
Warning: Expected color but found '#'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-3828c0fa-00098.css
Line: 1052
```

Thats just some of them. I know I can switch modes... I just have to remember/find out how.

Statik

---

### Post by Statik on 2008-10-22
Well of all the . . . I was looking through the setting of the Web Developer add-on that I use, looking for the mode switch, and I came across two disabled settings: Page Colors and Minimum Font Size. I didn't set them, but unsetting them brought my pages back!

Marking as solved.

Statik

---

