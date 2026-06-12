---
title: "[SOLVED] javascript code only runs if I put an alert() before it....huh?"
date: 2008-09-25
forum: Programming Talk
---

### Post by lucas4ce on 2008-09-25
As the title suggests really.

I have the following javascript function which only completes, by which I mean continues to the end of the script and fills up the html table, if I put an alert() where I've shown below.  Without the alert() in this location the function appears to stop just before the alert() position, i.e. it successfully clears the html table and appears to simply stop after the for(b=3;b<d;b++) loop.

This is just weird!  And slightly annoying, any help would be really appreciated..

```
function createdesigntable() // calls the creation of the results selection table
	{
		
		// copy inputdata into designinputdata and send to server for calculation

		//document.cookie = 'name=' + sessionobject.designinputdata[0];	
		//sessionobject.designinputdata = sessionobject.inputdata;
		senddatatoserver(serialise(sessionobject.inputdata));
		
		// clear the existing table except headers
		var b;
		var c = document.getElementById('designtablesteel');
		var d = c.rows.length;
		for(b=3;b<d;b++)
		{
			c.deleteRow(3);
		}
		**//the alert() goes here!!!**
		var t = steelsections.name.length;
		var s = t+3;
		var v; // row index
		var e; // cell index
		var w;
		var u; //array index
		var y;
		var str="designtablesteelrow";
		// column or cell index
		for(v=3;v<s;v++)
		{	
				w = c.insertRow(v);	
				x = c.rows[v];
				u=v-3;
				rowid=str+u;
				x.id = rowid;
				document.getElementById(rowid).onclick =  function() {designtablesteelrowpress(this.id)};
				w.insertCell(0).innerHTML=steelsections.name[u];	
				w.insertCell(1).innerHTML=steelsections.mass[u];	
				w.insertCell(2).innerHTML=steelsections.depth[u];
				w.insertCell(3).innerHTML=steelsections.breadth[u];
				w.insertCell(4).innerHTML=steelsections.deflection[u];
				w.insertCell(5).innerHTML=steelsections.urdef[u];
				w.insertCell(6).innerHTML=steelsections.urbend[u];
				w.insertCell(7).innerHTML=steelsections.urshear[u];
				for(e=0;e<8;e++)
				{
					z = x.cells[e];
					z.className = "designtablecell";
				}
		}	
		fillresults();    
	}
```

---

### Post by henchman on 2008-09-25
well i could imagine that 'steelsections', whatever it is, does not yet exist in the DOM... are you executing the script after the page has already been loaded (eg. window.onload=createdesigntable)?

try using the Error Console of Firefox (Tools->Error Console). Clean it once to remove the old error messages, refresh your page and it will tell you what's wrong :)

---

### Post by Reiger on 2008-09-26
Indeed, I think this is your problem: the timing of script execution is not right. You should probably know that JavaScript evaluation is of the 'look ahead' type: the script already runs when it is still being evaluated (and while the *page* itself is still being evaluated). Now that is why it is recommended to dump all references to scripts in the <head></head> section of your page, as it will cause the JavaScript to be fully evaluated before you (usually) can call a function (event handlers), and hence avoid silly 'undefined' errors.

Now the alert(); call has 2 effects: (1) it pops up the message box (so far, so good);.but (2) it halts the thread the JavaScript is using! However the browser's *other* threads will still continue to go on (HTML rendering...). So it may be one of those cases that you would benefit from a more elegant halting method, which is to only execute this (part of the) script when the document has been fully loaded; hence window.onload=....

---

### Post by lucas4ce on 2008-09-26
Ideal thank you guys, to give a little more information that may help, the senddatatoserver function activates an Http request to the web server, which then reponds by sending back a list of strings and numbers which are entered into the javascript steelsections array.

With the alert in place, and the OK button clicked, the html table fills up perfectly with items from the steelsections array, so I think the code to do this is kind of right. (Just noticed that whilst this works in IE with the alert() call, it doesn't work in Google Chrome, even with the alert(), that adds more confusion yeah?:confused:).  Haven't tried firefox yet, I'll do that tonight.

This creatdesignbtable function occurs when a button is clicked on the page, and the http request follows as above.  Doing it this way my page doesn't have to reload to receive the new table information, so I'm guessing the 'window.onload=' suggestions may not work for me?  Or am I mixing this up with the <body> onload event?

This function, and many others are in a php script page which is referenced in the <head><head/> section of the webpage.

I feel as if a stopandstartagain() function to replace the alert() would be handy here.

Any further help very gratefully received.:)

---

### Post by DrMega on 2008-09-26
Put all your functions in the <head> section to make sure they have been downloaded in their entirity before anything calls them.

If your page is rendered with php, use output buffering to make sure the page is fully prepared before the download begins.

---

### Post by lucas4ce on 2008-09-26
Thanks for everyone's interest and help!!

Right, after putting a lot of alerts around my code to try and find the problem I noticed that the javascript was indeed attempting to fill up the html table before the xmlHttp.readyState had completed (or become 4).

So it would, I noticed, fill up the table with the previously received http response information, and then update the new array information once the readyState had finally changed.  Clearly this was the wrong order of things.

Quickly googling the problem I, possibly luckily, found a bloke who had the same problem.  To solve it someone told him to put the code that fills up the table in the stateChanged() function of the ajax http request, ensuring that the table is only filled, or refilled, once new information is available.

Seems a very simple solution, ok little embarrased now but hey it works a treat so I'm happy.

Thanks again!  I'm sure I'll be back for the next problem!!:)

---

