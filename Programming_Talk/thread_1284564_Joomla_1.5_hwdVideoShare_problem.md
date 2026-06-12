---
title: "Joomla 1.5 hwdVideoShare problem"
date: 2009-10-06
forum: Programming Talk
---

### Post by Black Mage on 2009-10-06
I just recently installed the hwdVideoShare for videos in Joomla 1.5 and I thought I had it set up correctly except its not showing up. All the shows up is this: 

[http://www.tealtv.org/index.php?option=com_hwdvideoshare&task=categories&Itemid=6](http://www.tealtv.org/index.php?option=com_hwdvideoshare&task=categories&Itemid=6)

or this:

[http://www.ikeelliswill.com/index.php?option=com_hwdvideoshare&Itemid=10](http://www.ikeelliswill.com/index.php?option=com_hwdvideoshare&Itemid=10)

I tried it on two seperate layouts in case the template was the problem. So anyone know why this is happening?

---

### Post by januzi on 2009-10-06
There is a problem with the layout itself. Like in the second one: 
1. All I can see is tags-tree 
> 
<div>
 <div> 
  <div>
   <div>
etc

2. There are mess in the css file (like overflow: hidden in .clear).

As for videos, they are working just fine.

---

### Post by Black Mage on 2009-10-06
THANKS!!!


So its probably a CSS issue then.

I am assuming you were looking here: [http://www.ikeelliswill.com/components/com_hwdvideoshare/core/template.css](http://www.ikeelliswill.com/components/com_hwdvideoshare/core/template.css)

What would you suggest the overflow be changed to?

---

### Post by Black Mage on 2009-10-06
I seemed to have fixed it by removing this line.

.clear {clear: both; height: 1px; line-height: 1px; margin-bottom: -1px;}

---

