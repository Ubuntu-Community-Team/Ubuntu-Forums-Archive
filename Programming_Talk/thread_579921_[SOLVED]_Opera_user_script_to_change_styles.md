---
title: "[SOLVED] Opera user script to change styles"
date: 2007-10-18
forum: Programming Talk
---

### Post by happysmileman on 2007-10-18
I'm using Opera but thanks to my new KDE theme all text in textareas and input boxes is now blac, and so is the background :(

I've decided a user javascript file should be used to fix this but have no idea how it should work, and don't know much javascript, this is mainly juust some copy-pasted code hacked together. How can I get a script to change all input boxes and textareas to have a white background? Currently I have this
```
document.addEventListener(
	'load',
	function fix()
	{
		var emNodes = document.getElementsByTagName('textarea');
		var max = emNodes.length;
		for(var i = 0;i < max;i++)
		{
			var nodeObj = emNodes.item(i);
			nodeObj.style.backgroundColor = "#ffffff";
		}
	
		var emNodes = document.getElementsByTagName('input');
		var max = emNodes.length;
		for(var i = 0;i < max;i++)
		{
			var nodeObj = emNodes.item(i);
			nodeObj.style.backgroundColor = "#ffffff";
		}
	},
	true
);
```

Never mind, made a couple of stupid mistakes, the code in that box is now working for anyone who's interested

---

