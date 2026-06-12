---
title: "A PHP program"
date: 2009-07-28
forum: Programming Talk
---

### Post by AwesomeTux on 2009-07-28
Hello, I know this isn't quite the place I should be asking this, but I thought with all you smart Ubuntu users, you guys might be able to solve this PHP problem for me :P

So I have a form, that sends data to a PHP file via GET, under the query "q" And the PHP file runs "if(preg_match("/$_REQUEST[q]/i","$searchdata")){"

This script works for me, but if someone enters a '/' or '(' or any thing like that, the script breaks. How would I allow special characters in preg_match when the data is coming from a "$_REQUEST"?

---

### Post by credobyte on 2009-07-28
[htmlspecialchars]("http://us2.php.net/manual/en/function.htmlspecialchars.php") or [htmlentities]("http://us2.php.net/manual/en/function.htmlentities.php") should do the job.

---

### Post by Soxred93 on 2009-07-28
I think that the code you're looking for is this: 

```
if( preg_match( '/'.preg_quote($_REQUEST['q'],'/').'/i',$searchdata ) ) {
```

Hope this helps!

---

### Post by AwesomeTux on 2009-07-28
> **Soxred93 said:**
> I think that the code you're looking for is this: 

```
if( preg_match( '/'.preg_quote($_REQUEST['q'],'/').'/i',$searchdata ) ) {
```

Hope this helps!

That's it! Thanks a lot man.

---

### Post by AwesomeTux on 2009-07-30
[Sorry I messed up]

---

### Post by AwesomeTux on 2009-07-30
Alright, now, I've got another PHP question, no need to make a whole new thread for this, please help.

How can I pull query content from a HTTP_REFERER?

So if the HTTP_REFERER is "http://www.google.com/search?q=ubuntuforums.org"

I wanna pull the ?q=* content into a string or something, and echo it.

Is it possible?

---

### Post by v8YKxgHe on 2009-07-30
You really don't want to be using regex for that, and you should never use $_REQUEST super global.

What you need to use is [http://php.net/stripos](http://php.net/stripos) and check the return value does not equal false (using [not]identical operator), and use the $_GET super global.

Also note that variables do not need to be quoted, i.e $foo is fine, "$foo" is quite pointless under majority of cases.

Edit: for your latest question, [http://php.net/parse_url](http://php.net/parse_url)

---

