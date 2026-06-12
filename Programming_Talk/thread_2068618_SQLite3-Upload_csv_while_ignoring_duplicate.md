---
title: "SQLite3-Upload csv while ignoring duplicate"
date: 2012-10-09
forum: Programming Talk
---

### Post by zhogan85 on 2012-10-09
Using SQLite, if I have a table with two columns, one being the primary key, is there a way to upload a csv file to the table that would upload only data with a unique key?

I'm working on a problem at work, and am trying to decide whether to use MySQL or SQLite, and I think SQLite is the better solution if I can get this one part to work. I have no problem doing this in MySQL, I just can't figure out how in SQLite.

Thanks in advance!

---

### Post by bouncingwilf on 2012-10-09
Firstly, I assume you mean a table with two columns (not rows). If this is the case you can easily check if you are trying to add a duplicate entry to table with a unique primary key - the following is a small chunk of code from a gtk prog. of mine that checks for exactly this 


        g_snprintf(SqlStr,200,"INSERT into timestamps(timestamps) VALUES(%s);",DateStr);
        rc= sqlite3_exec(db,SqlStr,NULL,0,&zErrMsg);
            if(rc!=SQLITE_OK)
            {
                if(rc==19)    // Trying to add data already stored (duplicates)
                {
                msg_box("File Import","Data already stored in db!\nDuplicate records! ",2);
                sqlite3_free(zErrMsg);
                gtk_widget_destroy (dialog);
                free(filename);
                return;


Sorry , I've forgotten how to use code tags again! but you can see that the key is to check for error code 19 returned by Sqlite if you try to add a duplicate entry.

Bouncingwilf

---

### Post by zhogan85 on 2012-10-09
> **bouncingwilf said:**
> Firstly, I assume you mean a table with two columns (not rows).

Sorry, typo on my part.

But regarding the chunk of code you included, I can see that that is error code 19, but I'm not really clear what to do with that info. 

Sorry, I'm a bit of a SQL newb.

PS, to include code do the following, but with square brackets rather than curly brackets,
{CODE}example code{/CODE}

---

### Post by bouncingwilf on 2012-10-09
Well, I'm not sure what you want to do in the case of duplicate data ?

a) data's duplicate so discard and process next record ( i.e.return)
 or
b) update the other column in the record you are processing and change the value while leaving the unique key.
I really can't see what other options you have with that setup


Bouncingwilf

---

### Post by zhogan85 on 2012-10-09
> **bouncingwilf said:**
> Well, I'm not sure what you want to do in the case of duplicate data ?

a) data's duplicate so discard and process next record ( i.e.return)
 or
b) update the other column in the record you are processing and change the value while leaving the unique key.
I really can't see what other options you have with that setup


Bouncingwilf

Either of those options are fine, I'm just not sure how to do either of those things.

---

### Post by bouncingwilf on 2012-10-09
Well I'm not sure what language you are coding in but the methodology I would use in these circumstances is as follows:

1. open the Sqlite database 
2. open the csv file for reading
3. parse the csv file into the variables you wish to upload
4 write these variables into an SQL string and then execute the INSERT INTO sql statement 
rc= sqlite3_exec(db,SqlStr,NULL,0,&zErrMsg);
5 test the return code (rc) for SUCCESS or FAILURE
6 if FAILURE test error code for reason
     7. if Duplicate entry code (19) either skip back to the parsing loop and (try to) add next csv value
     else execute alternative sql statement (sql UPDATE statement rather than INSERT INTO        statement)
8 Deal with alternative cause of FAILURE
9 loop

Bouncingwilf

---

