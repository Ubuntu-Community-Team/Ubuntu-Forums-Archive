---
title: "Can anyone explain this SQL statement to me please?"
date: 2008-05-21
forum: Programming Talk
---

### Post by lefen on 2008-05-21
Hay all,

So I came across this post on Slashdot:

[http://developers.slashdot.org/comments.pl?sid=559156&cid=23485324](http://developers.slashdot.org/comments.pl?sid=559156&cid=23485324)

In it, the poster is giving an example of an insert statement into an SQLite database, which I have quoted below, along with his assessment of it:

```
set first "Spooky"
set last "Monster"
set email "spook@spammity.spam"
# In practice it's really easy to put values into variables
mydb eval {insert into contacts values (:first,:last,:email)}

The advantage? That code is now totally armour-plated against SQL injection attacks as well as being fast. Which is nice, really really nice.
```

So my question is, (1)what is it about the query that makes it resistant to SQL injection? and (2)could I use a similar query for the MYSQL db on my website, as an alternative to all the PHP I currently have in place to sanitise user input?

Many thanks :>

---

### Post by deuce868 on 2008-05-21
He's using a perl(?) db layer that takes care of escaping. It's basically the equivalent of PDO in PHP land. 

He's setup a prepared statement which takes care of sql injection attempts by auto escaping fields in a lower level. 

Check out this link:
[http://us.php.net/manual/en/pdo.prepared-statements.php](http://us.php.net/manual/en/pdo.prepared-statements.php)

---

### Post by lefen on 2008-05-21
Great stuff, thanks very much :>

---

### Post by stevescripts on 2008-05-21
> **lefen said:**
> Hay all,
...
So my question is, (1)what is it about the query that makes it resistant to SQL injection? and (2)could I use a similar query for the MYSQL db on my website, as an alternative to all the PHP I currently have in place to sanitise user input?

Many thanks :>

I thought folks might be ... interested ... in what makes SQLite resistant to
SQL injection, so, I went to the source ... ;)  The short answer, is, when properly used it is resistant to injection by design.


An extract of a chat between D. Richard Hipp (SQLite author) (drh below), and yours truly ...

```

steveo	drh - one more quick Q?
steveo	am I on firm ground telling folks that the tcl/C bindings to SQLite ***may*** be safer than the Python ones?

drh	Depends on how tall you are looking to build, I suppose....

steveo	re sqlinjection, in particular

drh	The use of "?" prevents SQL injection attacks,  but it is subject to counting errors (miscounting the number of ?s and binding the wrong values)
drh	But if python uses %s then it is subject to SQL injection.

steveo	TY!

drh	On the other hand, so is TCL if you use [db eval "INSERT... $value"] instead of [db eval {INSERT ...$value}]

   * steveo nods

drh	The primary advantage of the TCL interface is that the variable name is embedded in the SQL statement so that you don't have count ?s and match them up with arguments.

   * steveo would love to have this documented for public consumption
   * drh suggests that steveo write it down - perhaps in the SQLite wiki

drh	Which is safer...

drh	A:  db eval {INSERT INTO x VALUE(?,?,?,?,?)} $one $two $three $four
drh	B: db eval {INSERT INTO x VALUES($one,$two,$three,$four)}
drh	Now ask the question again assuming that the SQL text spans 20 lines and so an average of 10 lines of code separate each ? from its corresponding value?

   * steveo would never have even thought of using A ...

steveo	drh, TY again
   * steveo must pay attention to the paywork

drh	you're welcome

steveo	 - I couldnt get by w/out SQLite, FWIW

drh	Glad you find it useful!

steveo	extremely

```

So, the moral of this little story, is don't use %s bindings from Python.

I am basically clueless with regard to the question about MySQL...

Steve
(who always tries to have one eye focused on security...)

---

### Post by pacofvf on 2008-05-21
also i like a combination of java-script pre-preparation(there are tons of scripts  out there to do this task), followed with a php,perl,etc preparation like html_entities()

---

### Post by stevescripts on 2008-05-21
While I also do (and like) javascript pre-preparation, a caveat - don't rely on the javascript alone ... too many people have js turned off.  Ensure, that you use other tools to double-check.

Steve

---

### Post by deuce868 on 2008-05-21
> **stevescripts said:**
> While I also do (and like) javascript pre-preparation, a caveat - don't rely on the javascript alone ... too many people have js turned off.  Ensure, that you use other tools to double-check.

Steve

What? You mean not everyone alters the JS in firebug before submitting? :)

Why turn it off when you can *tweak* it

---

### Post by pmasiar on 2008-05-21
> **stevescripts said:**
> I thought folks might be ... interested ... in what makes SQLite resistant to SQL injection, 

... (shold have beent quoted and nod coded BTW :-)

So, the moral of this little story, is don't use %s bindings from Python.

I am basically clueless with regard to the question about MySQL...

Yup, you still seems not to get it. :-)

Preparing statement as above and then using parameter binding makes sure that original statement is executed, instead of injecting some string as parameter which ends original statement with syntactically correct string, and executing additional SQL command doing something malicious. Because in prepared statement, valid parameter is only string literal or number, while if you execute whole string without checking for content, malicious code can sneak in.

Perl has this useful facility to taint variables from user input, and you have to have check then to untaint them to be able to use them in any command interacting with the environment (os, DB).

So %s binding in Python can be right or wrong, depend how you untaint the variable which you want to substitute. Any string substitution, used wrongly, could subvert the statement you wanted to execute. Brute force is not substitute for agility, and vice versa :-)
 
And if you believe that you can trust any validation done clientside by JS, I have a bridge in good shape to sell you - excellent deal :-)

---

### Post by stevescripts on 2008-05-21
Of course you cant rely on js validation, that was one of my points ...

Yes, I am aware of PERL's taint, etc.  Also note, that tcl improperly quoted is
subject to SQL injection. (as noted by drh in the chat I quoted).


Steve
(who has years to go to grok Python at the level that I do tcl ... ;) , but is having
fun learning a bit)

---

