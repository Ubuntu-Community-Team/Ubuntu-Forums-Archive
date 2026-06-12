---
title: "mysql mystery call"
date: 2013-01-07
forum: Programming Talk
---

### Post by Anstice on 2013-01-07
Hi guys, the following code makes a call to a ```
preg_replace
``` function that I cant seem to find on the db.

```

CREATE DEFINER=`root`@`localhost` FUNCTION `makehash`(description text, raw_location text, title text) RETURNS varchar(32) CHARSET utf8
    NO SQL
    DETERMINISTIC
begin
    declare data longtext;
    declare hash varchar(32);
    set data = ifnull(description, '');
    set hash = null;
    if length(data) > 64 then
        set data = lower(concat(data, ifnull(raw_location, ''), ifnull(title, '')));
        set hash = md5(preg_replace('/[^a-z]/', '', data));
    end if;
return hash;
end 

```

Basically, I have two dbs and am moving from one to the other. I almost there apart from this last thing prevents things from running.

I have run ```
show procedure status
``` and ```
show function status
``` but can't see this anywhere. 

Are there another mysql constructs like functions and procedures that can be called like this that I may have missed?

---

### Post by Some Penguin on 2013-01-07
Regular expression handling.  Not a MySQL guru, but that line will set 'hash' to be the MD5 checksum of a modified version of 'data' where everything -except- lower-case letters (*) has been removed.


(*) specifically, a-z; I suspect that something like é would be removed because it is not within that set.  Encoding issues, oh joy!

---

### Post by Anstice on 2013-01-07
Thanks for the reply. I am aware of what the function is trying to but I cant find it in the table I copied the other function from even though everything runs fine on it.

---

### Post by Some Penguin on 2013-01-07
Turns out its a PHP function.

[http://php.net/manual/en/function.preg-replace.php]("http://php.net/manual/en/function.preg-replace.php")

---

