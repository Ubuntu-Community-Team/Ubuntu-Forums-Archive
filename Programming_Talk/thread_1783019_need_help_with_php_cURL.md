---
title: "need help with php cURL"
date: 2011-06-15
forum: Programming Talk
---

### Post by zobayer1 on 2011-06-15
I am trying to write a script which will help me to log into some site (using my account information) and fetch some other private pages, so that I can perform automated operation on those.
For example, [www.mysite.com]("http://www.mysite.com") be a site where, user must be logged in to view, [www.mysite.com/home.php]("http://www.mysite.com/home.php") (these are not real)
I want to read home.php file (obviously the html output).

Now I have searched on the net and found that I could use php cURL library with cookiejar. Can anyone lead me to some good example or tutorial about this?

Thanks in advance.

---

### Post by BkkBonanza on 2011-06-15
The info on the [PHP manual]("http://th.php.net/manual/en/curl.examples-basic.php") site is enough to figure out how this can be used. See the comments at page bottom too as much useful stuff is there.

curl can also be used from other languages or a shell script if you don't want to use PHP.

---

### Post by zobayer1 on 2011-06-15
> **BkkBonanza said:**
> The info on the [PHP manual]("http://th.php.net/manual/en/curl.examples-basic.php") site is enough to figure out how this can be used. See the comments at page bottom too as much useful stuff is there.

curl can also be used from other languages or a shell script if you don't want to use PHP.

Thanks, actually I wanted to use php, and I have tried something. Having a problem, and cannot find how to solve it..

Say, I am hitting a page [www.somesite.com/login.php](www.somesite.com/login.php) and sending post data for login, then the site is returning some page [www.somesite.com/success.php](www.somesite.com/success.php) but as I am testing from my apache localhost, I am having problem that, there is no such page localhost/success.php ?

Can you tell me how to bypass this site? As this page is coming, I already know login succeeded..

Please tell me if you can't understand what I am saying, so that I can describe more.

---

### Post by BkkBonanza on 2011-06-15
I'm not sure what you mean there. I would assume you capture the returned page content and interpret from that what to do next. Maybe listing a code fragment would better show what you are doing or intend to do. Presumably you can just ignore the success.php page, and move on to the page you want now that the cookiejar should be updated and allow correct access.

---

### Post by zobayer1 on 2011-06-15
> **BkkBonanza said:**
> I'm not sure what you mean there. I would assume you capture the returned page content and interpret from that what to do next. Maybe listing a code fragment would better show what you are doing or intend to do. Presumably you can just ignore the success.php page, and move on to the page you want now that the cookiejar should be updated and allow correct access.

Ok, here is the code fragment I am dealing with..
[PHP]
<?php
    extract($_POST);
    
    $data = array(
        'myuserid' => $username,
        'mypassword' => $password
    );

    $cookie_fname = md5($username . $password . rand(0, 2147483647));
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_COOKIEJAR, 'cookie/' . $cookie_fname);
    curl_setopt($ch, CURLOPT_URL,"http://180.211.224.73/lightoj/login_check.php");
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
    ob_start();
    curl_exec($ch);
    $info = curl_getinfo($ch);
    ob_end_clean();
    curl_close($ch);
    exit();
?>
[/PHP]

First, I forgot to use ob_start() and ob_end_clean() to prevent output.
That's why it was causing problem, and If I try to get output from curl_exec() it causes the same trouble again, should I omit RETURNTRANSFER ?

Ow, btw, I will describe the problem again. When I feed data to the above script, it is supposed to hit the url u can see here, and I know that, on success, the server returns login_success.php page. Well, that is not the problem, problem is, then I get 404 Not Found, because, in the address bar, I get that, I am trying to open localhost/mydir/login_success.php which is not in my server... 

After I used ob_start to prevent output, it is not doing such thing, but how can I be sure that it worked properly? just try to read my target page next?

---

### Post by zobayer1 on 2011-06-15
Actually it is not working :(

After I post login information, I try to access index.php page, but in the return, I get a html page in the last line having:
> 
[HTML]<b>Notice</b>:  Undefined index:  myuserid in <b>/var/www/html/lightoj/includes/top_menu.php</b> on line <b>2</b><br /> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1[/HTML]


Need help...

---

### Post by BkkBonanza on 2011-06-15
It sounds like you're trying to access index.php in your browser after login using curl. Maybe that's not what you meant. But if so, understand once you login with curl the session id will be in the cookiejar and only usable by curl. That is completely different from your browser accessing, which has it's own cookie.

You would need to make multiple curl_exec calls, once to get each page and each time make sure the same cookiejar is provided so curl knows it's state. curl is behvaing like a bowser here and as such needs to maintain it's cookie just as a browser would.

I had a look at some curl php code I wrote and have used for years without problem and it doesn't use the ob_start/ob_end_clean method because I use a call like,

$body = curl_exec($ch);

to capture the returned page content, (option RETURN_TRANSFER causes the return of exec to be the returned page content).

You will need to script each page you want to hit in step by step order. Ideally you may want to provide a string with one page url per line and have the script loop thru for each line calling curl_exec and then parsing any return page data if need be. You can use regex to grab content - that works, but in theory the best way is to use an html parser to correctly grab the data (if you need to).

I once wrote a web site test harness that did that to script a large list of page hits and verifying returned content.

---

### Post by zobayer1 on 2011-06-15
Thanks for replying. Obviously I was not trying from browser, I forgot to update the code.

I was trying to use the cookie file I am saving, but not sure what is the problem.

If I first login, get cookie, then close curl connection, and again init it with the cookie file, it is not working, but if I am not closing it, and call curl for fetching some consecutive pages on the fly, they work fine.

Can you tell me why?

This code doesn't work:
[PHP]    $cookie_fname = md5($username . $password . rand(0, 2147483647));
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_COOKIEJAR, 'cookie/' . $cookie_fname);
    curl_setopt($ch, CURLOPT_URL,"http://180.211.224.73/lightoj/login_check.php");
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
    $output = curl_exec($ch);
    $info = curl_getinfo($ch);
    curl_close($ch);

    unset($ch);

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_COOKIEFILE, 'cookie/' . $cookie_fname);
    curl_setopt($ch, CURLOPT_URL, 'http://180.211.224.73/lightoj/index.php');

    $buf2 = curl_exec($ch);

    curl_close($ch);[/PHP]

But this code works fine:
[php]
    $cookie_fname = md5($username . $password . rand(0, 2147483647));
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_COOKIEJAR, 'cookie/' . $cookie_fname);
    curl_setopt($ch, CURLOPT_URL,"http://180.211.224.73/lightoj/login_check.php");
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);

    $output = curl_exec($ch);
    $info = curl_getinfo($ch);
    
    curl_setopt($ch, CURLOPT_URL, 'http://180.211.224.73/lightoj/index.php');

    $buf2 = curl_exec($ch);

    curl_close($ch);
[/php]

So, how can I use the cookie file? Or That is not even needed if I don't close the connection? I mean what I want to know is, even if I close connection, shouldn't it be possible to explore pages using these cookies?

---

### Post by BkkBonanza on 2011-06-15
The cookiejar is supposed to save cookies between sessions. You might expermiment with COOKIESESSION option. And also have a look at the cookiejar contents before/after each session to see how it changes. It could be that the cookie is not set to live past a session anyway. Other than that nothing comes to mind.

Doing a search for cookiejar on the manual page comments turns up a note about cookiejar not working with relative filepaths:

> When using curl with cookies, Relative path doesn't seem to work.

Use absolute path for setting the variables CURLOPT_COOKIEFILE & CURLOPT_COOKIEJAR.

To make life easier use the realpath("file.txt") function to get the absolute path.

Maybe that has some effect.

---

### Post by zobayer1 on 2011-06-15
I also thought about that, but didn't work for me either. So I guess, I need to look through session.

However, If I want to do it for some complex login mode, like forms with having many hidden fields: here is one example:
[HTML]
<input id="mod_login_username" class="inputbox" type="text" size="10" name="username">
<input id="mod_login_password" class="inputbox" type="password" size="10" name="passwd">
<input type="hidden" value="login" name="op2">
<input type="hidden" value="english" name="lang">
<input type="hidden" value="1" name="force_session">
<input type="hidden" value="B:aHR0cDovL3V2YS5vbmxpbmVqdWRnZS5vcmcv" name="return">
<input type="hidden" value="0" name="message">
<input type="hidden" value="loginmodule" name="loginfrom">
<input type="hidden" value="cbm_32ea7055_2585050b_694fd3b023e1cef5e34d6ab6e9ade994" name="cbsecuritym3">
<input type="hidden" value="1" name="j23ac45d6c3e512e628fae769812a24a4">
<input id="mod_login_remember" type="checkbox" value="yes" name="remember">
<input class="button" type="submit" value="Login" name="Submit">
[/HTML]So basically this is the form.

And for each login, they provide different values, How can I login to this page using cURL? is it possible? I think it is possible as cURL acts just like a browser, but I don't know how to do it. Should I first parse the login page for the hidden fields? This is the page I am talking about, if anyone want to see the login form: [http://uva.onlinejudge.org/](http://uva.onlinejudge.org/)
Thank you very much :)

---

### Post by BkkBonanza on 2011-06-15
Yes, if they change the values for each login then you would use curl to get the page, parse the values and set the post data to pass to curl when you submit the form (using the form action url).

What's silly is that they don't force you onto an https (ssl) page for the login.

---

### Post by zobayer1 on 2011-06-18
> **BkkBonanza said:**
> Yes, if they change the values for each login then you would use curl to get the page, parse the values and set the post data to pass to curl when you submit the form (using the form action url).

What's silly is that they don't force you onto an https (ssl) page for the login.

Thanks :) I think that will work.

Well, if the force to go https, will cURL work then? haven't tested. And, that's a old site, probably they didn't introduce that, because not many people use it.

---

### Post by BkkBonanza on 2011-06-18
curl will work with https as well but you have to add a few more options to provide ssl/CA info. The ones I needed were,

curl_setopt ($ch, CURLOPT_SSL_VERIFYPEER, 1); 
curl_setopt ($ch, CURLOPT_SSL_VERIFYHOST, 2);
curl_setopt ($ch, CURLOPT_CAINFO, '/var/local/ssl/certs/optimal.crt');

But this was with my own self-signed CA (optimal.crt) and probably for regular public CAs you would use maybe, /etc/ssl/certs (just guessing) with CURLOPT_CAPATH instead. Just check the options table to verify if you ever need to go that way.

---

### Post by zobayer1 on 2011-06-18
> **BkkBonanza said:**
> curl will work with https as well but you have to add a few more options to provide ssl/CA info. The ones I needed were,

curl_setopt ($ch, CURLOPT_SSL_VERIFYPEER, 1); 
curl_setopt ($ch, CURLOPT_SSL_VERIFYHOST, 2);
curl_setopt ($ch, CURLOPT_CAINFO, '/var/local/ssl/certs/optimal.crt');

But this was with my own self-signed CA (optimal.crt) and probably for regular public CAs you would use maybe, /etc/ssl/certs (just guessing) with CURLOPT_CAPATH instead. Just check the options table to verify if you ever need to go that way.

Thanks very much.. surely I will do :)

---

