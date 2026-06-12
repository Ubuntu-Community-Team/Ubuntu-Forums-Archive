---
title: "[SOLVED] Please Check My SQL -Create Table"
date: 2008-12-19
forum: Programming Talk
---

### Post by s.fox on 2008-12-19
Hi,

I find myself in a rather unusual situation where I am writing some SQL to be executed that will hopefully create a table.  Its unusual because I do not directly have access to the database.  Someone else will be running my SQL for me.   The person who is going to run the SQL is in a different time zone to me (Westcoast America) and I won't be able to get in contact with him until much later today.

If someone could could have a quick look at some SQL I have done and point out possible syntax errors it would be very very helpful.    I think I have done it correctly but would value any input.  The database that the SQL is going to be run on is phpMyAdmin. 

```
CREATE TABLE userGroup
(
userGroupID INT(6) NOT NULL,
userID INT(6) NOT NULL,
groupID INT(6 NOT NULL),
PRIMARY KEY (userGroupID),
FOREIGN KEY (userID) REFERENCES user(userID), 
FOREIGN KEY (groupID) REFERENCES group(groupID) 
)
```

Once again thanks for any assistance.

P.S.  If my syntax is correct can someone please say.  

-Ash R

---

### Post by mike_g on 2008-12-19
If you setup mysql on your computer you could test your queries yourself before submitting them ;)

From a breif glance it looks like you have an error on this line:
> groupID INT(6 NOT NULL),

---

### Post by s.fox on 2008-12-19
Whoops.  Thanks for that one.

I found this [site]("http://developer.mimer.com/validator/parser200x/index.tml#parser") which validates SQL.

My SQL now looks like this

```
CREATE TABLE userGroup
(
userGroupID INT(6) NOT NULL,
userID INT(6) NOT NULL,
groupID INT(6) NOT NULL,
PRIMARY KEY (userGroupID),
FOREIGN KEY (userID) REFERENCES user(userID), 
FOREIGN KEY (groupID) REFERENCES group(groupID) 
)
```

That however gives this message:

```


CREATE TABLE userGroup 
( 
userGroupID INT(6) NOT NULL, 
userID INT(6) NOT NULL, 
groupID INT(6) NOT NULL, 
PRIMARY KEY (userGroupID), 
FOREIGN KEY (userID) REFERENCES user(userID),  
                                ^---
syntax error: user
  correction: <identifier>

FOREIGN KEY (groupID) REFERENCES group(groupID)  
                                 ^----
syntax error: group
  correction: <identifier>

)

```

What does that mean?  Is it only throwing that error up because the other tables I referenced don't exist?  

Once again many thanks

---

### Post by mike_g on 2008-12-19
> Is it only throwing that error up because the other tables I referenced don't exist?
Yeah probably.

On a side note, have you considered using a composite key instead?
If the userGroup tables purpose is to map a many to many relationship betweens users and groups, this should work quite well. The basic idea would be to drop your primary key and instead have a primary key made up of a combination of userId and groupId. might be worth googling.

---

### Post by s.fox on 2008-12-19
> **mike_g said:**
> On a side note, have you considered using a composite key instead?

Not a bad idea.   Thanks.  My SQL now looks like this:

```
CREATE TABLE userGroup(
userID INT(6) NOT NULL,
groupID INT(6) NOT NULL,
PRIMARY KEY (userID, groupID)
)
```

Would i be right in thinking that i don't really need to reference the ID's?

Once again thank you

---

### Post by mike_g on 2008-12-19
Yeah, AFAIK, you should not have to reference the ids.

---

### Post by s.fox on 2008-12-19
Thanks for all the help so far.  I think something is wrong with this SQL,  can somebody have a peak for me?

```
CREATE TABLE GROUP (
groupID INT( 6 ) NOT NULL AUTO_INCREMENT ,
groupName TEXT( 255 ) ,
groupCreator INT( 6 ) ,
groupCreateDate DATE,
groupCreateTime TIME,
PRIMARY KEY ( groupID ) ,
FOREIGN KEY ( groupCreator ) REFERENCES USER( userID )
)

```

---

### Post by mike_g on 2008-12-19
> groupName TEXT( 255 )
You dont define the size for a text field, I think you are after :
> groupName VARCHAR( 255 )
VARCHAR lets you specify a variable size, TEXT just allocates a big lump (I forgot how much).

Its also common to store the date and time together. So instead of:
```
groupCreateDate DATE,
groupCreateTime TIME,

```
You could do:
```
groupCreateTime DATETIME,
```
Or store the datetime in an integer field as a Unix Timestamp, but having them as seperate fields would also work.

---

