---
title: "Linking CSS - IE under Ubuntu"
date: 2006-07-29
forum: Programming Talk
---

### Post by Burgresso on 2006-07-29
My IE seems allergic to my linked CSS sheets. Of course, fire/swift fox finds them fine, but IE does not.

connecting like this works with the foxes:
<link rel="stylesheet" type="text/css" href="css.css" />
<link rel="stylesheet" type="text/css" href="/css.css" />

same story using @import, too.

Unfortunatly, I can't get IE to see these links to the css.

Here is the directory structure:

var/www/cms/thissite/homedirectory

the "homedirectory" is where the PHP and CSS files live.

While I'm at it, are there any path ("path" as in "../link.php") strategies that work well in developing php/html/css that you have had success with developing under linux?

gracias

burgresso

---

### Post by Loffe_ on 2006-07-29
Are you sure IE can't find them.

Maybe there is any errors in the css?

Firefox can parse correct, but IE refuses and skip the whole file.

Try comment out the styles leaveing only the first intact. Then look if IE can find the file...

/Loffe

---

### Post by Burgresso on 2006-07-29
Thanks for the response, Loffe_

The CSS only has one specification which changes the font. IT's pretty basic and is simple for testing purposes.

And check this out: 

> 
[FONT="Courier New"]<head>
	<title>Title</title>
	<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" 
	<link type="text/css" href="" />
	<style rel="stylesheet"  type="text/css">
		body {
			font-family: arial;
		}
	</style>
</head>[/FONT]


IE won't parse the in-document CSS without the fake "<link type="text/css" href="" />" statement before it!

---

### Post by Loffe_ on 2006-07-29
You have missed a '/>' in the meta-tag the row before the css-link ;) .

Try put it back there and it should render well.

---

### Post by Burgresso on 2006-07-29
#-o :oops: 

Oh my gosh...

I hope this thread falls into oblivion soon ;) ....

Thanks Loffe_!

---

### Post by Loffe_ on 2006-07-29
You're welcome...

---

### Post by ifokkema on 2006-07-29
> **Burgresso said:**
>  <style rel="stylesheet" type="text/css">
Just a note: a STYLE tag does not have a 'rel' attribute. Just the type should do fine.

---

