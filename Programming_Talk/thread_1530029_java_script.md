---
title: "java script"
date: 2010-07-13
forum: Programming Talk
---

### Post by 007casper on 2010-07-13
[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>Untitled Document</title>

</head>

<body>
<script language="JavaScript">
<!--

function random_imglink(){
  var myimages=new Array()
  //specify random images below. You can have as many as you wish
  myimages[1]="images/pic2.pg"
  myimages[2]="images/pic1.jpg"
  myimages[3]="images/pic3.jpg"
  myimages[4]="images/pic4.jpg"
  myimages[5]="images/pic5.jpg"

  //specify corresponding links below
  var imagelinks=new Array()
  imagelinks[1]="#"
  imagelinks[2]="#"
  imagelinks[3]="#"
  imagelinks[4]="#"
  imagelinks[5]="#"

  var ry=Math.floor(Math.random()*myimages.length)

  if (ry==0)
     ry=1
     document.write('<a href='+'"'+imagelinks[ry]+'"'+'><img src="'+myimages[ry]+'" border=0></a>')
}

  random_imglink()
//-->
</script> 
.
</body>
</html>[/HTML]

this is not really programming per se... however, I am a bit stuck.  If I dont put the period, images wont load.  After I put the period, I figured random images would load in a loop.  However, it doesnt.  It gets stuck and usually only displays the period.

any advise.... 

thank you.

---

### Post by howlingmadhowie on 2010-07-13
i haven't tried your code, but you're not shutting your a-tag. that can't be good.

usually javascript goes in the header as well.

you can set properties for a's and img's using javascript directly as well.

---

### Post by 007casper on 2010-07-13
got it thanks... got it working

---

