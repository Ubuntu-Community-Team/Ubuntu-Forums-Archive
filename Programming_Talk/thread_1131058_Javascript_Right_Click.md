---
title: "Javascript Right Click"
date: 2009-04-20
forum: Programming Talk
---

### Post by s.fox on 2009-04-20
Hi,

I have been trying to improve my knowledge of javascript and have a query.  I have been looking at the onclick event and I was wondering if the following was possible using javascript:

Can right clicking on a button have the same effect as a left click on the button?  Ideally I would like to call a function regardless if the button was left or right clicked.

Is this even possible?  If so can someone please post an example or a link to some useful reading.  Google seems to be obsessed with disabling the right click button when i run searches on the subject  :D

Thanks in advance,

Ash R

---

### Post by s.fox on 2009-04-20
Hi,

A bit of success!  Its sort of working,  but sometimes it plays up and behaves in an odd manner.  Can anybody help me put the finishing touches to it?

```
<HTML>
<HEAD>
<script language="javascript">
function makeAlert() {
    alert("you clicked a mouse button");
}

function testClick() {
    document.onmousedown=click
}

function click(e) {
    //detect right click
    if (navigator.appName == 'Netscape' && e.which == 3) {
        makeAlert();
    }
    if (navigator.appName == 'Microsoft Internet Explorer' && event.button==2){
        makeAlert();
    }
     

    //detect left click
    if (navigator.appName == 'Netscape' && e.which == 1) {     
        makeAlert();
    }
    if (navigator.appName == 'Microsoft Internet Explorer' && event.button==1){
        makeAlert();        
    }  
}
</script>
</HEAD>
<BODY>
<INPUT ID="BUTTON1" TYPE="BUTTON" VALUE="YES" onclick="testClick()"></INPUT>
<INPUT ID="BUTTON2" TYPE="BUTTON" VALUE="NO" onclick="alert('NO');" ></INPUT>
</BODY>
</HTML>

```Thanks for any input.


-Ash R

---

### Post by ddrichardson on 2009-04-20
Seems OK, doesn't pick up on the two buttons together though.

---

### Post by s.fox on 2009-04-20
> **ddrichardson said:**
> Seems OK, doesn't pick up on the two buttons together though.

I have also noticed that sometimes I have to double click a button to get a response.  Its very puzzling.

---

### Post by tturrisi on 2009-04-20
Default rt click ona a button will launch a form's context menu in IE and other browsers, but not in FF.  Have a look here:
[http://www.quirksmode.org/js/events_properties.html](http://www.quirksmode.org/js/events_properties.html)

---

### Post by s.fox on 2009-04-21
> **tturrisi said:**
> Default rt click ona a button will launch a form's context menu in IE and other browsers, but not in FF.  Have a look here:
[http://www.quirksmode.org/js/events_properties.html](http://www.quirksmode.org/js/events_properties.html)

Yes,  i noticed microfosoft set its own standard in internet explorer.  I believe i have gotten around this problem by using my e.which

I think i am very close now.  Here is the latest version of my code.

```
<HTML>
<HEAD>
<script language="javascript">
function noClick() {
    var mytext = document.getElementById("BUTTON3");
    mytext.focus(); 
    alert("NO clicked");
}

function makeAlert() {
    var mytext = document.getElementById("BUTTON3");
    mytext.focus(); 
    alert("you clicked a mouse button");
}

function testClick(buttonID) {
    BUTTON1.focus();        
    alert("This should always show when YES clicked");        
    document.theForm.BUTTON1.onmousedown=click    
}

function click(e) {
alert("click function was called");

    //detect right click
    if (navigator.appName == 'Netscape' && e.which == 3) {
        makeAlert();
    }
    if (navigator.appName == 'Microsoft Internet Explorer' && event.button==2){
        makeAlert();
    }
     
    //detect left click
    if (navigator.appName == 'Netscape' && e.which == 1) {
       makeAlert();
    }
    if (navigator.appName == 'Microsoft Internet Explorer' && event.button==1){
        makeAlert();
    
    }
      var mytext = document.getElementById("BUTTON3");
      mytext.focus(); 

}
</script>
</HEAD>
<BODY>
<FORM ID= "theForm" NAME="theForm">
<INPUT ID="BUTTON1" TYPE="BUTTON" VALUE="YES" onclick="testClick('BUTTON1')"></INPUT>
<INPUT ID="BUTTON2" TYPE="BUTTON" VALUE="NO" onclick="noClick();" ></INPUT>
<INPUT ID="BUTTON3" TYPE="BUTTON" VALUE="HOLD FOCUS AFTER CLICK"></INPUT>
</FORM>
</BODY>
</HTML>

```I have created a third button just to hold the focus after yes or no was clicked.  This was because I had a suspicion that the focus was not leaving the yes/ no buttons.  I think i was wrong,  bu just wanted to eliminate it as the cause.

Thanks for any input.

-Ash R

---

### Post by s.fox on 2009-04-22
1 day bump

---

### Post by myrtle1908 on 2009-04-23
> **Ash R said:**
> Ideally I would like to call a function regardless if the button was left or right clicked.


I haven't bothered with IE ...

[PHP]
<input type="button" value="You can click me with the right or left mouse button" id="myBtn" onclick="alert('clicked');">
<script language="javascript">
var myBtn = document.getElementById('myBtn');
myBtn.addEventListener("contextmenu", function(){
	this.click();
}, false);
</script>
[/PHP]

Is that what you wanted?

---

### Post by s.fox on 2009-04-25
> **myrtle1908 said:**
> I haven't bothered with IE ...

[php]
<input type="button" value="You can click me with the right or left mouse button" id="myBtn" onclick="alert('clicked');">
<script language="javascript">
var myBtn = document.getElementById('myBtn');
myBtn.addEventListener("contextmenu", function(){
    this.click();
}, false);
</script>
[/php]Is that what you wanted?

Thanks for your input.  I had not considered addEvenListener.  I am going to do a bit more reading up on it.   Looks like this little challenge is teaching me something :D  Would I be right in thinking that this wouldn't work in Internet Explorer?  

I am still a little unsure why my code doesn't work as expected.     I would have thought that the function testClick() would be called everytime I click the YES button.   Does anybody know why its not?

Thanks for all the support with this,

-Ash R

---

### Post by myrtle1908 on 2009-04-25
> **Ash R said:**
> Would I be right in thinking that this wouldn't work in Internet Explorer?

Pretty sure 'addEventListener' is not supported in IE.  You can use 'attachEvent' instead. For example (untested as I don't have IE):-

[PHP]var ua = navigator.userAgent.toLowerCase();
var isIE = (ua.indexOf("msie") != -1);
var myBtn = document.getElementById('myBtn');
if (!isIE) {
	myBtn.addEventListener("contextmenu", function(){ this.click(); }, false);
} else {
	myBtn.attachEvent("oncontextmenu", function(){ this.click(); });
}[/PHP]

---

### Post by MadCow108 on 2009-04-25
note that Opera doesn't allow scripts to disable it's rightclick contextmenu and you can't even capture rightclick events if its disabled in the browser configuration (and it is by default I think).

The only workaround known to me is drawing a temporary html button underneath the mouse on a rightclick. But I'm sure the developers consider that a bug which could be fixed in future versions.

---

