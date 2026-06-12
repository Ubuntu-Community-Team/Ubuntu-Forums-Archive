---
title: "XML issue"
date: 2007-01-01
forum: Programming Talk
---

### Post by welshboy on 2007-01-01
Hi guys,

I'm using OxygenXML to help me learn XML using a book I have.

The book gives the following syntax to import a CSS stylesheet so I can display it in firefox.

[COLOR="SeaGreen"]<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<?xml:stylesheet href="personnel.css" type="text/css"?>[/COLOR]

However, I seem to get an error :

[COLOR="Red"]The processing instruction target matching "[xX][mM][lL]" is not allowed.[/COLOR]

Even though the book swears blind that this is the way it works.  

Can anyone help me?

Many thanks

---

### Post by welshboy on 2007-01-01
Hi folks,

I have since found the solution.  It turns out that the book was using the wrong syntax,

Where it read:

[COLOR="SeaGreen"]<?xml:stylesheet href="personnel.css" type="text/css"?>[/COLOR]

it should have been:

[COLOR="SeaGreen"]<?xml-stylesheet href="personnel.css" type="text/css"?>[/COLOR]

NOTE: the dash rather than the colon.  Hope that prevents others making the same mistake.
[COLOR="DarkOrange"]
welshboy[/COLOR]

---

