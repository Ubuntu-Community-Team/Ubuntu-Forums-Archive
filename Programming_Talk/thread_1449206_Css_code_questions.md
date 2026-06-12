---
title: "Css code questions"
date: 2010-04-07
forum: Programming Talk
---

### Post by aloprot on 2010-04-07
Greetingz, I'm trying to get myself familiarized with CSS and I thought the best way I can do that is to actually read code and try to modify this and that to see how it works. As I did that I stumbled into some unknown lines and I need clarification as I don't understand them. I will post the css code to see what I'm talking about. The code that I don't understand is highlited in red. Thank you!
```
body { background-color:#E0E0E0;
	 }

#menu {  position:relative;
			vertical-align:middle;
			background-color:#000000;
			color:#FFFFFF;
			margin-left:5%;
			margin-right:5%;
			margin-top:2%;
			margin-bottom:1%;
			height:2.5em;
			width:90%;
			padding-bottom:1%;
			border-width:thin;
			border-color:black;
			border-style:solid;	
			font-size:x-large;
			overflow:visible;}

#menu ul{
			margin-top: 0.8em;
			overflow:visible;
			}

#menu ul li{
			display: inline;
			margin-left:2%;
			margin-right:2%;
			}
			
#menu a:link{
			color: white;
			font-family: sans-serif;
			font-size:x-large;
			text-decoration:none;
			}
#menu a:visited{
			color:white;
			font-family: sans-serif;
			font-size:x-large;
			text-decoration:none;
			}
#menu a:hover{
			text-decoration:underline;
			}
			
.menuleft{
	position:fixed;
	background-color:#E0E0E0;
	float:left;
	margin-left:5%;
	margin-right:3%;
	margin-top:3%;
	padding:0em;
	width:15%;
	display:inline;
	overflow:visible;
	}

	
.menuleft a{
	display:block;
	background-color:white;
	color:black;
	text-decoration:none;
	padding:5px 10px;
	margin:0 0 6px;
	overflow:visible;
	}

.menuleft a:hover{
	background-color:black;
	color:white;
	text-decoration:none;
	}

#text{	
			position:absolute;
			text-align:left;
			background-color:#FFFFFF;
			color:#000000;
			margin-left:23%;
			margin-right:5%;
			margin-top:3%;
			margin-bottom:3%;
			width:60%;
			border-color:black;
			border-style:solid;
			padding-bottom:2%;
			padding-left:5%;
			padding-right:5%;
			padding-top:2%;
			padding-bottom:2%;
			font-family:sans-serif;
			float:right;
		}
		
#text a:link{
			color:black;
			text-decoration:underline;
			font-style:italic;
			}
#text a:visited{
			font-style:italic;
			color:black;
			text-decoration:underline;
			}
#text a:hover{
			color:#C9C9C9;
			text-decoration:underline;
			}
			
#text h2{
			margin-left:-3%;
			}
			
#text h3{
			margin-left:-3%;
			margin-top: 6%;
			}
			


#text li{
	margin-top:0.5em;
}	
.menuleft a.link-active{
	border-style:thin;
	border-width:1px;
	}

[COLOR=Red].menuleft a.link-level2{[/COLOR][COLOR=Black](i don't understand what's level2?)[/COLOR]
	margin-left:8%;
	}
	
[COLOR=Red].menuleft a.link-level2-active{[/COLOR]
	margin-left:8%;
	border-style:solid;
	border-width:1px;
	}
[COLOR=Red]
a.uploaded{[/COLOR][COLOR=Black](??uploaded? this hasn't been defined in html code!)[/COLOR]
	text-decoration:none;
	color:#E31F1F;
	}

```
I just found a simple html and css website on the internet and I'm trying to study it. If you want the link to the website to get the full code please tell me. I don't want to put it here to get it advertised or something, which is not what I intend anyway. 
Thank you!

---

### Post by new_tolinux on 2010-04-07
[COLOR=Black]> (??uploaded? this hasn't been defined in html code!)It can be a default CSS-script, with another page (using the same CSS-script) using those statements.
 I actually use 1 CSS-script for all pages of 1 site, I guess it's obvious that I don't use all the defined things on every page.
[/COLOR]

---

### Post by Fougner on 2010-04-07
The code you don't understand is css selectors.

When you write something like a.something, it means that every a-tag (anchor, hyperlinks) with the class something, is selected. For example:

<a class="menu">Link</a> is selected by a.menu {color: #555} and results in a dark grey color on all anchors with class "menu".

Hope this clear things up! Good luck!

Also, by using only the .something selector, means it's independent of tags, so all tags with class "something" is selected.

---

### Post by Ravenshade on 2010-04-08
Level 2 - Just happens to be the name the programmer chose. 

Uploaded - This is likely to be defined somewhere, perhaps not on the page that you saw, but somewhere else. The advantage of CSS is that is can be referenced externally. So another page will likely have the reference. If not, it's useless code and it really doesn't matter. Create a reference for it?

---

### Post by tturrisi on 2010-04-09
level2 likely is intended for sub menus. Click a menu title and the menu appears, mouseover a menu item and a level2 menu appears IF there's code on the page to have sub menus.

study here:
[http://www.w3schools.com/css/default.asp](http://www.w3schools.com/css/default.asp)

---

