---
title: "PHP within PHP"
date: 2010-11-14
forum: Programming Talk
---

### Post by Sofia A on 2010-11-14
[FONT=verdana][SIZE=2][COLOR=#000000]Hi,  
 
I've been tearing my hair out trying to make this work. 
 
I have a menu list in a php which is called up by the header. 
 
The list is simple and looks like this: 
 
<li class="artist"><a href="artist.php" ></a></li> 
 
and I want to add this: 
 
<?php if ( $thisPage == "Artist" ) { 
echo '<img src="/images/50.png" width="50" height="20" />' ; 
} 
?>  
 
to the href. 
 
Both  sets of code work on their own, but obviously I can't just add the  second lines of code to the first because it's already within the php  tags. 
 
I know not to use echo and the <?php and ?>, but  there's more to it and I can't work it out for myself. Something to do  with .'? 
 
Please help before I have no hair left. Thanks :)  [/COLOR][/SIZE][/FONT]

---

### Post by Mmmbopdowedop on 2010-11-14
So this is what you have?
[PHP]<?php
    echo '<li class="artist"><a href="artist.php" ></a></li>';
?>[/PHP]

And you want to add the following?
[PHP]<?php
if( $thisPage == "Artist" )
{
    echo '<img src="/images/50.png" width="50" height="20" />' ;
}
?>[/PHP]

Why are you echo'ing it out?
You can close PHP to display HTML like so;

[PHP]<?php

if(1 ==1) //which it does!
{
    //then close PHP
    ?>
        <p>And print out my nice html here. :-)</p>
        <p>Which would be your nice menu list</p>
        <p>In which you could add php here normally, without adding
            the annoying backslashes all over the place! :-)</p>
        <br />
        <?php echo "This is an example!"; ?>
    <?php
} //And then close your if tag

?>[/PHP]


If this makes no sense, please post more of your code, because at the moment, what you gave is really confusing. :P

---

### Post by Sofia A on 2010-11-14
Yes, it's hard to explain, especially since I'm clearly confusing myself. Thanks for your patience.


Okay, so  I call up my header.php on every page, and the header.php looks like this (forget what I said re menu.php - it was superfluous...)

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />

<title>Sofia Antonia Milone</title>



<script type="text/javascript">
<!--
function MM_preloadImages() { //v3.0
  var d=document; if(d.images){ if(!d.MM_p) d.MM_p=new Array();
    var i,j=d.MM_p.length,a=MM_preloadImages.arguments; for(i=0; i<a.length; i++)
    if (a[i].indexOf("#")!=0){ d.MM_p[j]=new Image; d.MM_p[j++].src=a[i];}}
}

function MM_swapImgRestore() { //v3.0
  var i,x,a=document.MM_sr; for(i=0;a&&i<a.length&&(x=a[i])&&x.oSrc;i++) x.src=x.oSrc;
}

function MM_findObj(n, d) { //v4.01
  var p,i,x;  if(!d) d=document; if((p=n.indexOf("?"))>0&&parent.frames.length) {
    d=parent.frames[n.substring(p+1)].document; n=n.substring(0,p);}
  if(!(x=d[n])&&d.all) x=d.all[n]; for (i=0;!x&&i<d.forms.length;i++) x=d.forms[i][n];
  for(i=0;!x&&d.layers&&i<d.layers.length;i++) x=MM_findObj(n,d.layers[i].document);
  if(!x && d.getElementById) x=d.getElementById(n); return x;
}

function MM_swapImage() { //v3.0
  var i,j=0,x,a=MM_swapImage.arguments; document.MM_sr=new Array; for(i=0;i<(a.length-2);i+=3)
   if ((x=MM_findObj(a[i]))!=null){document.MM_sr[j++]=x; if(!x.oSrc) x.oSrc=x.src; x.src=a[i+2];}
}
function MM_nbGroup(event, grpName) { //v6.0
  var i,img,nbArr,args=MM_nbGroup.arguments;
  if (event == "init" && args.length > 2) {
    if ((img = MM_findObj(args[2])) != null && !img.MM_init) {
      img.MM_init = true; img.MM_up = args[3]; img.MM_dn = img.src;
      if ((nbArr = document[grpName]) == null) nbArr = document[grpName] = new Array();
      nbArr[nbArr.length] = img;
      for (i=4; i < args.length-1; i+=2) if ((img = MM_findObj(args[i])) != null) {
        if (!img.MM_up) img.MM_up = img.src;
        img.src = img.MM_dn = args[i+1];
        nbArr[nbArr.length] = img;
    } }
  } else if (event == "over") {
    document.MM_nbOver = nbArr = new Array();
    for (i=1; i < args.length-1; i+=3) if ((img = MM_findObj(args[i])) != null) {
      if (!img.MM_up) img.MM_up = img.src;
      img.src = (img.MM_dn && args[i+2]) ? args[i+2] : ((args[i+1])? args[i+1] : img.MM_up);
      nbArr[nbArr.length] = img;
    }
  } else if (event == "out" ) {
    for (i=0; i < document.MM_nbOver.length; i++) {
      img = document.MM_nbOver[i]; img.src = (img.MM_dn) ? img.MM_dn : img.MM_up; }
  } else if (event == "down") {
    nbArr = document[grpName];
    if (nbArr)
      for (i=0; i < nbArr.length; i++) { img=nbArr[i]; img.src = img.MM_up; img.MM_dn = 0; }
    document[grpName] = nbArr = new Array();
    for (i=2; i < args.length-1; i+=2) if ((img = MM_findObj(args[i])) != null) {
      if (!img.MM_up) img.MM_up = img.src;
      img.src = img.MM_dn = (args[i+1])? args[i+1] : img.MM_up;
      nbArr[nbArr.length] = img;
  } }
}
//-->
</script>

<link href="all.css" rel="stylesheet" type="text/css" />
<link href="main.css" rel="stylesheet" type="text/css" />
<link href="menu1.css" rel="stylesheet" type="text/css" />
</head>

<body onload="MM_preloadImages('images/nav1.png','images/nav2.png','images/nav3.png','images/nav4a.png')">

<!--- Start Wrapper--->
<div id="wrapper">
<div id="topper">
<div class="whitebody" id="topperbox">Home | Contact | Links | Share:</div>
</div>
<!--- Start Mainframe--->
<div id="mainframe">
<div id="headergap"></div>
<div id="header">

<ul class="cssmenu">
    <li class="artist"><a href="artist.php" ></a></li>
    <li  class="writer"><a href="writer.php"></a></li>
    <li class="musician"><a href="musician.php"></a></li>
    <li class="design"><a href="#"></a></li>
   
</ul>

</div>
<div id="inttop">
</div>

<!--- End Header content --->


What I was going to do was add a style for the current page, so I popped in a title for each page on the page in question: <?php $thisPage="Musician"; ?> for example. So that the nav bar would display 'a:selected' correctly. I couldn't get this to work, so I thought it might be something to do with trying to code php within php.

Knowing I could get the echo to work through my pages using <?php $thisPage="Musician"; ?> etc, and I haven't yet managed to get 'a:selected' to display properly, I was hoping to just substitute that instead of the style 'a:selected'

I'm sure I'm over complicating the matter... Apologies.

This is the page in question: [http://fia.me.uk/artist.php](http://fia.me.uk/artist.php)

Thanks

---

### Post by bitscarre on 2010-11-15
[PHP]<li class="artist"><a href="artist.php" <?php if(substr($_SERVER['SCRIPT_NAME'], 1, -4) == "artist") echo "class=\"selected\""; ?>></a></li>
<li class="writer"><a href="writer.php" <?php if(substr($_SERVER['SCRIPT_NAME'], 1, -4) == "writer") echo "class=\"selected\""; ?>></a></li>
<li class="musician"><a href="musician.php" <?php if(substr($_SERVER['SCRIPT_NAME'], 1, -4) == "musician") echo "class=\"selected\""; ?>></a></li>
<li class="design"><a href="#" <?php if(substr($_SERVER['SCRIPT_NAME'], 1, -4) == "design") echo "class=\"selected\""; ?>></a></li>[/PHP]I think this is what you are trying to achieve. The solution I propose is very basic, but should do the job.

Make sure you have a case for empty script name, you should default to the artist menu, or whichever should display by default.

---

### Post by Sofia A on 2010-11-15
Hi, 

Apologies, I figured this out last night too! Yes, that what I wanted pretty much.

My final code is this:

<?php
echo '<li class="artist"><a href="artist.php" '.(($thisPage == "Artist") ? 'class=selected' : '').'></a></li>';
echo '<li class="writer"><a href="writer.php" '.(($thisPage == "Writer") ? 'class=selected' : '').'></a></li>';
echo '<li class="musician"><a href="musician.php" '.(($thisPage == "Musician") ? 'class=selected' : '').'></a></li>';
?>

Thanks to all who have helped me get there in the end ;)

p.s I came across these forums in a search engine, but I have NOTHING to do with this 'ubuntu' I think I'm not supposed to be here!

Sofia

---

### Post by bitscarre on 2010-11-15
You should try Ubuntu. It can "program in php by itself". 

Try it, try it! :D

:guitar:

---

### Post by Sofia A on 2010-11-15
Well that sounds good, but I'd like to program php 'by' myself :) I expect it could be a useful tool ;)

---

