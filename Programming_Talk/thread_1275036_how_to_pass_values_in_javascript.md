---
title: "how to pass values in javascript?"
date: 2009-09-25
forum: Programming Talk
---

### Post by abhilashm86 on 2009-09-25
i can call a function from <body> in javascript,  can i pass values to a function? check this.....[PHP]<html>
<head>
<title>
mul table
</title>
</head>

<script language="javascript">

function abhimul() {
var abhi=prompt("enter a number");
document.write("you entered " +abhi+ "<br>");
	
for(var i=1; i<=10; i++)
{
	document.write(abhi +" * " + i + "=" +(i*abhi)+ "<br>");
}

}
</script>

<body>
<a href="javascript:abhimul()">know tables</a>
</body>

</html>
[/PHP]

if i want to send values, i tried but din't work....
[PHP]
<body>
var abhi=prompt("enter a number");
document.write("you entered " +abhi+ "<br>");
abhimul(abhi);
</body>
[/PHP]
in called function, can i recieve it as abhimul(var abhi) ?
how to pass values?

---

### Post by CyberJack on 2009-09-25
You try to use javascript without script tags in the body of your html page. That is not going to work.
From the example I guess you want the user to enter a number and let javascript use the given number.

Javascript functions can have parameters like so:
```

<script type="text/javascript">
function test(param1, param2)
{
  alert( param1 +' '+ param2 );
}
</script>

```

Now you can call the javascript function the way you did in your first example, only now with 2 parameters.
This will result in a alert with the message "test param1 test param2'
```

<a href="javascript:test('test param1', 'test param2')">link</a> 

```

So I guess this is what you want:
```

<script type="text/javascript">
function askNumber()
{
  var number = prompt("enter a number");
  alertNumber( number );
}

function alertNumber( number )
{
  alert( number );
}
</script>

```
Then from you html body you create a link calling the "askNumber" function the same way you did in your first example.

More on javascript function: [http://www.w3schools.com/jS/js_functions.asp](http://www.w3schools.com/jS/js_functions.asp)

---

### Post by abhilashm86 on 2009-09-25
> **CyberJack said:**
> You try to use javascript without script tags in the body of your html page. That is not going to work.
From the example I guess you want the user to enter a number and let javascript use the given number.



thanks a lot, i made a very bad mistake, din't know javascript is this much syntax oriented!!
see this,
```
<script type="javascript/text">
function test(p1,p2)
{
	alert(p1+ ' '+ p2);
}

</script>
```
i had put "javascript" before text, i was scratching my head!! you gave a link w3schools, it saved!! 
also i tried doing same to above program, but its not taking parameters,
[PHP]<html>
<title>
mul table
</title>

<body>
<script type="text/javascript">

function abhimul(abhi) 
{
for(var i=1; i<=10; i++)
{
	
	document.write(abhi +" * " + i + "=" +(i*abhi)+ "<br>");
}
}
</body>
</script>


<body>
<script type="text.javascript>
<a href="javascript:abhimul(10);">get-tables</a>
</script>
</body>
</html>
[/PHP]
what is wrong now, if i add <script type> to end of <body>, there is error.....

---

### Post by abhilashm86 on 2009-09-25
i figured out error!! sorry, script needs to closed before body...........
[PHP]<html>
<title>
mul table
</title>

<body>
<script type="text/javascript">

function abhimul(abhi) 
{
for(var i=1; i<=10; i++)
{
	
	document.write(abhi +" * " + i + "=" +(i*abhi)+ "<br>");
}
}
</script>
</body>

<body>
<script type="text/javascript">
function abhitake()
{
	var abhi=prompt("enter a number");
	abhimul(abhi);
}

</script>
</body>


<body>
<a href="javascript:abhitake();">get-tables</a>
</body>
</html>

[/PHP]

now i'l try using a good editor than plain text........

---

