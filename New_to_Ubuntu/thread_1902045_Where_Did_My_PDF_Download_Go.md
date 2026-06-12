---
title: "Where Did My PDF Download Go?"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by rs321 on 2011-12-29
Folks,

I just downloaded a pdf file and as soon as it completed it disappeared from the list.  Where can I find it?  I'm afraid I was able to get nowhere with a search here.

-Randy

---

### Post by oldos2er on 2011-12-29
If you downloaded it with Firefox, by default it goes to /home/user/Downloads.

---

### Post by rs321 on 2011-12-29
Ann,

Thanks, that's just where the little beggar was hiding!  I thought I looked for downloads there before and didn't find them, but silly me I missed it.

Thanks again.

-Randy

---

### Post by oldos2er on 2011-12-30
You're welcome.

---

### Post by RayArdia on 2011-12-31
Similar problem, which I've never had before - and when I search I can't find the downloaded .pdf file. I have looked in Downloads and ran another search there but with no luck.
What am I doing wrong?
Ray

---

### Post by morhin on 2011-12-31
I'm a noobie running 10.04. 

When I tried to download a web page I found I had to ***print*** it to a file. 
After a few times of not being able to find what I had downloaded I realized the print window default is set to create a .ps file.
I had to click on the create a .pdf file. After that I found them right where I asked them to go.

file / print / print to file / select pdf / change folder if desired / print

morhin

my wife tells me I'm wrong so often I'm thinking about becoming a weatherman

---

### Post by gandaran on 2011-12-31
> **morhin said:**
> I'm a noobie running 10.04. 

When I tried to download a web page I found I had to ***print*** it to a file. 
After a few times of not being able to find what I had downloaded I realized the print window default is set to create a .ps file.
I had to click on the create a .pdf file. After that I found them right where I asked them to go.

file / print / print to file / select pdf / change folder if desired / print

morhin

my wife tells me I'm wrong so often I'm thinking about becoming a weatherman
you have to name the pdf file, if you just use ".pdf" you will find the file in the hidden home folder, click to view hidden files.

---

### Post by andrew.46 on 2012-01-01
> **RayArdia said:**
> Similar problem, which I've never had before - and when I search I can't find the downloaded .pdf file.

More than likely it is in your home folder so something like the following would help:

```
find $HOME -iname *.pdf
```

More information about 'find' can be found here:

find
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

---

