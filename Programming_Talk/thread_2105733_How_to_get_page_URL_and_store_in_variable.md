---
title: "How to get page URL and store in variable"
date: 2013-01-16
forum: Programming Talk
---

### Post by temporos on 2013-01-16
I like to think I'm decent with JavaScript.  That said, the Google's APIs for Chrome extensions are **awful!**  They're less helpful than chewing sand in a dentist office.

My first extension is a page action, and it's supposed to appear when the active tab navigates to a certain domain.  When the user clicks the page action's icon, a popup is supposed to appear which shows the URL of the tab (useless, I know, but it's for learning purposes).

I can get the page action to show up (and not show up) when it's supposed to.  I **can't** get the popup to show the tab's URL.  Can someone please point out the flaw in my code and why it's wrong?

**manifest.json**
```

{
	"manifest_version": 2,

	"name": "SFC Helper",
	"version": "0.1",
	"description": "This extension searches for debris in surrounding systems.",

	"background": {"scripts": ["background.js"]},
	"page_action": {
		"default_icon": "SFClogo19.png",
		"default_title": "Find resources.",
		"default_popup": "SFChelper.html"
	},
	"permissions": [
		"tabs",
		"http://playstarfleet.com/"
	],
	"icons": {
		"38": "SFClogo38.png",
		"128": "SFClogo128.png"
	}
}
```

**SFChelper.html** (popup)
```

<!doctype html>
<html>

<head>
<style type="text/css">
	body {
		background: #999999;
		color: #FF0000;
	}
</style>
</head>

<body>
<div id="test">Something here.</div>
<script src="SFChelper.js"></script>
</body>

</html>
```

**SFChelper.js**
```

chrome.tabs.getSelected(null, function(tab) {var address = tab.url});
document.getElementById("test").innerHTML=address;
```

The output in the popup says "Something here." like the script is being ignored (Chrome doesn't allow screenshots while extension popups are open).

---

### Post by temporos on 2013-01-18
*bump*  Anyone?  I still cant find a solution to this.

---

