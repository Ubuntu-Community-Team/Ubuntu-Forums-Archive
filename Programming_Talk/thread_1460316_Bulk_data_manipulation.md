---
title: "Bulk data manipulation"
date: 2010-04-22
forum: Programming Talk
---

### Post by J V on 2010-04-22
Would it be possible (Has it already been done) to create a GUI program that would take values and transform them into another format?

Something that could take plugins to handle CSV, SQL, simple text etc, that would be able to bulk transform any data into any data?

If it hasn't been done, what would be needed to make such a device?

Wouldn't it be great? Have you tried importing hotmail contacts into Evolution?

---

### Post by Aped on 2010-04-22
Google yields a number of hits on this. Not sure if any are as all-encompassing as you seem to want but there are a lot of tools out there to do at least some part of this job. 

I think making a mega-converter with a GUI and anything else you want (I assume you'd want to have user-specified formatting and such for certain types of data?) would be a pretty hefty task. 

A few for-instances: 
[http://csv2sql.evandavey.com/](http://csv2sql.evandavey.com/) has a CSV-to-SQL converter but requires specific formatting beforehand. Might defeat the purpose to some extent. 
[http://www.dbf2002.com/csv-converter/](http://www.dbf2002.com/csv-converter/) will convert CSV to a whole host of other formats, but doesn't seem to support multiple-csv-to-one-db, or *-to-CSV conversion. 


Idunno. Good luck, I guess.

---

### Post by J V on 2010-04-22
I was focusing more on similar things like csv to csv (Cause csv formats are often wierd)

It would have to be modular of course, one to handle csv input/output, one to handle sql input/output...

All the main program would be doing is parsing strings, with in them using mainly regex filters or split() functions to handle the conversion, in theory it should be fairly simple...

---

### Post by lisati on 2010-04-22
Unless there's something that I'm missing, I don't think there's a "one size fits all" answer.

It probably wouldn't be too hard to write something where the source format and target format are sufficiently similar, e.g. OFC and OFX, or CSV and TSV.

Where I see a challenge arising is when there are differences in the overall file structure, e.g. converting between OFX and CSV or vice versa.

---

### Post by TheFu on 2010-04-22
I believe these already exists - EDL is what they call it.  It is used to connect different systems together since outputs from "system A" don't feed perfectly into "system B."  The vendors who make this are many, and sadly, I can't think of any besides Mercador [http://www.informationweek.com/780/mercator.htm](http://www.informationweek.com/780/mercator.htm)

These days, I suspect a general translator app would be controlled by XML, but I'd probably just modify an existing perl script to handle each specific case quickly.

Translating non-row-based data becomes more complex, unless the source is XML.

---

### Post by J V on 2010-04-23
Considering you could build-in plugins that allow you to easily select different parts of XML, HTML, text, SQL and put them into the program, by the time they get to the actual "move" part they could be almost the same.

Has anyone here ever used drupal views? Very good system, I was looking to model this something similar.

I could write a python or bash script for every type of data transfer, but a GUI and a way to save transfer types in a config file would help people a lot.

---

