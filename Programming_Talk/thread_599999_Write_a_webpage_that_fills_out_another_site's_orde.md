---
title: "Write a webpage that fills out another site's order form...?"
date: 2007-11-01
forum: Programming Talk
---

### Post by cacycleworks on 2007-11-01
Hi Everyone,

I'm wanting to automate things in my business and I'd love to be able to make a php page that can load a vendor's URL in the bottom half/frame and then read the form and pre-fill it with info my script read from my mysql database.

I'm pretty good at programming, but researching this really has me stumped -- I don't even know the terms to use to search. :(  I know a few steps, but having more of a recipe would be awesome...

something like...
use port(url) to open the stream
use frame->target to display in frame
...
from that I can google the functions and sort out the specifics.

Yeah, I know ... if a vendor changes their form, my page will break. :) And one of them has a "calculate shipping" button I have to press as part of the process. :P

Thanks!!
Chris

---

### Post by cacycleworks on 2007-11-01
Oh, I meant to also say that I'd have the form pre-filled then we'd look at the info on the top and bottom for accuracy before hitting the submit button. I'm cool if we have to click the "calculate shipping" applet for their DHL tool, too.

Oh part 2, how to handle logging in. 

*thinks: will google the logging in thing more after dinner*

---

### Post by nanotube on 2007-11-02
don't know much about php, 
but if you don't figure out how to do it with php, you could consider using python and the "mechanize" module  [http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

---

### Post by gradedcheese on 2007-11-02
If you know what fields their form contains, just send it an HTTP POST request directly.  There's no need to automate the filling out of the form itself, you can just make the requests you need.  If you don't know enough about HTTP and POST, read the spec (or something similar) for a bit and it should make sense.

This, by the way, is usually what spammers do to automatically post SPAM in comments, sign up for PHPBB accounts, etc ;)

---

### Post by ThinkBuntu on 2007-11-02
Form fields are defined by value="". The only way to affect this value would be if you could load a script (JS most likely, but PHP also can do it) which of course you can't do.

---

### Post by cacycleworks on 2007-11-02
> **ThinkBuntu said:**
> Form fields are defined by value="". The only way to affect this value would be if you could load a script (JS most likely, but PHP also can do it) which of course you can't do.

Did you mean I can't load a script on the target website (which is a duh) or sarcasm that I don't have access to the LAMP server at work (or that I can't write php) ?  :)  ;)  

I guess another way to put it is that I'd like to have my script be an interpreter for the target website. Kind of like web QA tools, etc. But it's that I have no clue where to start looking for it and was hoping to get a jump start. :)

---

### Post by cacycleworks on 2007-11-02
OK, some more googling and I learn this is scraping, like the action of to scrape...

here's some urls and methodologies:
// Scraping /////////////////////////
== php+curl =========================
[http://www.php.net/manual/en/function.curl-getinfo.php](http://www.php.net/manual/en/function.curl-getinfo.php)
[http://curl.haxx.se/libcurl/php/examples/](http://curl.haxx.se/libcurl/php/examples/)

Howto:
[http://www.bluehatseo.com/guest-post-scraping-links-with-php/](http://www.bluehatseo.com/guest-post-scraping-links-with-php/)


== PHP no-curl ======================
[http://www.webmasterworld.com/forum88/5488.htm](http://www.webmasterworld.com/forum88/5488.htm)
 If you simply want to grab html page and save it in database for later usage then it's really easy.

you can use [http://www.php.net/manual/en/function.file-get-contents.php](http://www.php.net/manual/en/function.file-get-contents.php) then all u need is one insert query and you're set
>>
You can use a URL as a filename with this function if the fopen wrappers have been enabled. See fopen() for more details on how to specify the filename and Appendix O, List of Supported Protocols/Wrappers for a list of supported URL protocols.

-- WGET -----------------------------
Whoadang, example with wget!  [http://forums.worsethanfailure.com/forums/post/120208.aspx](http://forums.worsethanfailure.com/forums/post/120208.aspx)
$content = shell_exec("/usr/local/bin/wget --no-check-certificate -O - --save-cookies cookies.txt --keep-session-cookies --post-data='login_username=XXXX&login_password=XXXX&action=login' [https://XXXXXX/cacti/index.php](https://XXXXXX/cacti/index.php) >/dev/null 2>&1;/usr/local/bin/wget --no-check-certificate -O - --load-cookies cookies.txt '".$url."'");

-- PHP Scraper ----------------------
[http://www.phpclasses.org/browse/package/1754.html](http://www.phpclasses.org/browse/package/1754.html)
PHP Scraper  Support forum
Base name: 	phpscraper
Description: 	Extract structured data from remote HTML pages



== RUBY =============================
ruby? [http://agora.scrubyt.org/forums/4/topics/66](http://agora.scrubyt.org/forums/4/topics/66)
has a WWW::Mechanize class...
 display output on web page
gdw 5 posts : What’s the best way to display the scrapped info on a web page? I’ve been using rhtml files. Scrubyt puts out xml, so I’ve just been combining those with xsl to add formatting. What would be the recommended way though?
scrubber 346 posts : xml + xslt is a great combo if you are into that sort of stuff.

Otherwsie, check out the to_hash function (i.e. instead of writing something.to_xml, use something.to_hash) and then you can use the results in the same way as you would use the params hash in rails…


== PEAR =============================
[http://pear.php.net/manual/en/package.http.http-request.php](http://pear.php.net/manual/en/package.http.http-request.php)
HTTP_Request

Table of Contents
Introduction --  Introduction to HTTP_Request
Basic Authentication --  Authentication for protected websites
Cookies --  Making use of Cookies within HTTP_Request.
File uploads --  Uploading files via HTTP
Request headers --  Adding additional headers to the HTTP request.
Proxy Authorization --  Making use of a HTTP proxy
Response Evaluation --  Evaluating the information from a HTTP response
HTTP_Request_Listener --  attaching listeners to HTTP_Request operations

The package provides an easy way to perform HTTP requests. It supports GET/POST/HEAD/TRACE/PUT/DELETE, Basic authentication, Proxy, Proxy Authentication, SSL, file uploads etc. 


== PYTHON ===========================
[http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)


Here's some working code I came up with:

[PHP]
<html><head><title>Fill out $vendor_name data</title></head>
<body>


<?
$url="http://vendor_names_url.com";
$content=file_get_contents($url);
?><pre><?
echo htmlentities($content);
?>

------------------------------------------------------------

<?
$vendor_name=Array( "username\" value=\"\"" => "username\" value=\"my_user\"", 
					"password\" value=\"\"" => "password\" value=\"my_pass\"",
					"action=\"" => "action=\"$url",
					"href=\"" =>  "href=\"$url"
					 );

foreach( $vendor_name as $key => $value ) {	
	$content=str_replace( $key, $value, $content);
}
echo htmlentities($content);
?></pre><hr><?

unset($vendor_name);
$vendor_name=explode("form", $content);

// ASSumes only one form at a time here...
echo "<br><br>Login form:<br><form".$vendor_name[1]."form>";


?></body></html>
[/PHP]

It's getting there... ultimately, I'd like to have the order info on the left pane and the login info on the right, refilled out, and we just click the buttons...

next to figure out is how to split up the page and have a form on one side and it can spew the resulting html to the other side via my $content variable.

Seriously -- any help appreciated. I'm not a paid developer... I'm doing this in my "spare time" while trying to run my biz. :D

---

### Post by smartbei on 2007-11-02
Look up html frames for showing their page on one side and your form on the other. Though they are terrible design practice (very nearly always) in your case they coule be ok.

---

