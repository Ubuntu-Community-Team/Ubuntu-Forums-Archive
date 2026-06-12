---
title: "MySql or Postgres?"
date: 2008-04-28
forum: Programming Talk
---

### Post by fifth on 2008-04-28
I'm replacing an old in-house system in work (originally written years ago in Delphi 1!) and am currently working on the database design.

I'm familiar with MySql so that would really be my first choice. However, I've been trying out Postgres as an alternative and generally find it works well, but occassionaly quirky compared to what I expect.

Whats the general opinion or your personal preferences for db's?

---

### Post by CptPicard on 2008-04-28
Strong preference for PostgreSQL here, but one of the reasons for that really is that I made that choice back in the days when MySQL simply was hopelessly behind on features. Haven't looked back and never considered switching.

PostgreSQL is very full-featured and secure when it comes to transactions and such. The multiversion concurrency is a very powerful, and efficient, concept.

I'm curious, what are these quirks you mention? :)

---

### Post by fifth on 2008-04-28
> **CptPicard said:**
> 
I'm curious, what are these quirks you mention? :)

'Quirks' was probably a bit unfair, its really me not being used to Postgres. I was, and still am slightly, struggling with user setup and permissions. And I've just discovered that selects are case sensitive, which doesn't suit my needs, although I'm reading upon how to do an 'in'sensitive lookup.

---

### Post by LaRoza on 2008-04-28
Use what works. MySQL and PostgreSQL are both fine RDMS.

If you know MySQL already, there would have to be a reason to change wouldn't there?

---

### Post by skeeterbug on 2008-04-28
> **fifth said:**
> 'Quirks' was probably a bit unfair, its really me not being used to Postgres. I was, and still am slightly, struggling with user setup and permissions. And I've just discovered that selects are case sensitive, which doesn't suit my needs, although I'm reading upon how to do an 'in'sensitive lookup.

Are you sure you weren't wrapping it in double quotes?

```
SELECT *
  FROM GrOuPs;
```


```
SELECT *
  FROM groups;
```

Both work and return the same result set.


```
SELECT *
  FROM "GrOuPs";
```

Gives me:

ERROR:  relation "GrOuPs" does not exist

********** Error **********

ERROR: relation "GrOuPs" does not exist
SQL state: 42P01

and finally
```
SELECT *
  FROM "groups";
```

returns the result set.

---

### Post by fifth on 2008-04-29
> **skeeterbug said:**
> Are you sure you weren't wrapping it in double quotes?

```
SELECT *
  FROM "GrOuPs";
```

Gives me:

ERROR:  relation "GrOuPs" does not exist


Sorry, i was being vague again :\ What i meant was when using 'select where ...'. The default string comparison is case sensitive. What I want for my app is the search/filter to ignore the case. I've read up a bit on PostgreSql and am now using the LOWER() function to solve this. For example, here is my filter method (in python code):

```

    def changeFilter(self):
        f = QString('%'+self.filterEdit.text().toLower()+'%')
        self.customerModel.setFilter("LOWER(name) LIKE '%s'" % f)
```

The above setFilter method is equivalent to executing;

```

SELECT * FROM 'customerTable' WHERE LOWER(name) LIKE '%sOmeNaMe%'
```

I originally tried also using the PostgreSql function LCASE() to change the filter string to lower case (without success :( ). So I took the easy road and converted the string to lower case before including it in the sql.

---

### Post by skeeterbug on 2008-04-29
> The key word ILIKE can be used instead of LIKE to make the match case insensitive according to the active locale. This is not in the SQL standard but is a PostgreSQL extension.

From the Postges docs.

```

SELECT id, "name", comments, valid_id, create_time, create_by, change_time, 
       change_by
  FROM groups WHERE "name" ILIKE 'UsErS'

```

Returns the group with the name users.

---

### Post by fifth on 2008-04-29
> **skeeterbug said:**
> From the Postges docs.

```

SELECT id, "name", comments, valid_id, create_time, create_by, change_time, 
       change_by
  FROM groups WHERE "name" ILIKE 'UsErS'

```

Returns the group with the name users.

Thanks Skeet, I had tried ILIKE (from code) but couldn't get it to work, although i just tested a query directly to PostgreSql and it works great :D I'll need to check what string my python code was producing.

---

