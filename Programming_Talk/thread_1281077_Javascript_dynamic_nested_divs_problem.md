---
title: "Javascript dynamic nested divs problem"
date: 2009-10-02
forum: Programming Talk
---

### Post by gradysghost on 2009-10-02
I really hope I can get some help here.  I'm having a problem.  I'll start with a snippet (the important part) of my JavaScript:

```
this.domFrame=document.createElement("div");
this.domFrame.id=this.domId;
this.domFrame.setAttribute("class", "window");
this.domFrame.style.top=this.location.y+"px";
this.domFrame.style.left=this.location.x+"px";
this.domFrame.style.width=this.size.width+"px";
this.domFrame.style.height=this.size.height+"px";

this.domTitle=document.createElement("div");
this.domTitle.id=domId+"title";
this.domTitle.setAttribute("class", "windowtitle");
this.domTitle.setAttribute("onmousedown", "dragMe(event, '"+domId+"');");

this.domContents=document.createElement("div");
this.domContents.id=domId+"contents";
this.domContents.setAttribute("class", "windowcontents");
this.domContents.setAttribute("onclick", "bringToFront('"+this.domId+"');");

this.parent.appendChild(this.domFrame);
this.domFrame.appendChild(this.domTitle);
this.domFrame.appendChild(this.domContents);
```

Please understand that this is inside of a function-style JavaScript "class" with certain variables already defined, hence the "this" keyword all over the place.  This code is supposed to generate a div which contains two other divs.  The end result is a "window" looking thing with a title bar that can be dragged and a separate region for the window's contents.  The window as a whole is one div.  It contains another div for the window title and a second div for the contents.  When I run this, here is the output according to FireBug in Firefox 3.5:

```
<div id="toplevel">
<script type="text/javascript">
</script>
<div id="navigator" class="window" style="top: 10px; left: 10px; width: 300px; height: 150px;">
<div id="navigatortitle" class="windowtitle" onmousedown="dragMe(event, 'navigator');"/>
<div id="navigatorcontents" class="windowcontents" onclick="bringToFront('navigator');"/>
</div>
<div id="chatroom" class="window" style="top: 50px; left: 350px; width: 150px; height: 200px;">
<div id="chatroomtitle" class="windowtitle" onmousedown="dragMe(event, 'chatroom');"/>
<div id="chatroomcontents" class="windowcontents" onclick="bringToFront('chatroom');"/>
</div>
</div>
```

The stuff in the hidden <script> tag calls the Create() function, which is the source of the above JS code.  As you can see, the larger "window" region, which contains the "title" and "contents" regions, gets closed properly and contains the child elements properly.  However, those child elements, the "title" and "contents" regions, do not get the required </div> tag they are supposed to receive.  This really screws things up.

I have tried about a dozen things, and for the life of me, I cannot convince JavaScript to close those tags and put stuff between the <div> and </div> for any of the "title" and "contents" areas.  I can't find an answer on Google.  All of my results are IE-related.  While that doesn't surprise me in the slightest, it's also not descriptive of my issue.

Please, please, please help!  I'm not getting any errors on the Firefox error console, and Firebug doesn't throw any errors at render time.  What am I doing wrong?

---

### Post by zoff_ita on 2009-10-03
EDIT: forget what i wrote before.

DOM methods use implicit closing when elements are empty...
If you add a node or a text content to divs you'll get </div> closign tag...

---

### Post by gradysghost on 2009-10-08
Yeah, I figured that out after enough trial and error.  What you said before has some merit as well, and I've offloaded all of my scripting into other files to set all the event handlers.  The project is going well now, and you helped a lot.  Thanks!

For anybody else who happens across this thread, it's pretty much like zoff_ita said.  You have to actually specify content to go into a new element or the browser will treat it as if it's a standalone element, even when you know it's not.

---

