---
title: "Problem setting PHP cookies on localhost"
date: 2008-06-27
forum: Programming Talk
---

### Post by mike_g on 2008-06-27
I have been trying for ages now and I cant seem to get cookies set via php on the localhost. THis is the code I'm using to set the cookie:
```
	function CarCookie($row, $num)
	{
		
		$name ="car_1";
		$str = "blah";
		setcookie("car_1", "blah", false, "/", false);
	}
```
At the end of the page I call this function to print out the cookie:
```
	function Printout()
	{
		 echo "cookie:";
		 print_r($_COOKIE);
	}
```
But nothing is ever set o_0 Can anyone say why this is?

---

### Post by LoneWolfJack on 2008-06-27
First off, enable error_reporting by putting 

```
error_reporting(E_ALL);
```

at the first line of any script. Some retard decided to deactivate error reporting by default in PHP 5.

As for the cookie, I am not sure PHP will let you get away with providing "false" where you should provide a timestamp.

Try a more basic form like this:
```
setcookie('car_1','blah');
```

Also, you are actually making the necessary function calls and your browser is not set to automatically decline all cookies, right?

---

### Post by mike_g on 2008-06-28
Cheers for the error reporting bit; I'll use that in future. Apparently the setcookie function needed those extra parameters when  running via the localhost/loopback according to what I had read. I had originally tried it w/o them. Edit: Oh and according to the manual if theres no timestamp the cookies die when the browser is closed.

I never got the cookies working, but managed to transfer the MySQL data to Javascript by writing Javascript code with PHP. So, my problems is solved; or at least until I need to use cookies again.

---

