---
title: "javascript keyboard controls"
date: 2007-09-23
forum: Programming Talk
---

### Post by zach12 on 2007-09-23
Hello 
i've been useing javascript for a few weeks and am trying to make a game

Any way i just need some help with useing the arrow keys with keyp

this does not work with firefox (1.5 or 2.0)on ubuntu

left arrow  37
up arrow     38
right arrow  39
down arrow 40

and here's my code
> function getkeypress(keypress) {

 //when they press a key, if it is a movement key, set the movement variable

 keyp = (isNS || isNS6) ? keypress.which : window.event.keyCode;

 //alert(keyp);

 if (keyp == 37) p1y = -1;  //K8

 if (keyp == 40) p1y = 1;   //K2

 if (keyp == 39) p1x = -1;  //K4

 if (keyp == 38) p1x = 1;   //K6

 

 return false;

}
thanks:lolflag:

---

### Post by zach12 on 2007-09-23
"bump"

---

### Post by mssever on 2007-09-24
Have you used the Firebug extension to find out which key codes are actually being sent?

---

### Post by zach12 on 2007-09-24
no have not i will try it

---

### Post by mssever on 2007-09-24
Another thing: Browser detection is evil. Don't do it. Use object detection instead. Can you really test your script in every browser that any visitor will ever use? See [http://www.quirksmode.org/js/support.html](http://www.quirksmode.org/js/support.html) for a bit more.

---

### Post by zach12 on 2007-09-24
will someone test this out
it's just not working

---

### Post by mssever on 2007-09-24
You just gave a bare function. It does nothing. Make up a test case, then maybe someone will try it.

---

### Post by zach12 on 2007-09-25
Here's my code and i will attach the js map file
thanks a ton!
> <html>

<body leftmargin="0" topmargin="0" marginheight="0" marginwidth="0">

<div id="player1" name="player1" style="position:absolute;top:0;left:0;z-index:2;"><img name="player1icon" src="guy_right.gif"></div>



<script>

//initial global variable for map and load map.js to set map values

scrn = new Array();

</script>

<script src="map.js"></script>



<script>

//isNS is true if the browser is Netscape, false if it is Internet Explorer

isIE = (document.all) ? 1 : 0;

isNS = (!document.getElementById && document.layers) ? 1 : 0;

isNS6 = (!document.all && document.getElementById) ? 1 : 0;



//set browser to capture keystrokes

if (isNS || isNS6) window.captureEvents(Event.KEYPRESS);

if (isNS || isNS6) document.captureEvents(Event.KEYPRESS);

window.onkeypress = getkeypress;

document.onkeypress = getkeypress;



rows = 10;     //number of table rows and columns

iconsize = 31; //size of each grid cell

p1CurX=0;      //player1 current x position

p1CurY=0;      //player1 current y position

p1x=0;         //player1 x movement

p1y=0;         //player1 y movement

map=0;         //current screen



//draw the map grid

document.write('<table background="grass.gif" cellspacing="0" cellpadding="0" border="0">');

for (i=0; i<rows; i++) {

 document.write(' <tr>');

 for (j=0; j<rows ;j++) {

  document.write('<td><img name="r'+i+'c'+j+'" src="no.gif"></td>');

 }

 document.write(' </tr>');

}

document.write('</table>');



//initalize empty array to store the type of each map cell

iconType = new Array(rows);

for (i=0; i<rows; i++) {

 iconType[i] = new Array(rows);

}



//p1 is a reference to the <div> player1

if (isNS) p1 = document.player1;

else if (isNS6) p1 = document.getElementById("player1").style;

else if (isIE) p1 = document.all.player1.style;



//p1icon is a reference to the player image icon

if (isNS) p1icon = document.player1.document.player1icon;

else if (isNS6) p1icon = document.getElementById("player1").getElementsByTagName("img")[0];

else if (isIE) p1icon = document.all.player1icon;



setstart(); //sets player starting position on map

showmap();  //draws the map



//every 100 miliseconds, call the animate function

setInterval('animate()',100);



function setstart() {

  //set player starting position on map

  p1icon.src = "guy_right.gif";

  p1CurX = 1;

  p1CurY = 1;

  

  p1.left = p1CurX * iconsize;

  p1.top = p1CurY * iconsize;

}



function showmap() {

 

 

 for(i=0; i <= rows-1; i++) {  

  for(j=0; j <= rows-1; j++) { 

   

   if (scrn[map].split("\n")[i].split(";")[j*2] != "") { 

    eval('document.r' + i + 'c' + j + '.src="' + scrn[map].split("\n")[i].split(";")[j*2] + '.gif"');

   } else {
    eval('document.r' + i + 'c' + j + '.src="no.gif"');

   }

  
   iconType[i][j] = scrn[map].split("\n")[i].split(";")[(j*2)+1];

  }

 }

}



function animate() {

 

 if (p1x != 0) {

  if (p1x > 0) p1icon.src = "guy_right.gif";

  if (p1x < 0) p1icon.src = "guy_left.gif";

  

  

  if ((p1CurX + p1x >= 0) && (p1CurX + p1x < rows)) {

   )

   if (iconType[p1CurY][(p1CurX * 1) + (p1x * 1)] == 0) {

    

    p1CurX += p1x;

    p1.left = p1CurX * iconsize;

   } else if (iconType[p1CurY][(p1CurX * 1) + (p1x * 1)].indexOf("2") == 0) {

   

    doJump(iconType[p1CurY][(p1CurX * 1) + (p1x * 1)]);

   }

  }

  p1x = 0;

 }

 



 if (p1y != 0) {

  if (p1y > 0) p1icon.src = "guy_front.gif";

  if (p1y < 0) p1icon.src = "guy_back.gif";

 
  if ((p1CurY + p1y >= 0) && (p1CurY + p1y < rows)) {


   if (iconType[(p1CurY * 1) + (p1y * 1)][p1CurX] == 0) {

  

    p1CurY += p1y;

    p1.top = p1CurY * iconsize;

   } else if (iconType[(p1CurY * 1) + (p1y * 1)][p1CurX].indexOf("2") == 0) {

    

    doJump(iconType[(p1CurY * 1) + (p1y * 1)][p1CurX]);

   }

  }

  

  p1y = 0;

 }

}



function doJump(tmpType) {  

 map = tmpType.split("-")[1] * 1;

 p1CurX = tmpType.split('-')[2] * 1;

 p1CurY = tmpType.split('-')[3] * 1;

 p1.left = p1CurX * iconsize;

 p1.top = p1CurY * iconsize;

 showmap();

}



function getkeypress(keypress) {

 
 keyp = (isNS || isNS6) ? keypress.which : window.event.keyCode;

 //alert(keyp);

 if (keyp == 38) p1y = -1;  //K8

 if (keyp == 40) p1y = 1;   //K2

 if (keyp == 39) p1x = -1;  //K4

 if (keyp == 37) p1x = 1;   //K6

 if (keyp == 55) {p1x = -1;p1y = -1;} //K7

 if (keyp == 57) {p1x = 1;p1y = -1;}  //K9

 if (keyp == 49) {p1x = -1;p1y = 1;}  //K1

 if (keyp == 51) {p1x = 1;p1y = 1;}   //K3

 return false;

}
//this is a rpg game coded just for fun!
</script>



</body>

</html>


---

### Post by zach12 on 2007-09-25
ok and here's my map
thanks

PS 
ubuntu forums doen't like you to attach .js file


so here's the map code
just save it as js

> scrn[0] = ""
scrn[0] += "tower;2-1-1-1;block;0;tree;1;water_left;1;water;1;water;1;water_right;1;block;0;tree;1;tower;2-1-1-1;\n"
scrn[0] += "tree;1;block;0;inverter%20houes;2-9-8-8;water_start_up;1;water_up;1;water_up;1;water_end_up;1;block;0;tree;1;tree;1;\n"
scrn[0] += "block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;\n"
scrn[0] += "tree;1;block;0;tree;1;wall_bridge;0;block;0;wall_bridge;0;tree;1;block;0;tower2;2-0-9-9;tower2;2-0-0-7;\n"
scrn[0] += "shop3;2-9-7-4;block;0;hobbit%20hut%20HA;2-9-9-9;block;0;manehut;2-8-9-0;block;0;toy%20shop;2-9-9-4;block;0;shop1;2-9-9-7;block;0;\n"
scrn[0] += "block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;\n"
scrn[0] += "tree;1;block;0;tree;1;block;0;manehut;2-2-1-1;block;0;tree;1;block;0;treefirm;1;treefirm;1;\n"
scrn[0] += "portpod;0;block;0;tree;1;tree;1;block;0;tree;1;portpod1;0;block;0;treefirm;1;treefirm;1;\n"
scrn[0] += "block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;block;0;\n"
scrn[0] += "tower;2-1-1-1;wall;0;wall_down;1;wall;0;wall;0;wall_down;1;wall;0;wall_down;1;wall;0;tower;2-1-1-1;\n"


---

### Post by mssever on 2007-09-25
Can you make up a test case? In other words, the function that has a problem and some minimal code that calls it. That way, it's possible to isolate the problem, rather than working through the whole program. Also, please surround code in [CODE] tags, not [QUOTE] tags. CODE tags preserve formatting.

Also, you can use document.getElementById without using a browser detect. All browsers except for dinosaurs support it. No need for browser detects.

---

### Post by zach12 on 2007-09-26
ok thanks
i will do that

---

