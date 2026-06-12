---
title: "IP Tracker / Hostname / loggers embedded into HTML code?"
date: 2011-06-29
forum: Programming Talk
---

### Post by honeybear on 2011-06-29
Hello, 

I would be interested to know how to make possible to log the IP address + also the hostname and provider, of the persons that opens the index.html.

Is it possible? PHP works, I tried once with that site. But in this present case it shoudl be embedded into the html code

I would rather use PHP than JAVA. PHP is nice, universal, I know a bit of it, and I guess it is well adapted for that challenge... 

Any help would be welcome

---

### Post by honeybear on 2011-06-29
(1) First issue: OK If I use:

test.php
```
<?php
$ip = $_SERVER['REMOTE_ADDR'];
$pagina = $_SERVER['REQUEST_URI'];
$datum = date("d-m-y / H:i:s");
$invoegen = $datum . " - " . $ip . " - " . $pagina . "<br />";
$fopen = fopen("ips.html", "a");
fwrite($fopen, $invoegen);
fclose($fopen);
?>
```
then it works. but it displays only the IP address.
How to get the hostname + provider internet url? 


(2) Second issue: how to implement those lines into the test.html page? 

test.html
```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html><head>

hello <br>
**[COLOR="Red"]  <------- cannot we put here the content of test.php???[/COLOR]**
</head></html>


```

---

### Post by juancarlospaco on 2011-06-29
> **honeybear said:**
> 
```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html><head>

hello <br>
**[COLOR="Red"]  <------- cannot we put here the content of test.php???[/COLOR]**
</head></html>

```

```
<iframe src="test.php" width="820" height="210" border="0" alt="Hi, im an iFrame"></iframe>
```

This is not the most beautiful method, but always work; besides i dunno PHP.

---

### Post by slavik on 2011-06-29
how about parsing apache http server log?

---

### Post by juancarlospaco on 2011-06-29
I think he want to display that to users directly, and he didnt say that is using apache,
it may work, but CLI parsing sometimes can be slow, depends on the parser tool...   :)

---

### Post by SoFl W on 2011-06-29
Get really clever...

[[IMG]http://www.danasoft.com/sig/Anexample24085.jpg[/IMG]]("http://www.danasoft.com/sig/Anexample24085.jpg")

(These things have been around forever, you can make your own with php)

---

### Post by doas777 on 2011-06-29
well, there are several methods available for getting the hostname. look at [http://php.net/manual/en/function.gethostbyaddr.php](http://php.net/manual/en/function.gethostbyaddr.php) for the php-native way, or if that doesn;t work out, parse the output of dig or nslookup.

isp url is harder. you may have to parse the output of a whois query. this may help:
[http://www.phpwhois.org/](http://www.phpwhois.org/)

---

### Post by slavik on 2011-06-30
> **juancarlospaco said:**
> I think he want to display that to users directly, and he didnt say that is using apache,
it may work, but CLI parsing sometimes can be slow, depends on the parser tool...   :)
like splunk? ;)

or you mean Perl? ;)

In the end though, it depends on what the OP wants to do with that data.

---

### Post by juancarlospaco on 2011-06-30
On Python it is:
```

route('/myip')
def showip():
    ip = request.environ.get('REMOTE_ADDR')
    return % ip

```

---

### Post by honeybear on 2011-07-02
> **doas777 said:**
> well, there are several methods available for getting the hostname. look at [http://php.net/manual/en/function.gethostbyaddr.php](http://php.net/manual/en/function.gethostbyaddr.php) for the php-native way, or if that doesn;t work out, parse the output of dig or nslookup.

isp url is harder. you may have to parse the output of a whois query. this may help:
[http://www.phpwhois.org/](http://www.phpwhois.org/)

yes but php cannot be implemented into the html webpage... for above ... or how would you translate this into PHP, the whole thing + with an IP hostname and provider internet logger? 

```


<HTML>

<HEAD>

<TITLE>WEBSITE </TITLE>

</HEAD>

<FRAMESET COLS="200,*" NORESIZE FRAMEBORDER=0 BORDER=0 FRAMESPACING=0 TOOLBAR=NO>

<FRAMESET border="0" frameborder="0" framespacing="0" rows="0%, 100%">

      <FRAME name="page1" src="page1.html">

      <FRAME name="page2" src="page2.html">

  </FRAMESET>

  
<FRAME border="0" frameborder="0" framespacing="0" name="page" src="page.html">

  <NOFRAMES>

  </NOFRAMES>

</FRAMESET>


</HTML>



```




 
 
> **juancarlospaco said:**
> ```
<iframe src="test.php" width="820" height="210" border="0" alt="Hi, im an iFrame"></iframe>
```

This is not the most beautiful method, but always work; besides i dunno PHP.
Your method works and is completely hidden...? why?

edit: well, acutally, because it does not work. the iframe is not create and the PHP does not run ... :( :(



I am not using apache. it is an ftp/php website provider.

---

### Post by honeybear on 2011-07-02
Another solution is not to change one page to php?

 <?php 
 Echo "<html>";
 Echo "<title>HTML with PHP</title>";
 Echo "<b>My Example</b>";

 //your php code here

 Print "<i>Print works too!</i>"; 
 ?>

---

