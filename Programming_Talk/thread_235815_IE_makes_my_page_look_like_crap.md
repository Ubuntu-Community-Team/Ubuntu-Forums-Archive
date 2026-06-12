---
title: "IE makes my page look like crap"
date: 2006-08-13
forum: Programming Talk
---

### Post by aysiu on 2006-08-13
My wife is having a little problem coding a page for a church. Here she is: [quote=aysiu's wife]
help please.
I have a page with an expanding menu using an external javascript file that looks fine in all the other major browsers, but IE just sucks. I can't get it to work well with it, and although the javascript file has some hacks to deal with the IE-suckiness, I don't know enough about javascript to finagle it to work. 

Any javascript gurus out there?

this is the page: [http://www.missionbaycc.org/test/](http://www.missionbaycc.org/test/)

the links should all behave like the home button.
And the sub menus should have white backgrounds with underlines are rollovers. 

The dhtml script goes as such: ```

/* structural styles and offsets */
ul.expanding, ul.expanding li, ul.expanding ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
 
}

ul.expanding {
    position: relative;
    left:-8px;
    cursor: default;
    width: 135px;
    margin-top:35px;
}

ul.expanding li {
    position: relative;
    text-align: left;
    cursor: pointer;
    cursor: hand;
    width: 135px;
    margin: -1px 0 0 0;
    margin-top:5px;
}

ul.expanding ul {
    cursor: default;
    width: 140px;
    padding: 2px 0;
    position: absolute;
    left: -2000px;
}

ul.expanding ul li {
    width: 140px;
    
}


/* design styles */
ul.expanding a:link, ul.expanding a:visited {
    display: block;
    cursor: pointer;
    cursor: hand;
    background: white;
    border: 1px solid #1073a1;
    padding: 5px 0px;
    font-size: 8pt;
    font-family:"Helvetica", "Arial", "san-serif";
    font-weight: bold;
    letter-spacing: 1px;    
    color: #005263;
    text-decoration: none;
    text-indent:10px;
}

ul.expanding ul li a:link, ul.expanding ul li a:visited {
	display:block;
	background:white;
	border: none;
	cursor:pointer;
	cursor:hand;
	font-size:8pt;
	font-family:"georgia", "garamond", "serif"; 
	text-decoration: none;
	text-indent:12px;
	padding: 2px 0px;
	color:black;
	font-weight:normal;
	letter-spacing:0px;
}


/* main links */
ul.expanding a:hover, ul.expanding a:focus, ul.expanding a:active, 
ul.expanding a.rollover:link, ul.expanding a.rollover:visited {
  font-color: black;
  background: #a5de94;    
}
/* sublinks */
ul.expanding ul li a:hover, ul.expanding ul li a:focus, ul.expanding ul li a:active, 
ul.expanding ul li a.rollover:link, ul.expanding ul li a.rollover:visited {
  font-color: #1073a1;
  text-decoration: underline;   
}


/* submenu indicator arrows */

/* this is the color of the main link box but not the home button*/
ul.expanding li.hasmenu > a:link, ul.expanding li.hasmenu > a:visited {
    background: url(down-green.gif) white no-repeat 95% 50%;
}

/*this is the box hover color*/
ul.expanding li.hasmenu > a:hover, 
ul.expanding li.hasmenu > a:focus, 
ul.expanding li.hasmenu > a:active, 
ul.expanding li.hasmenu > a.rollover:link, 
ul.expanding li.hasmenu > a.rollover:visited {
    background: url(down-red.gif) #a5de94 no-repeat 95% 50%;
}

* html ul.expanding li.hasmenu a:link,
* html ul.expanding li.hasmenu a:visited {
    background: expression(/hasmenu/.test(this.parentNode.className) 
        ? "url(down-green.gif) #c6eff7 no-repeat 95% 50%" : "#c6eff7");
}

* html ul.expanding li.hasmenu a:hover, 
* html ul.expanding li.hasmenu a:active, 
* html ul.expanding li.hasmenu a.rollover:link, 
* html ul.expanding li.hasmenu a.rollover:visited {
    background: expression(/hasmenu/.test(this.parentNode.className) 
        ? "url(down-red.gif) #a5de94 no-repeat 95% 50%" : "#a5de94");
       
}

/* browser hacks */
@media screen, projection {
    * html ul.expanding li {
        display: inline; 
        f\loat: left; 
        background: #fff; 
    }
}
```


Please advise as IE is driving me nutso.
thanks [/quote] I've attached a couple of screenshots. The first is in Internet Explorer. The second is in Firefox. Any help you can give her would be much appreciated. Thanks!

---

### Post by yaaarrrgg on 2006-08-14
This doesn't look like a javascript problem as much as a css problem.  

My guess: 

You have nested <ul> tags.  The internal <ul> tag appears to be inheriting the css styles of the parent <ul>.  I think you'll need to specify another class for the internal <ul> and set the background to white.

---

### Post by huggy77 on 2006-08-14
ie is just flakey...  

check out:
[http://www.zipcss.com/](http://www.zipcss.com/)

nice framework for setting up your css but - download there files and check out some of the css hacks to include... They will help make you getting some IE/Firefox consistency....

---

### Post by aysiu on 2006-08-14
yaaarrrg and huggy77, thanks for the suggestions. I'll pass them on to my wife.

---

### Post by xtacocorex on 2006-08-15
Not so much a coding issue, but you have "About us" and then "Contact Us." The capitalization of 'Us' is different between the two.

I think yaaarrrg is on the right path with the nested lists.

Tell her that the site looks really nice.

---

### Post by aysiu on 2006-08-15
Thanks for the note about the capitalization difference. I'll pass that on to her.

The weird thing about the nested lists is that they work fine on every other major browser--Firefox, Opera, Safari--the child list not inheriting the colors of the parent list.

There's even a section of her CSS code that I believe is supposed to specifically address IE. Well, I've passed along the info to her.

---

