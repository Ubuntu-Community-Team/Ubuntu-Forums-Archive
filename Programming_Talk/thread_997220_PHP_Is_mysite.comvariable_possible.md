---
title: "PHP: Is mysite.com/?variable possible?"
date: 2008-11-29
forum: Programming Talk
---

### Post by secondstage on 2008-11-29
Is it possible, in PHP, to pass a variable through the URL, when said variable isn't assigned a name? So, "word", in this example URL would be passed...
```
http://www.thewebsite.com/?word
```

---

### Post by slavik on 2008-11-29
youcan pass any variable=value in the GET/POST string, it's the PHP code's responsibility to make sense of it all.

---

### Post by drubin on 2008-11-29
> **secondstage said:**
> Is it possible, in PHP, to pass a variable through the URL, when said variable isn't assigned a name? So, "word", in this example URL would be passed...
```
http://www.thewebsite.com/?word
```

Yes 100% possible. 

The code you would do for that is 
isset($_GET['word']);
or take a look at 
[http://www.php.net/manual/en/reserved.variables.server.php](http://www.php.net/manual/en/reserved.variables.server.php) 'QUERY_STRING'

EDIT:
btw this code would be in the index.php as this is the default file if you just specify a path.

---

### Post by secondstage on 2008-11-29
Thanks drubin, I didn't understand at first but now I get it. Is there a way that a user could exploit this? not to have the site print select-four-letter-words (that would be almost too easy), but maybe damage the server?

---

### Post by drubin on 2008-11-29
> **secondstage said:**
> Thanks drubin, I didn't understand at first but now I get it. Is there a way that a user could exploit this? not to have the site print select-four-letter-words (that would be almost too easy), but maybe damage the server?

Pleasure, but still have no idea what you are trying to get at here. Maybe describe what you are wanting to do in a little more detail. 

Every thing *can* be exploited. Take simple webiste that just have static html. You can dos attack them till the server crashes and gives you a nice error page with some server info and you can take it from there.... 

But as for your question about a 4 letter word being an exploit I have no idea what you are doing with this 4 letter word.

---

### Post by jpeddicord on 2008-11-29
Trust nothing. Sanitize database inputs. Then you're safe. :)
(If you're using mysql**i** in PHP5, this is already done for you.)

That variable can be accessed using $_SERVER['QUERY_STRING']. In this case, it would be 'word.'

---

### Post by drubin on 2008-11-29
> **jacobmp92 said:**
> Trust nothing. Sanitize database inputs. Then you're safe. :)
(If you're using mysql**i** in PHP5, this is already done for you.)

That variable can be accessed using $_SERVER['QUERY_STRING']. In this case, it would be 'word.'

Not only DB inputs. You can inject code into post data.  so the php code is executed when the form is generated. same thing goes with javascript.

This is something one has to leart over time/experience. but a good place to start is looking up [code injection]("http://en.wikipedia.org/wiki/Code_injection")

---

### Post by jpeddicord on 2008-11-29
> **drubin said:**
> Not only DB inputs. You can inject code into post data.  so the php code is executed when the form is generated. same thing goes with javascript.

This is something one has to leart over time/experience. but a good place to start is looking up [code injection]("http://en.wikipedia.org/wiki/Code_injection")

Er.. no, that's not really directly possible unless you took the postdata and threw it into an eval() call, which is a sorta dumb thing to do from the start.

---

### Post by drubin on 2008-11-29
> **jacobmp92 said:**
> Er.. no, that's not really directly possible unless you took the postdata and threw it into an eval() call, which is a sorta dumb thing to do from the start.

**drubin uploads an image file with a mime type of text/php and extension .php then hits image location in a browser.

But yes some things seem simple when you know how to provent them but if not it can be a nightmare. 

Also was more talking about javascript injection to get peoples logged in sessions.

---

