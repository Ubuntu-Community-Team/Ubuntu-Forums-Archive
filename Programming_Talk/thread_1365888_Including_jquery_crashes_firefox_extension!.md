---
title: "Including jquery crashes firefox extension!"
date: 2009-12-27
forum: Programming Talk
---

### Post by daemon3 on 2009-12-27
I was writing an extension the wrong way.  I started out by writing a preferences window with the <window> type.  After doing some research, I found I had to use the <prefwindow> type.  The scripts already worked perfectly for the <window> type (including jquery).  However, upon rewriting the xul file, when I include jquery, NOTHING renders in the window.  Here's a vague example about what's going on:
```

<?xml version="1.0"?>
<?xml-stylesheet href="chrome://global/skin/" type="text/css"?>
<prefwindow id="covenantfox-prefs" xmlns="http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul" width="400" height="600">
	[COLOR="Red"]<script src="jquery-1.3.2.js" />[/COLOR]
	<script src="./otherscript.js" />
	<script>
		jQuery.noConflict();
	</script>
	<prefpane> ....
	</prefpane>
</prefwindow>

```
That highlighted script tag is the problem.  If I include it, the prefwindow doesn't render its children.  If I exclude the line, the prefwindow is just fine (except for the fact that the otherscripts.js functions don't work since they depend on jquery).

Any ideas?  Thanks.  I'm getting really frustrated.

---

