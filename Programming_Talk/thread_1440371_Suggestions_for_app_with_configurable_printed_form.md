---
title: "Suggestions for app with configurable printed forms"
date: 2010-03-27
forum: Programming Talk
---

### Post by bhold on 2010-03-27
Hello -  I have been asked to develop an application which would allow the user to configure a printable output form through a gui, and then later print the form incorporating some external data. In the configurable form I would like to be able to specify numeric and text field positions, fonts, and define array sizes for printing of numeric fields. I would also like to configure grid lines around the output fields. This will be used for generating scoring and results sheets for events and later tabulation of results.

I have some C, C++, and a little Java knowledge but would like to minimize programming effort. I thought I might look at Open Office Database or sqlite and see if those would cover some of these requirements. Suggestions appreciated. Although this will be developed and run on Linux, easy and free portability to MS Windows would be a plus.

---

### Post by myrtle1908 on 2010-03-28
Have your GUI generate a file (eg. XML or JSON) which describes the document.  Then write some code which parses the file to create a printable document eg. PDF.

For example, if you went with XML and the free Java PDF library iText ...

```
<document>
  <fonts>
   <font id="label" family="verdana" style="bold" size="12"/>
   <font id="normal" family="verdana" style="normal" size="12"/>
  </fonts>
  <table>
   <row>
     <col font="label">Label 1</col>
     <col font="normal">Some text</col>
   </row>
   <!-- and so on -->
  <table>
</document>
```

Then you can easily parse this XML to create a PDF with iText using the PdfPTable classes etc.

Good luck.

[http://itextpdf.com/](http://itextpdf.com/)

**Later edit: I just re-read your post and it seems you would like to minimize programming effort. Given this, my idea is not so suitable.**

---

### Post by ic3man5 on 2010-03-28
myrtle1908's suggestion would be the most portable and most user configurable (they can edit the file with a text file). Using sqlite has always been my preference because its extremely easy to work with as long as you know basic sql. Also to make it portable the easiest solution would be gtk or qt (qt being the easier one IMO because it already has a database class).

My choice would be qt + sqlite.

---

