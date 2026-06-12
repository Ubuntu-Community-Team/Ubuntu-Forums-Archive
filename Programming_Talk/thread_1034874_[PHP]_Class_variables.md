---
title: "[PHP] Class variables"
date: 2009-01-09
forum: Programming Talk
---

### Post by pokerbirch on 2009-01-09
Ok, i did this in Python with PyCurl but now i've found out that the person i'm writing it for wants it in PHP. ](*,)

Basic problem is setting up curl so that i can create an instance in the class constructor and keep it until the class deconstructor is called. The question is: how do i make the curl instance available to all functions within the class? I've chopped out all the curl_setopt() stuff as it's not relevent to my problem:
[PHP]
class curly {
/*
NOTE: these all fail due to syntax error = unexpected '('
	$ch = curl_init();
	var $ch = curl_init();
	public $ch = curl_init();
*/
	function __construct() {
		// setup curl
		$ch = curl_init();
	}

	function __destruct() {
		// clean up
		curl_close($ch); // FAIL = "not a valid curl handle"
	}
}[/PHP]

---

### Post by Compyx on 2009-01-09
You're creating a local variable in __construct(), which goes out of scope as soon as __construct() reaches its end.

To have $ch available inside all class methods, use '$this->ch'. I suggest reading up on PHP classes a bit: [http://www.php.net/manual/en/language.oop5.php]("http://www.php.net/manual/en/language.oop5.php")

---

### Post by constrictor on 2009-01-09
> **pokerbirch said:**
> Ok, i did this in Python with PyCurl but now i've found out that the person i'm writing it for wants it in PHP. ](*,)

Basic problem is setting up curl so that i can create an instance in the class constructor and keep it until the class deconstructor is called. The question is: how do i make the curl instance available to all functions within the class? I've chopped out all the curl_setopt() stuff as it's not relevent to my problem:
[PHP]
class curly {
/*
NOTE: these all fail due to syntax error = unexpected '('
	$ch = curl_init();
	var $ch = curl_init();
	public $ch = curl_init();
*/
	function __construct() {
		// setup curl
		$ch = curl_init();
	}

	function __destruct() {
		// clean up
		curl_close($ch); // FAIL = "not a valid curl handle"
	}
}[/PHP]

ok firstly you will have to define the scope of $ch with $this->ch and this will become available to all functions
as long as you call them with $this->ch.

And if you need to reference it outside of the class you will have to call it with for example where $mycurl is the new instance of your curly class.
```
$mycurl = new curly();
```
to reference the ch variable from that object you will call it using
```
$mycurl->ch;
```

so in effect you __construct should read something like this

```
function __construct() {
	// setup curl
       $this->ch = curl_init();
}
```

---

