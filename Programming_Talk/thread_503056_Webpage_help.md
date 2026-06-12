---
title: "Webpage help"
date: 2007-07-17
forum: Programming Talk
---

### Post by ebp on 2007-07-17
I want to move the "News" box from here:

[IMG]http://farm2.static.flickr.com/1370/838563762_e78eeeedd0.jpg[/IMG]

To here:

[IMG]http://farm2.static.flickr.com/1420/838887194_8dca836022.jpg[/IMG]


Index:

```
<html>

	<head>
		<link rel="stylesheet" type="text/css" href="style/style.css">

		<title>leetmachine's</title>
	</head>

	<body>
	
		<div id="boks1">

		<img src="/pictures/banner.jpg" />

			<div id="menu">

			<p><h2>Menu</h2></p>

			<p><a href="../1.htm">1</a></p>
			
			<p><a href="../2.htm">2</a></p>

			<p><a href="../3.htm">4</a></p>

			<p><a href="../4.htm">5</a></p>

			<p><a href="../5.htm">6</a></p>
		
			</div>

			<div id="boks2">
		
			<h1>News</h1>

			<p><i>22/6-07 12:23</i></p>
		
			<p>Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla Bla</p>

			<p><i>~leetmachine</i></p>

			<hr width="98%" color="black" style="margin-bottom:60;">
	
			</div>	

		</div>
		
	</body>

</html>
```

Stylesheet:

```
body {
	background-color: #f0f0f0;		
}

a:hover {
	color: orange;
	font-style: italic;
}

#menu {
	position:relative;
	top:1px;
	left:20px;
	width:159px;
	border-style: dashed;
}

#boks2 {
	position:relative;
	top:1px;
	left:300px;
	width:500px;
	border-style: dashed;
}

#boks1 {
	position:absolute;
	top:120px;
	left:100px;
	border-style: solid;
	background-color: #ffffff;
}

```

---

### Post by LaRoza on 2007-07-17
I can't tell what you want, could you edit the screen shot and circle the problem area?

---

### Post by ebp on 2007-07-17
> **LaRoza said:**
> I can't tell what you want, could you edit the screen shot and circle the problem area?

I've added one more picture to make my post more understanable.

---

### Post by LaRoza on 2007-07-17
> **ebp said:**
> 

```
body {
	background-color: #f0f0f0;		
}

a:hover {
	color: orange;
	font-style: italic;
}

#menu {
	position:relative;
	top:1px;
	left:20px;
	width:159px;
	border-style: dashed;
}

#boks2 {
	position:relative;
	top:1px;
	left:300px;
	width:500px;
	border-style: dashed;
}

#boks1 {
	position:absolute;
	top:120px;
	left:100px;
	border-style: solid;
	background-color: #ffffff;
}

```

#boks1 is at 100% width, make it more narrow and the other div, #boks2, will move right up.

---

### Post by ebp on 2007-07-17
I still can't get it to work, could to post the code with the changes?

---

### Post by LaRoza on 2007-07-17
Hold on, I am caught between two posters, JavaScript on one side and CSS on the other, I'll get right back, I haven't tested it yet.

-EDIT What are the dimensions of the image? width and height.

---

### Post by ebp on 2007-07-17
The dimensions of the picture is: 1024x200

---

### Post by LaRoza on 2007-07-17
Let me know how this style sheet works, I don't have the dimensions of the image, so it might work differently for you.

```

body {
	background-color: #f0f0f0;		
}

a:hover {
	color: orange;
	font-style: italic;
}

#menu {
	position:relative;
	top:1px;
	left:20px;
	width:159px;
	border-style: dashed;
}

#boks2 {
	position:relative;
	top:-229px;
	left:300px;
	width:500px;
	border-style: dashed;
}

#boks1 {
	position:absolute;
	top:120px;
	left:100px;
	border-style: solid;
	background-color: #ffffff;
}
```

It looks like what you wanted on my machine with Opera 9.10.

---

### Post by ebp on 2007-07-17
i use opera 9.21

---

### Post by LaRoza on 2007-07-17
> **ebp said:**
> i use opera 9.21

It shouldn't matter, did it work?

---

### Post by ebp on 2007-07-17
> **LaRoza said:**
> It shouldn't matter, did it work?

no

---

### Post by LaRoza on 2007-07-17
What happened?

---

### Post by ebp on 2007-07-18
I changed the width of "boks1" to 80%, the only thing that happened was that some of the border of "boks1" dissaperaed.

[IMG]http://farm2.static.flickr.com/1234/845112138_ea063f479f.jpg[/IMG] 

Here you can see what i've changed:

```
body {
	background-color: #f0f0f0;		
}

a:hover {
	color: orange;
	font-style: italic;
}

#menu {
	position:relative;
	top:1px;
	left:20px;
	width:159px;
	border-style: dashed;
}

#boks2 {
	position:relative;
	top:1px;
	left:300px;
	width:500px;
	border-style: dashed;
}

#boks1 {
	position:absolute;
	top:120px;
	left:100px;
	width:80%;
	border-style: solid;
	background-color: #ffffff;
}

```

---

