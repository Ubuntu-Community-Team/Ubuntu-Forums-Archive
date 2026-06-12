---
title: "using PHP to get file name from URL"
date: 2008-06-21
forum: Programming Talk
---

### Post by akahige on 2008-06-21
I'm in over my head here, not really knowing PHP, but struggling to figure things out anyway.

I've got a PHP script that parses a file and outputs formated source code. It gets the file like this:
```
$source = file_get_contents(dirname(__FILE__).'/subdir/example.html');
```

What I'd like to do is to make this dynamic so that it will output the source from any page. I can grab the referring page using this--
```
$_SERVER['HTTP_REFERER'];
```
--but since it returns the entire URL, the path isn't found on the server and the whole thing breaks.

I'm thinking that if I can parse the page out of the referring URL (with regex, maybe?) as a variable, then I could use that where the html file is in the first example. Also, the files that will be parsed will not be in a sub directory, so the dirname may be superfluous.

Unfortunately, I've exhausted what little knowledge I have and am now totally lost. Can anybody help?

---

### Post by fahadsadah on 2008-06-22
The following regex will get everything beginning with the first / in a string:
```
[^/]+?(/.+?)
```
You will want to strip the http:// part, otherwise this may confuse the regex.

---

### Post by akahige on 2008-06-22
Thanks for posting.

Tried your regex like so--
```
preg_match('[^/]+?(/.+?)', $host, $matches);
```
--and got this error: "Unknown modifier '+'" I can't see what what's going wrong.

This is the entire code block I'm using:
```
	preg_match('@^(?:http://)?([^/]+)@i', $_SERVER['HTTP_REFERER'], $matches);
	$host = $matches[1];
	preg_match('[^/]+?(/.+?)', $host, $matches);
	$source = file_get_contents( $matches[0] );

```

There's probably a simpler way, since what really needs to happen is that the capture should be everything AFTER the last "/"...

The server is running PHP 4.3.2, and I don't have any control over upgrading that.

---

### Post by LoneWolfJack on 2008-06-22
I'm still not sure what you are trying to do. If you want to parse the filename out of a URL, try something like

```

$url = 'http://www.foo.bar/foofile.php';
$file = substr($url,strrpos($url,'/'),strlen($url));
echo $file;

```


Also, PHP 4 has long reached end of life and you should not be using it - if you can't update it, find a new host.

---

### Post by akahige on 2008-06-22
That did the trick! Had to add a +1 offset so I didn't grab the slash, but it worked great.


In trying to expand the concept of grabbing a URL and doing something with it, I'm confused by something: if I do this--
```
	$url = 'http://google.com.index.html';
	$source = file_get_contents($url);

```
--it works fine. But if I replace the Google page with one on my domain, I get an error.

> Warning:  file_get_contents([http://domain.org/v2/file.html):](http://domain.org/v2/file.html):) failed to open stream: HTTP request failed! HTTP/1.1 404 Not Found
 in /home/webadmin/domain.org/html/v2/source.html on line 5

(Source.html is the file that's fetching the URL.)

Even though the URL is being explicitly defined, PHP is obviously treating it as if it's on the local file system (which it actually is, but I don't want to call it that way). Why would it be different? And is there a workaround?

---

### Post by LoneWolfJack on 2008-06-22
I have four guesses:

- you mistyped the url (duh!)
- your server is configured not to respond to automatic requests
- file_get_contents() is using a broken HTTP-header (use fopen() or cURL)
- you're running into a problem I had a long time ago... I intended to parse sites on my own server... worked fine for all domains except one... even a sysadmin I hired wasn't able to figure out what the problem was


... or you just need to add the "www" stuff to your url. ;)
this would certainly be the case if you can only access your domain through [www.domain.org](www.domain.org) in your browser.

---

### Post by akahige on 2008-06-22
> **LoneWolfJack said:**
> I have four guesses:

- you mistyped the url (duh!)
Nah... Although I definitely check it more than once.  :)


> **LoneWolfJack said:**
> - your server is configured not to respond to automatic requests
That's certainly possible. Could you elaborate on this any? I can look into this if I know what I'm looking for.

> **LoneWolfJack said:**
> - file_get_contents() is using a broken HTTP-header (use fopen() or cURL)
Tried fopen(), but actually got the same error as with file_get_contents()


> **LoneWolfJack said:**
> - you're running into a problem I had a long time ago... I intended to parse sites on my own server... worked fine for all domains except one... even a sysadmin I hired wasn't able to figure out what the problem was
I sure hope it's not that...

---

### Post by LoneWolfJack on 2008-06-22
first, try cURL. it's meant for bypassing the fopen wrappers.

naturally, its slow and it doesn't really care for utf-8 but if this works, you likely have some problem with the fopen wrappers.

```

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,$url);
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_exec($ch);
curl_close($ch);

```

---

### Post by akahige on 2008-06-23
I hate to seem dense, but I couldn't figure out how to make this work with the other code we've been hacking together. Actually, I think I got it working, but it still generated a variant of the "file not found" error.

Think I'm going to have to dig into the server config and see if I can't figure out why this keeps happening. (Hopefully, the answer won't be "because of me". :) )

---

