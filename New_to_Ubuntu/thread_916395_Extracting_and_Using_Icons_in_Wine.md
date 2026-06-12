---
title: "Extracting and Using Icons in Wine"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by anachronon on 2008-09-10
I have a couple Windows programs that I am using under Wine.  I want to extract the Windows Icons, so that I can access those Wine programs directly from my desktop, as I would in Windows.

I have been directed to use "icoutils".  However, after much searching for instructions, I am left frustrated.  So far, all of the directions have been as clear as mud.  Can someone talk me through this?

To this point, I have used apt-get to install icoutils.  Next, I have made a copy of the .exe file that I wish to search in my home directory.  Using "wrestool", I have searched that .exe file, and located the icons.

That is as far as I got.  There are over a hundred icons alone.  Which do I choose?  How do I specify the one I want?  What do I do with it then? etc

---

### Post by anachronon on 2008-09-11
Update:  I have found a way to extract the icons that I need, directly from the original Windows application:

```
$ wrestool -x --output=. -t14 ~/.wine/drive_c/(PATH)/(FILENAME).exe
```

This gave me about 40 .ico files in my home folder.  From there, I used this loop routine to convert to .png:

```
for i in *.ico; do convert "$i" "$i.png"; done
```

So now, I have a total of 160 icon files in my home folder (40 .ico and 120 .png).  My next question is, how do I select the icon that I want, move it to my desktop, and link it to the .exe file.

I will keep looking for more info, and post what I find.  Meanwhile, does anyone have any tips?

---

### Post by Endolith on 2009-01-18
I'd like to make this automatic.  See [https://bugs.launchpad.net/ubuntu/+source/libgnomeui/+bug/292504](https://bugs.launchpad.net/ubuntu/+source/libgnomeui/+bug/292504)

---

