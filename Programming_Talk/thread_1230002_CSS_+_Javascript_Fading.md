---
title: "CSS + Javascript Fading?"
date: 2009-08-02
forum: Programming Talk
---

### Post by ArmenianLeader4 on 2009-08-02
I'm working on a website where I need to use a mouseover CSS + JavaScript function to make buttons display seperate images on mouseover. Here's part of my code:
> <style type="text/css"> 
<!-- 
body { 
    background-color: #FFFFFF; 
    background-image: url("default.jpg"); 
 
} 
#tic { 
  border: .05em #000000 solid; 
  font-size:0.85em; 
  padding:10px; 
  inset;background-color:white; 
  width:400px; 
  line-height:20px; 
} 
#tic * { 
  font-size: 1em; 
  margin:0px; 
  color:#000000; 
  padding:0px; 
  display:none; 
} 
#tic a { 
  display:inline; 
  color:#000000; 
} 
#drawing { 
    position:absolute; 
    width:206px; 
    height:191px; 
    z-index:1; 
    visibility: hidden; 
} 
#figure { 
    position:absolute; 
    width:206; 
    height:191; 
    z-index:2; 
    visibility: hidden; 
} 
#interior { 
    position:absolute; 
    width:206; 
    height:191; 
    z-index:3; 
    visibility: hidden; 
} 
#landscape { 
    position:absolute; 
    width:206; 
    height:191; 
    z-index:4; 
    visibility: hidden; 
} 
#stilllife { 
    position:absolute; 
    width:206; 
    height:191; 
    z-index:5; 
    visibility: hidden; 
} 
--> 
</style> 
<script type="text/JavaScript"> 
<!-- 
function MM_findObj(n, d) { //v4.01 
  var p,i,x;  if(!d) d=document; if((p=n.indexOf("?"))>0&&parent.frames.length) { 
    d=parent.frames[n.substring(p+1)].document; n=n.substring(0,p);} 
  if(!(x=d[n])&&d.all) x=d.all[n]; for (i=0;!x&&i<d.forms.length;i++) x=d.forms[i][n]; 
  for(i=0;!x&&d.layers&&i<d.layers.length;i++) x=MM_findObj(n,d.layers[i].document); 
  if(!x && d.getElementById) x=d.getElementById(n); return x; 
} 
 
function MM_showHideLayers() { //v6.0 
  var i,p,v,obj,args=MM_showHideLayers.arguments; 
  for (i=0; i<(args.length-2); i+=3) if ((obj=MM_findObj(args[i]))!=null) { v=args[i+2]; 
    if (obj.style) { obj=obj.style; v=(v=='show')?'visible':(v=='hide')?'hidden':v; } 
    obj.visibility=v; } 
} 
//--> 
</script>

Is there any way that I can create a fade-to-black type effect between image transitions using Java?

---

### Post by Reiger on 2009-08-02
Using JavaScript? Yes. If you do a bit of Google-research for "alpha" "opacity" and "JavaScript" you should get plenty of hits (including tutorials) on how to get a (reasonably) cross-browser effect to fade (make translucent) images.

Wrap that functionality in a JavaScript functions of your own, define a wrapper function to call that function and which calls itself after a timeout like so:

```

function fade(img) {
 var opacity = getOpacity(img); // helper function returns opacity in percent
 if(opacity > 0) {
   setOpacity(img, opacity - 10); // helper function sets opacity in percent
   return true;
 }
 return false;
}

function fadeOut(img) {
  if(fade(img)) {
    setTimeout(fadeOut, 50, img);
  }
}

```

---

### Post by Mirge on 2009-08-02
[jQuery]("http://www.jquery.com/")

---

