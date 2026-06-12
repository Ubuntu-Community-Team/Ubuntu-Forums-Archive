---
title: "Auto Scale page to fit any browser/resolution css"
date: 2008-04-17
forum: Programming Talk
---

### Post by anfractuosities on 2008-04-17
I am new to advanced html/css. Here is a link to my page.

[http://unsend.atspace.com](http://unsend.atspace.com)

Like my subject said, I would like to make my page scrolless in any browser / res. Is this possible? I don't mind black space surrounding my content.

The page is built using slices. also, How does my code look?

THanks


here is my html code
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">

<head>

<title>USAX</title>

<meta http-equiv="USAX UnSend Mail Art Exchange" content="text/html; charset=iso-8859-1" />

   <link href="css.css" rel="stylesheet" type="text/css" media="all" />



</head>

<body>

<div id="title_">

<a href="index.html"><img id="title" src="images/title.gif" width="1200" height="216" alt="" border=0;/></a>

</div>

<div id="main02_">

<img id="main02" src="images/main02.gif" width="44" height="684" alt="" />

</div>

<div id="members_">

<a href="members.html">

<img id="members" src="images/members.gif" width="243" height="62" border="0" alt="" />

</a></div>

<div id="main04_">

<img id="main04" src="images/main04.gif" width="913" height="121" alt="" />

</div>

<div id="main05_">

<img id="main05" src="images/main05.gif" width="243" height="59" alt="" />

</div>

<div id="main06_">

<img id="main06" src="images/main06.gif" width="146" height="319" alt="" />

</div>

<div id="info_">

         <a href="information.html"><img id="info" src="images/info.gif" width="257" height="36" border="0" alt="" /></a></div>

<div id="main08_">

<img id="main08" src="images/main08.gif" width="753" height="104" alt="" />

</div>

<div id="main09_">

<img id="main09" src="images/main09.gif" width="257" height="68" alt="" />

</div>

<div id="main10_">

<img id="main10" src="images/main10.gif" width="156" height="121" alt="" />

</div>

<div id="collect_">

         <a href="collet.html"><img id="collect" src="images/collect.gif" width="261" height="52" border="0" alt="" /></a></div>

<div id="main12_">

<img id="main12" src="images/main12.gif" width="593" height="459" alt="" />

</div>

<div id="main13_">

<img id="main13" src="images/main13.gif" width="261" height="69" alt="" />

</div>

<div id="main14_">

<img id="main14" src="images/main14.gif" width="77" height="94" alt="" />

</div>

<div id="postman_">

         <a href="post.html"><img id="postman" src="images/postman.gif" width="209" height="48" border="0" alt="" /></a></div>

<div id="main16_">

<img id="main16" src="images/main16.gif" width="131" height="338" alt="" />

</div>

<div id="main17_">

<img id="main17" src="images/main17.gif" width="209" height="46" alt="" />

</div>

<div id="main18_">

<img id="main18" src="images/main18.gif" width="48" height="244" alt="" />

</div>

<div id="future_">

         <a href="future.html"><img id="future" src="images/future.gif" width="195" height="52" border="0" alt="" /></a></div>

<div id="main20_">

<img id="main20" src="images/main20.gif" width="189" height="244" alt="" />

</div>

<div id="main21_">

<img id="main21" src="images/main21.gif" width="195" height="192" alt="" />

</div>

<div id="hungry_">

<img id="hungry" src="images/hungry.gif" width="595" height="738" alt="" />

</div></body>

</html>


```
and here is my css
```


body {

color: #DDD;

font-family: "Courier New", Courier, Monaco, monospace;

background-color: #000;

text-align: left;

font-size: 14pt;

font-weight: 600;

border=0;

}

a:link {

color: white;

text-decoration: none;

}



a:visited {

color: white;

text-decoration: none;

}



a:hover {

color: white;

text-decoration: none;

}



a:active {

color: white;

text-decoration: none;

}



#title_ {

position:absolute;

left:0px;

top:0px;

width:1200px;

height:216px;

}



#main02_ {

position:absolute;

left:0px;

top:216px;

width:44px;

height:684px;

}



#members_ {

position:absolute;

left:44px;

top:216px;

width:243px;

height:62px;

}



#main04_ {

position:absolute;

left:287px;

top:216px;

width:913px;

height:121px;

}



#main05_ {

position:absolute;

left:44px;

top:278px;

width:243px;

height:59px;

}



#main06_ {

position:absolute;

left:44px;

top:337px;

width:146px;

height:319px;

}



#info_ {

position:absolute;

left:190px;

top:337px;

width:257px;

height:36px;

}



#main08_ {

position:absolute;

left:447px;

top:337px;

width:753px;

height:104px;

}



#main09_ {

position:absolute;

left:190px;

top:373px;

width:257px;

height:68px;

}



#main10_ {

position:absolute;

left:190px;

top:441px;

width:156px;

height:121px;

}



#collect_ {

position:absolute;

left:346px;

top:441px;

width:261px;

height:52px;

z-index: 3;

}



#textbox_ {

position:absolute;

left:620px;

top:207px;

width:580px;

height:693px;

z-index: 3;

}



#main12_ {

position:absolute;

left:607px;

top:441px;

width:593px;

height:459px;

}



#main13_ {

position:absolute;

left:346px;

top:493px;

width:261px;

height:69px;

}



#main14_ {

position:absolute;

left:190px;

top:562px;

width:77px;

height:94px;

}



#postman_ {

position:absolute;

left:267px;

top:562px;

width:209px;

height:48px;

}



#main16_ {

position:absolute;

left:476px;

top:562px;

width:131px;

height:338px;

}



#main17_ {

position:absolute;

left:267px;

top:610px;

width:209px;

height:46px;

}



#main18_ {

position:absolute;

left:44px;

top:656px;

width:48px;

height:244px;

}



#future_ {

position:absolute;

left:92px;

top:656px;

width:195px;

height:52px;

}



#main20_ {

position:absolute;

left:287px;

top:656px;

width:189px;

height:244px;

}



#main21_ {

position:absolute;

left:92px;

top:708px;

width:195px;

height:192px;

}



#hungry_ {

position:absolute;

left:482px;

top:162px;

width:595px;

height:738px;

}

```

---

### Post by Can+~ on 2008-04-17
Slices are a terrible practice for websites, use divs instead.

Most pages should be about fluid designs, but if you're building a static page (meaning that there's no dynamic content), you can take certain liberties about the use of div, like using absolute/relative positioning for elements.

Second, the font of the buttons is unreadable, the font that appears when you click them, should be a non-serif font, for readability.

And I'll  [repeat myself](http://ubuntuforums.org/showpost.php?p=4737314&postcount=11) about design (posted on a similar thread before). Before you try to make web design,first look at good design.

---

### Post by mssever on 2008-04-17
> **anfractuosities said:**
> Like my subject said, I would like to make my page scrolless in any browser / res. Is this possible? I don't mind black space surrounding my content.

The page is built using slices. also, How does my code look?
First, you need to use a fluid layout. I haven't read your HTML, but your page is much too wide for my 1024x768 screen. A fluid layout, specified in percentages, is what you want. Also be careful about how you use images. They can easily defeat a fluid layout. Try to put your nav items up against the margin instead of spread all around. It also helps consistently. Remember, all your visitors spend the majority of their time on other sites. So if your site looks significantly different from the rest, they'll end up confused. The key to artistic web design is subtlety, not something new.

Also, the fonts you're using are illegible. And it doesn't help that your background blends with your fonts. Again, most people are impatient. If they can't easily read your site, they'll leave. Any font that isn't easily legible is useless, in my opinion. I don't get why some people design useless fonts.

EDIT: I just noticed that your links are identical to your normal text. That means that most users will never notice your links. Links need to be obviously different. A different color and/or underlined.

---

### Post by anfractuosities on 2008-04-18
Thanks for the input,  I am currently reading the oreilly html/xhmtl guide.  After that its on to CSS.  I have a lot to learn, and I think I figured out how to do what I want to do...

I think this might be what you guys are talking about too.  I can make the background one solid image, and then have divs of the individual images float around on top of it.

Also, as far as the readability of the design goes, I am not attempting to appeal to the masses.  I know Ill prob take smack for this but, The overall ascetic of the page is more important to me than the usability.  It is meant to be accessed by members, who are artists that are familiar with the page, and such.  

As far as the non underlined links go, the only non-image link is an email address.  Most people I know use web based email anyway, so they will just copy the text and paste it in gmail or something.

Thanks for the quick reply...

---

### Post by skybrady on 2008-05-15
Hi everyone

I really want help with this

my website is 100% in HTML

it looks brilliant on 19 inch monitors but pretty bad on smaller


I want to fit it all on one screen so it shrinks to fit.
HLP!

[www.skyscottvideography.com.au](www.skyscottvideography.com.au)

---

### Post by anfractuosities on 2008-05-16
I am almost positive that you must use CSS.  It is pretty easy to learn, it is pretty much putting alot of your html code into a different syntax.  With CSS you can place your elements with % s so that they resize relative to the browser window.  Does that help?

---

### Post by Delever on 2008-05-16
I don't have solution for static page other than using fluid CSS design.

I remember writing some readjusting code for dynamic pages, though.

Basically, after page was loaded, i got window width with Javascript, then checked if current layout is good for that. If not, redirected to another page. Let me find some code:

[PHP]
	<script type="text/javascript">

		// helper functions
		function f_clientWidth() {

			return f_filterResults (

				window.innerWidth ? window.innerWidth : 0,

				document.documentElement ? document.documentElement.clientWidth : 0,

				document.body ? document.body.clientWidth : 0

			);

		}

		function f_clientHeight() {

			return f_filterResults (

				window.innerHeight ? window.innerHeight : 0,

				document.documentElement ? document.documentElement.clientHeight : 0,

				document.body ? document.body.clientHeight : 0

			);

		}

		function f_scrollLeft() {

			return f_filterResults (

				window.pageXOffset ? window.pageXOffset : 0,

				document.documentElement ? document.documentElement.scrollLeft : 0,

				document.body ? document.body.scrollLeft : 0

			);

		}

		function f_scrollTop() {

			return f_filterResults (

				window.pageYOffset ? window.pageYOffset : 0,

				document.documentElement ? document.documentElement.scrollTop : 0,

				document.body ? document.body.scrollTop : 0

			);

		}

		function f_filterResults(n_win, n_docel, n_body) {

			var n_result = n_win ? n_win : 0;

			if (n_docel && (!n_result || (n_result > n_docel)))

				n_result = n_docel;

			return n_body && (!n_result || (n_result > n_body)) ? n_body : n_result;

		}


		
		// get doc width
		var docwidth = f_clientWidth();


		
		// then use some code to check if docwidth is ok
		if (<docwidth is not ok>) {

			window.location = 'other_location.html';
		}

	</script>
[/PHP]

---

