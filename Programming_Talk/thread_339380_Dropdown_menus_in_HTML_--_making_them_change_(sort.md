---
title: "Dropdown menus in HTML -- making them change (sorta)"
date: 2007-01-15
forum: Programming Talk
---

### Post by LotsOfPhil on 2007-01-15
Can anyone help me out with some HTML? I am trying to make something like this site:

[http://www.kaosweaver.com/demo/index.php?id=25](http://www.kaosweaver.com/demo/index.php?id=25)

I have a series of dropdown menus. I want the contents of unselected ones to change as you select values in the other ones. 

Say menu 1 let you choose "apple" or "orange"
If you choose apple, menu 2 lets you choose "peeled" or "unpeeled"
If you choose orange, menu 2 only has "peeled"

I don't have any idea how to do this, so it is tough to even search the internet. I don't know if it will use javascript or what.

---

### Post by lloyd mcclendon on 2007-01-15
view source is your friend

```
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<title>Untitled Document</title>
<link href="demo.css" rel="stylesheet" type="text/css">
<script type="text/JavaScript">
<!--
function MM_findObj(n, d) { //v4.01
  var p,i,x;  if(!d) d=document; if((p=n.indexOf("?"))>0&&parent.frames.length) {
    d=parent.frames[n.substring(p+1)].document; n=n.substring(0,p);}
  if(!(x=d[n])&&d.all) x=d.all[n]; for (i=0;!x&&i<d.forms.length;i++) x=d.forms[i][n];
  for(i=0;!x&&d.layers&&i<d.layers.length;i++) x=MM_findObj(n,d.layers[i].document);
  if(!x && d.getElementById) x=d.getElementById(n); return x;
}

function KW_updateItems(d,o,fn) { //v2.6 By Paul Davis www.kaosweaver.com
  var i,s,l=MM_findObj(d),b,z=o.options[o.selectedIndex].value;
  l.length=0;l.options[0]=new Option('tbd','tbd');b=(z!='nill')?eval(z+'_items'):0;
  for(i=0;i<b.length;i++){s=b[i].split("|");l.options[i]=new Option(s[1],s[0]);}
  l.selectedIndex=0;if (!fn) return;eval(fn)
}
//-->
</script>
</head>

<body>
<div id="demoTop">Demo - features: Dropdown Rewrite</div>
<div id="demoLeft">
  <p class="fDesc">Feature Description: </p>

  <p>Select an entry in the first dropdown to have the second dropdown change in accordance to the selection in the first box.</p>
</div>
<div id="demoRight">
  <p></p>
  <form name="form1" method="post" action="">
    <select name="maker" onChange="KW_updateItems('model',this)">
      <option selected value="nill">Please Select</option>
      <option value="ford">Ford</option>

      <option value="nissan">Nissan</option>
    </select>
    <select name="model">
      <option value='tbd'>Waiting for Selection</option>
      <option value='tbd'>Waiting for Selection</option>
      <option value='tbd'>Waiting for Selection</option>
    </select>

  </form>
  <p> </p>
</div>
<script language="JavaScript">
// KW DROPDOWN INSTALL CONTROL LINE START - DO NOT REMOVE


var ford_items = new Array();

 ford_items[0]='F150|F150';
 ford_items[1]='Mustang|Mustang';
 ford_items[2]='Explorer|Explorer';


var nissan_items = new Array();

 nissan_items[0]='Altima|Altima';
 nissan_items[1]='Maxima|Maxima';
 nissan_items[2]='Quest|Quest';

// KW DROPDOWN INSTALL CONTROL LINE END - DO NOT REMOVE


</script>
</body>
</html>
```

you may want to spend a few minutes formatting those javascript functions up top so you can read them, but all the pieces of code you need are right there.

---

### Post by Wybiral on 2007-01-15
Go here... [http://www.kaosweaver.com/demo/dropdown.php](http://www.kaosweaver.com/demo/dropdown.php)

Right click on the page and go to "View page source" (depends on your browser)

That will show you how THEY did it.

Javascript is probably going to be required, but javascript isn't that hard. If you want to do dynamic web stuff like that, it will definitely come in handy to learn.

---

### Post by LotsOfPhil on 2007-01-16
Thanks a lot ot both of you. Wish me luck :)

---

