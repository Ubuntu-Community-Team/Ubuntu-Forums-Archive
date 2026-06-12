---
title: "Resolution in JavaScript"
date: 2009-06-08
forum: Programming Talk
---

### Post by vandetta on 2009-06-08
I have a problem with JavaScript application,
This application would not display anything if we open it in high screen resolution
It is designed quite a time ago when the wide screen monitors is not widely used
It is designed on 1024 x 768 resolution. If we open it in 1024 x 768 and below (800 x 600, 640 x 480) it will display the content normally
But if we open in in higher screen resolution like 1152 x 864, 1280 x 600, 1280 x 720, 1280 x 768 and 1440 x 900 it would not display the content
What might be the problem?
Here I put together screen shot and the coding.

Cannot display, in 1440 x 900 resolution
[img]http://i16.photobucket.com/albums/b34/lazrus/NotOK.jpg[/img]

Displayed, in 1024 x 768 resolution
[img]http://i16.photobucket.com/albums/b34/lazrus/OK.jpg[/img]

I think there might be problem at this part in the coding, but you guys can take a look at the coding then

function setSH(hi){
if(hi==600){sHeight=403}
if(hi==768){sHeight=535}
if(hi==864){sHeight=575}
if(hi==1024){sHeight=719}
}

In order to use it in higher screen resolution, we need to lower the resolution, very troublesome, hope you guys can give me suggestion on solutions, help is highly appreciated!

---

### Post by leblancmeneses on 2009-06-08
why use javascript for this?

much easier with basic html and a couple of css rules.. 
example:
```




<body style="margin:0px; padding:0px;">
  <div style="position:absolute; left:25px; right:25px; top:0px;">
     <table>
       <tr>
            <td>
               row 1 column 1
             <td>
            <td>
               row 1 column 2
             <td>
         </tr>
       <tr>
            <td>
               row 2 column 1
             <td>
            <td>
               row 2 column 2
             <td>
         </tr>
      </table>

  </div>
</body>


```

---

### Post by vandetta on 2009-06-08
Mean that I have to change the HTML part and put the table and column like that?

I think it is already like that, but will try to edit again.

---

### Post by vandetta on 2009-06-08
Not working, still same.. Other suggestion guys?

---

### Post by Reiger on 2009-06-08
```

function setSH(hi){
if(hi==600){sHeight=403}
if(hi==768){sHeight=535}
if(hi==864){sHeight=575}
if(hi==1024){sHeight=719}
}
```

Pardon my words but that is some poor coding there (this kind of comparison should use a switch() statement; there are only 4 cases out of a myriad of possibilities covered; lacking semi colons, and the code style makes it look much more ambiguous than it needs to be)

A cleaned up version would be akin to:
[php]
function setSH(hi){
  switch(hi) { 
    case 600 : sHeight= 403; break;
    case 768 : sHeight= 535; break;
    case 864 : sHeight= 575; break;
    case 1024: sHeight= 719; break;
    default  : sHeight= Math.floor(0.5 + hi * 0.7); /* by default return 70% of the hi value because that looks like the ratios of the other figures */
  }
}
[/php]

A more elaborate solution (which you may prefer) is to do this as follows: 

```

function setSH(hi,algorithm) {
  var myfunc;
  if(typeof(algorithm) != 'undefined')
   myfunc = algorithm;
  else
   myfunc = function (value) {
    switch(value) { /* return bypasses the break anyways, therefore omit it. */
     case 600 : return 403;
     case 768 : return 535; 
     case 864 : return 575;
     case 1024: return 719;
     default : return Math.floor(0.5 + 0.7 * value); // return 70% of the value, looks like the other ratios
    }
  };
  sHeight = myfunc(hi);
}

```

If you want to supply your custom re-sizing algorithms you can then do so using a function that can take 1 argument.

---

### Post by vandetta on 2009-06-08
I have found the solution by myself, need to edit few lines of coding as I pasted below:

setSH(screen.height)
Propath=par2[2]+"/"+par2[2]+"/"+par2[2]
Propath2="|"+par2[2]+"|"+par2[2]+"|"+par2[2]
MainJs.src=Propath+"/Main.js"
Myscript.src="Lngjs/"+par2[0]+".js"
Myscript.src="Lngjs/"+par2[0]+".js"
userlang.src="Level1/LangInfo/"+par2[0]+".js"

function setSH(hi){
if(hi<=600) sHeight=403;
else if(hi<=768) sHeight=535;
else if(hi<=864) sHeight=575;
else sHeight=719;
}

</script>

<script src='index.js'></script>
<script>
var OnMenu=0;Box='';BoxT='';BoL=0
document.write('<div style="position: absolute; width: 50px; height: 50px; z-index: 3; left:10px; top:20px;visibility:hidden;" id="MenuBox"></div>')

Thank you!

---

### Post by vandetta on 2009-06-08
BTW, thank you Reiger, I came out with the idea after read your suggestion :)

---

