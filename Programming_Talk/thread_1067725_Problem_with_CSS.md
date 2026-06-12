---
title: "Problem with CSS"
date: 2009-02-12
forum: Programming Talk
---

### Post by sheffrem on 2009-02-12
Hi, all of you.
I'm working on a school project  about a web site, and most of the student are using basic html table to to the work. Since we where not taught enough of css, i decided to go that way. Due to lack of idea i downloaded a wordpress theme that i really like here is the link 
[http://wpthemes.amazing-christmas-ideas.com/vc/](http://wpthemes.amazing-christmas-ideas.com/vc/)

I deleted the php file since my site wont use php. Now i just want to replicate the same with simple html but got stuck with the css.
I understand the css perfectly, but how to make use of the class and id's in the index.html that i'm creating, here is the content of the css.
Note that i wont use the search and other things. Please i dont ask to do my project but just need some help being a novice.
Thanks in advance.

/*  
Theme Name: Vermilion Christmas
Theme URI: [http://wpthemes.amazing-christmas-ideas.com/vc/](http://wpthemes.amazing-christmas-ideas.com/vc/)
Description: Vermilion Christmas is a holiday theme with a vivid red and green color scheme. The header graphic depicts a wintertime forest of white Christmas trees with a subtle image of Santa Claus and his reindeer flying over the snowy treetops in the distance on Christmas Eve. You can even make out the faint glow of Rudolf's nose! The design is SE-friendly with clean title tags and content put before navigation. Visit the <a href="http://wpthemes.amazing-christmas-ideas.com/vc/">Vermilion Christmas blog</a> for support.
Version: 2.0
Author: Amazing Christmas Ideas
Author URI: [http://www.amazing-christmas-ideas.com/](http://www.amazing-christmas-ideas.com/)
Tags: christmas, holiday, red, green, two columns, fixed width, widgets

		Copyright (c) Amazing-Christmas-Ideas.com. Some rights reserved.
			This WordPress theme is licensed under a Creative Commons 
			Attribution-ShareAlike 2.5 License. You may use it and modify
			it as you see fit, provided that the credit and hyperlink in
			the footer.php file remain intact and unaltered in any version
			of this template you create.

*/

body {
	font-family: Verdana, Arial, Helvetica, sans-serif;
	font-size: 14px;
	background-color: #467839;
	color: #343434;
	margin: 0px 0px 50px;
}

#page {
	background-image: url(images/page-background.gif);
	background-repeat: repeat-y;
	background-position: center;
	margin: 0px auto 0px auto;
}

#page2 {
	width: 770px;
	margin: 0px auto 0px auto;
	padding: 0px;
	float: none;
	position: relative;
}

#wide-page {
	width: 770px;
	margin: 0px auto 0px auto;
	background-image: url(images/page-background-alt.gif);
}


/* ---- BEGIN GLOBAL ELEMENTS ---- */

h1, h2, h3, h4, h5, h6 {
	font-family: Georgia, Times New Roman, Times, serif;
}

h1 {
	color: #FFFFFF;
	font-size: 24px;
	margin-bottom: 0px;
	padding-bottom: 0px;
	line-height: normal;
}

h2 {
	color: #477400;
	font-size: 20px;
}

h3 {
	color: #477400;
	font-size: 18px;
}

h4 {
	color: #638000;
	font-size: 16px;
}

h5 {
	color: #638000;
	font-size: 16px;
}

h6 {
	color: #638000;
	font-size: 16px;
}

a {
	color: #990000;
}

a:visited {
	color: #343434;
}

a:hover {
	color: #FF0000;
}

a:active {
	color: #FF0000;
}

blockquote {
	font-family: Georgia, "Times New Roman", Times, serif;
	font-size:16px;
	font-style: italic;
	color:#5E5E5E;
	margin: 0px 30px 0px 30px;
}

blockquote blockquote {
	margin: 0px 30px 0px 30px;
}

img {
	border: 0px none;
}

img.left {
	float: left;
	margin-right: 20px;
	margin-left: 0px;
}

img.right {
	float: right;
	margin-right: 0px;
	margin-left: 20px;
}

img.center {
	clear: both;
	text-align: center;
}

small {
	font-size: 80%;
}

/* ---- END GLOBAL ELEMENTS ---- */


/* ---- BEGIN HEADER STYLES ----*/

#header {
	background-image: url(images/header.jpg);
	background-color: #467839;
	background-repeat: no-repeat;
	background-position: center top;
	height: 137px;
	position: relative;
}

#header-title {
	padding-top: 50px;
	color: #FFFFFF;
	padding-left: 100px;
	margin: 0px auto;
	position: relative;
	padding-right: 150px;
	width: 510px;
}

#header-title h1 {
	margin-top: 0px;
	margin-bottom: 0px;
	line-height: 31px;
	font-weight: normal;
	font-variant: small-caps;
	font-size: 30px;
}

#header-title a:link {
	color: #FFFFFF;
}

#header-title a:visited {
	color: #FFFFFF;
}

#header-title a:hover {
	color: #FFFFFF;
}

#header-title a:active {
	color: #FFFFFF;
}

#header-title p {
	margin-top: 4px;
	margin-bottom: 0px;
	color: #FFFFFF;
	font-size: 12px;
	line-height: 13px;
}

/* ---- END HEADER STYLES ----*/


/* ---- BEGIN CONTENT STYLES ---- */

#content {
	width: 543px;
	background-image: url(images/content-background.gif);
	background-repeat: no-repeat;
	background-position: right top;
	position: relative;
	padding-top: 25px;
	float: right;
	padding-right: 20px;
	padding-left: 20px;
	margin: 0px;
	padding-bottom: 15px;
}

#wide-content {
	padding: 40px;
	width: 690px;
	background-image: url(images/content-background.gif);
	background-repeat: no-repeat;
	background-position: right top;
}

h2.post-title {
	margin-top: 0px;
	padding-right: 50px;
	margin-bottom: 0px;
}

h3.post-title {
	margin-top: 0px;
	padding-right: 50px;
	margin-bottom: 0px;
}

h2.archive-title {
	margin-top: 0px;
	padding-right: 50px;
	margin-bottom: 30px;
	font-size: 24px;
}

h2.page-title {
	margin-top: 0px;
}

h2.search-title {
	margin-top: 0px;
	padding-right: 50px;
	margin-bottom: 30px;
	font-size: 24px;
}

.post {
	background-image: url(images/post-background.gif);
	background-repeat: no-repeat;
	background-position: center bottom;
	padding-bottom: 35px;
	margin-bottom: 40px;
	clear: both;
}

.post-single {
	background-image: url(images/post-background.gif);
	background-repeat: no-repeat;
	background-position: center bottom;
	padding-bottom: 40px;
	margin-bottom: 0px;
	clear: both;
}

.entry {
	line-height: 1.4em;
}

.postmetadata {
	font-size: 12px;
	margin-bottom: 0px;
	clear: both;
	border-top-width: 3px;
	border-top-style: double;
	border-top-color: #EBEBEB;
	padding-top: 5px;
}

.commentlink {
	background-image: url(images/comment-bubble.gif);
	background-repeat: no-repeat;
	background-position: left center;
	padding-left: 20px;
}

.trackback {
	background-image: url(images/trackback.gif);
	background-repeat: no-repeat;
	background-position: left center;
	padding-left: 20px;
}

.edit {
	text-align: center;
	margin-top: 12px;
}

.edit a {
	text-decoration: none;
}

.navigation-single {
	margin-top: 10px;
	margin-bottom: 20px;
	font-size:12px;
	line-height: 1.4em;
}

.next-single {
	background-image: url(images/arrow-next.gif);
	background-repeat: no-repeat;
	background-position: left center;
	padding-left: 12px;
}

.previous-single {
	background-image: url(images/arrow-previous.gif);
	background-repeat: no-repeat;
	background-position: left center;
	padding-left: 12px;
}

#content ul li {
	list-style-type: none;
	list-style-image: url(images/bullet-red.gif);
}

#content ul {
	margin-left: 0px;
	padding-left: 40px;
}

#content ul ul li {
	list-style-type: none;
	list-style-image: url(images/bullet-red-child.gif);
}

#content ul ul ul li {
	list-style-type: none;
	list-style-image: url(images/bullet-red-square.gif);
}

#content li {
	margin-bottom: 14px;
}

#content li li {
	margin-top: 10px;
	padding-bottom: 0px;
	line-height: normal;
}

.navigation {
	font-size: 18px;
	margin-bottom: 0px;
	text-align: center;
	margin-top: 0px;
	padding-top: 10px;
	padding-bottom: 20px;
	padding-right: 25px;
	font-family: Georgia, "Times New Roman", Times, serif;
}

.navigation a {
	text-decoration: none;
}

.next {
	background-image: url(images/arrow-next.gif);
	background-repeat: no-repeat;
	background-position: right center;
	padding-right: 12px;
}

.previous {
	background-image: url(images/arrow-previous.gif);
	background-repeat: no-repeat;
	background-position: left center;
	padding-left: 12px;
}

.alignright {
	text-align: right;
}

.alignleft {
	text-align: left;
	padding-top: 20px;
	padding-right: 20px;
	padding-bottom: 0px;
	padding-left: 0px;
}

#intro {
	margin-bottom: 30px;
	padding-bottom: 31px;
	background-image: url(images/post-background.gif);
	background-repeat: no-repeat;
	background-position: center bottom;
	border: none;
}

#intro h2 {
	margin-top: 0px;
	padding-right: 30px;
	font-size: 32px;
	font-weight: normal;
	font-variant: small-caps;
}

.attachment {
	text-align: center;
}

.attachment img {
	padding: 5px;
	border: 1px solid #A1A973;
}

.justify {
	text-align: justify;
}

/* ---- END CONTENT STYLES ----*/


/* ---- BEGIN SIDEBAR STYLES ----*/

#sidebar {
	background-image: url(images/main-menu.gif);
	position: relative;
	background-repeat: no-repeat;
	background-position: right top;
	width: 165px;
	padding-top: 43px;
	font-size: 12px;
	color: #343434;
	float: left;
	clear: left;
	padding-right: 11px;
	padding-left: 11px;
}

#sidebar ul li h3 {
	font-size: 14px;
	font-variant: small-caps;
	margin-bottom: 0px;
	margin-top: 0px;
}

#sidebar ul li h2 {
	font-size: 14px;
	font-variant: small-caps;
	margin-bottom: 0px;
	margin-top: 0px;
}

#sidebar ul {
	list-style-type: none;
	margin-left: 0px;
	padding-left: 0px;
	margin-top: 0px;
}

#sidebar li li {
	padding-top: 1px;
	padding-bottom: 1px;
	list-style-image: url(images/bullet-green.gif);
	margin-left: 15px;
}

#sidebar a {
	color: #990000;
	text-decoration: none;
	font-weight: bold;
}

#sidebar a:visited {
	color: #343434;
	text-decoration: none;
}

#sidebar a:hover {
	color: #FF0000;
	text-decoration: underline;
}

#sidebar a:active {
	color: #FF0000;
	text-decoration: none;
}

#sidebar li li li {
	padding-top: 1px;
	font-size: 92%;
	list-style-image: url(images/bullet-green-child.gif);
	margin-left: 15px;
}

#sidebar li li li li {
	padding-top: 1px;
	font-size: 92%;
	list-style-image: url(images/bullet-green-square.gif);
	margin-left: 15px;
}

#feeds ul li {
	margin-left: 0px;
	list-style-type: none;
	list-style-image: none;
}

#feeds ul li a {
	background-image: url(images/feed-icon-12x12.gif);
	background-repeat: no-repeat;
	background-position: left top;
	padding-left: 20px;
}

#feeds ul li a:visited {}

#feeds ul li a:hover {
	background-repeat: no-repeat;
	background-position: left center;
	color: #E85F11;
}

#feeds ul li a:active{}

.space {
	margin-bottom: 16px;
	background-image: url(images/sidebar-underline.gif);
	background-repeat: no-repeat;
	background-position: left top;
	margin-top: 0px;
	padding-top: 2px;
}

#wp-calendar {
}

#wp-calendar caption {
	text-align: left;
	font-size: 14px;
	font-variant: small-caps;
	background-image: url(images/sidebar-underline.gif);
	background-repeat: no-repeat;
	background-position: left bottom;
	font-weight: bold;
	color: #477400;
	font-family: Georgia, "Times New Roman", Times, serif;
	margin: 0px 0px 2px;
}

#wp-calendar th {
	background-color: #D1D5BC;
	padding: 1px;
	border: 1px solid #A7AA94;
}

#wp-calendar td {
	border: 1px solid #CCCCCC;
	padding: 1px;
	text-align: center;
}

#wp-calendar a {
	display: block;
}

#wp-calendar a:hover{
	background-color: #FFFFFF;
	text-decoration: none;
}

td#prev a {
	text-align: left;
	padding-left: 2px;
}

td#next a {
	text-align: right;
	padding-right: 2px;
}

.widget {
	margin-top: 0px;
	margin-bottom: 15px;
}

.linkcat h2 {font: bold small-caps 11px Georgia, "Times New Roman", Times, serif !important;}

#content .linkcat h2 {
	font: bold 14px Georgia, "Times New Roman", Times, serif !important;
	margin: 35px 0 15px 0;
}

/* ---- END SIDEBAR STYLES ----*/


/* ---- BEGIN FOOTER STYLES ---- */

#footer {
	background-image: url(images/footer-background.jpg);
	background-repeat: no-repeat;
	background-position: center bottom;
	clear: both;
	visibility: visible;
	height: 140px;
	padding-top: 12px;
	font-size: 12px;
	margin-top: 0px;
	margin-right: auto;
	margin-left: auto;
}

#footer-wrap {
	width: 770px;
	margin-top: 0px;
	margin-right: auto;
	margin-left: auto;
}

#footer-right {
	width: 543px;
	padding-right: 20px;
	padding-bottom: 80px;
	padding-left: 20px;
	background-image: url(images/footer-divider.gif);
	background-repeat: no-repeat;
	background-position: 20px 0px;
	padding-top: 10px;
	margin-top: 0px;
	margin-bottom: 0px;
	position: relative;
	margin-left: auto;
}

#footer-right ul {
	margin-left: 0px;
	padding-left: 0px;
}

#footer-right li {
	list-style-type: none;
	display: inline;
	padding-right: 12px;
}

#footer-left {
	width: 165px;
	float: left;
	padding-right: 11px;
	padding-left: 11px;
	padding-bottom: 40px;
}

#footer-meta {
	color:#585858;
	clear: both;
	margin: 0px;
	padding-bottom: 10px;
}

#footer-meta a {
	color: #585858;
}

#footer-meta ul {
	margin: 0px;
}

#footer-meta li {
	list-style-type: none;
	display: inline;
	margin: 0px;
	padding-right: 5px;
	font-size: 10px;
	text-align: right;
}

/* ---- END FOOTER STYLES ----*/


/* ---- BEGIN SEARCH FORM STYLES ---- */

#searchform {
	padding: 0px;
	text-align: left;
	line-height: normal;
	font-size: 14px;
	margin: 0px;
}

#s {
	width: 115px;
	padding: 2px;
	background-color: #F5F6EC;
	font-size: 12px;
	font-family: Verdana, Arial, Helvetica, sans-serif;
	margin: 0px;
	vertical-align: top;
	color: #343434;
	border-top: 1px solid #799029;
	border-right: 1px solid #799029;
	border-bottom: 1px solid #799029;
	border-left: 1px solid #799029;
}
	
#searchform input {
	margin: 3px 0px 0px;
}

#searchsubmit {
	font-family: Verdana, Arial, Helvetica, sans-serif;
	color: #FFFFFF;
	font-size: 12px;
	font-weight: bolder;
	vertical-align: middle;
	background-color: #A7B176;
	width: 30px;
	border: 1px solid #638000;
	padding-top: 1px;
	padding-bottom: 1px;
}

/* ---- END SEARCH FORM STYLES ----*/


/* ---- BEGIN COMMMENT FORM STYLES ---- */

#commentform {}

#commentform p {
	margin-top: 0px;
	margin-bottom: 5px;
}

#author, #email, #url  {
	width: 200px;
	padding: 2px;
	margin-top: 0px;
	margin-bottom: 0px;
	font-family: Verdana, Arial, Helvetica, sans-serif;
	font-size: 12px;
	color: #343434;
	border-top-width: 1px;
	border-right-width: 1px;
	border-bottom-width: 1px;
	border-left-width: 1px;
	border-top-style: solid;
	border-right-style: solid;
	border-bottom-style: solid;
	border-left-style: solid;
	border-top-color: #666666;
	border-right-color: #CCCCCC;
	border-bottom-color: #CCCCCC;
	border-left-color: #666666;
}

#comment {
	width: 98%;
	padding: 2px;
	font-family: Verdana, Arial, Helvetica, sans-serif;
	font-size: 14px;
	line-height: normal;
	color: #343434;
	border-top-width: 1px;
	border-right-width: 1px;
	border-bottom-width: 1px;
	border-left-width: 1px;
	border-top-style: solid;
	border-right-style: solid;
	border-bottom-style: solid;
	border-left-style: solid;
	border-top-color: #666666;
	border-right-color: #CCCCCC;
	border-bottom-color: #CCCCCC;
	border-left-color: #666666;
}

#submit {
	padding: 4px;
	background: url(images/submit-background.gif) repeat-x bottom;
	width: 12em;
	border-top: 3px double #B7C781;
	border-right: 3px double #758346;
	border-bottom: 3px double #758346;
	border-left: 3px double #B7C781;
	font: bold 14px Georgia, "Times New Roman", Times, serif;
	cursor: pointer;
	color: #758346;
}

/* ---- END COMMENT FORM STYLES ----*/


/* ---- BEGIN COMMENTS STYLES ---- */

h3#comments {
	margin-top: 0px;
	padding-top: 5px;
}

h3#respond {
	margin-top: 0px;
	padding-top: 5px;
}

.commentfeed {
	background-image: url(images/feed-icon-12x12.gif);
	background-repeat: no-repeat;
	background-position: left center;
	padding-left: 16px;
	margin-bottom: 0px;
	float: right;
	padding-bottom: 1px;
}

ol.commentlist {
	list-style-type: none;
	margin-left: 0px;
	padding-left: 0px;
	clear: both;
}

ol.commentlist cite {
	font-style: normal;
	font-weight: bold;
}

.comment-body {
	margin: 0 0 10px 0;
	padding: 15px 15px 10px 15px;
	background: #FAFBF2;
	border: 1px solid #F0F1E8;
	position: relative;
}

.comment-body p {
}

.commentmetadata {
}

.comment-author {
}

.comment-count {
	font-family: Georgia, "Times New Roman", Times, serif;
	float: right;
	text-align: right;
	font-size: 20px;
	color: #C7CCAF;
	font-weight: bold;
	padding: 0px 6px;
	background: #FFFFFF;
	border: 1px solid #f0f0e0;
	position: relative;
	top: 0px;
	right: 0px;
}

.alt {
}

/* ---- END COMMENTS STYLES ----*/

---

### Post by Nevon on 2009-02-12
*I just feel like posting a huge facepalm...*

The html was embedded in the php-files. You essentially threw away the structure of the site. Also, weren't you supposed to make the site yourself? In that case, you should make the site yourself instead of using someone elses code. Using it for inspiration is fine, I guess. But what you're doing is essentially cheating.

---

### Post by sheffrem on 2009-02-12
> **Nevon said:**
> *I just feel like posting a huge facepalm...*

The html was embedded in the php-files. You essentially threw away the structure of the site. Also, weren't you supposed to make the site yourself? In that case, you should make the site yourself instead of using someone elses code. Using it for inspiration is fine, I guess. But what you're doing is essentially cheating.


Im not cheating that is why i deleted the php file,and i can do it with html table, but for knowledge sake i want to do it in css and html 
I just want the formatting and the style. Here is how i want it to look like. [www.koonimo.tk](www.koonimo.tk)

---

### Post by Nevon on 2009-02-12
> **sheffrem said:**
> Im not cheating that is why i deleted the php file,and i can do it with html table, but for knowledge sake i want to do it in css and html 
I just want the formatting and the style. Here is how i want it to look like. [www.koonimo.tk](www.koonimo.tk)

And like I said, the html structure was embedded in the php files. It would be quite difficult to rebuild the site with only the css to look at for reference. Not undoable, but hard. Still, I don't see what it is you're asking. You have the css, and you say you want to write the html on your own - so just do it.

---

### Post by sheffrem on 2009-02-12
i just dont know how to insert the id and class's inside html.pls help

---

### Post by Nevon on 2009-02-12
> **sheffrem said:**
> i just dont know how to insert the id and class's inside html.pls help

Well that depends on what element it is you want to apply the class to. For example, a div would be <div id="id" class="class"></div>.

---

### Post by stevescripts on 2009-02-12
Duh ... have you looked at/worked through the w3 schools CSS tutorial?

[http://www.w3schools.com/css/default.asp](http://www.w3schools.com/css/default.asp)

Steve

---

### Post by tturrisi on 2009-02-12
Gee wiz, just navigate to a site that uses the theme you like and view the source code of the page.  Yes, php spits out the html, but you can SEE the html in the page's source code.  Element ids and classes are visible as well.

---

### Post by kavon89 on 2009-02-12
> **Nevon said:**
> *I just feel like posting a huge facepalm...*

[IMG]http://i43.tinypic.com/314y22w.jpg[/IMG]

---

