---
title: "Javascript and Sound Syntax"
date: 2013-01-03
forum: Programming Talk
---

### Post by Merrattic on 2013-01-03
I have found the code that lets you play a sound if you click on a link or image:
```
<!DOCTYPE html> 
<html> 
<head> 
<script language="javascript" type="text/javascript"> 
 function playSound(soundfile) { 
 document.getElementById("dummy").innerHTML= 
 "<embed src=\""+soundfile+"\" hidden=\"true\" autostart=\"true\" loop=\"false\" />"; 
 } 
 </script> 
  
</head> 
 
<body> 
 
<h1>My Web Page</h1> 
<span id="dummy"></span> 
 <a href="#" onclick="playSound('snack1.ogg');">Click here to hear a sound</a> 
 <img onclick="playSound('snack1.ogg');" src="snack2.png" > 
 
</body> 
</html>
```
This works fine. I would like to be able to create a function with conditions, so depending on the name/id of the image being displayed a corresponding sound is player. I have tried modifying the existing script to what i think should work, but it doesn't?

```
<!DOCTYPE html> 
<html> 
<head> 
 
<script language="javascript" type="text/javascript"> 
 function playSound() { 
 document.getElementById("dummy").innerHTML="<embed src="snack1.ogg" hidden=\"true\" autostart=\"true\" loop=\"false\" />"; 
 } 
 </script> 
 
</head> 
 
<body> 
 
<h1>My Web Page</h1> 
<span id="dummy"></span> 

<a href="#" onclick="playSound()">Plays a sound</a> 
 
</body> 
</html>
```

Any help much appreciated  ):P

---

### Post by dooma14 on 2013-01-03
The quotation marks make the bug of your code.
The second quotation mark close the string which you intend to fill the span tag.
```
document.getElementById("dummy").innerHTML="<embed src="snack1.ogg" hidden=\"true\" autostart=\"true\" loop=\"false\" />"; 
```
You can try this two options
```
document.getElementById("dummy").innerHTML="<embed src=\"snack1.ogg\" hidden=\"true\" autostart=\"true\" loop=\"false\" />"; 
document.getElementById("dummy").innerHTML="<embed src='snack1.ogg' hidden=\"true\" autostart=\"true\" loop=\"false\" />"; 

```

---

### Post by Merrattic on 2013-01-03
Hmmph, can't test at present, my linux firefox refusing to play any oggs unless I use htm5 <audio>:
```
<audio autoplay><source src="snack1.ogg" type="audio/ogg"></audio>
```

---

### Post by Merrattic on 2013-01-05
I think I have found solutions:

```
<script> 
var snd1 = new Audio("snack1.ogg"); 
var snd2 = new Audio("snack2.ogg"); 
</script> 
<img onclick="snd1.play();" src="snack1.png" >
<img onclick="snd2.play();" src="snack2.png" >
```Also some useful stuff on using sound with javascript here:

[http://dl.dropbox.com/u/2400/mirror/jai/jai-x.htm](http://dl.dropbox.com/u/2400/mirror/jai/jai-x.htm)

---

