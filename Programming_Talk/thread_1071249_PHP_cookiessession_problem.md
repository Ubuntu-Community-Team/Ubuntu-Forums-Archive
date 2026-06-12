---
title: "PHP cookies/session problem"
date: 2009-02-16
forum: Programming Talk
---

### Post by cerealtx on 2009-02-16
hey i am write a php script that logins into a site, but once i try to navigate in the site, im not logged in, how do i save the cookies i have tried a few things but its not working, here is my code so far

this works fine
```
function loginpof($username, $password)
{
$postfields = "?username=" . urlencode($username);
$postfields .= "&password=" . urlencode($password);
$pof = "http://www.website.com/inbox.aspx".$postfields;
$randnum = rand(1,9999999);
$useragent="Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.1) Gecko/20061204 Firefox/2.0.0.1";

	  $ch = curl_init(); 
	  curl_setopt($ch, CURLOPT_USERAGENT, $useragent);  
      curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
      curl_setopt($ch, CURLOPT_URL, $pof); 
	  $result = curl_exec($ch);
return($result);
}
```
but from here it goes all wrong
```

function search()
{
	
	$ch = curl_init();
	curl_setopt($ch, CURLOPT_RETURNTRANSFER,1);
	curl_setopt($ch, CURLOPT_URL, "http://www.website.com/basicsearch.aspx");
	$result = curl_exec($ch);
	curl_close($ch);
	return($result);
}
```

---

### Post by rharriso on 2009-02-17
you're making this way to complicated.
You need to use session variables, not cookies with php.
PHP runs on the server side, and Sessions are stored on the server. You should really only use cookies for javascript, because that runs on the client side and can read cookies stored on clients machine. 

[http://us2.php.net/session]("http://us2.php.net/session")

---

### Post by Tibuda on 2009-02-17
> **rharriso said:**
> you're making this way to complicated.
You need to use session variables, not cookies with php.
PHP runs on the server side, and Sessions are stored on the server. You should really only use cookies for javascript, because that runs on the client side and can read cookies stored on clients machine. 

[http://us2.php.net/session]("http://us2.php.net/session")

I agree in most situations, sessions is the way to go, as it is safer. But if you want to store data in the browser, so the user can close it, you SHOULD use cookies. Sessions are lost once the browser is closed. So, cookies are not only for JavaScript, but for PHP too.

---

