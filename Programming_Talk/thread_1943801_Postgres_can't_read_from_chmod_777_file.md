---
title: "Postgres can't read from chmod 777 file?"
date: 2012-03-20
forum: Programming Talk
---

### Post by kramer65 on 2012-03-20
Hello,


I want to insert a csv file into a PostgreSQL database. For this I run the following command

```
COPY table_name
FROM '/home/kramer65/Bureaublad/table_data.csv'
WITH DELIMITER ',' CSV HEADER
QUOTE '"'
```

Unfortunately, it says: *ERROR:  could not open file "/home/kramer65/Bureaublad/table_data.csv" for reading: Permission denied*

So I did a "chmod 777 table_data.csv", but to no avail: it results in the same error.

Any idea what I am doing wrong here?

---

### Post by r-senior on 2012-03-20
What about the directories? If the account that postgres is running under can't see inside your home directory, it can't see the file.

---

### Post by kramer65 on 2012-03-20
The folder Bureaublad ("Desktop" in Dutch) has the following rights: drwxr-xr-x

I guess that is not enough, but I don't want to go chmodding my Desktop to 777. So I just copied the file to /tmp and from there it works!

I never did anything with /tmp before. Is this a good solution or is it rather stupid?


[EDIT]
Wait, not so fast. It started, but after about 10 seconds it got into new error: *ERROR:  invalid input syntax for type double precision: "\N"*
This should be put in as NULL, so I added the following to my query: *NULL as E'\\N'*, but that doesn't work. Any idea how I could solve this?

Any idea how I could solve this new error?

---

### Post by r-senior on 2012-03-20
> **kramer65 said:**
> I guess that is not enough, but I don't want to go chmodding my Desktop to 777. I just copied the file to /tmp and from there it works!

I never did anything with /tmp before. Is this a good solution or is it rather stupid?
As a one-off solution, I don't see a problem with /tmp.

If you plan on doing this a lot, group permissions are probably the best solution. I don't have postgres installed but I assume it runs in a postgres group. If you put yourself in the same group, you can use group permissions to share files in a controlled way.

---

### Post by kramer65 on 2012-03-20
> **r-senior said:**
> As a one-off solution, I don't see a problem with /tmp.

If you plan on doing this a lot, group permissions are probably the best solution. I don't have postgres installed but I assume it runs in a postgres group. If you put yourself in the same group, you can use group permissions to share files in a controlled way.

Alright. Since it is a one time thing I will leave it like this. Thanks a lot!

Although I know it is not really related (plus you don't seem to use postgresql), but if you happen to know a solution for my "\N"-errors, I'd be really happy.

If not, thanks a lot anyway! :D

---

### Post by r-senior on 2012-03-20
I don't know about the \N. It would only be a guess - maybe something to do with new lines, e.g. If the file came from Windows or Mac?

[http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline)

---

### Post by SeijiSensei on 2012-03-20
Are you actually wrapping the \N with quotes?  If so, remove them.  Also according to the [documentation]("http://www.postgresql.org/docs/8.3/static/sql-copy.html"):

"The string that represents a null value. The default is \N (backslash-N) in text mode, and a empty value with no quotes in CSV mode. You might prefer an empty string even in text mode for cases where you don't want to distinguish nulls from empty strings."

So if you're using CSV mode, a null is represented by adjacent commas ",,".

As for permissions, remember that the PG server is running as user postgres and has only the permissions of that user.  You can use the \COPY command instead of just COPY if you want to read a file owned by an ordinary user.  COPY works on the server side with the server's permissions; \COPY works on the client side with the client user's permissions.

---

