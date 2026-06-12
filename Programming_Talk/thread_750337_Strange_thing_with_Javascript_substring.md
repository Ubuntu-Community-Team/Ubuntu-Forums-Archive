---
title: "Strange thing with Javascript substring"
date: 2008-04-09
forum: Programming Talk
---

### Post by mike_g on 2008-04-09
Heres some javascript code:
```
function ClearCartCookies()
{
	var cookie_array = document.cookie.split(";");
	var cookie_prefix
	for(i=0; i<cookie_array.length; i++)
	{
		cookie_prefix = cookie_array[i].substring(0, 5);
		document.write(cookie_prefix+" <br/>");
	}
	
}
```
I want to get the first 5 characters to see if they match "cart_" on the first iteration my code prints "cart_" as it should, but for all cookies after that it only prints the first 4 characters. This is wierd. Cn anyone explain why this is happening?

---

### Post by Zugzwang on 2008-04-09
Isn't there a ";" missing in line 4?

What does *document.write(document.cookie + "</BR>")* reveal?

---

### Post by mike_g on 2008-04-09
Youre right there was a semicolon missing, but AFAIK you dont actually need them; I just add them as out of habit. I put it in now though ;) I also added a pipe after the variable to see where the string ended, but it dident seem to give any clues:
```
document.write(cookie_prefix+"|<br/>");
```
My output is:
```
cart_|
cart|
cart|
cart|
```
with four cookies in my browser, each starting with "cart_".

---

### Post by lnostdal on 2008-04-09
try writing out the full strings .. ("before" you call substring) .. just to check ...

```
...
document.write(cookie_array[i] + "<br/>");
...

```

---

### Post by mike_g on 2008-04-09
Thanks, I managed to solve my problem. In a bit of an ugly way though. It seems that on each iteration atfer the first there was some invisible character infront of the string. This seems to work:
```
function ClearCartCookies()
{
	var cookie_array = document.cookie.split(";");
	var cookie_prefix;
	for(i=0; i<cookie_array.length; i++)
	{
		cookie_prefix = cookie_array[i].substring(1, 5);
		document.write(cookie_prefix+" <br/>");
		if(cookie_prefix == "art_" || cookie_prefix == "cart")
			document.write("Deleted!<br/>");
	}	
}
```
Is there a trim function in JS? I cant seem to find one mentioned on the W3 site.

---

