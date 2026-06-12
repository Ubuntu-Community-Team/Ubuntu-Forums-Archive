---
title: "Flash &amp; CSS Menus in Firefox screwed up!"
date: 2007-06-01
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-06-01
Hi

I have the age old problem with css menus not displying over the top of flash animations.

I tried the IFRAME shim trick and this worked for IE but not FIrefox. I also tried the wmode=tranparent thing too but that makes no difference either as well as using the opaque setting instead.

Is anyone else having this problem? does anyone have any solutions of alternatives?

Mike

---

### Post by tturrisi on 2007-06-01
Does z-index work if use w3c compliant flash code?
<div style="z-index:1000;">menu here</div>
<div style="z-index:0;"><object type="application/x-shockwave-flash" data="xxx.swf" width="xxx" height="xxx">
<param name="movie" value="xxx.swf"><a href="http://www.adobe.com" target="_new"><img src="make-own-img-called-noflash.gif" width="xxx" height="xxx" alt="xxx"></a>
</object></div>

---

### Post by Mickeysofine1972 on 2007-06-04
sorry nope it doesnt :(

I have tried this on a few different versions of firefox too and get the same results on different machines.

Mike

---

### Post by nitro_n2o on 2007-06-04
did you try:```
 overflow: hidden
``` for the flash div ?

---

### Post by Mickeysofine1972 on 2007-06-04
> **nitro_n2o said:**
> did you try:```
 overflow: hidden
``` for the flash div ?

hmmm tried it but no cigar :-S

Mike

EDIT: Grrr I fixed that problem but now it wont work in IE! it turns out to be crap java that I didn't write myself! anyone have a decent script that will work on both?

---

### Post by tturrisi on 2007-06-04
post the page url

---

### Post by Mickeysofine1972 on 2007-06-04
sorry I cant it only on my internal dev server atm :-(

I've been using the chrome css menu system as I dont do Java myself and really dont have time to learn it right now.

Mike

---

### Post by tturrisi on 2007-06-04
> **Mickeysofine1972 said:**
> sorry I cant it only on my internal dev server atm :-(

I've been using the chrome css menu system as I dont do Java myself and really dont have time to learn it right now.

Mike
gee wiz, then copy+paste the source code!

---

### Post by rock freak on 2007-06-04
pop the css and html source up and ill have alook!  had a simlar problem in IE but never with firefox! have you validated your code?? check everthing is trim and proper?

---

### Post by Mickeysofine1972 on 2007-06-05
> **rock freak said:**
> pop the css and html source up and ill have alook!  had a simlar problem in IE but never with firefox! have you validated your code?? check everthing is trim and proper?

ok here goes:

the flashplayer:

[PHP]
<div class="flashcontent" >


<object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" codebase="http://fpdownload.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=7,0,0,0" width="500" height="300" id="320x240" align="middle">
<PARAM NAME=allowFlashAutoInstall VALUE=true>
<param name=Flashvars value="url=<?=$url?>">
<param name="allowScriptAccess" value="sameDomain" />
<param name="movie" value="320x240.swf" />
<param name="quality" value="high" />
<param name="wmode" value="transparent" />

<param name=menu value="false"> 
<embed src="320x240.swf" swLiveConnect="true" Flashvars="url=<?=$url?>"  wmode="transparent" quality="high" width="500" height="300" name="320x240" align="right" allowScriptAccess="sameDomain" type="application/x-shockwave-flash" pluginspage="http://www.macromedia.com/go/getflashplayer" ></embed>
</object>
</div>

[/PHP]

the CSS (not validated and very mess atm):

```

/* hide from ie on mac */
html {
height: 100%;
overflow: hidden;
}

#flashcontent {
    height: 100%;
	margin-top:15px; 
	
	z-index: 1;
}
/* end hide */



body {
	font:11px arial,helvetica,sans-serif; 
	background: url(../../images/background.png) no-repeat;
}


.margin_top_none {
	margin-top:0;
}

/* Fix IE Win \*/
* html a { height: 1px; }
/* End Fix */

.alert {
	background: #fff6bf url(../../images/information.png) center no-repeat;
	background-position: 15px 50%; /* x-pos y-pos */
	text-align: left;
	padding: 5px 20px 5px 45px;
	border-top: 2px solid #ffd324;
	border-bottom: 2px solid #ffd324;
	width: 60%;
	}

.info {
	background: #fff6bf url(../../images/information.png) center no-repeat;
	background-position: 15px 50%; /* x-pos y-pos */
	text-align: left;
	padding: 5px 20px 5px 45px;
	border-top: 2px solid #ffd324;
	border-bottom: 2px solid #ffd324;
	margin-top:15px;
	width: 60%;
	}

.success {
	background: #fff6bf url(../../images/tick.png) center no-repeat;
	background-position: 15px 50%; /* x-pos y-pos */
	text-align: left;
	padding: 5px 20px 5px 45px;
	border-top: 2px solid #ffd324;
	border-bottom: 2px solid #ffd324;
	width: 60%;
	}


table {
	font:11px arial,helvetica,sans-serif; 
}

input.send-btn {
width: 60px;
height: 25px;
background: #333 url(../../images/btn-send.png) no-repeat;
outline: none;
}
input.send-btn:hover {
background: #666 url(../../images/btn-send.png) no-repeat 0 -25px;
}

input.reg-btn {
width: 60px;
height: 25px;
background: #333 url(../../images/btn-reg.png) no-repeat;
outline: none;
}
input.reg-btn:hover {
background: #666 url(../../images/btn-reg.png) no-repeat 0 -25px;
}

#Title {
	position: relative;
	height:90px;
	
	float: left;
	
	padding-top: 0.3em;
	padding-left: 8px;
	font-size: 32px;
	color: white;
	background-color: transparent;
	margin-right:0;
}


#Title h3 {
	font:32px arial,helvetica,sans-serif; 
	color: white;
	
}

#Title img {
	
	float: right;
}

#Title_img {
	position: relative;
	width: 9%;
	float: right;
	
	margin-left:0;
}

#Navigation {
	position: relative;
	/* top:46px;
	left: 0px; */
	height: 46px;
}

#Page {
	position: absolute;
	background-image: url(../../images/background.png);
	top:0px;
	left:0px;
	width: 100%;
	height:100%;
}

#Header {
	position: relative;
	width: 100%;
	height:90px;
	background-image: url('../../images/title-background.png');
	background-repeat: repeat-x;
	z-index:10;
}

#Content {
	position: relative;
	text-align: center;
	float: left;
	width:50%; 
	height: 100%;
	z-index:2;
	margin-top:0;
	padding-left: 10px;
	padding-right: 10px;
}

#Info {
	position: relative;
	float: left;
	clear: both;
	width: 20%; 
	
	margin-top:15px;
	margin-left:1em;
	margin-right:1em;
	background-color:transparent;
	border:1px solid #CCCCCC;
	padding-left:1em;
	padding-right:1em;
	color:grey;
	
}

#Footer {

}

#Categories	{
	position: relative;
	float: left;
	width: 15%;
	border:1px solid #CCCCCC;
	padding: 10px;
	margin-top:15px;
}

#Categories	ul {
	padding: 0;
	list-style: none;
}

#Categories	a {
	text-decoration: none;
	
}

/* ================================= MENU SYSTEM ================================ */


.menustyle{


width: 99%;

	position: absolute;
	top: 39px;
	left:0;
	width:100%;
	z-index:1000;
	/*font-weight: bold;
*/

}



.menustyle:after{ /*Add margin between menu and rest of content in Firefox*/

content: "."; 

display: block; 

height: 0; 

clear: both; 

visibility: hidden;
z-index:1000;

}



.menustyle ul{

/* border: 1px solid #BBB;*/
width: 100%;

/* background: url(chromebg.gif) center center repeat-x;*/ /*THEME CHANGE HERE*/

padding: 4px 0;

margin: 0;

text-align: center; /*set value to "left", "center", or "right"*/
z-index:1000;

}



.menustyle ul li{

display: inline;

z-index:1000;
}



.menustyle ul li a{

color: white; /*#494949;
*/
padding: 4px 7px;

margin: 0;

float:left;
text-decoration: none;

/*border-right: 1px solid #DADADA;*/
z-index:1000;

}



.menustyle ul li a:hover{

/*background: url(chromebg-over.gif) center center repeat-x;*/ /*THEME CHANGE HERE*/

	color: #fb9600;
	z-index:1000;
}



.menustyle ul li a[rel]:after{ /*HTML to indicate drop down link*/

/*content: " v";
*/
/*content: " " url(downimage.gif); /*uncomment this line to use an image instead*/
z-index:1000;

}





/* ######### Style for Drop Down Menu ######### */



.dropmenudiv{

position:absolute;

top: 0;

/*border: 1px solid #BBB;*/ /*THEME CHANGE HERE*/

/*border-bottom-width: 0;*/
/*font:normal 12px Verdana;
*/
line-height:18px;

z-index:1000;

background-color: white;

width: 140px;

visibility: hidden;


filter: progid:DXImageTransform.Microsoft.Shadow(color=#CACACA,direction=135,strength=4); /*Add Shadow in IE. Remove if desired*/

}





.dropmenudiv a{

width: auto;

display: block;

text-indent: 8px;
z-index:1000;

/*border-bottom: 1px solid #BBB;*/ /*THEME CHANGE HERE*/

padding: 2px 0;

text-decoration: none;

/*font-weight: bold;
*/
color: black;

background-color: #dbdbdc;
}



* html .dropmenudiv a{ /*IE only hack*/

width: 100%;
z-index:1000;

}



.dropmenudiv a:hover{ /*THEME CHANGE HERE*/

/* background-color: #F0F0F0;
*/
z-index:1000;
background-color: #dbdbdc;
color: #fb9600;
}
/* ================================= MENU SYSTEM END ================================ */
/* End CSS Popout Menu */

```

and the JS:

```

//Chrome Drop Down Menu v2.01- Author: Dynamic Drive (http://www.dynamicdrive.com)

//Last updated: November 14th 06- added iframe shim technique



var cssdropdown={

disappeardelay: 250, //set delay in miliseconds before menu disappears onmouseout

disablemenuclick: true, //when user clicks on a menu item with a drop down menu, disable menu item's link?

enableswipe: 1, //enable swipe effect? 1 for yes, 0 for no

enableiframeshim: 1, //enable "iframe shim" technique to get drop down menus to correctly appear on top of controls such as form objects in IE5.5/IE6? 1 for yes, 0 for no



//No need to edit beyond here////////////////////////

dropmenuobj: null, ie: document.all, firefox: document.getElementById&&!document.all, swipetimer: undefined, bottomclip:0,



getposOffset:function(what, offsettype){

var totaloffset=(offsettype=="left")? what.offsetLeft : what.offsetTop;

var parentEl=what.offsetParent;

while (parentEl!=null){

totaloffset=(offsettype=="left")? totaloffset+parentEl.offsetLeft : totaloffset+parentEl.offsetTop;

parentEl=parentEl.offsetParent;

}

return totaloffset;

},



swipeeffect:function(){

if (this.bottomclip<parseInt(this.dropmenuobj.offsetHeight)){

this.bottomclip+=10+(this.bottomclip/10) //unclip drop down menu visibility gradually

this.dropmenuobj.style.clip="rect(0 auto "+this.bottomclip+"px 0)"

}

else

return

this.swipetimer=setTimeout("cssdropdown.swipeeffect()", 10)

},



showhide:function(obj, e){

if (this.ie || this.firefox)

this.dropmenuobj.style.left=this.dropmenuobj.style.top="-500px"

if (e.type=="click" && obj.visibility==hidden || e.type=="mouseover"){

if (this.enableswipe==1){

if (typeof this.swipetimer!="undefined")

clearTimeout(this.swipetimer)

obj.clip="rect(0 auto 0 0)" //hide menu via clipping

this.bottomclip=0

this.swipeeffect()

}

obj.visibility="visible"

}

else if (e.type=="click")

obj.visibility="hidden"

},



iecompattest:function(){

return (document.compatMode && document.compatMode!="BackCompat")? document.documentElement : document.body

},



clearbrowseredge:function(obj, whichedge){

var edgeoffset=0

if (whichedge=="rightedge"){

var windowedge=this.ie && !window.opera? this.iecompattest().scrollLeft+this.iecompattest().clientWidth-15 : window.pageXOffset+window.innerWidth-15

this.dropmenuobj.contentmeasure=this.dropmenuobj.offsetWidth

if (windowedge-this.dropmenuobj.x < this.dropmenuobj.contentmeasure)  //move menu to the left?

edgeoffset=this.dropmenuobj.contentmeasure-obj.offsetWidth

}

else{

var topedge=this.ie && !window.opera? this.iecompattest().scrollTop : window.pageYOffset

var windowedge=this.ie && !window.opera? this.iecompattest().scrollTop+this.iecompattest().clientHeight-15 : window.pageYOffset+window.innerHeight-18

this.dropmenuobj.contentmeasure=this.dropmenuobj.offsetHeight

if (windowedge-this.dropmenuobj.y < this.dropmenuobj.contentmeasure){ //move up?

edgeoffset=this.dropmenuobj.contentmeasure+obj.offsetHeight

if ((this.dropmenuobj.y-topedge)<this.dropmenuobj.contentmeasure) //up no good either?

edgeoffset=this.dropmenuobj.y+obj.offsetHeight-topedge

}

}

return edgeoffset

},



dropit:function(obj, e, dropmenuID){

if (this.dropmenuobj!=null) //hide previous menu

this.dropmenuobj.style.visibility="hidden" //hide menu

this.clearhidemenu()

if (this.ie||this.firefox){

obj.onmouseout=function(){cssdropdown.delayhidemenu()}

obj.onclick=function(){return !cssdropdown.disablemenuclick} //disable main menu item link onclick?

this.dropmenuobj=document.getElementById(dropmenuID)

this.dropmenuobj.onmouseover=function(){cssdropdown.clearhidemenu()}

this.dropmenuobj.onmouseout=function(e){cssdropdown.dynamichide(e)}

this.dropmenuobj.onclick=function(){cssdropdown.delayhidemenu()}

this.showhide(this.dropmenuobj.style, e)

this.dropmenuobj.x=this.getposOffset(obj, "left")

this.dropmenuobj.y=this.getposOffset(obj, "top")

this.dropmenuobj.style.left=this.dropmenuobj.x-this.clearbrowseredge(obj, "rightedge")+"px"

this.dropmenuobj.style.top=this.dropmenuobj.y-this.clearbrowseredge(obj, "bottomedge")+obj.offsetHeight+1+"px"

this.positionshim() //call iframe shim function

}

},



positionshim:function(){ //display iframe shim function

if (this.enableiframeshim && typeof this.shimobject!="undefined"){

if (this.dropmenuobj.style.visibility=="visible"){

this.shimobject.style.width=this.dropmenuobj.offsetWidth+"px"

this.shimobject.style.height=this.dropmenuobj.offsetHeight+"px"

this.shimobject.style.left=this.dropmenuobj.style.left

this.shimobject.style.top=this.dropmenuobj.style.top

}

this.shimobject.style.display=(this.dropmenuobj.style.visibility=="visible")? "block" : "none"

}

},



hideshim:function(){

if (this.enableiframeshim && typeof this.shimobject!="undefined")

this.shimobject.style.display='none'

},



contains_firefox:function(a, b) {

while (b.parentNode)

if ((b = b.parentNode) == a)

return true;

return false;

},



dynamichide:function(e){

var evtobj=window.event? window.event : e

if (this.ie&&!this.dropmenuobj.contains(evtobj.toElement))

this.delayhidemenu()

else if (this.firefox&&e.currentTarget!= evtobj.relatedTarget&& !this.contains_firefox(evtobj.currentTarget, evtobj.relatedTarget))

this.delayhidemenu()

},



delayhidemenu:function(){

this.delayhide=setTimeout("cssdropdown.dropmenuobj.style.visibility='hidden'; cssdropdown.hideshim()",this.disappeardelay) //hide menu

},



clearhidemenu:function(){

if (this.delayhide!="undefined")

clearTimeout(this.delayhide)

},



startmenu:function(){

for (var ids=0; ids<arguments.length; ids++){

var menuitems=document.getElementById(arguments[ids]).getElementsByTagName("a")

for (var i=0; i<menuitems.length; i++){

if (menuitems[i].getAttribute("rel")){

var relvalue=menuitems[i].getAttribute("rel")

menuitems[i].onmouseover=function(e){

var event=typeof e!="undefined"? e : window.event

cssdropdown.dropit(this,event,this.getAttribute("rel"))

}

}

}

}

if (window.createPopup && !window.XmlHttpRequest){ //if IE5.5 to IE6, create iframe for iframe shim technique

document.write('<IFRAME id="iframeshim"  src="" style="display: none; left: 0; top: 0; z-index: 999; position: absolute; filter: progid:DXImageTransform.Microsoft.Alpha(style=0,opacity=0)" frameBorder="0" scrolling="no"></IFRAME>')

this.shimobject=document.getElementById("iframeshim") //reference iframe object

}

}



}


```

Its working fine for IE5.5+ but firefox dies!. It did this moring attempt the display properly but crashed the browser after a few seconds of flash!

Mike

---

### Post by Mickeysofine1972 on 2007-06-06
I just tried the menu on a windows version of firefox and its fine!

could this be a flaw in flash 9 for linux?

Mike

---

### Post by tturrisi on 2007-06-06
I'd use a difgferent dropdown menu.  That css chrome dropdown is buggy even on the dynamicdrive demos!  It's slow and laggy.
More than likely this is an issue w/ firefox  linux versions only.  For example, see this page which has a solution to the dhtml-flash layering problem that works in both firefox & IE on windows, but dooes not work w/ firefox on linux, at least not on my deb system.
[http://www.communitymx.com/content/source/E5141/wmodetrans.htm](http://www.communitymx.com/content/source/E5141/wmodetrans.htm)

---

### Post by cytutchi on 2007-06-06
Having the same problem here as well with the firefox and Conq.
i would like some help as well

i can provide a link to a website that gives me this problem if you want...

P.S. I am a newby kinda as well!!! :/

---

