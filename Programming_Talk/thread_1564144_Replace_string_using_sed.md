---
title: "Replace string using sed"
date: 2010-08-30
forum: Programming Talk
---

### Post by al_mic on 2010-08-30
Hi,

Do you know how to replace a string using sed, if the string I want to write contains special characters, like ' ?

$ cat test_file 
define('DNS', '1.2.3.4');

$ sed 's/define('DNS', '1.2.3.4');/define('DNS', '5.6.7.8');/' test_file

I tried escaping some characters, but I don't know how and some times a get a hanging prompt:
> 
and some times an error like:
bash: syntax error near unexpected token `)'

Thanks

---

### Post by geirha on 2010-08-30
in single quotes, all characters are treated literally, even \, so you can't have single quotes inside single quotes. You have two options there. End the single quote, add a literal single quote (\'), start a single quote again:

```
$ echo 'foo'\''bar'
foo'bar

```

The other option, is to use double quotes.
```
$ echo "foo'bar"
foo'bar

```
but then you'll need to make sure to escape certian characters. In your case, there are none, so that's the best option in this case.
```

sed "s/define('DNS', '1.2.3.4');/define('DNS', '5.6.7.8');/" test_file

```

[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://wiki.bash-hackers.org/syntax/words](http://wiki.bash-hackers.org/syntax/words)
[http://wiki.bash-hackers.org/syntax/quoting](http://wiki.bash-hackers.org/syntax/quoting)

---

### Post by ghostdog74 on 2010-08-30
```

sed '/define('\''DNS/s@,.*$@,5.6.7.8)@' file

```

---

### Post by al_mic on 2010-08-30
Hey, thank you both!
It worked.

Didn't know I can use " instead of ' in this case :) that was cool to find out.

Second reply ghostdog74 one, is nice too. 

In the end I tried this:

$ sed "s/define('DNS', '.*');/define('DNS', '5.6.7.8');/" test_file


Thank you! :)

---

