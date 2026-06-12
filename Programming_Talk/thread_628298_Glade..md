---
title: "Glade."
date: 2007-12-01
forum: Programming Talk
---

### Post by Kadrus on 2007-12-01
Euuh...I am having some problems compiling a GLADE project..
When I draw the interface and all...and I "build it"...there is something called autogen.sh...
But I cannot run the program...can anyone help?

---

### Post by Majorix on 2007-12-01
This doesn't belong in this section.

I have never used Glade (only wxGlade) but are you sure you made the file executable?
```
chmod a+x autogen.sh
./autogen.sh
```

---

### Post by LaRoza on 2007-12-01
> **Majorix said:**
> This doesn't belong in this section.


It involves compiling a program, Programming Talk is one of two forums where this question fits.

---

### Post by Kadrus on 2007-12-01
> **Majorix said:**
> This doesn't belong in this section.

I have never used Glade (only wxGlade) but are you sure you made the file executable?
```
chmod a+x autogen.sh
./autogen.sh
```

I am getting this...
```
**Error**: Directory `.' does not look like the top-level package directory

```
how can I fix that?

---

### Post by Majorix on 2007-12-01
Could you upload your autogen.sh? I believe it should read "./" instead of "." somewhere in it.

---

### Post by Kadrus on 2007-12-01
You mean an attached file?

---

### Post by Majorix on 2007-12-01
If it's short enough, wrap it in [code] tags. If not, upload it on a free hosting site. I don't think attaching would work, but you could try. I always imagined attachments to be picture-only.

---

### Post by Kadrus on 2007-12-01
> **Majorix said:**
> If it's short enough, wrap it in [code] tags. If not, upload it on a free hosting site. I don't think attaching would work, but you could try. I always imagined attachments to be picture-only.
Euuh I am going to try an attachment..if it doesn't work...I will try on a web site..

So it appears that it works :)

---

### Post by Majorix on 2007-12-01
It appears you lack the file configure.in in the folder of the autogen.sh. This told me that:
```
(test -f $srcdir/configure.in)
```
The code above produces the exact error message you posted when it throws an exception.

Try finding the file mentioned, and then change srcdir in line 5 to represent the directory. Do NOT use an ending /, it adds that automatically from what I see.

---

### Post by Kadrus on 2007-12-01
> **Majorix said:**
> It appears you lack the file configure.in in the folder of the autogen.sh. This told me that:
```
(test -f $srcdir/configure.in)
```
The code above produces the exact error message you posted when it throws an exception.

Try finding the file mentioned, and then change srcdir in line 5 to represent the directory. Do NOT use an ending /, it adds that automatically from what I see.
Weird..it's telling me "You must have `glib' installed."
And when i go to this site:
[ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)

I can't  find...anyway...i won't be using GLADE anymore..
So thanks anyway :)

---

### Post by MicahCarrick on 2007-12-01
The "Build" feature of glade is deprecated, and the current version of glade (glade3) no longer uses it at all. But, it was attempting to generate a build script for you. You would need to have all the development files necessary for it to work (libgtk2-dev, libglib-2.0-dev, etc.) as well as the various auto tools (automake, intltool, etc).

Now days, we use a library called Libglade from our application (be it C, Python, C++, PHP, etc.) to build the interface we design in glade. This post: [Very, very simple example using libglade]("http://www.gtkforums.com/about187.html")

In this example, if you copy/paste that .glade file in the text editor of your choice and save with the .glade extension, you'll be able to open in in glade. Then, there's a few lines of C code which implement that .glade file.

---

### Post by Kadrus on 2007-12-01
> **MicahCarrick said:**
> The "Build" feature of glade is deprecated, and the current version of glade (glade3) no longer uses it at all. But, it was attempting to generate a build script for you. You would need to have all the development files necessary for it to work (libgtk2-dev, libglib-2.0-dev, etc.) as well as the various auto tools (automake, intltool, etc).

Now days, we use a library called Libglade from our application (be it C, Python, C++, PHP, etc.) to build the interface we design in glade. This post: [Very, very simple example using libglade]("http://www.gtkforums.com/about187.html")

In this example, if you copy/paste that .glade file in the text editor of your choice and save with the .glade extension, you'll be able to open in in glade. Then, there's a few lines of C code which implement that .glade file.
Oh alright..thanks a lot Micah :D
Appreciated :)

---

