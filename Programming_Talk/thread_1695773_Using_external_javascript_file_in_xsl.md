---
title: "Using external javascript file in xsl"
date: 2011-02-26
forum: Programming Talk
---

### Post by BerryLawson on 2011-02-26
Hi you experienced people...

I am writing a small website using small .xml datafiles, displayed with .xsl.  How do I include a function from an external javascript file?  I have searched your FAQs and the wider internet, but not found anything my inexperienced mind can understand.

The code I am trying (not working) is this:


..........
<xsl:template match="/">

<html><head>
     <script type="javascript" src="doMenu.js"></script>
     <style type="text/css"><title>Tiverton U3A - Monthly Diary</title></style>
</head>

<body style="background:url(resources/Background2.jpg) repeat fixed;">
<script type="javascript">menubuttons();</script>
......etc


Same code works ok in an ordinary .html file, and correctly displays my 'menu' buttons, but does not work in the .xsl file.

Help!

Berry Lawson

---

