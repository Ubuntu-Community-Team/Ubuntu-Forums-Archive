---
title: "HOWTO: Easily print LaTeX beamer slides in Linux"
date: 2008-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by hyperboloid on 2008-12-06
The LaTeX beamer class creates lovely slides for presentations including overlays, pauses, and other nice effects. And since it is LaTeX, it handles math, tables, and graphics spectacularly well. However, it is not so easy under Linux to format the slides for printing. This post presents a solution to this common problem.

0. You must have a working TeX installation ('texlive' is a good choice).

1. Install the 'pdfjam' package if you haven't already done so. This provides some nice tools for manipulating PDF files (joining, rotating, etc).
```
sudo apt-get install pdfjam
```

2. Download the attached script, unzip it anywhere you like, and make the resulting file 'makehandouts' executable:
```
chmod +x makehandouts
```

3. Move the script 'makehandouts' somewhere in your search path, such as (for example) /usr/local/bin:
```
sudo mv makehandouts /usr/local/bin
```
To make sure that the place you put it really is in your search path, do: 
```
echo $PATH
```


Installation is now finished. Assuming that you have a LaTeX beamer source file named 'xxx.tex' in some folder, in a terminal navigate to that folder and type:
```
makehandouts xxx
```
(note that the file extension is NOT included). Of course, substitute your *actual* file name in place of "xxx". The 'makehandouts' command creates 4 new PDF files, as follows:
[LIST]
[*]xxx-handout.pdf is a viewable version of your slides, without pauses and overlays.

[*] xxx-handout1up.pdf is a printable version of the slides, one slide per page, rotated by 90 degrees (in landscape mode) for proper printing.

[*] xxx-handout2up.pdf is a printable version of the slides, showing two slides per page. 

[*] xxx-handout4up.pdf is a printable version of the slides, rotated 90 degrees to landscape mode, showing four slides per page.
[/LIST]
**NOTE:** It is probably important to use 'acroread' to print the slides, since that tool fits everything to the page, and other tools are not so good at that. Enjoy...;)

---

### Post by teich on 2009-08-26
Hey, that's pretty handy.  Thanks.  :)

teich

---

### Post by mimicotiffany on 2010-07-10
Thank-you to whoever wrote this script!  This is exactly what I needed!

Cheers.

---

### Post by Gladk on 2010-09-28
Thanks a lot for this excellent script!

---

### Post by Dr.Gonzo08 on 2010-11-24
should also work with the following lines:
```

\documentclass[handout]{beamer}
\usepackage{pgfpages} 
%\pgfpagesuselayout{2 on 1}[a4paper,border shrink=3mm]
\pgfpagesuselayout{4 on 1}[a4paper,landscape,border shrink=3mm]

```
looks pretty nice for me... and you wouldn´t need other packages for use.

---

### Post by dple on 2011-06-17
Thank a lots. This one helps me so much.

---

