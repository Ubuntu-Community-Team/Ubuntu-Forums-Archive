---
title: "AJAX innerHTML scrolling problem..."
date: 2009-07-16
forum: Programming Talk
---

### Post by gradysghost on 2009-07-16
Ladies and gentlemen who are bound to be smarter than me, I have encountered a problem that I have so far been unable to surmount.  Here's a basic description.  Code to come.

I'm developing a web app that's supposed to be like a chat room, similar in design to IRC, but via a webpage instead of an external client, and using AJAX in lieu of the actual IRC protocol.  I've got a <div> whose ID is "allchat" that is set up with no content at the initial page load.  Through user entry, it begins to populate.  I do this using document.getElementById("allchat").innerHTML and adding content to the HTML.  That works beautifully.

The problem is that if I scroll to see something that runs off the right or bottom of that <div>, the next time the JavaScript updates its contents, the <div> scrolls back to the top left.  I don't want this.

I've found several pages on the net saying that adding a "return false;" to the event handler call will resolve this.  It doesn't, but that's because the event handler is not responding to user interaction.  I'm using setTimeout to check for updates to the chat log every so often (right now 500 ms, but longer or shorter depending on what I'm testing).

I have been able to reduce this problem by only updating innerHTML when there's actually something to update it with, but the problem is not 100% gone, and I'd like it to be.  Anybody have any ideas?  Code to follow:

This is my main collection of JS functions.
```
<script type="text/javascript"><!--
function getHttpObject() {
	if (window.ActiveXObject) { return new ActiveXObject("Microsoft.XMLHTTP"); }
	else if (window.XMLHttpRequest) { return new XMLHttpRequest(); }
	else {
		alert("Your browser does not support AJAX.  Get something from this century.  I recommend Firefox.");
		return null;
	}
}

function handleUpdate() {
	if (updater.readyState==4) {
		var stop=updater.responseText.indexOf('!');
		var since=updater.responseText.substring(0,stop);
		var display=updater.responseText.substring(stop+1,updater.responseText.length);
		document.getElementById("since").value = since;
		if (display.length > 0) {
			document.getElementById("allchat").innerHTML=display+document.getElementById("allchat").innerHTML;
		}
	}
}

function sendMessage(evt) {
	if (evt.keyCode == 13) {
		sender = getHttpObject();
		if (sender != null) {
			sender.open("GET", "chatexe.php?action=post&msg="+document.getElementById("in").value+"&cid="+document.getElementById("chatid").value, true);
			sender.send(null);
			sender.onreadystatechange=confOfDelivery;
			document.getElementById("in").value="";
		}
	}
}

function confOfDelivery() {
	if (sender.readyState==4) {
		document.getElementById("allchat").innerHTML += sender.responseText;
	}
}


function updateMessages() {
	updater = getHttpObject();
	var url = "chatexe.php?action=update&cid="+document.getElementById("chatid").value+"&since="+document.getElementById("since").value;
	updater.open("GET", url, true);
	updater.send(null);
	updater.onreadystatechange=handleUpdate;
	setTimeout("updateMessages();", 500);
}

var sender=null;
var updater=null;
var d=null;
var toMessage=null;
var toMembers=null;

--></script>
```

And this is the relevant bit of HTML.  The last script here loads AFTER the above script and after the HTML.  It's designed to simply kick off the updates, which then self-replicate.  The PHP is there to set the ID and last received message.  Don't worry, that data is echoing just fine.

```
<?php
echo "<input type=\"hidden\" name=\"chatid\" id=\"chatid\" value=\"".$_GET['id']."\">";
echo "<input type=\"hidden\" name=\"since\" id=\"since\" value=\"".$since['MessageID']."\">";
?>

<div class="allchat"><span id="allchat"></span></div>
<div class="members"></div>

<div id="chatin" class="chatin">
<input type="text" id="in" class="textin" onkeyup="sendMessage(event);return false;">
</div>

<script type="text/javascript">
updateMessages();
</script>
```

I really appreciate any help you guys could give me on this.  I've Googled until I just can't Google no more.  I'm mad as hell and I'm not going to take it anymore.  I'm boldly going where...  Well, you get the idea.

---

### Post by Raccoon&#9789; on 2009-07-16
Don't use innerHTML, just appendChild, it's so much faster and much less load on the browser.

See my AJAX chat, it supports all the basic goodies such as campsites aka rooms, shows you when who's been on, scrolls down automatically, very small server load, etc (even icons lol).

[http://queatz.com/campfire/](http://queatz.com/campfire/)

Feel free to grab any code you find useful in there.

---

