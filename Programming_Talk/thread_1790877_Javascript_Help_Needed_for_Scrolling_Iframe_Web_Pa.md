---
title: "Javascript Help Needed for Scrolling Iframe Web Page"
date: 2011-06-25
forum: Programming Talk
---

### Post by Jose Catre-Vandis on 2011-06-25
Probably going about this all the wrong way but here goes:

Looking to set up an old PC to serve up a variety of static web pages on a big TV at work, to act like a news reader for staff. The Pc will be standalone (not on any network or connected to the internet (so please note the websites in the array are for ease of testing only), and I will probably use an ad-hoc wireless network to upload new files and administer.

I am using javascript to load a list of web pages into an iframe and another piece of javascript to scroll a div on the page. This _nearly_ works and just need an expert to point me in the right direction.

The entire web page:
> <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html>

<head>

<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

<title>Changing Pages... Please Wait</title>

<link type="text/css" rel="stylesheet" href="scroll.css">

<script type="text/javascript">

//change speed=1 to another integer to alter the scroll speed. Greater is faster
var speed=1
//variables for the scroll functions
var currentpos=0,alt=1,curpos1=0,curpos2=-1

//the array for web pages and viewing times
var myframes = Array('http://www.google.co.uk/', 60,
'http://ubuntuforums.org/', 60,
'http://yahoo.com/', 60,
'http://ask.com/', 60);
//variables for the rolling web page function
var i = 0, len = myframes.length;

//these three functions cause the whole page to scroll to the bottom, called by ChangeSrc
function scroller(){
startit()
}

function scrollwindow(){
if (document.all &&
!document.getElementById)
temp=document.body.scrollTop
else
temp=window.pageYOffset
if (alt==0)
alt=2
else
alt=1
if (alt==1)
curpos1=temp
else
curpos2=temp
if (curpos1!=curpos2){
if (document.all)
currentpos=document.body.scrollTop+speed
else
currentpos=window.pageYOffset+speed
window.scroll(0,currentpos)
}
else{
currentpos=0
window.scroll(0,currentpos)
}
}

function startit(){
setInterval("scrollwindow()",50)
}

//this function calls the changing web pages and the whole page scroll
function ChangeSrc()
{

if (i >= len) {i = 0;} //start over
document.getElementById('my-iframe').src = myframes[i++];
setTimeout('scroll(0,0)',3000);
setTimeout('ChangeSrc()', (myframes[i++]*1000));
setTimeout('scroller()',5000);

}

//this calls ChangeSrc on loading of page
window.onload = ChangeSrc;
</script>



</head>

<body>
<div id="my-div">
<iframe src="" id="my-iframe" scrolling="no" ></iframe>
</div>
</body>

</html>

and the style.css file that goes with it (named scroll.css)
> /* scroll css */

#my-div
{
    width    : 100%;
    height   : 2000px;
    position : relative;
}
 
#my-iframe
{
    position : absolute;
    width    : 100%;
    height   : 2000px;
    border   : 0;
}


Both bits of scripting work, but the web sites don't seem to load as per the timings set and scrolling is jerky and doesn't happen when expected (and more often than expected)...

My logic tells me:

a) load the html page

b) load the iframe
c) wait and then start scrolling the html page
d) stop scrolling at the bottom of the html page
e) next iframe page is called
f) scroll to top of the html page

g) repeat from b) adinfinitum

think I need another couple of steps in ChangeSrc between e), f) and b) ??


1. Would be grateful if someone could have a look and advise on the scripting?

2. is there another / better way to achieve this?

3. How could I use a text file to create the array of website addresses (so I only have to modify the text file and not the web page?

Thanks

---

