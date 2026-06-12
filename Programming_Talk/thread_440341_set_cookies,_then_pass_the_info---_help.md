---
title: "set cookies, then pass the info--- help"
date: 2007-05-11
forum: Programming Talk
---

### Post by ubiwankanubi on 2007-05-11
I've written some php pages that take a passed variable and sent to a cookie as such:

<?php
$value=$_GET['value'];
setcookie("cookie", $value, time()+720); ?>

but now, I want to enter the text from that cookie into a flex2 application.
I have a function such as:
text="hello NAME"
I want to replace the text "NAME" with the cookie results of "cookie"

this should be pretty straightforward, how can I accomplish this?

---

### Post by regetch on 2007-05-11
Use the variable $_COOKIE['cookie']

---

### Post by ubiwankanubi on 2007-05-11
I'm not sure how I should put that variable in flex. do you mean like this:

<?xml version="1.0" encoding="utf-8" ?>
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml">
<mx:Label text="{$_COOKIE['cookie']}" />
</mx:Application>

in which case i get the error: Access of undefined property $_COOKIE

or

<?xml version="1.0" encoding="utf-8" ?>
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml">
<mx:Script>
		<![CDATA[
			public var cookie:String = new cookie("$_COOKIE");
		]]>
</mx:Script>

<mx:Label text="{cookie}" />
</mx:Application>

in which case i get the error:
 Error: Constructor functions must be instance methods.
                        public var cookie:String = new cookie("$_COOKIE");

---

### Post by regetch on 2007-05-12
Sorry I have no idea, I was just telling you what it is in PHP, I've no experience with flex so can't help sorry.

---

