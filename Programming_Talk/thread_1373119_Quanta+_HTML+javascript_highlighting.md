---
title: "Quanta+ HTML+javascript highlighting?"
date: 2010-01-05
forum: Programming Talk
---

### Post by barisurum on 2010-01-05
Hello my problem is;

When I create a new html file quanta+ highlights the html code but does nothing to javascript code. 

Highlight setting is Markup/XML everytime I create a file. 

When I change it to Markup/HTML it highlights javascript coreectly. My default doctype is xhtml 1.1 How can I make quanta+ to highlight javascript by default? Thank you.

---

### Post by Hellkeepa on 2010-01-05
HELLo!

Just guessing here, since you haven't given us any example code, but try to use CDATA comments for your JS.

Happy codin'!

---

### Post by barisurum on 2010-01-07
```
<html>

<head><meta/>
	<title>Validating an email entry with JS</title>

	<script type="text/javascript">
		
<![CDATA[
	function validate_email()
	{
	}
]]>
	</script>
</head>
</html>
```

I did as you suggested but highlighting doesn't change. It changes when I do tools -> highlighting -> markup -> HTML. Do I have to make the doctype HTML instead of XHTML?

edit: Maybe it is better to use an external js file for the code in XHTML?

---

### Post by Hellkeepa on 2010-01-07
HELLo!

Well, can't help you on this one then, sounds like you need to take it up with the developers of Quanta.
That being said, it is always preferred to use a dedicated JS file for your JavaScript needs. Allows the browsers and proxies to cache it, as well as making it much easier to maintain. ;-)

Happy codin'!

---

### Post by barisurum on 2010-01-07
Thanks, happy codin' to you too :)

---

