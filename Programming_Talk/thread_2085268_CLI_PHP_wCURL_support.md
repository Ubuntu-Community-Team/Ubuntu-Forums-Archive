---
title: "CLI PHP w/CURL support?"
date: 2012-11-17
forum: Programming Talk
---

### Post by Dewed on 2012-11-17
I wanted to write a little XML fetcher/parser that I'll launch via cron. on my Ubuntu 12.04 desktop. I wanted to use CLI PHP and curl, since I'm familiar with it and already have scripts running that do similar tasks on webservers I maintain.

I only need PHP support via CLI, I won't be using a browser, so Im thinking I dont need Apache, but it also seems that the PHP5-curl package does not provide curl access to the php-cli package...

Anyone had any luck using curl via a CLI php script? If so, what do I need to do ?:confused:

oh, ps I also prefer curl over the XML & simpleXML function methods since curl can easily navigate the proxy servers I am likely to be dealing with.

Any insights would be greatly apreciated.

---

### Post by greenpeace on 2012-11-19
Hi, 

There's no need to use Apache for a script running from the CLI.

(note... personally, I prefer to use Python for these sort of scripts, as there are so many libraries (eg. BeautifulSoup[1] for XML parsing) to make the tasks easier.)


**1. Curl in PHP needs to be installed before you can use it:**
```
sudo apt-get install php5-curl
```

then you can use it according to the documentation on the php.net manual [2]


**2. Parsing the XML you get from curl:**

Now you have the XML from the curl request, **this** is the point where you need to process it with something like SimpleXML [3]


[1] [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)
[2] [http://www.php.net/manual/en/curl.examples-basic.php](http://www.php.net/manual/en/curl.examples-basic.php)
[3] [http://blog.teamtreehouse.com/how-to-parse-xml-with-php5](http://blog.teamtreehouse.com/how-to-parse-xml-with-php5)

---

### Post by Dewed on 2012-11-19
sadly I dont know python, although I suppose it is time I tear into it.

 And yes I have installed the package you mention, although I think I yanked it and installed php-cli thinking that was the solution. Both gave the same result in that  CLI launched PHP scripts complain of a missing curl function.  I'm away from my system now, but I'll double check shortly.

thanks for you input :)

---

### Post by Dewed on 2012-11-20
Ok, it does appear to work, I get no more errors regarding missing curl function,, although I have yet to actually fetch and parse.

Anyway, in case some one else has similar problems, I have installed

php5  php5-common, php5-curl and php5-cli    all v. 5.3.10

I think maybe the fix was installing the cli package AFTER I already had PHP with curl support installed, because that's the only thing I recall doing differently from my previous attempts..

---

