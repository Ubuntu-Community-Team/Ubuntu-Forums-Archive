---
title: "Taking a look at linux sourcecodes"
date: 2008-08-08
forum: Programming Talk
---

### Post by tuxerman on 2008-08-08
I want to get hold of source code for some small linux program (a utility or some such thing, for instance) to see how it has been programmed and implemented. I have a fairly moderate knowledge of programming with c and c++, but I am yet to teach myself making GUI-based programs. 
Could anyone give me a site to get my hands on code for some program that runs on linux... for example I thought I would take a look at knotes, but I couldnt find the code for it on the web. Or does it mean I may have to download the entire KDE source code to get the Kntoes code?

---

### Post by geogur on 2008-08-08
go down one thread and read it`s awsome thats wher i`ll be.

---

### Post by mssever on 2008-08-08
Use ```
apt-get source packagename
# Example:
apt-get source inkscape
```That'll download you Ubuntu's source package and extract it to the current directory. Note that you DON'T need sudo for this command.

If you want upstream sources, the method will vary by project. Very often it'll be svn, or cvs, or bzr, or whatever.

---

### Post by mssever on 2008-08-08
> **geogur said:**
> go down one thread and read it`s awsome thats wher i`ll be.
Which thread is that? "[need grep regular expression for link grabbing]("http://ubuntuforums.org/showthread.php?t=261161")"? Threads change their order regularly. If you want to refer to a thread, please provide a link so others will know what you're referring to.

---

### Post by nvteighen on 2008-08-08
Just a friendly advice: 'apt-get sources' will download the source to the current diretory, so, you'd probably want to create a new directory, change to it and then run 'apt-get sources'... It's amazing what a mess you can produce if you don't do that...

---

### Post by tuxerman on 2008-08-08
Thanks everyone... and mssever, the thread geogur meant was this: [Entry Point into Open Source Development]("http://ubuntuforums.org/showthread.php?t=883130")

---

