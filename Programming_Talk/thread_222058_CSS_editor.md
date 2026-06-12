---
title: "CSS editor"
date: 2006-07-24
forum: Programming Talk
---

### Post by ivan.virtuale on 2006-07-24
Hi,
please help me... What's the best css editor for Gnome?
With graphic preview inside (like TopStyle Pro in winzozz) ?
Ivan

---

### Post by jayemef on 2006-07-24
I'm a fan of [Bluefish]("http://bluefish.openoffice.nl/index.html") for web development in general, including CSS. You might want to check out [CSSed]("http://cssed.sourceforge.net/") as well, but the last time I used it, it was still rather buggy.

Bluefish is available via apt:
```
$ sudo apt-get install bluefish
```
Not sure about CSSed, but I wouldn't be surprised if it is also.

---

### Post by OneSeventeen on 2006-07-25
My favorite CSS editor is the [Web Developer](http://addons.mozilla.org/firefox/60) extension for firefox.  You simply load the page, go to "Edit CSS" from the "CSS" menu on the Web Developer toolbar, and it pops open a sidebar with the CSS file, then you can edit it to your heart's content, with the page constantly updating in the viewer with your changes.

This is also great for dynamic pages, because you can load automagically generated pages, and edit the CSS based on the final output.

You do have to manually type all of the CSS, and it doesn't do code completion, but for being able to see the results instantaneously in a real-world browser I find it is worth it.

---

### Post by abrari on 2009-11-06
I don't know before that WebDeveloper add-on has an amazing feature like that.
Thanks.

---

### Post by dabbish on 2011-04-12
> **OneSeventeen said:**
> My favorite CSS editor is the [Web Developer](http://addons.mozilla.org/firefox/60) extension for firefox.  You simply load the page, go to "Edit CSS" from the "CSS" menu on the Web Developer toolbar, and it pops open a sidebar with the CSS file, then you can edit it to your heart's content, with the page constantly updating in the viewer with your changes.
 

Too bad it doesn't have any syntax highlighting. Pretty useless without that as an editor.

---

### Post by JacksSmith on 2011-04-13
BlueFish is the best editor for CSS. It is very easy to use.

---

### Post by davidvandoren on 2011-04-16
I find firebug to be very easy to use and useful.
It has auto complete.
You can open any page and select them by clicking on them then change the css and see the results instantaneously. 

[http://getfirebug.com/](http://getfirebug.com/)

---

### Post by Enigmapond on 2011-04-16
> **JacksSmith said:**
> BlueFish is the best editor for CSS. It is very easy to use.
+1

And it will do what you are asking. Although, for CSS, Leafpad is also great but I always use Bluefish.

---

### Post by holes88 on 2011-04-18
Bluefish is very good, but quanta is good too if you want a preview feature.:P

---

### Post by juditk on 2011-08-10
I tried to install quanta but it gave the folowing error in the  Ubuntu Software Center 
> libqt3-mt (>= 3:3.3.8-b) but it is not going to be installed
        Depends: kfilereplace-kde3 (= 4:3.5.10-0ubuntu4) but 4:3.5.10-0ubuntu4 is to be installed
        Depends: klinkstatus-kde3 (= 4:3.5.10-0ubuntu4) but 4:3.5.10-0ubuntu4 is to be installed
        Depends: kommander-kde3 (= 4:3.5.10-0ubuntu4) but 4:3.5.10-0ubuntu4 is to be installed
        Depends: tidy but it is not going to be installed

and in Synaptic:

> Depends: kdelibs4c2a but it is not going to be installed
 Depends: libqt3-mt (>=3:3.3.8-b) but it is not installable
 Depends: kfilereplace-kde3 but it is not going to be installed
 Depends: klinkstatus-kde3 but it is not going to be installed
 Depends: kommander-kde3 but it is not going to be installed
 Depends: tidy  but it is not installable
 Recommends: cervisia  but it is not installable
 Recommends: kompare  but it is not installable
 Recommends: kxsldbg (=4:3.5.10-0ubuntu4) but it is not installable

I'm using Ubuntu 11.4. 
Is quanta not available anymore? Or am I doing something wrong?
What confuses me is that it says "it is not going to be installed". Why? I don't know what I should do with that. :confused:

---

