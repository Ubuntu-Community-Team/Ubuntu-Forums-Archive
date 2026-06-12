---
title: "Inserting url in MySql 5.0"
date: 2008-05-15
forum: Programming Talk
---

### Post by Sportingfan on 2008-05-15
Hi all,

i'm willing to store url's in my MySql 5.0 database but it causes an internal server error.

Here's a piece of code:
```

$name = ...
$date = ...
$link = trim(addslashes($_POST["link"]));
	
$sql = "INSERT INTO $table (name, date, link) VALUES ('$name', '$date', '$link')";
mysql_query($sql);

```

When $link is empty, there's no error and the values are stored in the db.

Any ideas?

ty

---

### Post by escapee on 2008-05-15
What's your MySQL datatype for the link column?

---

### Post by Sportingfan on 2008-05-16
I'm using a text datatype.
Should it better be varchar or ..?

Ty

---

### Post by Verminox on 2008-05-16
What is the charset your database/table is using? There could be an error if your link contains characters that the database does not support.

Anyway, give it a try with varchar. I guess 500 should be a reasonable size for a URI if it is going to be a normal link (although URIs with a lot of GET queries can get insanely huge).

---

### Post by Sportingfan on 2008-05-16
I outcommented the sql statement and i still get the internal server error. It seems to have a problem sending url's via post.

Any idea?

ty

---

### Post by Sportingfan on 2008-05-19
btw, this is what i found in the error log.

```

mod_security: Access denied with code 500. 
Pattern match "!/imp/login\\.php" at HEADER("Referer") 
[id "300018"] 
[rev "3"] 
[msg "Generic PHP code injection protection via ARGS"] 
[severity "CRITICAL"]

```

ty

---

### Post by Wim Sturkenboom on 2008-05-19
Not sure, but that double backslash looks funny to me. It looks like slashes are already added and you add another one.

```

function doslashes($str)
{
    if(!get_magic_quotes_gpc())
        $str=addslashes($str);

    return $str;
}

```
I first test with *get_magic_quotes_gpc()* to see if quotes are already added and depending on the result process the string with *addslashes()*.

But I might be completely wrong with regards of the cause (I run a Slackware 12 box and have not encountered the problem (yet)).

---

### Post by Sportingfan on 2008-05-19
The error is triggered in the post action. 
It also occurs when i just do:
```

$link = $_POST["link"];

```

If i send an url without "http://" everything works fine.
I'm gonna ask the user for an url withour "http://" untill i found the cause of the error.

Could it be that posting "//" is not allowed by some php setting?

ty

---

### Post by Wim Sturkenboom on 2008-05-20
Found in [http://www.onlamp.com/pub/a/apache/2003/11/26/mod_security.html](http://www.onlamp.com/pub/a/apache/2003/11/26/mod_security.html)
```

    # Should mod_security inspect POST payloads
    SecFilterScanPOST On

    # By default log and deny suspicious requests
    # with HTTP status 500
    SecFilterDefaultAction "deny,log,status:500"

```
Please read the whole article and try to find more info as I'm not sure what the implications are.

Further I think this link is important: [http://www.modsecurity.org/](http://www.modsecurity.org/)

---

