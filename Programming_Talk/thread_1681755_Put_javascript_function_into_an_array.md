---
title: "Put javascript function into an array"
date: 2011-02-04
forum: Programming Talk
---

### Post by rabbitfarmer on 2011-02-04
hello, i'm starting to learn basic HTML/javascript/CSS. I am making a web page that displays a random paragraph every time it starts up. My problem is this, the only way i know how to randomly choose a word is by a function like

> WordVP=new Array
WordVP[0]="walk"
WordVP[1]="fight"
WordVP[2]="cry"
WordVP[3]="go swimming"
WordVP[4]="attack"
WordVP[5]="punch"
WordVP[6]="write"
WordVP[7]="slide"
WordVP[8]="grow"
WordVP[9]="climb"
WordVP[10]="run"
WordVP[11]="speak"
WordVP[12]="oscillate"
WordVP[13]="fly"
WordVP[14]="crunch"
WordVP[15]="rock"
WordVP[16]="pick"
WordVP[17]="sit"

VPCount=WordVP.length
javascript=picphraseVP();

function picPhraseVP() {
randomNum=Math.floor ((Math.random() * VPCount))
trashTalk=WordVP[randomNum]
document.write ("<title>" + trashTalk + "</title>")
document.write ("<p align='center'>" + trashTalk + "</p>")
}this part of my script works well and fine, however i now need to create a function that will randomly call another function. I believe it should go something like this

> SenTest=new Array
SenTest[0]= picphraseVS()
SenTest[1]= picphraseVS()


SSCount=SenTest.length
javascript=picPhraseSS();

function picPhraseSS() {
randomNum=Math.floor ((Math.random() * SSCount))
trashTalk=SenTest[randomNum]
document.write ("<title>" + trashTalk + "</title>")
document.write ("<p align='center'>" + trashTalk + "</p>")
}
but this doesn't show anything. I once managed to get the syntax right, but then the random words were displayed just by entering <script src=""></script> tags in my html page. I need the array to call the function when the function for the array is called, if that makes any sense. any help would be appreciated,  thanks.

---

### Post by shadylookin on 2011-02-04
you can do it like this with anonymous functions being stored inside an array

[PHP]var funcArray = new Array();
funcArray[0]= function(){alert("1");};
funcArray[1] = function(){alert("2");};

var func = funcArray[1];
func();
[/PHP]

or something like this

[PHP]
function myFunction1(){
 alert("1");
}

function myFunction2(){
 alert("2");
}

var funcArray = new Array();
funcArray[0]= myFunction1;
funcArray[1] = myFunction2;

var func = funcArray[1];
func();
[/PHP]

---

### Post by worksofcraft on 2011-02-04
Hum... well it's an awful long time since I looked at this, but I CAN tell you that back then I decided that the ["Pizza" compiler]("http://pizzacompiler.sourceforge.net/") was the right way to create Java applications.

Basically they provide you with what is known as "function pointers" amongst other things.

p.s. alternatively you could probably use "listener" objects ala Sun methodology but IMO they are simply asinine.

---

### Post by shadylookin on 2011-02-04
> **worksofcraft said:**
> Hum... well it's an awful long time since I looked at this, but I CAN tell you that back then I decided that the ["Pizza" compiler]("http://pizzacompiler.sourceforge.net/") was the right way to create Java applications.

Basically they provide you with what is known as "function pointers" amongst other things.

p.s. alternatively you could probably use "listener" objects ala Sun methodology but IMO they are simply asinine.

what he's asking about is javascript not java there's a difference

---

### Post by rabbitfarmer on 2011-02-05
Ok thanks for the help Shady. I understand most of the code but i have one question, what does the alert"1" and such do. i understand most of it except that, i'm not very experience with php yet

---

### Post by shadylookin on 2011-02-05
> **rabbitfarmer said:**
> Ok thanks for the help Shady. I understand most of the code but i have one question, what does the alert"1" and such do. i understand most of it except that, i'm not very experience with php yet

it's not php it's javascript. The box may say php code, but that just a way to display code with syntax highlighting(very misleading of the forum software, but oh well).  

It prints out an annoying box in your browser that will say 1. If you really want to see it in action then just paste this as an html file and open it in a browser

[PHP]<html>
<script>
var funcArray = new Array();
funcArray[0]= function(){alert("1");};
funcArray[1] = function(){alert("2");};

var func = funcArray[1];
func();
</script>
</html>[/PHP]

I just did it as an example. Rather than an alert call you should put whatever programming logic you wanted to do there.

---

### Post by myrtle1908 on 2011-02-05
> **rabbitfarmer said:**
> hello, i'm starting to learn basic HTML/javascript/CSS. I am making a web page that displays a random paragraph every time it starts up.

```
<script language="javascript">
window.onload = function() {
 var words = 'walk,fight,cry,swim,eat,drink'.split(',');
 alert(words[Math.floor(Math.random()*words.length)]);
}
</script>
```

---

### Post by rabbitfarmer on 2011-02-05
ah lol XD got it now thanks for all the help!

---

### Post by rabbitfarmer on 2011-02-08
Well i've been trying for a few days now, but i can't seem to get it to work. the functions are running without being called, and they don't work when they are called. i don't understand what's wrong. if anybody has advice it would be appreciated, thanks.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>paragraph funzies</title>
<h1 align="center">header<h2>

<script LANGUAGE="Javascript" type="text/javascript" src="senTest.js"></script>
</head>

<body>
<div align="center">
<a href="testpage.html">
<button align="center">Refresh me!
</button>
</a>
</div>
<div>
<table align="center" height="auto" width="auto" border="0">

<tr width="auto">
<td width="auto">
<SCRIPT LANGUAGE="JavaScript" type="text/javascript">
        
           javascript: picfun();
         
</SCRIPT>
</td>
<td width="auto">
.
</td>
</tr>
</table>

</div>
</body>
</html>
```

that's the html
now here's the javascript 

```
var funcArray = new Array();
funcArray[0]= alert ("1");
funcArray[1] = alert ("2");
funcArray[2] = alert ("3");



var func = funcArray[Math.floor ((Math.random() * funcArray.length))];


if (randomNum==undefined) {
    document.write ("omg stop it plox")
}

javascript=picfun();

function picfun() {

document.write ("<title>" + func + "</title>")

document.write ("<p align='center'>" + func + "</p>")

}

WordCN=new Array
WordCN[0]="because he wants"
WordCN[1]="to become"
WordCN[2]="to the top of"
WordCN[3]="underneath"
WordCN[4]="for"
WordCN[5]=""
WordCN[6]="forcefully at"
WordCN[7]="to the side of"
WordCN[8]="all the way around"
WordCN[9]="outside of"



CNCount=WordCN.length
javascript=picPhraseCN();

function picPhraseCN() {
randomNum1=Math.floor ((Math.random() * CNCount))
trashTalk1=WordCN[randomNum1]
document.write ("<title>" + trashTalk1 + "</title>")
document.write ("<p align='center'>" + trashTalk1 + "</p>")
}

WordTS=new Array
WordTS[0]=" This initiates"
WordTS[1]=" This triggers"
WordTS[2]=" Indirectly, this causes"
WordTS[3]=" This starts a chain of events that causes"
WordTS[4]=" This in turn causes"
WordTS[5]=" This causes"


TSCount=WordTS.length
javascript=picPhraseTS();

function picPhraseTS() {
randomNum2=Math.floor ((Math.random() * TSCount))
trashTalk2=WordTS[randomNum2]
document.write ("<title>" + trashTalk2 + "</title>")
document.write ("<p align='center'>" + trashTalk2 + "</p>")
}

WordNS=new Array
WordNS[0]="A man"
WordNS[1]="Your friend"
WordNS[2]="A small dog"
WordNS[3]="An upsidedown cake"
WordNS[4]="The NBA"
WordNS[5]="Chuck Norris"
WordNS[6]="Herbie Hancock"
WordNS[7]="Steve Jobs"
WordNS[8]="A Bannana"
WordNS[9]="A small, furry animal"
WordNS[10]="Bigfoot"
WordNS[11]="Obama"
WordNS[12]="A pnuematic actuator"
WordNS[13]="A soccer ball"
WordNS[14]="A chip"
WordNS[15]="A chair"
WordNS[16]="A very strange man"


NSCount=WordNS.length
javascript=picPhraseNS();

function picPhraseNS() {
randomNum3=Math.floor ((Math.random() * NSCount))
trashTalk3=WordNS[randomNum3]
document.write ("<title>" + trashTalk3 + "</title>")
document.write ("<p align='center'>" + trashTalk3 + "</p>")
}

```
as you can see i've tried to disable the functions i want called on and replaced them with alerts. when i load the page, they all pop up, as well as all the functions. they do this where the script code is in the head. When i actually call the function further down, all i get is "undefined". any help would be nice

---

### Post by myrtle1908 on 2011-02-08
There are far far too many problems with your code to point out.  I'm afraid it's a mess!

Are you simply trying to randomly select items (strings) from a number of arrays, then write them to the screen?  If so, adapt the example I posted a few days ago.

I don't see the need for all these functions.  You only need three arrays (your strings), code to select items at random and do something with the strings ... or am I misunderstanding what you want?

---

### Post by rabbitfarmer on 2011-02-08
okay, so in the end what i finally want to do is make a random paragraph generator. I want a function to randomly choose one of my predefined sentence structures. each of these sentences will randomly choose words according to their type. So, i need to create a function that will randomly choose a string of functions to write on my html page. I have tried writing it many different ways, but i can't seem to figure out how to make a function randomly choose a function. I know how to make it randomly choose and write a word, but basically i can't get the syntax right to write the value of a function instead. I know my above example was pretty bad, i was just messing around trying to get it to work, most of it i don't even need there. so basically how do i write a function that calls a string of other functions?

---

### Post by myrtle1908 on 2011-02-09
> **rabbitfarmer said:**
> So, i need to create a function that will randomly choose a string of functions to write on my html page.

You mean to write a function to the page that will be called in-line?  For example like you attempted in an earlier post ...

```
var func = funcArray[Math.floor ((Math.random() * funcArray.length))];

... snip ...

document.write ("<title>" + func + "</title>")
```

This is generally not good practice (and actually won't work in that example).  There are much better ways ...

See if the following example can point you in the right direction.  Sure it's crude but should demonstrate how you could build up your paragraph (sentence in my example) and write it to an area on the screen/page (in this case a DIV with ID 'mySentence').

Save the following to a HTML file and open in Firefox or Chrome.  Hit refresh and the sentence should change slightly.

```
<script language="javascript">

var writeSentence = function(){
  var greets = 'Hi,Hello,Hey'.split(','),
      peeps = 'Jim,John,Jack'.split(','),
      time = 'morning,day,evening'.split(',');
  var i = Math.floor(Math.random()*greets.length);
  var j = Math.floor(Math.random()*peeps.length);
  var k = Math.floor(Math.random()*time.length);
  var s = [];
  s.push(greets[i]);
  s.push(peeps[j] + ', how are you this fine');
  s.push(time[k] + '?');
  document.getElementById('mySentence').innerHTML = s.join(' ');
  
};

window.onload = writeSentence;

</script>

<div id="mySentence"></div>
```

Also, you should use Firebug or Chrome's dev tools to help you step through JavaScript code and inspect the DOM at runtime etc.

---

### Post by rabbitfarmer on 2011-02-17
okay sorry for the long delay and thanks for the help, but I can already generate a random sentence fairly well, what i need to do is randomly adjust the order of said sentences. Well i did want to and now i have given up on that, instead switching to replacing the contents of a division on click, and have the division go through pre-set paragraph structures in a pre-determined order. I have almost figured out how to do this, but i can't seem to make it work right, instead it just writes my function value over the whole web page, deleting the header and all other elements. here is the code i am using,
```

<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>paragraph funzies</title>
<h1 align="center">header<h2>

<script LANGUAGE="Javascript" type="text/javascript" src="WordTS.js"></script>

<script LANGUAGE="Javascript" type="text/javascript" src="senTest.js"></script>
</head>

<body>
<div align="center">

<button onclick="rewrite()" align="center">Refresh me!
</button>


</div>
<div>

<script  id="words" type="text/javascript">

</script>


</div>
</body>
</html>
```
that's the html, here are the two js files

```
 function rewrite(){
    document.getElementById("words").innerHTML = picPhraseTS()
}
```

```

WordTS=new Array
WordTS[0]=" This initiates"
WordTS[1]=" This triggers"
WordTS[2]=" Indirectly, this causes"
WordTS[3]=" This starts a chain of events that causes"
WordTS[4]=" This in turn causes"
WordTS[5]=" This causes"


TSCount=WordTS.length


function picPhraseTS() {
randomNum=Math.floor ((Math.random() * TSCount))
trashTalk=WordTS[randomNum]
document.write ("<title>" + trashTalk + "</title>")
document.write ("<p align='center'>" + trashTalk + "</p>")
}
```

right now i'm just trying to get this to work, but for some reason it won't. and i tried putting document.getElementById("words").innerHTML = "javascript: picPhraseTS();" and then nothing happened.

---

### Post by rabbitfarmer on 2011-02-26
anyone, anything?

---

### Post by ve4cib on 2011-02-27
Your picPhraseTS function is not returning anything, so your innerHTML=... line is setting the inner html to undefined.

You either need to remove the assignment and have picPhraseTS function do the writing by setting the div's inner html, or change that function to return a string.

---

### Post by rabbitfarmer on 2011-03-02
ok i think i understand that. I have one more question, and i know this may not be the right place to post it, but maybe you guys know something. On another page of mine i have a bunch of functions that call another function in three seconds. this part works good, but i cannot figure out how to stop it. i think i'm close but not quite sure. here is the .js file

```
function next () {
     document.getElementById("pond").innerHTML="<img src='blocks/block1.png' height='76px' width='76px' onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next2()",3000);
     
 }

 

 function next2 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block2.png' height='76px' width='76px' onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next3()",3000);

 }
 
 function next3 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block3.png' height='76px' width='76px'  onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next4()",3000);

 }
 
 function next4 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block4.png' height='76px' width='76px'  onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next5()",3000);

 }
 
 function next5 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block5.png' height='76px' width='76px'  onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next6()",3000);

 }
 
 function next6 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block6.png' height='76px' width='76px'  onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next7()",3000);

 }
 
  function next7 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block7.png' height='76px' width='76px'  onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next8()",3000);

 }
 
  function next8 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block8.png' height='76px' width='76px'  onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next9()",3000);

 }
 
  function next9 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block9.png' height='76px' width='76px'  onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next10()",3000);

 }
 
  function next10 () {
     document.getElementById("pond").innerHTML="<img src='blocks/block10.png' height='76px' width='76px'  onmouseout='reset()' onmouseup='reset()'>"
     var t=setTimeout("next11()",3000);

 }
 
  function next11 () {
     document.getElementById("pond").innerHTML=""
     document.getElementById("pond").onclick="next()"
     

 }

  function reset () {
     document.getElementById("pond").innerHTML=""
         document.getElementById("pond").onclick="next()"
     clearTimeout();
     
 }
 
```

the reset() function is the one i want to stop all the timed functions, any advice?

---

### Post by ve4cib on 2011-03-02
You need to specify what timeout you want to clear.  Simply calling "clearTimeout();" will not do anything; it needs an argument.

I would probably tweak your code to look something more like this:

```

var myTimeout;

function startTimer() {
    myTimeout = setTimeout(doSomething, 3000);
}

function reset() {
    clearTimeout(myTimeout);
}

function doSomething() {
   ...
}

```

The key difference is that myTimeout's scope is not contained within any particular function; it's effectively global, and therefore accessible from any function.  When you call clearTimeout you pass it the timeout you want to clear (myTimeout in this example).

---

### Post by myrtle1908 on 2011-03-02
You could push all your timeout IDs into an array and loop through that array in reset and clear the timeouts.  For example (untested)...

```
var TID = [];
function next() {
  ...
  TID.push(setTimeout("next2()",3000));
}
function next2() {
  ...
  TID.push(setTimeout("next3()",3000));
}
...
function reset() {
  ...
  for (var i=0; i<TID.length; i++) {
    clearTimeout(TID[i]);
  }
}
```

As an aside, you probably only need a single generic *next* function ... however, that's most likely beyond the scope of OPs question.

---

### Post by rabbitfarmer on 2011-03-02
Ah thanks so much! set a global variable and then used it in all the functions, made all the difference thanks for all the help!

---

