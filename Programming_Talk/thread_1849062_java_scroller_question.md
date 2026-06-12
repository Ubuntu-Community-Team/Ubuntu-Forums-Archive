---
title: "java scroller question"
date: 2011-09-23
forum: Programming Talk
---

### Post by w0296094 on 2011-09-23
Not sure if the html tags below will turn my script active so that it is easier to read, so point me in the right direction if it doesn't. I have a code below for a scroller in java. What I want to do is get to assign names to each image on the scroller. These names will show up in the bottom of the image that is being conveyed. How do I do it?


[HTML]
<?

<HTML>
<HEAD>
<TITLE>Horizontal Image Scroller 3</TITLE>

<script type="text/javascript">
<!--

// Jeff
// www.huntingground.freeserve.co.uk

// ********** User Defining Area **********

data=[
[["\includes\scrollerpics\p1.jpg","Player1","\testsite1\includes\scrollerpics\p1.jpg"],
["\includes\scrollerpics\p2.jpg","Player2","\testsite1\includes\scrollerpics\p2.jpg"],
["includes/scrollerpics/p3.jpg","Player3","/includes/scrollerpics/p3.jpg"],
["pic04sm.jpg","Player4","includes/scrollerpics/p4.jpg"],
["pic05sm.jpg","player5","includes/scrollerpics/p5.jpg"],
["pic06sm.jpg","Player6","includes/scrollerpics/p6.jpg"],
["pic07sm.jpg","Player7","includes/scrollerpics/p7.jpg"],
["pic08sm.jpg","Player8","includes/scrollerpics/p8.jpg"]
 // no comma at end of last index
]

imgPlaces=5 // number of images visible
imgWidth=100 // width of the images
imgHeight=100 // height of the images
imgSpacer=4 // space between the images

dir=0 // 0 = left, 1 = right

newWindow=1 // 0 = Open a new window for links 0 = no  1 = yes

// ********** End User Defining Area **********

moz=document.getElementById&&!document.all

step=1
timer=""
speed=50
nextPic=0
initPos=new Array()
nowDivPos=new Array()

function initHIS3(){

for(var i=0;i<imgPlaces+1;i++){ // create image holders
newImg=document.createElement("IMG")
newImg.setAttribute("id","pic_"+i)
newImg.setAttribute("src","")
newImg.style.position="absolute"
newImg.style.width=imgWidth+"px"
newImg.style.height=imgHeight+"px"
newImg.style.border=0
newImg.alt=""
newImg.i=i
newImg.onclick=function(){his3Win(data[this.i][2])}
document.getElementById("display_area").appendChild(newImg)
}

containerEL=document.getElementById("his3container")
displayArea=document.getElementById("display_area")
pic0=document.getElementById("pic_0")

containerBorder=(document.compatMode=="CSS1Compat"?0:parseInt(containerEL.style.borderWidth)*2)
containerWidth=(imgPlaces*imgWidth)+((imgPlaces-1)*imgSpacer)
containerEL.style.width=containerWidth+(!moz?containerBorder:"")+"px"
containerEL.style.height=imgHeight+(!moz?containerBorder:"")+"px"

displayArea.style.width=containerWidth+"px"
displayArea.style.clip="rect(0,"+(containerWidth+"px")+","+(imgHeight+"px")+",0)"
displayArea.onmouseover=function(){stopHIS3()}
displayArea.onmouseout=function(){scrollHIS3()}

imgPos= -pic0.width

for(var i=0;i<imgPlaces+1;i++){
currentImage=document.getElementById("pic_"+i)

if(dir==0){imgPos+=pic0.width+imgSpacer} // if left

initPos[i]=imgPos
if(dir==0){currentImage.style.left=initPos[i]+"px"} // if left

if(dir==1){ // if right
document.getElementById("pic_"+[(imgPlaces-i)]).style.left=initPos[i]+"px"
imgPos+=pic0.width+imgSpacer
}

if(nextPic==data.length){nextPic=0}

currentImage.src=data[$list_box_contents[$row][$col]['text']][0]
currentImage.alt=data[$list_box_contents[$row][$col]['text']][1]
currentImage.i=nextPic
currentImage.onclick=function(){his3Win(data[this.i][2])}
nextPic++
}

scrollHIS3()
}

timer=""
function scrollHIS3(){
clearTimeout(timer)
for(var i=0;i<imgPlaces+1;i++){
currentImage=document.getElementById("pic_"+i)

nowDivPos[i]=parseInt(currentImage.style.left)

if(dir==0){nowDivPos[i]-=step}
if(dir==1){nowDivPos[i]+=step}

if(dir==0&&nowDivPos[i]<= -(pic0.width+imgSpacer) || dir==1&&nowDivPos[i]>containerWidth){

if(dir==0){currentImage.style.left=containerWidth+imgSpacer+"px"}
if(dir==1){currentImage.style.left= -pic0.width-(imgSpacer*2)+"px"}

if(nextPic>data.length-1){nextPic=0}

currentImage.src=data[$columnvar][0]
currentImage.alt=data[$columnvar][1]
currentImage.i=nextPic
currentImage.onclick=function(){his3Win(data[this.i][2])}

nextPic++

}
else{
currentImage.style.left=nowDivPos[i]+"px"
}

}
timer=setTimeout("scrollHIS3()",speed)

}

function stopHIS3(){
clearTimeout(timer)
}

function his3Win(loc){
if(loc==""){return}
if(newWindow==0){
location=loc
}
else{
//window.open(loc)
newin=window.open(loc,'win1','left=430,top=340,width=300,height=300') // use for specific size and positioned window
newin.focus()
}
}

// add onload="initHIS3()" to the opening BODY tag

// -->
</script>

</HEAD>
<BODY onload="initHIS3()">

<center>

<DIV id="his3container" style="position:relative; width:0px;height:0px; border:1px solid red;overflow:hidden">

<div id="display_area" style="position:absolute; left:0; top:0; width:0px; height:0px; clip:rect(0,0,0,0)"></div>

</DIV>

</BODY>
</HTML>
?>

[/HTML]
My main goal at first, was to be able to call the values from a php page, and output these values into the scroller(In other words the images saved with php would be outputted with java). However, it seems challenging to integrate java and php. You will see the whole code on the next post

---

### Post by w0296094 on 2011-09-23
The whole code for the page is written below:


[HTML]
<?php
/**
 * Common Template - tpl_columnar_display.php
 *
 * This file is used for generating tabular output where needed, based on the supplied array of table-cell contents.
 *
 * @package templateSystem
 * @copyright Copyright 2003-2006 Zen Cart Development Team
 * @copyright Portions Copyright 2003 osCommerce
 * @license http://www.zen-cart.com/license/2_0.txt GNU Public License V2.0
 * @version $Id: tpl_columnar_display.php 3157 2006-03-10 23:24:22Z drbyte $
 */

?>
<?php
  if ($title) {
  ?>
<?php echo $title; ?>
<?php
 }
 ?>
<?php
if (is_array($list_box_contents) > 0 ) {
 for($row=0;$row<sizeof($list_box_contents);$row++) {
    $params = "";
    //if (isset($list_box_contents[$row]['params'])) $params .= ' ' . $list_box_contents[$row]['params'];
?>

<?php
    for($col=0;$col<sizeof($list_box_contents[$row]);$col++) {
      $r_params = "";
      if (isset($list_box_contents[$row][$col]['params'])) $r_params .= ' ' . (string)$list_box_contents[$row][$col]['params'];
     if (isset($list_box_contents[$row][$col]['text'])) {
?>
    <?php echo '<div' . $r_params . '>' . $list_box_contents[$row][$col]['text'] .  '</div>' . "\n"; ?>
<?php
      }
    }
?>
<br class="clearBoth" />
<?php
  }
}
$list_box_contents[$row][$col]['text'] = $columnvar;

?>

<?

<HTML>
<HEAD>
<TITLE>Horizontal Image Scroller 3</TITLE>

<script type="text/javascript">
<!--

// Jeff
// www.huntingground.freeserve.co.uk

// ********** User Defining Area **********

data=[
[["\includes\scrollerpics\p1.jpg","Player1","\testsite1\includes\scrollerpics\p1.jpg"],
["\includes\scrollerpics\p2.jpg","Player2","\testsite1\includes\scrollerpics\p2.jpg"],
["includes/scrollerpics/p3.jpg","Player3","/includes/scrollerpics/p3.jpg"],
["pic04sm.jpg","Player4","includes/scrollerpics/p4.jpg"],
["pic05sm.jpg","player5","includes/scrollerpics/p5.jpg"],
["pic06sm.jpg","Player6","includes/scrollerpics/p6.jpg"],
["pic07sm.jpg","Player7","includes/scrollerpics/p7.jpg"],
["pic08sm.jpg","Player8","includes/scrollerpics/p8.jpg"]
 // no comma at end of last index
]

imgPlaces=5 // number of images visible
imgWidth=100 // width of the images
imgHeight=100 // height of the images
imgSpacer=4 // space between the images

dir=0 // 0 = left, 1 = right

newWindow=1 // 0 = Open a new window for links 0 = no  1 = yes

// ********** End User Defining Area **********

moz=document.getElementById&&!document.all

step=1
timer=""
speed=50
nextPic=0
initPos=new Array()
nowDivPos=new Array()

function initHIS3(){

for(var i=0;i<imgPlaces+1;i++){ // create image holders
newImg=document.createElement("IMG")
newImg.setAttribute("id","pic_"+i)
newImg.setAttribute("src","")
newImg.style.position="absolute"
newImg.style.width=imgWidth+"px"
newImg.style.height=imgHeight+"px"
newImg.style.border=0
newImg.alt=""
newImg.i=i
newImg.onclick=function(){his3Win(data[this.i][2])}
document.getElementById("display_area").appendChild(newImg)
}

containerEL=document.getElementById("his3container")
displayArea=document.getElementById("display_area")
pic0=document.getElementById("pic_0")

containerBorder=(document.compatMode=="CSS1Compat"?0:parseInt(containerEL.style.borderWidth)*2)
containerWidth=(imgPlaces*imgWidth)+((imgPlaces-1)*imgSpacer)
containerEL.style.width=containerWidth+(!moz?containerBorder:"")+"px"
containerEL.style.height=imgHeight+(!moz?containerBorder:"")+"px"

displayArea.style.width=containerWidth+"px"
displayArea.style.clip="rect(0,"+(containerWidth+"px")+","+(imgHeight+"px")+",0)"
displayArea.onmouseover=function(){stopHIS3()}
displayArea.onmouseout=function(){scrollHIS3()}

imgPos= -pic0.width

for(var i=0;i<imgPlaces+1;i++){
currentImage=document.getElementById("pic_"+i)

if(dir==0){imgPos+=pic0.width+imgSpacer} // if left

initPos[i]=imgPos
if(dir==0){currentImage.style.left=initPos[i]+"px"} // if left

if(dir==1){ // if right
document.getElementById("pic_"+[(imgPlaces-i)]).style.left=initPos[i]+"px"
imgPos+=pic0.width+imgSpacer
}

if(nextPic==data.length){nextPic=0}

currentImage.src=data[$list_box_contents[$row][$col]['text']][0]
currentImage.alt=data[$list_box_contents[$row][$col]['text']][1]
currentImage.i=nextPic
currentImage.onclick=function(){his3Win(data[this.i][2])}
nextPic++
}

scrollHIS3()
}

timer=""
function scrollHIS3(){
clearTimeout(timer)
for(var i=0;i<imgPlaces+1;i++){
currentImage=document.getElementById("pic_"+i)

nowDivPos[i]=parseInt(currentImage.style.left)

if(dir==0){nowDivPos[i]-=step}
if(dir==1){nowDivPos[i]+=step}

if(dir==0&&nowDivPos[i]<= -(pic0.width+imgSpacer) || dir==1&&nowDivPos[i]>containerWidth){

if(dir==0){currentImage.style.left=containerWidth+imgSpacer+"px"}
if(dir==1){currentImage.style.left= -pic0.width-(imgSpacer*2)+"px"}

if(nextPic>data.length-1){nextPic=0}

currentImage.src=data[$columnvar][0]
currentImage.alt=data[$columnvar][1]
currentImage.i=nextPic
currentImage.onclick=function(){his3Win(data[this.i][2])}

nextPic++

}
else{
currentImage.style.left=nowDivPos[i]+"px"
}

}
timer=setTimeout("scrollHIS3()",speed)

}

function stopHIS3(){
clearTimeout(timer)
}

function his3Win(loc){
if(loc==""){return}
if(newWindow==0){
location=loc
}
else{
//window.open(loc)
newin=window.open(loc,'win1','left=430,top=340,width=300,height=300') // use for specific size and positioned window
newin.focus()
}
}

// add onload="initHIS3()" to the opening BODY tag

// -->
</script>

</HEAD>
<BODY onload="initHIS3()">

<center>

<DIV id="his3container" style="position:relative; width:0px;height:0px; border:1px solid red;overflow:hidden">

<div id="display_area" style="position:absolute; left:0; top:0; width:0px; height:0px; clip:rect(0,0,0,0)"></div>

</DIV>

</BODY>
</HTML>
?>

[/HTML]So what I want to do is get the information that is under the following variable(which contains both images and image captions):

[HTML]$list_box_contents[$row]['params'][/HTML]and allow it to show on the scroller. The scroller information location is retrieved with this code:

[HTML]
data=[
["images/scrollerpics/p1.jpg","Player1","pic01.jpg"],
["images/scrollerpics/p2.jpg","Player2","pic02.jpg"],
[/HTML]

where images/scrollerpics... is the path where the image is stored.

---

### Post by w0296094 on 2011-09-30
ok anyone have a clue of what I am talking about. Do you need elaboration?

---

