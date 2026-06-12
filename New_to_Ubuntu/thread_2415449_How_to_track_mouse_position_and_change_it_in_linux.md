---
title: "How to track mouse position and change it in linux"
date: 2019-03-25
forum: New to Ubuntu
---

### Post by outwere on 2019-03-25
In windows I can use <windows.h> and

 POINT p;
 while (1) {
  GetCursorPos(&p);
  SetCursorPos(p.x + 3, p.y);

to get the position and change it.

How do I do the same in Linux? Thanks.

---

### Post by wildmanne39 on 2019-03-25
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by outwere on 2019-03-25
I found some said reading and writing in the file /dev/input/mice. 
It does not work on my computer, though. The system is Ubuntu 18.04.2 LTS

---

### Post by Impavidus on 2019-03-26
When I program I mostly make command line tools, or sometimes tools with command line input but graphical output, but I've made a few programs that use the mouse. I think it's best to use some API that can tell you the mouse position and that's somewhat portable at the same time. Last time I used GLFW. If you install it along with the documentation, the manual should be on your system.

/dev/input/mice shouldn't work, as applications should only know about mouse events in their own window. It only has read and write access for root and the input group.

---

### Post by TheFu on 2019-03-27
I've always used testing programs that send x-events - usually there isn't any need to move the mouse since we can just send the button-click event to the button directly.  There are keyboard and mouse recording tools which can be played back.  I've been out of this field long enough that I don't recall any names anymore. We used commercial tools which weren't too cheap.

Google found these: [https://nnc3.com/mags/LM10/Magazine/Archive/2007/84/056-059_xnee/article.html](https://nnc3.com/mags/LM10/Magazine/Archive/2007/84/056-059_xnee/article.html) says something about xnee, gnee, and cnee.
gnee and cnee are in the 16.04 repos.

---

