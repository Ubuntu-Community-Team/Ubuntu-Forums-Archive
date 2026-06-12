---
title: "xhtml and svg embedded"
date: 2007-02-03
forum: Programming Talk
---

### Post by MadeR on 2007-02-03
May be I made a mistake, but being an xhtml file a xml file, I really do not understand why the following code does not show a rectangle:

[HTML]
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:svg="http://www.w3.org/2000/svg" xml:lang="it">
	<head>
		<link rel="stylesheet" type="text/css" media="screen" href="styles.css" />
		<script type="text/javascript" src="commands.js"></script>
		<title>Pagina di prova</title>
	</head>
	<body>
		<svg:svg width="300" height="100" version="1.1" >
			<svg:rect x="50" y="50" rx="10" ry="10" width="300" height="200" style="fill:white;stroke:black;stroke-width:10" />
		</svg:svg>
		<fieldset>
			<legend>aa</legend>
			bb
		</fieldset>
	</body>
</html>
[/HTML]

can anybody help me?

thanks

---

### Post by WW on 2007-02-03
I tried this with firefox.  The rectangle is shown if the file name extension is .xhtml or .xml.  If the extension is .html, the rectangle does not appear.

By the way, your rectangle is too big, so you will actually only get part of the rectangle.  Try changing the svg:rect line to this, for example:
```
<svg:rect x="50" y="50" rx="10" ry="10" width="200" height="40" style="fill:white;stroke:black;stroke-width:10" />
```

---

