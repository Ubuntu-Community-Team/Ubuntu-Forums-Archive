---
title: "php regex help"
date: 2011-06-28
forum: Programming Talk
---

### Post by zobayer1 on 2011-06-28
I am trying to parse a webpage and read a few tags. For example, I have many <form> tags in the page and I want to get only a specific tag having a specific id, say "loginform"
[HTML]<form id="loginform" style="margin:0px;" action="targetpage.php" method="post">[/HTML]I just want to read this part.

So I created a pattern for preg_match:
[PHP]$pattern = '/\<form[.\s]*(id="loginform")+[^\>]*\>/i';[/PHP]Well, when I test is it works fine, if there are multiple forms, it just selects the one having "loginform" id.

But when I try to do that on actual page, it fails. May be the reason is, the actual page may contain newline characters, but I am not sure, can anyone tell me how to overcome the problem?

Thanks in advance.

---

### Post by myrtle1908 on 2011-06-29
> **zobayer1 said:**
> But when I try to do that on actual page, it fails. May be the reason is, the actual page may contain newline characters, but I am not sure, can anyone tell me how to overcome the problem?

Use the *m* modifier eg. in your case add '/im' to end of your regex.

---

### Post by zobayer1 on 2011-06-30
> **myrtle1908 said:**
> Use the *m* modifier eg. in your case add '/im' to end of your regex.

Doesn't help :(

---

### Post by zobayer1 on 2011-06-30
Here is an example about what I'm trying to do:
[PHP]
<?php
    $subject = '                <td class="modulecontent"><div class="modulecontent">
            <form action="http://livearchive.onlinejudge.org/index.php?option=com_comprofiler&amp;task=login" method="post" id="mod_loginform" class="cbLoginForm"style="margin:0px;">
<table width="100%" border="0" cellspacing="0" cellpadding="0" class="mod_login">
<tr><td><span id="mod_login_usernametext"><label for="mod_login_username">Username</label></span><br />
<input type="text" name="username" id="mod_login_username" class="inputbox" size="10" /><br />
<span id="mod_login_passwordtext"><label for="mod_login_password">Password</label></span><br /><span><input type="password" name="passwd" id="mod_login_password" class="inputbox" size="10" /></span><br />
<input type="hidden" name="op2" value="login" />
<input type="hidden" name="lang" value="english" />
<input type="hidden" name="force_session" value="1" />
<input type="hidden" name="return" value="B:aHR0cDovL2xpdmVhcmNoaXZlLm9ubGluZWp1ZGdlLm9yZy8=" />
<input type="hidden" name="message" value="0" />
<input type="hidden" name="loginfrom" value="loginmodule" />
<input type="hidden" name="cbsecuritym3" value="cbm_4c7f5e63_01469589_ef91f136ff61ba5f44cd8cbcb1f79cd0" />
<input type="hidden" name="jdc1bfec316f9f11a6c83ce0ffc31b6c4" value="1" />
<input type="checkbox" name="remember" id="mod_login_remember" value="yes" /> <span id="mod_login_remembermetext"><label for="mod_login_remember">Remember me</label></span><br />
<span class="cbLoginButtonSpan"><input type="submit" name="Submit" class="button" value="Login" /></span></td></tr>
<tr><td><a href="http://livearchive.onlinejudge.org/index.php?option=com_comprofiler&amp;task=lostpassword" class="mod_login">Forgot login?</a></td></tr>
<tr><td><a href="http://livearchive.onlinejudge.org/index.php?option=com_comprofiler&amp;task=registers" class="mod_login">Register</a></td></tr>
</table></form>                </div></td>
            </tr>
          </table>
        ';
?>
[/PHP]This is just a snapshot of actual data, which is the entire web page. I want to capture the block of code within <form> tag. Please someone help me to design the regex...

---

### Post by Arndt on 2011-06-30
> **zobayer1 said:**
> Here is an example about what I'm trying to do:
[PHP]
<?php
    $subject = '                <td class="modulecontent"><div class="modulecontent">
            <form action="http://livearchive.onlinejudge.org/index.php?option=com_comprofiler&amp;task=login" method="post" id="mod_loginform" class="cbLoginForm"style="margin:0px;">
<table width="100%" border="0" cellspacing="0" cellpadding="0" class="mod_login">
<tr><td><span id="mod_login_usernametext"><label for="mod_login_username">Username</label></span><br />
<input type="text" name="username" id="mod_login_username" class="inputbox" size="10" /><br />
<span id="mod_login_passwordtext"><label for="mod_login_password">Password</label></span><br /><span><input type="password" name="passwd" id="mod_login_password" class="inputbox" size="10" /></span><br />
<input type="hidden" name="op2" value="login" />
<input type="hidden" name="lang" value="english" />
<input type="hidden" name="force_session" value="1" />
<input type="hidden" name="return" value="B:aHR0cDovL2xpdmVhcmNoaXZlLm9ubGluZWp1ZGdlLm9yZy8=" />
<input type="hidden" name="message" value="0" />
<input type="hidden" name="loginfrom" value="loginmodule" />
<input type="hidden" name="cbsecuritym3" value="cbm_4c7f5e63_01469589_ef91f136ff61ba5f44cd8cbcb1f79cd0" />
<input type="hidden" name="jdc1bfec316f9f11a6c83ce0ffc31b6c4" value="1" />
<input type="checkbox" name="remember" id="mod_login_remember" value="yes" /> <span id="mod_login_remembermetext"><label for="mod_login_remember">Remember me</label></span><br />
<span class="cbLoginButtonSpan"><input type="submit" name="Submit" class="button" value="Login" /></span></td></tr>
<tr><td><a href="http://livearchive.onlinejudge.org/index.php?option=com_comprofiler&amp;task=lostpassword" class="mod_login">Forgot login?</a></td></tr>
<tr><td><a href="http://livearchive.onlinejudge.org/index.php?option=com_comprofiler&amp;task=registers" class="mod_login">Register</a></td></tr>
</table></form>                </div></td>
            </tr>
          </table>
        ';
?>
[/PHP]This is just a snapshot of actual data, which is the entire web page. I want to capture the block of code within <form> tag. Please someone help me to design the regex...

Your regexp looked for id="loginform", but in the data above, you have id="mod_loginform".

---

### Post by myrtle1908 on 2011-06-30
Here's a way in Perl.  The form tag can be broken up over multiple lines.

```
$subject =~ m/(<form.*?id="mod_loginform".*?>)/igsm;
print $1;
```

... prints ...

```
<form action="http://livearchive.onlinejudge.org/index.php?option=com_comprofiler&amp;task=login"
method="post" id="mod_loginform" class="cbLoginForm"style="margin:0px;">
```

---

### Post by myrtle1908 on 2011-06-30
Sorry ... realised you want what is inside the form tag ...

```
$subject =~ m/<form.*?id="mod_loginform".*?>(.*?)<\/form>/igsm;
print $1;
```

---

### Post by zobayer1 on 2011-07-01
> **Arndt said:**
> Your regexp looked for id="loginform", but in the data above, you have id="mod_loginform".
I know that, that was just an example.

---

### Post by zobayer1 on 2011-07-01
> **myrtle1908 said:**
> Sorry ... realised you want what is inside the form tag ...

```
$subject =~ m/<form.*?id="mod_loginform".*?>(.*?)<\/form>/igsm;
print $1;
```

Thanks so much, but I don't know perl, however, I will try to write a similar one for php. :)

---

### Post by zobayer1 on 2011-07-01
Well, This time I tried the following, but no luck so far
[PHP]
$pattern = '/\<form.+id="mod_loginform".*\>.+\<\/form\>/im';
[/PHP]What I am missing?

---

### Post by SeijiSensei on 2011-07-01
I use an entirely different method to parse things like this. 

First, read the page into an array using file().  I then iterate over the lines the in the resulting array until I find the entry that begins the block of text I want and append the remaining lines into a string until I find the string delimiting the end of the block.  Something like this:

```

$found='';
$foundstart=0;
$mypage=file("http://www.example.com/index.html");
for ($i=0; $i<count($mypage); $i++) {
     if (strstr($mypage[$i],'loginform')) { $foundstart=1; }
     
     if ($foundstart) {
         $found.=$mypage[$i];
         if (strstr($mypage[$i],'</form>')) { break; }
     }
}

```

The string variable $found should contain all the lines starting with the one that includes "loginform" until the closing "</form>" tag.

---

### Post by zobayer1 on 2011-07-01
> **SeijiSensei said:**
> I use an entirely different method to parse things like this. 

First, read the page into an array using file().  I then iterate over the lines the in the resulting array until I find the entry that begins the block of text I want and append the remaining lines into a string until I find the string delimiting the end of the block.  Something like this:

```

$found='';
$foundstart=0;
$mypage=file("http://www.example.com/index.html");
for ($i=0; $i<count($mypage); $i++) {
     if (strstr($mypage[$i],'loginform')) { $foundstart=1; }
     
     if ($foundstart) {
         $found.=$mypage[$i];
         if (strstr($mypage[$i],'</form>')) { break; }
     }
}

```The string variable $found should contain all the lines starting with the one that includes "loginform" until the closing "</form>" tag.
hmm, I understand that manually doing so will solve my problem, but I wanted to do it with regex because, web pages do not follow standards always.

More frustrating is that, when I run the regex on a snapshot of the webpage (manually copied) and it works fine, but when I read it with cURL and then run the same regex on it, it fails...

[PHP]$pattern = '/\<form.+id="mod_loginform".*\>.*\<\/form\>/ism';[/PHP]

This is the last one I tried..

---

### Post by SeijiSensei on 2011-07-02
> **zobayer1 said:**
> hmm, I understand that manually doing so will solve my problem, but I wanted to do it with regex because, web pages do not follow standards always.

Whether they follow standards or not really doesn't matter if you're simply parsing a page with a known, predictable format.  It doesn't appear you're trying to write some type of generic parser, just one that handles a known page.

---

### Post by zobayer1 on 2011-07-02
> **SeijiSensei said:**
> Whether they follow standards or not really doesn't matter if you're simply parsing a page with a known, predictable format.  It doesn't appear you're trying to write some type of generic parser, just one that handles a known page.

Hmm, I have also written a manual parser. It has a good side also, it can be implemented "as I wanted"... :D

---

### Post by zobayer1 on 2011-07-03
Finally, did this with regex:
[PHP]
    $loginform = 'Not Found !';
    if(preg_match_all('/<form(.*)>(.*)<\/form>/ismU', $page, $matches)) {
        foreach($matches[0] as &$value) {
            if(preg_match('/id="mod_loginform"/', $value)) {
                $loginform = $value;
                break;
            }
        }
    }
    echo '<hr/><pre>'.htmlspecialchars($loginform).'</pre><hr/>';
[/PHP]

---

