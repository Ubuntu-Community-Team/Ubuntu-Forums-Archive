---
title: "PHP cURL form submission again in trouble"
date: 2011-07-03
forum: Programming Talk
---

### Post by zobayer1 on 2011-07-03
I am trying to do this for last 2 days. I have used cURL to submit forms to pages, but this time it is slightly different and difficult. The page I am submitting to has 8 hidden fields. So what I did it, first open the page, parse the fields and then submit the login form to target address. But this is not working...

My target is to log in this site [http://livearchive.onlinejudge.org/](http://livearchive.onlinejudge.org/), so I just made a page with a simple form like, page named "la_submit.php"
[PHP]
<html><body>
<form action="la_process.php" method="post" enctype="multipart/form-data">
Username: <input name="username" type="text" maxlength="20" />
Password: <input name="password" type="password" maxlength="20" />
<input name="submit" type="submit" value="Log In" />
</form>
</body></html>
[/PHP]Then in la_process.php, I have done as follows, (well, there are some unused codes, please just ignore them, like file upload part, as I have copied it from my other simpler application)
[PHP]
<?php
    if(isset($_POST['submit'])===true) {
        extract($_POST);
        if($_FILES['srcefile']['error'] == 0) {
            // a file has been uploaded
            $temp = $_FILES['srcefile']['tmp_name'];
            $name = 'upload/'.basename($temp);
            
            move_uploaded_file($temp, $name);
            
            $fp = fopen($name, 'r');
            $srcecode = fread($fp, filesize($name));
            fclose($fp);
        }
    }
    else { header('location: la_submit.php'); }
    
    $cookie_fname = realpath('cookie').'/'.md5($username . $password . rand(0, 2147483647));
    echo '<style type="text/css">pre { padding-left:20px; }</style>';
    echo '<hr/><pre>Cookie Filename:<br/>'.$cookie_fname.'</pre>';
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_COOKIEJAR, $cookie_fname);
    curl_setopt($ch, CURLOPT_URL,"http://livearchive.onlinejudge.org/");
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

    $page = curl_exec($ch);
    $info = curl_getinfo($ch);

    $loginform = '!';
    $data['username'] = $username;
    $data['passwd'] = $password;
    if(preg_match_all('/<form(.*)>(.*)<\/form>/smU', $page, $matches)) {
        foreach($matches[0] as &$value) {
            if(preg_match('/id="mod_loginform"/', $value)) {
                $loginform = $value;
                echo '<hr/><pre>'.htmlspecialchars($loginform).'</pre>';
                preg_match_all('/<input.+type="hidden"(.*)>/', $loginform, $hidden);
                foreach($hidden[0] as &$field) {
                    echo '<hr/><pre>'.htmlspecialchars($field).'<br/>';
                    preg_match('/name="[^\s]*"/', $field, $field_name);
                    preg_match('/value="[^\s]*"/', $field, $field_value);
                    $tmp1 = preg_replace('/name="(.*)"/', '$1', $field_name[0]);
                    $tmp2 = preg_replace('/value="(.*)"/', '$1', $field_value[0]);
                    echo '['.$tmp1.']['.$tmp2.']</pre>';
                    $data[$tmp1] = $tmp2;
                }
                break;
            }
        }
    }
    $data['Submit'] = 'Login';
    if($loginform == '!') { header('location: la_submit.php'); }

    echo '<hr/><pre>';
    foreach($data as $tmp1 => $tmp2) {
        echo '['.$tmp1.']['.$tmp2.']<br/>';
    }
    echo '</pre>';

    $post_url = '';
    foreach($data as $key => $value)
        $post_url .= $key.'='.rawurlencode($value).'&';
    $post_url = rtrim($post_url, '&');
    echo '<hr/><pre>'.$post_url.'</pre>';

    curl_setopt($ch, CURLOPT_COOKIEFILE, $cookie_fname);
    curl_setopt($ch, CURLOPT_URL,"http://livearchive.onlinejudge.org/index.php?option=com_comprofiler&amp;task=login");
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $post_url);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

    $page = curl_exec($ch);
    $info = curl_getinfo($ch);
    echo '<hr/>'.$page. '<hr/>Curl Status: ';
    print_r($info);
?>
[/PHP]I always get the response that login failed. "Please log in or register to view or modify your profile.                      ", can anyone tell me please, what's wrong here...

So, how can I log in successfully here? please help me

Just for information, if you try to test it on your localhost / server, you will need to make two folders named "upload" and "cookie" with write permission for user.

---

### Post by zobayer1 on 2011-07-04
Sorry to bump, but could really use some help :)

---

### Post by Reiger on 2011-07-04
To quote:
> 
Some people, when confronted with a problem, think “I know, I'll use regular expressions.” Now they have two problems.

Therein lies your problem.

---

### Post by zobayer1 on 2011-07-04
> **Reiger said:**
> To quote:


Therein lies your problem.

Are you saying that the problem is in regex part? but can you please point it out a bit more? Because, as I am echoing everything, they seemed ok to me.. obviously I am not xpart in php / regex, but I want to know actually what is wrong ... Any more suggestions please?

---

### Post by Reiger on 2011-07-04
I'm fairly confident in saying you approached this problem as follows:

1) I want to log in to xyz
2) So I need submit my username & password to xyz over HTTP
3) It doesn't work.

4) Ooh there are all those hidden values in the page source.
5) I know, I'll use regular expressions -- to sniff them out of the page source.
6) It still doesn't work.

-- Apart from the fact the URL you use to login is wrong (escaped ampersand), the problem lies in your approach which the quote lucidly illustrates: you try to cut corners.

Instead what you should be doing is this:
1) I want to login.
2) I normally use a browser to login.
3) When I type my username and password in the login box, and click login the browser does .... what exactly? (Hint: what is JavaScript doing, any form field encoding going on, etc. etc.?)
4) Recreate the exact same behaviour from the browser in my PHP code

Why cutting corners won't work:
1) If the site is written by people remotely competent then they will make sure that the input conforms exactly to what they expect it to, based on what their frontend is doing.
2) Therefore if you are missing a trick in the frontend, this will show in your HTTP request.
3) Therefore your login request will be rejected without fail.

---

### Post by zobayer1 on 2011-07-04
> **Reiger said:**
> I'm fairly confident in saying you approached this problem as follows:
.....

Yes you are right.
> 
-- Apart from the fact the URL you use to login is wrong (escaped ampersand), the problem lies in your approach which the quote lucidly illustrates: you try to cut corners.

Well, when I used normal &, it returned 403, thats why I changed to that.
> 
Instead what you should be doing is this:
1) I want to login.
2) I normally use a browser to login.
3) When I type my username and password in the login box, and click login the browser does .... what exactly? (Hint: what is JavaScript doing, any form field encoding going on, etc. etc.?)
4) Recreate the exact same behaviour from the browser in my PHP code

How do I mimic javascript behaviours?
> 
Why cutting corners won't work:
1) If the site is written by people remotely competent then they will make sure that the input conforms exactly to what they expect it to, based on what their frontend is doing.
2) Therefore if you are missing a trick in the frontend, this will show in your HTTP request.
3) Therefore your login request will be rejected without fail.

I also though about there are some javascript validators...

Still thinking how to overcome this... :-s

---

### Post by zobayer1 on 2011-07-04
Well, one thing I know for sure is, it is possible to login to this site, as I have already did that with a python library, but I need to do it using php because python is not-so-popular in web servers, specially mine one doesn't support python...

---

### Post by Reiger on 2011-07-04
> **zobayer1 said:**
> Yes you are right.

Well, when I used normal &, it returned 403, thats why I changed to that.
And what is a 403? Forbidden/Access Denied.

> 

How do I mimic javascript behaviours?

By writing PHP code that generates the same output as the JavaScript code given its input, of course.

---

### Post by zobayer1 on 2011-07-04
> **Reiger said:**
> And what is a 403? Forbidden/Access Denied.


By writing PHP code that generates the same output as the JavaScript code given its input, of course.

By inspecting the page source and linked javascript, I could not find anything that could be related to loginform. Confused...

---

### Post by zobayer1 on 2011-07-05
Now I am sure that the site doesn't do any javascript trick with the login process... Now what?

---

