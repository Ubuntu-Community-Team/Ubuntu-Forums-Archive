---
title: "Ubuntu Website Project (PHP, JavaScript, HTML, CSS)"
date: 2011-08-16
forum: Programming Talk
---

### Post by ThePerson on 2011-08-16
I am quite a new web developer and I was working on making an Ubuntu blog in the style of Unity (Launcher with back, forward buttons, a dash, etc.

Then, when I was thinking of what to put, I had a new idea. Use the Unity design I had made and make a sort of mock up of Ubuntu, with things like shutdown, dash, etc. 

I have got the design ready and have a question and a request. 

Would I be allowed to get a screen shot of Ubuntu and take out window controls for use on my website or would that be illegal, I know it is open source but I just want to be sure?

The request is slightly different. I am working on this project but it will probably take a while so I thought of the way people make distros - They get software and put it together. So, the unity components I am making are a program. Taking in the massive amounts of software on Ubuntu, I think I would find it hard to make most of them, so if you know JavaScript and can do web design, can you make the form for a application (Not including the close buttons, I have a default theme for that).

Also, please do not include PHP as that requires a restart.

Oh, for restart it would refresh the page, for shutdown it would go to a page with a blank screen and a green button, and for a web browser it would have an include statement to make it able to browse the web.

Thank you for reading this, and I hope you help :D

---

### Post by ThePerson on 2011-08-16
An example of a application is:
[COLOR=Red]
<?php
echo <<<END
<head>
<script language="javascript">
function close(id) {
 document.getElementById(id).style.display='none';
}
function open(id) {
 document.getElementById(id).style.display='block';
}
function maxmin(id) {
 if (document.getElementById(id).style.top == '24px' and document.getElementById(id).style.left == '48px') {
 document.getElementById(id).style.top='10%';
 document.getElementById(id).style.width='50%';
 document.getElementById(id).style.height='50%';
 }
 else
 {
 document.getElementById(id).style.top='24px';
 document.getElementById(id).style.bottom='0px';
 document.getElementById(id).style.left='48px';
 document.getElementById(id).style.right='0px';
 }
}
</script>
END;
echo <<<END
<div style="height:50%;width:50%;position:absolute;top:20%;left:20%;" id = "text">
 <div style="height:28px;width:100%;position:inherit;top:0px;left:0px" id = "topbartext">
  <div style="height:100%;width:84px;top:0px;left:0px;">
   <a href="JavaScript" onclick="close(text)" style="height:100%;width:33%;background:url("../images/close");"></a>
   <a href="JavaScript" onclick="maxmin(text)" style="height:100%;width:33%;background:url("../images/max");"></a>
   <a href="JavaScript" onclick="maxmin(text)" style="height:100%;width:33%;background:url("../images/min");"></a>
  </div>
  <div style="left:84px;right:0px;height:100%;top:0px;">
   <p>gedit</p>
  </div>
 </div>
 <div style = "top:28px;bottom:0px;left:0px;width:100%;">
  <FORM NAME ="form1" METHOD ="POST" ACTION = "gedit.php">
  <input type="Text" value="Some Text" name="Text" style="height:100%;top:0px;left:0px;width:100%;">
 </div>
</div>
END;
?>[/COLOR]

Which I have not tested yet gives you an idea. It is a outline of a textbox, which would be the interpretation of Gedit (I know gedit is not just a text editor, but it is hard to represent all of its features).

---

### Post by slavik on 2011-08-16
man code tags :)

---

