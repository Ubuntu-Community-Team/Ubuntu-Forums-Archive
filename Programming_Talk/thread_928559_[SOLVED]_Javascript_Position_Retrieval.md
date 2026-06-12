---
title: "[SOLVED] Javascript Position Retrieval"
date: 2008-09-24
forum: Programming Talk
---

### Post by JohnSearle on 2008-09-24
I'm currently trying to determine the left and top positions of a table cell that is currently set to 'auto' (as opposed to 'absolute').

I can determine this by:

```
leftPos = element.style.left;
topPos = element.style.top;
```

when the element is an absolute position, but when it is set to auto it returns nothing. Is there anyway of determining this? 

I just attempted to nest a 'div' inside the cell with an undefined absolute position, hoping that it would be by default set by the parent cell, but it seems to have overridden the auto placement instead.

EDIT: I should also note, the reason why I have it set to auto is because I want to centre the entire document. If there was a way to centre the elements (similar to a center tag), but use absolute positioning so the left and top properties contain a value, then that would be good too.

Thanks for any help.

- John

---

### Post by JohnSearle on 2008-09-24
After quite a bit of searching, I found my answer...

Here's the function that needs to be created to determine the absolute position of a nested element.

```
function getAbsolutePosition(elementId) {
	var offsetTrail = document.getElementById(elementId);

	var leftPos = 0;
	var topPos = 0;
	
	while(offsetTrail) {
		leftPos += offsetTrail.offsetLeft;
		topPos += offsetTrail.offsetTop;
		
		offsetTrail = offsetTrail.offsetParent;		
	}
	
	return {left:leftPos, top:topPos};
}
```

The offsetLeft and offsetTop determine the position relative to the parent element, and offsetParent determines the parent element. So, you have to create a loop that keep jumping backwards and adding up all the offset positions to determine the absolute.

Maybe this will help someone at some point :)

- John

---

