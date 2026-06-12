---
title: "Text area problem"
date: 2009-06-01
forum: Programming Talk
---

### Post by Squigy Dunkens on 2009-06-01
wow, haven't asked an html question in a long time. I thought i had that down. anyway, here is the code for a form

```
<html>

<head>

<title>Contact</title>
<link rel = "stylesheet" type = "text/css" href = "cstyle.css"/>

<script type="text/javascript">
        var GB_ROOT_DIR = "http://placelandia.com/graybox/";
    </script>

    <script type="text/javascript" src="http://placelandia.com/graybox/AJS.js"></script>
    <script type="text/javascript" src="http://placelandia.com/graybox/AJS_fx.js"></script>

    <script type="text/javascript" src="http://placelandia.com/graybox/gb_scripts.js"></script>
    <link href="http://placelandia.com/graybox/gb_styles.css" rel="stylesheet" type="text/css" media="all" />
</head>

<body>

Use the contact form below to send me an email
<form action="contactsend.py">

<br />
Name: 
<input type="text" name="name"/><br />

<br />

Email: 
<input type="text" name="email"/><br />

<br />
Message: 
<textarea name="comment" rows="5" cols="40" />
<br />
<input type="submit" value="Send"/>

</form>
</body>

</html>

```

the problem is that the submit button won't show. The syntax highlighting, if viewed in firefox, stops after the textarea, so i assume i did something wrong with the text area. but i just can't figure it out.

---

### Post by Tibuda on 2009-06-01
```
<textarea name="comment" rows="5" cols="40"></textarea>
```

See [http://www.w3.org/TR/html401/interact/forms.html#h-17.7](http://www.w3.org/TR/html401/interact/forms.html#h-17.7)

---

### Post by Squigy Dunkens on 2009-06-01
It worked, thanx!

---

