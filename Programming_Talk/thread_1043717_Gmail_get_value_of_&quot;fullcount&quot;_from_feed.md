---
title: "Gmail: get value of &quot;fullcount&quot; from feed"
date: 2009-01-18
forum: Programming Talk
---

### Post by dbbolton on 2009-01-18
I am creating a custom homepage for my web browser (a local html file). It's mostly just links to web pages that I visit frequently, but I want to find out whether it's possible to put the number of unread messages in my Gmail inbox somewhere on the page.

I tried (unsuccessfully) using javascript to parse the feed file, located at [http://mail.google.com/mail/feed/atom](http://mail.google.com/mail/feed/atom) and containing the following:

```

<?xml version="1.0" encoding="UTF-8"?>
<feed version="0.3" xmlns="http://purl.org/atom/ns#">
<title>Gmail - Inbox for account name</title>
<tagline>New messages in your Gmail Inbox</tagline>
<fullcount>0</fullcount>
<link rel="alternate" href="http://mail.google.com/mail" type="text/html" />
<modified>time</modified>
</feed>

```Obviously the number I want is in the fullcount element. Does anyone know how to do this?

---

### Post by myrtle1908 on 2009-01-18
If you've got that XML as a string then it would be simple to use a regex like:-

[PHP]var s = '<?xml version="1.0" encoding="UTF-8"?><feed version="0.3" xmlns="http://purl.org/atom/ns#"><title>Gmail - Inbox for account name</title><tagline>New messages in your Gmail Inbox</tagline><fullcount>0</fullcount><link rel="alternate" href="http://mail.google.com/mail" type="text/html" /><modified>time</modified></feed>';
if (s.match(/.*?<fullcount>(\d+)<\/fullcount>/)) {
	alert(RegExp.$1);
}[/PHP]

---

### Post by dbbolton on 2009-01-18
> **myrtle1908 said:**
> If you've got that XML as a string then it would be simple to use a regex like:-

[php]var s = '<?xml version="1.0" encoding="UTF-8"?><feed version="0.3" xmlns="http://purl.org/atom/ns#"><title>Gmail - Inbox for account name</title><tagline>New messages in your Gmail Inbox</tagline><fullcount>0</fullcount><link rel="alternate" href="http://mail.google.com/mail" type="text/html" /><modified>time</modified></feed>';
if (s.match(/.*?<fullcount>(\d+)<\/fullcount>/)) {
    alert(RegExp.$1);
}[/php]
I think the problem is actually getting the data. I tried some methods on W3Schools' TryIt Editor and got this error message: "Access to restricted URI denied". Here is an example:

```

<html>
<head>
<script type="text/javascript" src="loadxmldoc.js"></script>
</head>
<body>
<script type="text/javascript">

xmlDoc=loadXMLDoc("http://mail.google.com/mail/feed/atom");

document.write(xmlDoc.getElementsByTagName("fullcount")[0].childNodes[0].nodeValue);

document.write("<br />");

</script>
</body>
</html>

```

---

### Post by DocForbin on 2009-01-18
There are probably ways around it, but in general, I believe remote (cross domain) scripting isn't allowed in javascript for security reasons.

Do you have a local web server installed? This would be easy in, say, PHP.

---

### Post by dbbolton on 2009-01-18
> **DocForbin said:**
> There are probably ways around it, but in general, I believe remote (cross domain) scripting isn't allowed in javascript for security reasons.

Do you have a local web server installed? This would be easy in, say, PHP.
I don't atm, but I suppose I could set one up. How could you do it in php?

---

### Post by DocForbin on 2009-01-18
> **dbbolton said:**
> I don't atm, but I suppose I could set one up. How could you do it in php?

Something like this:

<?php
$xmlString = file_get_contents("https://USERNAME:PASSWORD@mail.google.com/mail/feed/atom");
$xml = new SimpleXMLElement($xmlString);
echo 'Unread Mail: ' . $xml-> fullcount;
?>

---

