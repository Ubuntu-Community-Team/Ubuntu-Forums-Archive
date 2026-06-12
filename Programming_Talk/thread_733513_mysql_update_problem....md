---
title: "mysql update problem..."
date: 2008-03-23
forum: Programming Talk
---

### Post by hockey97 on 2008-03-23
HI I am getting a syntax error. is there somthing worng or missing in my code?? here is the code

[php]$c1="UPDATE Images SET on ='1' WHERE file ='$rm1';"; 
//query on top and bottom is mysql command to do the query.
$r1 = $db->query($c1);[/php]

the error says that I have an syntax error by  on ='1' WHERE file ='$rm1';";

I have looked at the mysql website and  it says it  needs to be like this [php] $query="UPDATE table SET colum='1' WHERE username='bob';";[/php]

---

### Post by [h2o] on 2008-03-24
If on is a integer field I am not sure you should have it quoted.

---

### Post by themusicwave on 2008-03-24
I know on postgres you can put quotes around everything and it works.

I haven't used MySQL in a while and it most likely doesn't like the quotes.  

Also, if you are trying to get the value out of $rml should it be something like this

Concatenate the sql string with the value of rml
$c1="UPDATE Images SET on ='1' WHERE file ='".$rm1."';";

I haven't used PHP in a bit, but in most languages putting a variable name in quotes just gives you a string literal. You would literally be getting $rml instead of the value stored in it.

Hope that helps.

---

### Post by hockey97 on 2008-03-24
well I tried what you guys said and I still get a syntax error.

here is what I exactly get as an error:  ```
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'on ='1' WHERE file =/home/linuxuser/WebPages/domainname.com/files/images/12063055' at line 1
```

I looked at the mysql page and still I can't find anything that might be wrong.

---

### Post by CptPicard on 2008-03-24
Well, it seems like from the MySQL error message that the file path string isn't quoted and the 1 is... did you really try removing quotes from the integer and made sure you've got your filename quoted?

---

### Post by wrightee on 2008-03-24
'on' is a mysql keyword - as in 'left join x on..', so it doesn't make sense.  If you have a column called 'on' and you can't change it, try wrapping in backticks `on`

C

---

### Post by hockey97 on 2008-03-24
ya that was the problem thanks for telling me. It works now.

---

