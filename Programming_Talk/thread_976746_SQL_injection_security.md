---
title: "SQL injection security"
date: 2008-11-09
forum: Programming Talk
---

### Post by tc101 on 2008-11-09
I am working on a legacy ASP system.  There is lots of SQL hard coded in the web pages, but all in client side script so a user could not see it.  The manager wants to move all the hard coded SQL to stored procedures because of the threat of SQL injection security breaches.  I am just starting to read about this and wonder who much of a threat it really is.  

For example, on a web page that just uses a radio button and a drop down list box to generate a table of information on the screen, is there any way a SQL injection could happen?

---

### Post by skeeterbug on 2008-11-09
> **tc101 said:**
> I am working on a legacy ASP system.  There is lots of SQL hard coded in the web pages, but all in client side script so a user could not see it.  The manager wants to move all the hard coded SQL to stored procedures because of the threat of SQL injection security breaches.  I am just starting to read about this and wonder who much of a threat it really is.  

For example, on a web page that just uses a radio button and a drop down list box to generate a table of information on the screen, is there any way a SQL injection could happen?

Yes, the attacker could modify the value of the form and inject his own SQL into it. Use stored procs or parametrize your SQL statements.

---

### Post by tom66 on 2008-11-09
There is a Firefox extension (Tamper Data: [https://addons.mozilla.org/en-US/firefox/addon/966](https://addons.mozilla.org/en-US/firefox/addon/966)) which allows you to modify what is sent to the server, so an option form like this:

[html]
<form action="catview.asp" method="post">
 <p>
  <b>Select category to view: </b>
  <select name="cat_id">
   <option value="1">...</option>
   <!-- ... -->
   <option value="n">...</option>
  </select>
 </p>
 <p>
  <input type="submit" />
 </p>
</form>
[/html]

executing the query:
```

SELECT * FROM items WHERE category_id = '{ID}'

```

could be abused, even though there is a select field, because it can be modified through JavaScript, using the Firefox extension, or any other kind of modification. For example, normal form data might be:

```

cat_id: 1

```

but an attacker could modify it to:

```

cat_id: 1'; DELETE * FROM items, users; #

```

---

