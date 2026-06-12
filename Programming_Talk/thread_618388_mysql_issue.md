---
title: "mysql issue"
date: 2007-11-20
forum: Programming Talk
---

### Post by puccaso on 2007-11-20
> [SIZE=3][FONT=MS Shell Dlg][COLOR=#000000]CREATE TABLE `customer` ( 
  `customer_id` int(8) NOT NULL auto_increment, 
  `username` varchar(20) collate ascii_bin NOT NULL default '', 
  `first_name` varchar(15) collate ascii_bin NOT NULL default '', 
  `last_name` varchar(30) collate ascii_bin NOT NULL default '', 
  `DOB` date NOT NULL default '0000-00-00', 
  `address_line1` varchar(20) collate ascii_bin NOT NULL default '', 
  `adress_line2` v[/COLOR][/FONT][/SIZE]


im trying to get the username table to be authentic, ie
i noticed i would have a problem with username duplication

what do i do to do the table or the db to make it spit and error out if a username is used twice..?

---

### Post by bobrocks on 2007-11-20
[PHP]CREATE TABLE `customer` (
`customer_id` int( NOT NULL auto_increment,
`username` varchar(20) collate ascii_bin NOT NULL default '', 

....
....

PRIMARY KEY  (`customer_id`),
  UNIQUE KEY `username_unique` (`username`)
)[/PHP]

Where you would declare your key constraints at the end mark the column as unique.

---

### Post by puccaso on 2007-11-20
as the mounty in due south says

thank you kindly :)

---

### Post by puccaso on 2007-11-20
mmm
one question

why username_unique tho?

---

### Post by Jawahir on 2007-11-20
'username_unique' is incorrect. Use this instead: UNIQUE KEY `username` (`username`)...

---

### Post by aks44 on 2007-11-20
> **puccaso said:**
> why username_unique tho?
Every index has to be given a name. In this case, bobrocks chose to call the index "username_unique" but it could have been anything.

> **Jawahir said:**
> 'username_unique' is incorrect.
Not even close to incorrect, it is perfectly valid. Try it and you'll see (as I said above, it's only the index name so it hardly matters but for ALTER TABLE statements that modify/delete that index).

---

### Post by bobrocks on 2007-11-20
What aks44 said. 

I just chose the name as it was a unique key on a username column.  No other reason, you can call it what ever you wish.

---

