---
title: "Any code to mark as offline?"
date: 2011-12-19
forum: Programming Talk
---

### Post by CoffeeRain on 2011-12-19
Hi, I have a web page and would like to list all the online users. I have the code to mark them as online when they enter the page, but I want to mark them offline when they leave. I got some javascript code to redirect to offline.php when a user is inactive, but I don't have code for when they leave the page. Any code would work, because it just has to redirect to my offline.php. Thanks! :popcorn:

---

### Post by simeon87 on 2011-12-19
That's not the way to do it. You measure the time of the user's last activity and you automatically mark them as "offline/inactive" when X minutes have passed. So when a page is requested and some users have not done anything in the past X minutes, they are considered inactive and displayed as such.

---

### Post by CoffeeRain on 2011-12-19
So would measuring the inactivity also work when they have closed the browser after just completing an action?

---

### Post by jwbrase on 2011-12-19
> **CoffeeRain said:**
> So would measuring the inactivity also work when they have closed the browser after just completing an action?

It would take a few minutes (or however long you set the timeout to) after they closed the browser, but yes.

---

### Post by Tony Flury on 2011-12-20
The thing to remember is that the Server has no knowledge of whether your browser is open or not - in fact all that the server knows is that your browser requested a particular page/image (called a resource). In particular there is no way that the server could know that a user left the page, unless they have gone to another page on the same server. If they for instance choose a completely different page (on a different site) from their bookmarks, the server they are "leaving", in general won't be told.

I think there is a way (in javascript) to do something when a page is unloaded from the browser and you could (in theory) organise for a message to be sent to the server in that case - but unless you want millisecond accuracy - a time based  mechnaism suggested by simeon87 is the way to do it.

---

### Post by ofnuts on 2011-12-20
> **Tony Flury said:**
> I think there is a way (in javascript) to do something when a page is unloaded from the browser and you could (in theory) organise for a message to be sent to the server in that case - but unless you want millisecond accuracy - a time based  mechnaism suggested by simeon87 is the way to do it.Yes, there is an "unload" event. However, sending a request to the server when this happens (ajax?) may prevent the user from going to the next page (following a link, for instance). 

In any case, that would be rather unreliable (navigator killed, system rebooted, power failure...)

---

### Post by Tony Flury on 2011-12-20
> **ofnuts said:**
> Yes, there is an "unload" event. However, sending a request to the server when this happens (ajax?) may prevent the user from going to the next page (following a link, for instance). 

In any case, that would be rather unreliable (navigator killed, system rebooted, power failure...)

Completely agree - I have never seen a design that actually sent a log off to the Server - or a server that relied solely on the USER going to the log off page, or sending a log off message in any way - there has to be some sort of Server side back-stop.

---

### Post by CoffeeRain on 2011-12-20
Thanks. I did try using onunload (which didn't work very well) and on a timeout, but now I know I don't have to. :D I really appreciate the help!

---

### Post by CoffeeRain on 2011-12-20
Oh yeah, just another quick question. When I use css to put something on the top left corner, I used ```
{float:left; clear:both; margin:0; padding:0;}
``` to put it there. In Firefox, it is a few lines down, but in someones Safari that I checked it with, it is where it should be. Is this because of one of the attributes I used, or because I used the <p> tag? Thanks.

---

### Post by Tony Flury on 2011-12-20
Probably best to open a new thread about your CSS question - normally stacking multiple diverse questions in one thread is not a great way of getting answers :-)

---

### Post by CoffeeRain on 2011-12-20
:) OK, thanks.

---

### Post by CoffeeRain on 2011-12-20
Sorry, but I've got to unsolve this thread. I have the code to check if someone is offline, but now I need to know how to make it check periodically. It isn't very useful to just check when the page loads. :|

---

### Post by ofnuts on 2011-12-20
> **Tony Flury said:**
> Completely agree - I have never seen a design that actually sent a log off to the Server - or a server that relied solely on the USER going to the log off page, or sending a log off message in any way - there has to be some sort of Server side back-stop.I have never seen such a design, but I've seen it in customer requirements (which usually means long meetings ahead :) )

---

### Post by CoffeeRain on 2011-12-21
Hi, here I am again! :| I decided to learn how to use AJAX. Here's my javascript. Could you tell me how to fix it? I don't think it works--

```
<script type="text/javascript">
// Offline AJAX function

var response;

function ajaxFunction(){
	var ajaxRequest;
	
	try{
		// Opera 8.0+, Firefox, Safari
		ajaxRequest = new XMLHttpRequest();
	} catch (e){
		// Internet Explorer Browsers
		try{
			ajaxRequest = new ActiveXObject("Msxml2.XMLHTTP");
		} catch (e) {
			try{
				ajaxRequest = new ActiveXObject("Microsoft.XMLHTTP");
			} catch (e){
				// Something went wrong
				alert("Your browser broke!");
				return false;
			}
		}
	}
	// Create a function that will receive data sent from the server
	ajaxRequest.onreadystatechange = function(){
		if(ajaxRequest.readyState == 4){
			response = ajaxRequest.responseText;
		}
	}
	var username = "<?php echo $_COOKIE[loggedin]?>";
	var queryString = "?name="+username;
	ajaxRequest.open("GET", "offline.php" + queryString, true);
	ajaxRequest.send(null); 
}


// Timout calling

var username;
username="<?php if (isset($_COOKIE['loggedin'])) {echo $_COOKIE['loggedin'];} else {echo 'Null';}?>";

var t;
document.onkeypress=to
document.onclick=to

function logout()
{
ajaxFunction();
alert('ajaxFunction should have been called');
}

function to()
{
alert('clearing timeout');
clearTimeout(t);
t=setTimeout(logout, 5000); //sets offline in 5 seconds
}

</script>
```

---

### Post by simeon87 on 2011-12-21
What do you mean "it doesn't work"? What precisely does not work? It appears you've adapted this from a tutorial so you may need to investigate further how to adapt it to your situation. Lastly, you could consider using a library such as jQuery which has done quite a bit of work for all of us to make ajax calls work.

---

