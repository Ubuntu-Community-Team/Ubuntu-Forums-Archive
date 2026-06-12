---
title: "imacros"
date: 2011-07-08
forum: Programming Talk
---

### Post by conradin on 2011-07-08
HI all Im trying to do a data extract from a specific loaction, for a random bit of data using imacros.
Im trying to use a SEARCH SOURCE=REGEXP query but the query structure is a mystery to me. 
Ive read: [http://wiki.imacros.net/SEARCH](http://wiki.imacros.net/SEARCH)
but this doesn't explain enough so that I can figure out how to make it useful in building my own query. 

A sample bit of the source webpage is:
```
<table cellpadding=0 cellspacing=0><tr><td width="220px"><div style="width:200; height:25; background:url(/images/timedcombat-background.png); border:1px solid #000000;"></div></td><td>Next target: <b>6 seconds</b></i></td></tr></table>
```

So Ive tried: a whole bunch of stuff trying to figure out how the query structure works but I haven't go it.
```

Imacros Notes on using SEARCH REGEXP
SEARCH SOURCE=REGEXP:"target:..[^]"          EXTRACT=$1  | gives: undefined
SEARCH SOURCE=REGEXP:"target:..[^s]"         EXTRACT=$1  | gives: undefined
SEARCH SOURCE=REGEXP:"target:..[^0-9]"      EXTRACT=$1  | gives: undefined
SEARCH SOURCE=REGEXP:".*target..([0-9]+)"  EXTRACT=$1  | gives: Source Doesnt match target
SEARCH SOURCE=REGEXP:"target..([0-9]+)"     EXTRACT=$1  | gives: Source Doesnt match target
SEARCH SOURCE=REGEXP:"target:..([0-9]+)"    EXTRACT=$1  | gives:Source Doesnt match target
SEARCH SOURCE=REGEXP:"target:..([^0-9]+)"  EXTRACT=$1  | gives:Source Doesnt match target
SEARCH SOURCE=REGEXP:"target:..([^0-9])"    EXTRACT=$1 | gives: b
SEARCH SOURCE=REGEXP:"target:.([^0-9])"     EXTRACT=$1 | gives: <
SEARCH SOURCE=REGEXP:"target:([^0-9])"      EXTRACT=$1 | gives:  Blank, literaly, the space character I think..
SEARCH SOURCE=REGEXP:"target:?([^0-9])"     EXTRACT=$1 | gives: ;
SEARCH SOURCE=REGEXP:"target:?.([^0-9])"    EXTRACT=$1 | gives: <
SEARCH SOURCE=REGEXP:"target:?.([^0-9])"    EXTRACT=$1 | gives:  Blank, literaly, the space character I think..
SEARCH SOURCE=REGEXP:"target:?.([^0-9]+)" EXTRACT=$1 | gives: UGH,.. some part of the Imacros source code?
		var altKey;
		var ctrlKey;
		var metaKey;
		if (window.event != null) {
			c=String.fromCharCode(window.event.keyCode).toUpperCase();
			altKey=window.event.altKey;
			ctrlKey=window.event.ctrlKey;
			metaKey=window.event.metaKey;
		}else{
			c=String.fromCharCode(e.charCode).toUpperCase();
			altKey=e.altKey;
			ctrlKey=e.ctrlKey;
			metaKey=e.metaKey;
		}
		if (window.event != null)
			target=window.event.srcElement;
		else
			target=e.originalTarget;
		if (target.nodeName.toUpperCase()=='INPUT' || target.nodeName.toUpperCase()=='TEXTAREA' || altKey || ctrlKey || metaKey){
		}else{
			if (c == '



```
So Then I decided I need help. Yes, I'm on the imacros forums, but help there is hit and miss. 
is there documentation of how exactly to form Search Source queries using imacros? Or does anyone use Imacros, and could explain this to me.

---

### Post by conradin on 2011-07-09
Ok, I finally got it:
```
VERSION BUILD=7220523 RECORDER=FX
SEARCH SOURCE=REGEXP:"target: <b>([0-9]+)" EXTRACT=$1
SET !VAR1 {{!EXTRACT}}
PROMPT {{!EXTRACT}}
```

That works well enough, I didnt know I could put a space in a REGEXP.
I also learned that imacros is a script, at least as it is running as an add-on in Firefox. Thats why the source code that I got looks like code and not assembly language. Im sure that could be useful later on, right now Im more happy my macro is working.

---

### Post by Gaet86 on 2012-05-29
Hi boys...
I 'm beginner to Imacros.
I have this webpage and i want extract text.

The code is:
```

<table>
<tbody>
<tr>
<td>
Email....
</td>
</tr>
<tr>
<td>
The link for active the account is http:\\www....................... insert to browser
</td>
</tr>

<\tbody>
<\table>
```
I have more table and tr and td... But i want search the link http:\\[www..](www..)..................... and extract in Var.
The link isn't whit tag href.

Thanks...in advance

---

