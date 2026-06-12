---
title: "Facebook read page through php with curl"
date: 2009-04-02
forum: Programming Talk
---

### Post by micdhack on 2009-04-02
I created this algorithm from various source that i found on the net. Its a simple algorithm that logs in into a facebook account and drags into an array the profile id and name of the friendlist. Later using the function i want to connect to the Fan pages list of each user and pull this information. Doing it directly through browser it works but maybe im missing something. can you help?

here is the code:
```
function read_fanpages_return_array ($user_id)
{
	//echo 'https://login.facebook.com/login.php?&next=http://www.facebook.com/s.php?k=100000004&id='.$user_id.'&gr=102&next=http://www.facebook.com/s.php?k=100000004&id='.$user_id.'&gr=102';
	//die();
	$ch = curl_init();
	curl_setopt($ch, CURLOPT_URL, 'https://login.facebook.com/login.php?&next=http://www.facebook.com/s.php?k=100000004&id='.$user_id.'&gr=102');
	curl_setopt($ch, CURLOPT_POSTFIELDS,'email='.urlencode("email").'&pass='.urlencode("password").'&login=Login');
	curl_setopt($ch, CURLOPT_POST, 1);
	curl_setopt($ch, CURLOPT_HEADER, 0);
	curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
	curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
	curl_setopt($ch, CURLOPT_COOKIEJAR, "cookie.txt");
	curl_setopt($ch, CURLOPT_COOKIEFILE, "cookie.txt");
	curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
	curl_setopt($ch, CURLOPT_USERAGENT, "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.3) Gecko/20070309 Firefox/2.0.0.3");
	echo $line = curl_exec($ch);
}

$ch = curl_init();
// curl_setopt($ch, CURLOPT_URL, 'https://login.facebook.com/login.php?&next=http://www.facebook.com/home.php');
curl_setopt($ch, CURLOPT_URL, 'https://login.facebook.com/login.php?&next=http://www.facebook.com/friends/?everyone&ref=tn');
curl_setopt($ch, CURLOPT_POSTFIELDS,'email='.urlencode("email").'&pass='.urlencode("password").'&login=Login');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
curl_setopt($ch, CURLOPT_COOKIEJAR, "cookie.txt");
curl_setopt($ch, CURLOPT_COOKIEFILE, "cookie.txt");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_USERAGENT, "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.3) Gecko/20070309 Firefox/2.0.0.3");
$line = curl_exec($ch);


preg_match_all('@profile\.php\?id\=(.*?)\">(.*?)<@i',$line,$matches);
echo "<pre>";
//print_r($matches);
$clean_array=array();
while (list($var, $val) = each($matches[1])) {
	if (!strpos($val,"fname") === false) {
		$val=str_replace(chr(92),"",$val);
		$val=str_replace('" class="fname',"",$val);
		$clean_array[0][]=$val;
		$clean_array[1][]=$matches[2][$var];
	}
}
//print_r($clean_array);

read_fanpages_return_array($clean_array[0][0]);
```

---

### Post by micdhack on 2009-04-03
it seems that even in browser if i put this url:
```
https://login.facebook.com/login.php?&next=http://www.facebook.com/s.php?k=100000004&id=601557505&gr=102&sid=f88b6f9a2ae029ff1de7e4e29a61a331
```

still it doesnt work and redirects me to a search page.

So considering that i have cookies and all is there a way that i could browse the site like it was from my browser?
Im not good in curl so i dont know which options i should remove from the function etc. cause since i already logged in once it seems to me that is not necessery to put the whole url.

---

### Post by PaulFr on 2009-04-03
**_[https://login.facebook.com/login.php](https://login.facebook.com/login.php)_** seems to go to their login page, so why the rest of the URL ?

---

### Post by micdhack on 2009-04-04
see that the thing..after loggin in i dont want to go to my homepage but to:
[http://www.facebook.com/s.php?k=100000004&id=601557505&gr=102](http://www.facebook.com/s.php?k=100000004&id=601557505&gr=102)
which is the fan pages for each profile i have on my friendlist if you replace the id with the number of your friend. Thing is that with this &next= trick i can go to someones profile but not to profile fan pages. So is there any way that with curl i can login, put the info to cookies and continue browsing to pages like i was from a browser?

---

### Post by micdhack on 2009-04-10
i couldnt solve the problem but i found out 2 alternatives. The first is to just go to the page where all fan pages are and read it.

The other and much...way much more easier is to do through facebook application and specificaly through the FQL system which is something like mysql queries only for the tables of the facebook.

---

