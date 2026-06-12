---
title: "curl include problem...PHP"
date: 2008-11-02
forum: Programming Talk
---

### Post by Xavieran on 2008-11-02
I'm trying to use the curl library in a script to work with google's AJAX API, but I get this error when I run it:
```
Warning: include(curl) [function.include]: failed to open stream: No such file or directory in /var/www/gget.php on line 3

Warning: include() [function.include]: Failed opening 'curl' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/gget.php on line 3
```

I've already installed php5-curl (and am using php 5), and have restarted the apache2 web server.

Any ideas?

```
<?php
$url = "http://ajax.googleapis.com/ajax/services/search/web?v=1.0&q=Linux";
include curl;
// sendRequest
// note how referer is set manually
$ch = curl_init($url);
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_REFERER, "http://www.mysite.com/index.html");
$body = curl_exec($ch);
curl_close($ch);

// now, process the JSON string
$json = json_decode($body);
// now have some fun with the results...
echo $json;
?>
```

---

### Post by drubin on 2008-11-02
Firstly you do not need to "include" the curl lib. it is there by deFirstly take a look at the php default. see [this]("http://www.php.net/manual/en/curl.examples.php").

Just know the include statment takes is a string representation of the file you wish to include either relative or absolute path.

If you remove the line include ....; your file will execute but with a json decode issue I have not used the api enough to know what it is supposed to return.

---

