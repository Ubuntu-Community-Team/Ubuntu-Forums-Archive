---
title: "Javascript Issue"
date: 2008-03-08
forum: Programming Talk
---

### Post by The Titan on 2008-03-08
this issue is eiser showed than said:

```

window.onload = initAll;
var xPos, yPos;
var xhr = false;

function initAll(){
    var allSpan = document.getElementsByTagName("span");
    
    for(var i=0; i<allSpan.length; i++){
    
        allSpan[i].onmouseover = showPreview;
        
    }

}

function showPreview(evt){
    if(evt){
        var url = "includes/mouseover.php?id=" + (i want to get an attribute off of whatever element/tag this is in)
    }else{
        evt = window.event;
        var url = "includes/mouseover.php?id=" + (i want to get an attribute off of whatever element/tag this is in)
    }
    xPos = evt.clientX;
    yPos = evt.clientY;

```this is not near the entire script, just the necessary part.  I am really bad at javascript... can someone help please?

---

### Post by smartbei on 2008-03-08
If I understand you correctly, you want to add mouse-over functionality to all the spans in your html page (quite odd really - wouldn't it make more sense to use a class?) and want the behavior to be different, depending on which span was mouse-overed.

I think you can find what you are looking for here: [http://www.quirksmode.org/js/events_properties.html#target](http://www.quirksmode.org/js/events_properties.html#target)

---

### Post by The Titan on 2008-03-08
haha, i do everything odd.  i was using spans because i couldn't think of anything else to use.  You just double helped me out..  Thank you VERY MUCH!

---

