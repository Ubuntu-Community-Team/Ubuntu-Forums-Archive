---
title: "function help sanitize our data to be SQL injection safe"
date: 2010-08-02
forum: Programming Talk
---

### Post by astkboy2008 on 2010-08-02
function help sanitize our data to be SQL injection safe
[PHP]_clean($_POST);
_clean($_GET);
_clean($_REQUEST);// and so on..[/PHP]
[the function]("http://www.jooria.com/snippets?snippet=123")

---

### Post by Barrucadu on 2010-08-02
What's wrong with mysql_real_escape_string() or mysqli_real_escape_string()?

---

### Post by ja660k on 2010-08-02
I could look super sweet and list all the items myself...
but take a look at...

[http://www.owasp.org/index.php/SQL_Injection_Prevention_Cheat_Sheet](http://www.owasp.org/index.php/SQL_Injection_Prevention_Cheat_Sheet)

It has some examples using php. but the concepts carry from language to language

have fun
;)

**edit** I would _STAY AWAY_ from using Stored procedures, theyre only plausible use is query that take's up too much processing time.

---

### Post by Hellkeepa on 2010-08-07
HELLo!

**astkboy2008**: That function does little to make a string "safe", but boy can it mangle it.
Besides, there is no blanket operation that can be done to make input safe. It is *completely* dependant upon how you're going to *use* the input. For instance, HTML requires a completely different action than SQL, which again requires something completely different than "printf ()", which again is completely different from pure text.
And now we're only talking about escaping output, not validating input. The latter which is what you *always* should do first, before you do anything else with user-submitted data.

Validating the input means that you verify that the data you're getting is within a expected pattern. If it's not, then it's either an attack on your application, or a user mistake. Neither of which should be allowed to get used further in your code, as it could do serious damage.
Again, validating the input isn't some blanket operation, as it depends upon what data you're expecting (as opposed to where you're sending it). For instance, a name would require some different validation rules than a name. Both of which would be completely from an e-mail address validation rule, which again would be completely different to a rule validating a forum post.

I recommend having a good look at the cheat sheet linked to by **ja660k**, and I would also recommend you to read the following article very carefully: [Security: Input and output in PHP](http://translate.google.no/translate?hl=en&sl=no&u=http://norskwebforum.no/viewtopic.php%3Ff%3D39%26t%3D36681&ei=dRBeTN7OJMeIOOSn7ZQP&sa=X&oi=translate&ct=result&resnum=1&ved=0CB0Q7gEwAA&prev=/search%3Fq%3Doutput%2Bog%2Binput%2Bi%2Bphp%2Bsikkerhet%26hl%3Den%26client%3Dopera%26hs%3D4uv%26rls%3Den-GB%26prmd%3Ddf).
It's translated by google, so there might be some odd grammar and the occasional nonsensical word in there, but it should still be quite understandable.

If not, then it's just to ask. ;-)

Happy readin'!

---

