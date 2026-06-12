---
title: "PHP Question - Posting To PostgreSQL, Reading It Back"
date: 2007-02-13
forum: Programming Talk
---

### Post by SuperMike on 2007-02-13
Gaah! I'm ripping my hair out on this one. Here's my problem. I want to post text field data from these HTML TEXTAREA tags to a PostgreSQL database and have it reappear back on another page exactly as I had typed it. Over the years I have done this but only did it with simple text. This time around, I want to handle much more complex text. I need to preserve some kinds of features.

(Yes, I have turned off magic quotes.)

- Need to strip diacritics. I learned I could use htmlentities to catch &?grave;, &?acute;, &?circ; &?uml; &?tilde; &?cedil; and the ? can become the character I wish to preserve and strip the others.

- Need all text to be saved in US-ASCII format.

- Need to save all \r and \n as literally that in the database so that SQL selects show everything on one line. This makes it easier to deal with the records with the psql command.

- Need to preserve all US-ASCII characters so that things, such as ', ", \, <, >, %, &, and --, are preserved. I want the database to be able to store these items and not munge them on me reading them back out. For instance, if someone types in HTML, PHP source, or SQL language code into a text field, I want the database to store it and let me retrieve it without munging it.

- I fear storing the data as htmlentity, hexadecimal, or octal because it adds huge width to the text column in the database. So, storing it in some other format like slash-delimited would be best.

Basically I have a $web object with a Request('fieldname') method and I need this function to handle the above for me on reading field data so that it's ready to post to the database. I then have another $strings object with a PrepareTextArea($s) method that helps me translate this database data back into text prepared for either ordinary HTML display or to put back into the TEXTAREA gadget on the page.

Any advice would be greatly appreciated.

---

