---
title: "Basic Application Security Question"
date: 2009-08-22
forum: Programming Talk
---

### Post by jstgtpaid on 2009-08-22
I am working on an open source python application for small medical offices.  The application is a client/server application and data is stored in a mysql database.

I would like to help setup basic security.  Currently users need to login using a single username in mysql.  However, one could use the password to connect directly to mysql and bypass the app.

I would like the users to login to mysql, but I want their usernames to be unique to them.  In addition, I don't want the users to be able to modify the application tables without going through the app.

I am considering creating a table in the application database and giving the users select rights to only that table.  The application would use the users signon to log into the database and select the row from the application table to retrieve the application password.  The application would use that password to log back into mysql.

The password would be encrypted in the database, but it would be decrypted by the app and used to log back into mysql.

Does this appear to be a prudent way to handle my security concerns?  Is there a better way to do this?

Thanks in advance,
Steven

---

