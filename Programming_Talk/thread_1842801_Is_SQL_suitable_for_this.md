---
title: "Is SQL suitable for this?"
date: 2011-09-12
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2011-09-12
Hi,

I was searching for a good open source and cross-platform address book program but I didn't find any. There are good programs for Linux but windows-builds don't exist. So for now, I will be using Thunderbird's address book. But I would like something standalone and light.

Anyway, as a hobbyist programmer I am contemplating with the idea of creating my own open source, cross-platform address book program. I figured that the difficult part is the design of the database, or in other words how do I store and manage the data.

A typical address book program has these features:
[LIST=1]
[*]It allows to split your contacts under various categories/groups/tags
[*]It allows to enter various **standard** info about a certain contact, eg address/home phone/cell phone/email etc
[*]It also allows to define custom/user-defined fields
[/LIST]

I thought that this looks like a job for a database to handle, so it would be best to use an SQL database. This is easy if you want to do items 1 and 2. You predefine a certain amount of columns each for every predefined field. But for item 3 you can't know before hand the amount of fields and thus you don't know how many columns you need. So I am stuck.

What do you propose?
Is an SQL database suitable for this program or should I use something else?
Should I use the SQL database differently? eg define multiple tables each for every contact
Generally, please tell me your design ideas.

Some other info: I am pretty good with C++. I will use it and nothing else, so please don't bother telling me to use python or something else. My SQL experience is pretty close to zero. If I go with SQL I will use SQLite since it is the easiest lib to integrate. As far as I know, all other solutions require running an SQL server in the background, which is too much for me.

---

### Post by PaulM1985 on 2011-09-12
You could allow the user to add pre-defined fields to the database.  This shouldn't be much of a big issue to implement since you only need to add a new column to a table.  If this were to be implemented in XML and user-defined fields were to be added then all you would do would be to add some new XML tags for the new field.  Isn't this essentially the same?

I would say that you would want a table from all contacts and then maybe other tables for other stuff.  "define multiple tables each for every contact" doesn't sound like the way I would go with it.

EDIT: I would say SQL is fine for a task like this.

Paul

---

### Post by PaulM1985 on 2011-09-12
After putting on my "user" hat, I don't know if I would like to have a program to store contacts which would install an SQL server on my computer.  I see SQL server as quite heavy weight and if everything that stored a bit of information required an SQL server, how many would end up being installed?  What would happen if you wanted to remove the software and another program happened to have been installed at some point and also uses the SQL server, how do you know whether to uninstall the SQL server.  Have you thought about your own file type or some XML based data storage?

Paul

---

### Post by ofnuts on 2011-09-12
> **PaulM1985 said:**
> After putting on my "user" hat, I don't know if I would like to have a program to store contacts which would install an SQL server on my computer.  I see SQL server as quite heavy weight and if everything that stored a bit of information required an SQL server, how many would end up being installed?  What would happen if you wanted to remove the software and another program happened to have been installed at some point and also uses the SQL server, how do you know whether to uninstall the SQL server.  Have you thought about your own file type or some XML based data storage?

PaulI second the idea that noone is wiling to install a SQL server for a mere contact list, but the code can use SQLite (built-in SQL support libs). 

Another solution is to use RDF, like Firefox and Thunderbird.

---

### Post by SledgeHammer_999 on 2011-09-12
> **PaulM1985 said:**
> After putting on my "user" hat, I don't know if I would like to have a program to store contacts which would install an SQL server on my computer.  I see SQL server as quite heavy weight and if everything that stored a bit of information required an SQL server, how many would end up being installed?  What would happen if you wanted to remove the software and another program happened to have been installed at some point and also uses the SQL server, how do you know whether to uninstall the SQL server.  Have you thought about your own file type or some XML based data storage?

Paul

[quote=SledgeHammer_999]If I go with SQL I will use **SQLite** since it is the easiest lib to integrate. As far as I know, all other solutions require running an SQL server in the background, which is too much for me. [/quote]

[quote=PaulM1985]After putting on my "user" hat, I don't know if I would like to have a program to store contacts which would install an SQL server on my computer. I see SQL server as quite heavy weight and if everything that stored a bit of information required an SQL server, how many would end up being installed? What would happen if you wanted to remove the software and another program happened to have been installed at some point and also uses the SQL server, how do you know whether to uninstall the SQL server. Have you thought about your own file type or some XML based data storage?
[/quote]

This is how I imagine it. I create a table with X columns. The first column would be the "contact name". The others would be some predefined fields. Let's we have 20 contacts that use the predefined fields only. The user wants to add another contact and he also wants to create a custom field. In this case if I create another column in the table(as you suggest), how do I differentiate from the first 20 contacts and this last one? The first 20 contacts don't have this new field/column set and they don't need it. I think this will become quickly a mess if add afterwards more and more columns to the table. I need a way to know for which contact a field/column is.

Another approach I am thinking is this:
1.Create a table with 2 columns.The first stores the contacts' names and the second has a unique id.
2. Use this unique id to create a table with 3 columns. The first column stores the field's name(standard or custom it doesn't matter), the second stores the value and the third stores the type of the value(string,binary, number etc)

Thus I will have a database which will contain (number of contacts + 1) tables. Is this adviced?

---

### Post by karlson on 2011-09-12
> **SledgeHammer_999 said:**
> 
What do you propose?

Unless you are planning to have a complete US phonebook in there I would start with something simple like files with <TAG>:<value> format.  May be XML
> 
Is an SQL database suitable for this program or should I use something else?

Might be an overkill for your purpose.  I'd look at Berkeley DB or SQLite if you really want to use a database for this.
> 
Should I use the SQL database differently? eg define multiple tables each for every contact

If you are really have your mind set on using a Database I suggest looking at database normalization and define tables based on the types of data you are going to store.
> 
Some other info: I am pretty good with C++. I will use it and nothing else, so please don't bother telling me to use python or something else.

Suit yourself....

---

### Post by PaulM1985 on 2011-09-12
If you are using SQLlite then I think this is fine.

Can you give some ideas of custom columns people might want?

You could maybe tell the difference by keeping a list of the columns that you specified, then any additional columns defined by the user would be different to your list of pre-defined columns.  That's how you could tell between them.  Is this what you mean?

You said: "how do I differentiate from the first 20 contacts and this last one?"

If you add a new "custom" column to your table, depending on your implementation, the column can contain a default value, or contain NULL (which is a specified SQL value to indicate that the value is unknown or not necessary).  NULL is a quite common value in SQL and can be used in lots of cases to indicate whether information is mandatory or not.

So say for example your pre-defined list didn't have email address, someone added a new custom field of email-address, all the existing people in the contacts list would have NULL as their email address.  Does this address your problem?

I am not keen on your second solution.  It doesn't really sound like a very usual database approach.

Paul

---

### Post by PaulM1985 on 2011-09-12
> **SledgeHammer_999 said:**
> 
Another approach I am thinking is this:
1.Create a table with 2 columns.The first stores the contacts' names and the second has a unique id.
2. Use this unique id to create a table with 3 columns. The first column stores the field's name(standard or custom it doesn't matter), the second stores the value and the third stores the type of the value(string,binary, number etc)

Thus I will have a database which will contain (number of contacts + 1) tables. Is this adviced?

Some potential drawbacks:
What if someone wants to have a special custom entry for all their contacts?  You would need to create a large amount of tables with the same columns in them.  Would they have to enter the name and data type of the custom field for every contact?

Table names are needed to be distinct in the database.  I imagine table naming would become awkward and clumsy.

How would you look up information relating to people?  Look in every single table until you find them?  I imagine this will have some sort of performance problem.

If you added these custom fields as columns to the appropriate contacts table, you could allow the user to provide some sort of validation information so that they can't input bad data.  This validation would only have to be done on one column in a table instead of multiple columns in multiple tables.

Paul

---

### Post by slavik on 2011-09-12
How about using something that was _made_ to store name/contact information? I am talking about LDAP.

For example, Perl has Mozilla::LDAP::LDIF to allow you to store a local copy of the ldap data (similar to how SQLite works). You can even use the file directly to import to a "real" LDAP server.

---

### Post by trent.josephsen on 2011-09-12
Well, I'm not much at DB design, but couldn't you do this with two or three tables at most?

Contacts have certain predefined attributes (which are part of the entry in the 'contacts' table).  They *may* also have other attributes, as many as you care to associate with them.  So just have a second table called 'attributes' with three fields: key, value, and contact ID (obviously a foreign key to 'contacts').  Every attribute is associated with a contact, every contact can have as many attributes as it needs, and it requires only two tables.

I'd add a third to keep track of attribute types (so you can quickly associate attributes of different contacts with the same type), but that's not necessary.

---

### Post by llanitedave on 2011-09-12
The main problem with allowing user-defined fields is that to get the most value for them you end up expecting the user to become a programmer too.  Is the user going to define business rules for those fields?  Search indexes?  New many to one or many to many relationships?  The more complexity you allow the user to add, the more unwieldy the overall application will become, and it will ultimately become less useful or practical.

If you want users to be database designers, then you'll have to supply some kind of wizard that will not only supply options for new fields, but impose the kind of restrictions that will protect users from themselves.  Otherwise they will ruin the application and blame you.

In this, I am the voice of experience.  I tried creating a user-defined database application, and it worked after a fashion, but the users themselves wanted no part of that complexity, and the most difficult features to provide (those that gave it the most flexibility) were the ones that were most ignored by the users themselves.

Far better to create a basic, generic application which you can then customize as necessary FOR individual clients with specialized needs.  Otherwise the internal costs of user training will far outweigh the costs of the software, and you'll be left with an unmarketable dinosaur.

Invest the time up front to find out exactly what the client's needs are in advance, and then provide them with a tool that efficiently satisfies those needs.  Don't try and create something for everyone in a single app.


All that said, if all you are talking about is the ability to add a few passive information fields,  with no required extra logic or functionality, then trent.josephsen's idea above is a reasonable one.

---

