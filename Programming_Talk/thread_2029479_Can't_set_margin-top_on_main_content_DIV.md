---
title: "Can't set margin-top on main content DIV"
date: 2012-07-19
forum: Programming Talk
---

### Post by nikonian on 2012-07-19
Hi all :)

I have a page, and it has a floating (fixed) nav bar at the top, which fades to 0.1% opacity when not in use. The nav bar sits at the VERY TOP of the page, but I cannot get the main DIV to have a 50-100px margin between the bottom of the nav bar, and where the main DIV starts; at the moment, the nav bar is ACROSS the main DIV, and not separated by a neat space. Any ideas? I have pasted the code AND attached the source in ZIP:

Thanks

HTML
~~~~

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
	<head>
		<title>Tree</title>
		<link rel="stylesheet" type="text/css" href="./css/style.css"/>
	</head>

	<body id="body">

		<div id="bar"></div>
		<div id="wrapper">
			<div id="main-content">

			</div>

		</div>

	</body>
</html>

```

CSS
~~~

```
* {
	margin: 0;
	padding: 0;
}

#body {
	background: url('../img/page-bg-50-pc.jpg') no-repeat center center fixed;
	-webkit-background-size: cover;
	-moz-background-size: cover;
	-o-background-size: cover;
	background-size: cover;
}

#bar {
	
	width: 100%;
	height: 75px;
	position: fixed;
	/* transition for fading */

	transition: opacity 1.5s ease-in-out;
	-moz-transition: opacity 1.5s ease-in-out;
	-webkit-transition: opacity 1.5s ease-in-out;
	opacity: 0.1;
	border-bottom: 1px solid #a68114;
	-webkit-box-shadow: 0px 0px 15px #333;
	box-shadow: 0px 0px 15px #333;
	/* Safari 4-5, Chrome 1-9 */
	background: -webkit-gradient(linear, 0% 0%, 0% 100%, from(#a68114), to(#40260f));
	/* Safari 5.1, Chrome 10+ */
	background: -webkit-linear-gradient(top, #a68114, #40260f);
	/* Firefox 3.6+ */
	background: -moz-linear-gradient(top, #a68114, #40260f);
	/* IE 10 */
	background: -ms-linear-gradient(top, #a68114, #40260f);
	/* Opera 11.10+ */
	background: -o-linear-gradient(top, #a68114, #40260f);
}

#bar:hover {
	opacity: 1;
	transition: opacity 0.25s ease-in-out;
	-moz-transition: opacity 0.25s ease-in-out;
	-webkit-transition: opacity 0.25s ease-in-out;
}

#wrapper {
	margin: 0 auto;
	width: 750px;
	height: auto;
}

#main-content {
	height: 2000px;
	background-color: #f2e9ce;
	border: 1px solid #a68114;
	-webkit-box-shadow: 0px 0px 25px #333;
	box-shadow: 0px 0px 25px #333;
}

```

---

### Post by trent.josephsen on 2012-07-19
Positioning (absolute or fixed) removes the element from flow, so the #wrapper div is being flowed onto the page as if it were the first element in the body. I believe this means its margin is collapsed with the body's... I don't remember the rules on when that happens.

You might be able to set a padding on the body to offset the #wrapper from the top. Or, alternatively, you might use relative positioning to offset the #wrapper from where it's flowed; then you'd have to account for the possibility of weird things at the bottom of the page.

You could also position the #wrapper using either absolute or fixed positioning, with different consequences -- but those measures may require more drastic changes to your CSS.

I don't really feel like writing example code for any of these possibilities, but hey, you asked for ideas, right? :)

---

### Post by nikonian on 2012-07-19
Thank you :)

[EDIT]

```
#wrapper {
	[COLOR="Blue"]padding-top: 100px;[/COLOR]
	margin: 0 auto;
	width: 750px;
	height: auto;
}
```

Seems to fix it :-) - look:



[http://www.youtube.com/watch?v=LX5iVcGDCAg](http://www.youtube.com/watch?v=LX5iVcGDCAg)

---

