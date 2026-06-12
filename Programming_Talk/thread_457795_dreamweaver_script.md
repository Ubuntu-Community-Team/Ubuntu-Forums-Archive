---
title: "dreamweaver script"
date: 2007-05-29
forum: Programming Talk
---

### Post by zerobinary on 2007-05-29
i need help on dreamweaver script i wnat to program a pop ups for my site don't know how to  do it 
can someone help if u have the script can u post it here and how do u add it to dreamweaver 
i am a newbie at dreamweaver so can u go steps by step plz 
i know this is kind of not realted to programming but plz help this is part of my it homework
sorry for bugging u guys but plz help

---

### Post by barmazal on 2007-05-29
alert('it's called javascript and not dreamweaver');

---

### Post by zerobinary on 2007-05-29
ok but can anyone help me 
and how dp u add the script to dreamweaver

---

### Post by Rogers on 2007-05-29
dreamweaver is a development tool used for ColdFusion/CSS/HTML/and more..... what language are you using?  If you target is a simple alert box, I suggest going to google and searching for "java scriplt alert box tutorial" :popcorn:

---

### Post by zerobinary on 2007-05-29
i can find it just that i don't know how to add it in dreamweaver

---

### Post by nitro_n2o on 2007-05-29
You add it in code not in dreamweaver .. i guess, but if you are so into dreamweaver, Dreamweaver has built in Javascript functions that you can find somewhere in the window menu.. i didn't use dreamweaver for quite some time.. 
If you post your code, i would say some one would help u 

good luck

---

### Post by barmazal on 2007-05-29
i think you have on event handler in Dreamwaver which has pop up window

---

### Post by Mirrorball on 2007-05-29
Please try to understand what you are doing. There is no "adding popup windows to Dreamweaver." There are javascript functions, event handlers, HTML code etc. There is MUCH MORE to building a website than clicking and dragging text to Dreamweaver. If you are serious about web design, please study HTML, CSS, and Javascript. And then you'll know why you are not getting a decent answer to your question and Dreamweaver will make sense to you.

---

### Post by zerobinary on 2007-05-30
```
<html>
[CODE]<body bgcolor="#FFFFFF">
<title>CodeAve.com(JavaScript: Confirm Alert Box)</title>

<script language="JavaScript">
<!--
function confirm_entry()
{
input_box=confirm("Click OK or Cancel to Continue");
if (input_box==true)

{ 
// Output when OK is clicked
alert ("You clicked OK"); 
}

else
{
// Output when Cancel is clicked
alert ("You clicked cancel");
}

}
-->
</script>

Click <a href="JavaScript:confirm_entry()">here</a>


<p>

<form onSubmit="confirm_entry()">
<input type="submit" >
</form>

</body>
</html> 
```
or this one which one is better 

<html>
<title>Codeave.com(JavaScript: Alert Box)</title>
<body bgcolor="#ffffff">

<!-- Example of a form button that will open an alert box -->

<form>
<input type="button" value="Open Alert Box" 
onClick='alert("Place Your message here... \n Click OK to contine.")'>
</form>

<p>

<!-- Example of a link that will open an alert box -->

<a href='javascript:onClick=alert("Place Your message here... \n Click OK to contine.")'>
Open Alert Box</a>


</body>
</html> [/CODE]
but how do i chnage it to welcome alert boxand how to add it to dreamweaver

---

