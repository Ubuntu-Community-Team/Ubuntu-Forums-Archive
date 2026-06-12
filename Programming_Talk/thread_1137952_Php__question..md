---
title: "Php  question."
date: 2009-04-26
forum: Programming Talk
---

### Post by hockey97 on 2009-04-26
Hi, I got a question about php. 

Is their any way to add fields to existing tables in mysql database?

I want to use php code to add or delete fields in  a table.

I am trying to make a css layout that is customizable.

I am still in the planning stage. 


I need to make a layout editor that can add new things to the layout.

what I mean is that by default they get a default layout without music or videos.

If they want to add music or vidoes to their layout they can do so.

I will add it threw code. How ever I need to edit that users record in the database to add a new field or delete one. 

Is it possible to do such a thing?

---

### Post by slavik on 2009-04-26
you're looking for syntax to "alter table".

---

### Post by ad_267 on 2009-04-26
Yes you can run any MySQL command from PHP. The user you are logged in as just has to have permission to do so.

---

### Post by doorman on 2009-04-26
Although you can execute DDL commands from php, doing so poses some risks you might not be aware of:


[LIST]
[*]**data loss** - when dropping a column, all data contained in that column gets deleted also
[*]**inconsistency problems** - if you drop a column for which there's a foreign key, there are two possible outcomes - all the columns related to it get dropped too (the "cascade" effect), or the column won't be deleted at all
[/LIST]

Those problems can easily leed to system crashes, and turn maintenance into a very hard task.

On the other hand, when those tables hold only the page layout, generating DDL from a certain layout might be a great idea once the layout is completed (i.e. you first create the layout, and afterwards propagate it to the db). However, it still makes maintanance a hard task, since it could leed to system inconsistency - two layouts have different underlying interpretation, which basically means hard time integrating these layouts onto the same page.

---

### Post by s.fox on 2009-04-26
Hi,

I would read [this]("http://www.w3schools.com/PHP/php_mysql_intro.asp") page onwards on w3Schools.  It is about running SQL from PHP.

Hope it proves useful.

-Ash R

---

### Post by hockey97 on 2009-04-26
I know how to use mysql with php. 

I am trying to figure out how to do this task.


What I am trying to figure out is how I should go abouts doing this.


I need to make a layout editor that can add elements to the layout.

Like youtube videos  or music play list and much more.

I know I can generated the html code with php.

I just don't know how I can store this.


I first planned to store the css values  in mysql and have a php script have css code that uses variables where the values are needed.

The problem I face is how can I allow users to add many different elements and have it stored. 

I mean If I only have 5 fields  what if a user wants to add video could I add a field just for that user?

from what I know is that you can't without losing data. 

I knew this but Some people where tellimg me their is a why so I asked here.

If their isn't a way then what can I do to store extra elements people put on their layout?

should I just make a text file for each user signed up and put that data in that file?

---

### Post by Reiger on 2009-04-26
You are creating a WYSIWYG editor that should output a subset of XHMTL (only `safe' code) within the context of your website? In that case, why not create your own XML format using XSLT to transform it to the desired XHTML (with inline CSS if you must, or link href it against an external sheet) ?

'that would be fairly easy: you store the XML as a raw string in the DB, and in the PHP code it is a matter of loading it into a DOMDocument, creating an XSLT Processor instance which is assigned another DOMDocument object as stylesheet ... then let the XSLT processor transform the original XML from the DB in XHTML?

The main benefit is that the XML can be fairly complex without having to worry about the structure of your data base... much. Also XML can be much less verbose because you do not need to incorporate wrapper elements (for the benefit of layout etc.), the wrappers can be automatically generated from the XML using the XSLT.

---

### Post by tturrisi on 2009-04-27
Uou can also use generic fields in a table.  Instead of storing html elements in separate fields, use some fields for the basic layout and then use generic fields for additional stuff, or use separate tables for the extra stuff.

Suggest downloading Wordpress package and study the php scripts it implements with its editor.

---

### Post by hockey97 on 2009-04-27
when I download wordpress. Does it give you the soure code in php?

---

### Post by hockey97 on 2009-04-28
What I need is to allow users to add many videos or music.

This can mean videos from youtube or any website.

So I can't just have a field just for video.

I would need many fields. What I am thinking is I might be able to allow the user to create many rows that are similar but have different video data for each video they add.

Not sure but that's what I was thinking.

---

