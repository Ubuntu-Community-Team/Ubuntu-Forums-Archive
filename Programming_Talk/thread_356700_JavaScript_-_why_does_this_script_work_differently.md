---
title: "JavaScript - why does this script work differently on Firefox than on IE or Opera?"
date: 2007-02-08
forum: Programming Talk
---

### Post by Van_Gogh on 2007-02-08
Hi,

I'm trying to get a site's javascript to work with Mozilla Firefox. I'm trying to get JavaScript to correctly resize a div.  The code is almost working, but the onMouseUp works differently for FF than for IE or Opera.

That is, clicking and resizing a <td> element works fine for all browsers, but on <td><img></td> Firefox won't let onMouseUp run and set move to false.

For reference, this is the script. I'd appreciate any help.

```
<script>
// Resize listboxes

var move = false;
var position;
var new_position;
var listbox;
document.onmouseup = onMouseUp;
document.onmousemove = onMouseMove;

function onMouseDown(event, boxno) 
{
   move = true;
   if(event) position = event.pageX
   else      position = window.event.x;
   listbox = boxno;
}
function onMouseMove(event) 
{
   if (move) 
  {
	  if(event) new_position = event.pageX
	  else      new_position = window.event.x;
      ResizeListbox(new_position - position, listbox);
      position = new_position;
      return false;
   }
}
function onMouseUp() 
{
   move = false;
}

function ResizeListbox(whereto, boxno) 
{
	var begin = document.forms['main'].elements[boxno].style.width;
	var intbegin = parseInt(begin);
	var newwidth = intbegin + whereto;
	if (newwidth > 0) 
	{
		document.forms['main'].elements[boxno].style.width = newwidth;
	}
}

//-->
</script>

```

---

### Post by Note360 on 2007-02-08
IDK why but I know that IE and Opera use different systems to handle JS.

---

### Post by mavigozler on 2007-02-09
1. You need to verify that an event can be associated with a DOM object.  Not all mouse events work for all DOM objects, despite your defining the event handling for the "document" object.  Check the HTML 4 specification.  Yes, IE and other browsers may do handle an event for a TD or IMG element, but Microsoft is notorious for going beyond standards.  Do NOT rely on extensions not defined by the W3C.  Mozillla/Firefox is probably one of the few to stick to the standards, and which is why the event does not work the way you expect it to.

2. You might want to specifically define an event handler for all element (all document objects of a certain type) or a specific elements (e.g. <td onmouseup="myEventHander();return (false);">) rather than hope that there is an event capture as the event moves up or down.  Note that IE and FF and others differ about the start and finish (direction) of an event and what object captures it.

---

### Post by Grey on 2007-02-09
This should be your bible when it comes to DOM scripting.  The [Gecko DOM Reference](http://developer.mozilla.org/en/docs/Gecko_DOM_Reference).  It specifies what Mozilla supports, and specifies whether the features are legacy, or standard.  In this case, I might suggest trying [event listeners](http://developer.mozilla.org/en/docs/DOM:element.addEventListener), instead of the explicit events.  With a bit of work, they work in IE as well.  You just need to write a wrapper function that uses IE's attachevent, rather than an eventListener, if the browser is found not to support W3C standards.

---

