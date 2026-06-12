---
title: "javascript  apply funtion......."
date: 2009-09-28
forum: Programming Talk
---

### Post by abhilashm86 on 2009-09-28
i tried using apply in order to use a method in more than one object, why does this stop executing further more statements?
[PHP]<html>
<head>
<title>fun objs</title>
</head>

<script type="text/javascript">
function a(color1)
{
	this.color=color1;
	this.saycolor= function() 
	{
		alert(this.color);
	};
}

function b(color2, name2)
{
	a.apply(this,arguments);
	this.color=color2;
	this.name=name2;
	this.sayname==function () {
		alert(this.name);
	};
}

var obja=new a("red");
var objb=new b("black","sadgh");
obja.saycolor();
objb.saycolor();
objb.sayname();

</script>
</html>
[/PHP]

objb.sayname();

this is not getting executed?

---

### Post by CyberJack on 2009-09-28
replace this.sayname==function () { to this.sayname = function () { 
(double to single = character)

---

### Post by abhilashm86 on 2009-09-28
> **CyberJack said:**
> replace this.sayname==function () { to this.sayname = function () { 
(double to single = character)

that was my bad mistake!! shoud'nt have posted:) in hurry, i din't see that!!

---

