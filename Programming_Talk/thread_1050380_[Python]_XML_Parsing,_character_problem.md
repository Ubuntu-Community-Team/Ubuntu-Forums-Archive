---
title: "[Python] XML Parsing, character problem"
date: 2009-01-25
forum: Programming Talk
---

### Post by kjohansen on 2009-01-25
I have an XML file, when I attempt to parse it using the minidom I get illegal character errors.  Checking the file there weird characters, excerpt include below. When I remove all the special characters everything works as I expect.  The problem is that I have several thousand of these files and cannot remove these values by hand is there way to ignore the special characters in the minidom, or do I have to write a separate script to remove all the special characters?

Look in the "unknown" tag...
> 
<REUTERS TOPICS="YES" LEWISSPLIT="TRAIN" CGISPLIT="TRAINING-SET" OLDID="5544" NEWID="1">
<DATE>26-FEB-1987 15:01:01.79</DATE>
<TOPICS><D>cocoa</D></TOPICS>
<PLACES><D>el-salvador</D><D>usa</D><D>uruguay</D></PLACES>
<PEOPLE></PEOPLE>
<ORGS></ORGS>
<EXCHANGES></EXCHANGES>
<COMPANIES></COMPANIES>
<UNKNOWN> 
&#5;&#5;&#5;C T
&#22;&#22;&#1;f0704&#31;reute
u f BC-BAHIA-COCOA-REVIEW   02-26 0105</UNKNOWN>
<TEXT>&#2;
<TITLE>BAHIA COCOA REVIEW</TITLE>
<DATELINE>    SALVADOR, Feb 26 - </DATELINE><BODY>Showers continued throughout the week in
the Bahia cocoa zone, alleviating the drought since early


---

### Post by capitalistpiglet on 2009-01-25
The problem is that your not viewing the text using the correct character set. I dont know what the correct charset would be for this. Your best bet is to open it up in a text editor, and keep changing the charset until it looks better.

---

### Post by kjohansen on 2009-01-25
the characters that are causing problems are all of the form "<Ampersand>#<somenumber>;".

If it is a different character set can I set that in the xml minidom?

---

### Post by pp. on 2009-01-25
What character set is noted in the <?XML ..> line?

---

