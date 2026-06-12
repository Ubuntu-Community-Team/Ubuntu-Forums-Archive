---
title: "sqlite db not getting created during python/easygui script"
date: 2011-12-06
forum: Programming Talk
---

### Post by memilanuk on 2011-12-06
Hello all,

I'm working on modifying the EasyGUI script from [here]("http://easygui.sourceforge.net/apps/registration_system/index.html") for my own needs - primarily education and my own amusement ;)

This is what I have so far (using Portable Python 2.7)...

[PHP]
#-------------------------------------------------------------------------------
# Name:        easygui-addressbook.py
# Purpose:     Simple GUI addressbook
#
# Author:      Monte Milanuk
#
# Created:     12/05/2011
#-------------------------------------------------------------------------------
#!/usr/bin/env python

import sqlite3
import pprint
import os
from easygui import *

TITLE = "Address Book"
DATABASE_FILE = "address_book.db"
debugging = "False"
cursor = None      # a global
name_id = None     # a global
sep = "."


#
#  create database & tables
#

def createTables():
    global connection
    cursor = connection.cursor()

    cursor.execute('''CREATE TABLE names (id INTEGER PRIMARY KEY AUTOINCREMENT
    , first_name TEXT
    , mid_init TEXT
    , last_name TEXT
    , street_address TEXT
    , city TEXT
    , state TEXT
    , zip TEXT)''')

    cursor.execute('''INSERT INTO names(first_name, mid_init, last_name, street_address
    , city, state, zip) VALUES("Monte", "E", "Milanuk", "1325 Methow St.", "Wenatchee"
    , "WA", "98801")''')

    connection.commit()
    cursor.close()
    msgbox("Database initialized", TITLE)

def main():
    pass

#-----------------------------------------------------------------------
#          start everything
#-----------------------------------------------------------------------
if __name__ == "__main__":
	print TITLE, "starts"
	if debugging:
		connection = sqlite3.connect(':memory:')
		createTables()
	else:
		if os.path.exists(DATABASE_FILE):
			connection = sqlite3.connect(DATABASE_FILE)
		else:
			connection = sqlite3.connect(DATABASE_FILE)
			createTables()

	cursor = connection.cursor()
	main()
	connection.close()
	print TITLE, "ends"

[/PHP]

Every time I run it, it fires off, prints the line 'Address Book starts.', pops up the message box saying 'Database initialized.' and once I acknowledge that, closes the message box and prints the line 'Address Book ends' and exits.  No error messages of any kind, but its apparently not creating the database file as planned, because its not there in the directory afterwards.  Every time I run it, it goes thru the createTables function again.  I figure it must be something simple, but I'll be danged if I can find it...

TIA,

Monte

---

### Post by Petrolea on 2011-12-06
Edit: Problem solved a second after I posted.

---

### Post by memilanuk on 2011-12-06
Found the problem... 

[PHP]debugging = "False" [/PHP]

should have been

[PHP]debugging = False[/PHP]

which led it down the debugging branch, opening an in-memory sqlite database instead of creating a database file.

Doh!

---

