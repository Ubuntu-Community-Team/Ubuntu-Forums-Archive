---
title: "Combine the best bits of two javascript scripts?"
date: 2011-10-13
forum: Programming Talk
---

### Post by Jose Catre-Vandis on 2011-10-13
Hi

I have an html slideshow up and running that uses a javascript to change the images, but requires manual entries to the code to update the images. What is good about this script is that it offers "Previous / Auto or Stop / Next" links for the slides

I have a second html slideshow with javascript that uses a php script to dynamically create the array for images to be used. This is great as I have to update the slideshow on a daily basis. Sadly this script does not have the "Previous / Auto or Stop / Next" links which I would like.

So seeking to combine the two, but the scripts are quite different and beyond my understanding of javascripting. If someone can advise on what needs to be changed I would be most grateful.

1. Script (full html) with manual entries and links
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"

  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">



<head>

	<title>Slideshow</title>

<SCRIPT LANGUAGE="JavaScript">
<!-- Begin
NewImg = new Array (
"0001.jpg",
"0002.jpg",
"0003.jpg",
"0004.jpg",
"0005.jpg",
"0006.jpg"
);
var ImgNum = 0;
var ImgLength = NewImg.length - 1;

//Time delay between Slides in milliseconds
var delay = 15000;

var lock = false;
var run;
function chgImg(direction) {
if (document.images) {
ImgNum = ImgNum + direction;
if (ImgNum > ImgLength) {
ImgNum = 0;
}
if (ImgNum < 0) {
ImgNum = ImgLength;
}
document.slideshow.src = NewImg[ImgNum];
   }
}
function auto() {
if (lock == true) {
lock = false;
window.clearInterval(run);
}
else if (lock == false) {
lock = true;
run = setInterval("chgImg(1)", delay);
   }
}

auto()
//  End -->
</script>

</head>



<body bgcolor=#cde969>
<div style="text-align:center;">
<img src="0001.jpg" name="slideshow">
</div>

<div style="text-align:center;">
<a href="javascript:chgImg(-1)">Previous</a>
<a href="javascript:auto()">Auto/Stop</a>
<a href="javascript:chgImg(1)">Next</a>
</div>

</body>

</html>


```

2. Script (full html) with dynamic array
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"

  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">



<head>

	<title>Slideshow</title>

	<meta http-equiv="content-type" content="text/html;charset=utf-8" />


</head>



<body bgcolor="#cde969">
<script src="pics/getimages.php"></script>

<script type="text/javascript">

var curimg=0
function rotateimages(){
document.getElementById("slideshow").setAttribute("src", "pics/"+galleryarray[curimg])
curimg=(curimg<galleryarray.length-1)? curimg+1 : 0
}

window.onload=function(){
setInterval("rotateimages()", 10000)
}
</script>

<div style="text-align:center;">
<img id="slideshow" src="pics/0001.jpg" />
</div>
	

</body>

</html>

```

If it helps, here is the php file too:
```
<?
//PHP SCRIPT: getimages.php
Header("content-type: application/x-javascript");

//This function gets the file names of all images in the current directory
//and ouputs them as a JavaScript array
function returnimages($dirname=".") {
$pattern="(\.jpg$)|(\.png$)|(\.jpeg$)|(\.gif$)"; //valid image extensions
$files = array();
$curimage=0;
if($handle = opendir($dirname)) {
while(false !== ($file = readdir($handle))){
if(eregi($pattern, $file)){ //if this file is a valid image
//Output it as a JavaScript array element
echo 'galleryarray['.$curimage.']="'.$file .'";';
$curimage++;
}
}

closedir($handle);
}
return($files);
}

echo 'var galleryarray=new Array();'; //Define array in JavaScript
returnimages() //Output the array elements containing the image file names
?> 

```

Thanks in anticipation

---

### Post by Jose Catre-Vandis on 2011-10-13
Ah well, with no responses to guide me I went to work on it myself and fixed it! Simply a case of substitution, just a matter of what and where ;)

New php file:
```
<?
//PHP SCRIPT: getimages.php
Header("content-type: application/x-javascript");

//This function gets the file names of all images in the current directory
//and ouputs them as a JavaScript array
function returnimages($dirname=".") {
$pattern="(\.jpg$)|(\.png$)|(\.jpeg$)|(\.gif$)"; //valid image extensions
$files = array();
$curimage=0;
if($handle = opendir($dirname)) {
while(false !== ($file = readdir($handle))){
if(eregi($pattern, $file)){ //if this file is a valid image
//Output it as a JavaScript array element
echo '**NewImg**['.$curimage.']="'.$file .'";';
$curimage++;
}
}

closedir($handle);
}
return($files);
}

echo 'var **NewImg**=new Array();'; //Define array in JavaScript
returnimages() //Output the array elements containing the image file names
?> 

```

New html / javascript file:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"

  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>

	<title>Slideshow</title>

	<meta http-equiv="content-type" content="text/html;charset=utf-8" />

**<script src="pics/getimages.php"></script>**

<SCRIPT LANGUAGE="JavaScript">
**<!-- Remove original array -->**
var ImgNum = 0;
var ImgLength = NewImg.length - 1;

//Time delay between Slides in milliseconds
var delay = 15000;

var lock = false;
var run;
function chgImg(direction) {
if (document.images) {
ImgNum = ImgNum + direction;
if (ImgNum > ImgLength) {
ImgNum = 0;
}
if (ImgNum < 0) {
ImgNum = ImgLength;
}
document.slideshow.src = **"pics/"+**NewImg[ImgNum];
   }
}
function auto() {
if (lock == true) {
lock = false;
window.clearInterval(run);
}
else if (lock == false) {
lock = true;
run = setInterval("chgImg(1)", delay);
   }
}

auto()

</script>

</head>



<body bgcolor=#cde969>

	<div style="text-align:center;">
		<img src="**pics/**0001.jpg" name="slideshow">
	</div>

	<div style="text-align:center;">
		<a href="javascript:chgImg(-1)">Previous</a>
		<a href="javascript:auto()">Auto/Stop</a>
		<a href="javascript:chgImg(1)">Next</a>
	</div>

</body>

</html>

```

The html file is in the "top" directory, the php file is in the pics directory along with the images. Main changes to files shown in bold

---

