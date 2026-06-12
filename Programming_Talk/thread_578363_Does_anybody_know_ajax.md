---
title: "Does anybody know ajax?"
date: 2007-10-17
forum: Programming Talk
---

### Post by Druke on 2007-10-17
hmm ajax is not a language, its a method of web programming using JavaScript and css techniques. I personally bought a book on it from Apress "Beginning Ajax with PHP", though was kind of a waste of money, frst few chapters where all I needed, but where very good... so maybe not a waste...

as for sites [http://www.w3schools.com/ajax/default.asp](http://www.w3schools.com/ajax/default.asp)

---

### Post by pmasiar on 2007-10-17
AJAX is new name for technology available for quite a some time (since javascript in browsers).
[http://en.wikipedia.org/wiki/Ajax_%28programming%29](http://en.wikipedia.org/wiki/Ajax_%28programming%29)

---

### Post by Druke on 2007-10-17
weird the original post is gone...

---

### Post by #Reistlehr- on 2007-10-17
It's a nice little technique. Server Side wise, it's sloppy, i think, but it's nice with the visuals it provides.

The best bet is to check out to Scripta.****.us site, for their release of the prototype framework, and their scripts.

It's nice, cause you can say add this to Update.php:
```
if($_POST['Category'] == 'Edit')
{
	while(list($Field, $Value) = each($_POST))
	{
		if($Field != 'Edit'  && $Field != 'ID')
		{
			$A = $_POST[$Field];
			
			mysql_query('UPDATE '.$dbPrefix.'cats SET '. $Field .' = \''. $A .'\' WHERE ID = \''. $_POST['ID'] .'\'');
		}
	}
	echo $A;
}
else if($_REQUEST['Edit'] == 'Remove')
{
	mysql_query('DELETE FROM '. $dbPrefix.'subcats WHERE ID = \''.$_REQUEST['ID'].'\'');
}

```

and in your HTML do something like:

```

<div id="Sub{subcat.ID}" style="display:inline; " class="EditSSC">{subcat.Name}</div> - Remove [<a href="#" onClick="new Ajax.Request('Update.php?Edit=Remove&ID={subcat.ID}&', {method:'post', postBody:escape('C=1')}), new Effect.Highlight({subcat.Name}), new Effect.Fade({subcat.Name})" >x</a>]
	new Ajax.InPlaceEditor('Sub{subcat.ID}', 'Update.php', {callback: function(form, value) { return 'Category=EditSub&ID={subcat.ID}&Name=' + escape(value) }})

```

You have a nice little javascript call to the PHP file to make changes without having to refresh the page.

Comes in handy sometimes, i only do it when the client cares more about looks than performance.

---

### Post by reckless2k2 on 2007-10-17
i use that all the time around the house. good stuff.

---

### Post by KCPokes on 2007-10-17
> **#Reistlehr- said:**
> Comes in handy sometimes, i only do it when the client cares more about looks than performance.

I agree for the most part, but truthfully Ajax comes in handy when creating more of a dynamic experience for the user.  For example, I developed a real estate web site in which we used Ajax for the search.  This allowed the user to select specific features at which time an event is trigger to pull back only those results that match the criteria, allowing them to continue to drill down until they get a manageable number of matches to browse through.  More instant gradification for the user then performing a search only to find there are a hundred matches to wade through; knowing instantly that you matched a hundred allows them to tweak their criteria to narrow the selection without even submitting the search.  

I would second the use of the Prototype framework.  It simplifies the implementation by providing you a useable framework right out of the box.

---

### Post by #Reistlehr- on 2007-10-17
This very true. There are MILLIONS of tutorials online for free, so i would personally bypass the purchase of a book, and rely more on my fellow programmers abroad.

---

### Post by kokenge on 2007-10-17
I wrote a javascript routine that you can include in your code. It will do most of the stuff you want. Go here: ajax.andbest.info
You can download it from there.
It has examples.

HTH.
Have a great day..

---

