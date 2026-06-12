---
title: "Python problem"
date: 2012-04-25
forum: Programming Talk
---

### Post by sscpord on 2012-04-25
@font-face {   font-family: "Times New Roman"; }p.MsoNormal, li.MsoNormal, div.MsoNormal { margin: 0in 0in 0.0001pt; font-size: 12pt; font-family: "Times New Roman"; }table.MsoNormalTable { font-size: 10pt; font-family: "Times New Roman"; }div.Section1 { page: Section1; }    Hi
   
  I am having a lot of difficulty getting my head around what to do and how to write this with my very limited knowledge of python so any help would be appreciated.
   
   
  I have a geodatabase called Buckinghamshire_ County.gdb with a number of feature classes , one of which is called Test. Within this Test feature class there are four fields titled   linenumber,  startpoint, endpoint  and identity.
   
  What I would like to do is to begin on the first row and take the value from the endpoint field. Then using this value search through all the values of the startpoint field until a match is found. When a match is found I then want to get the value of the linenumber on the row where the match is found and insert it into the identity field on the first row. 
   
  When that is complete I want to move onto the second row and redo the process of searching and inserting so that in the end I have populated the identity field for all the matching endpoint and startpoint values.
   
  It would be great to run the python code from the field calculate tool but I don’t know if that will be possible this is not possible

---

### Post by corrytonapple on 2012-04-25
Post your question here:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

That is where some programmers hang out.

Actually, I'll see if a mod can move it too.

---

### Post by sscpord on 2012-04-25
Hi

I'd be grateful if you were able to arrange for the question to be moved. Thanks for taking the time to do that

Derek

---

### Post by corrytonapple on 2012-04-25
I put it in the que so a mod can move it.

---

### Post by sffvba[e0rt on 2012-04-25
*Thread moved to **Programming Talk**.*


404

---

### Post by LemursDontExist on 2012-04-25
I don't know much about geodatabase files, but I thought I'd see what I can do about being helpful anyway!

It looks as .gdb files are created by a proprietary program called ArcGIS.  A little searching turned up [GDAL]("http://www.gdal.org/"), which seems to be an open source GIS library with python bindings which supports .gdb files, though it's a little unclear to me whether it supports them out of the box, or if you need to install an extra library.  I'd suggest trying to install GDAL, and then reading their documentation and figuring out how to work with it - they seem to have some basic python examples on their tutorial page.

Anyway, maybe someone who knows more about GIS will come along, but in case they don't this is where I'd start on this project!

Once you've looked around their website and fiddled with the library a little, if you have any questions more specific to python, I'm sure the forum will be more able to help!

---

