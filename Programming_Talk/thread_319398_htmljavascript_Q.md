---
title: "html/javascript Q"
date: 2006-12-15
forum: Programming Talk
---

### Post by derby007 on 2006-12-15
<!-- Your task should u should choose to accept is: 
Reduce the following to a shorter version, using HTML, JavaScript  &/or  CSS.
I've used functions to reduce the original below, but maybe someone can improve :-)
Also interested in other languages, if it produces the same o/p.  -->

<html>
<TABLE> 
 <TR bgcolor="#AAAAAA">
  <TD COLSPAN="7" ALIGN="center"><B>December 2006</B></TD> 
 </TR>

<TR bgcolor="#AA7755"> 
<TH ALIGN="center">Mon</TH>
<TH ALIGN="center">Tue</TH>
<TH ALIGN="center">Wed</TH>
<TH ALIGN="center">Thu</TH>
<TH ALIGN="center" width="30px">Fri</TH>
<TH ALIGN="center">Sat</TH>
<TH ALIGN="center">Sun</TH>
</TR>

<TR bgcolor="#AAAA00"> 
<TD ALIGN="center">1</TD>
<TD ALIGN="center" bgcolor="#ff0505" 
    onMouseOver="document.myform.name.value='2nd: New Album Released'"
    onMouseOut="document.myform.name.value=''">
    <font color="white">2</font></TD>
<TD ALIGN="center">3</TD>
<TD ALIGN="center">4</TD>
<TD ALIGN="center">5</TD>
<TD ALIGN="center">6</TD>
<TD ALIGN="center">7</TD>
</TR>

<TR bgcolor="#AAAA00"> 
<TD ALIGN="center">8</TD>
<TD ALIGN="center">9</TD>
<TD ALIGN="center">10</TD>
<TD ALIGN="center" bgcolor="#ff0505" 
    onMouseOver="document.myform.name.value='11th: Press Conference'"
    onMouseOut="document.myform.name.value=''">
    <font color="white">11</font></TD>
<TD ALIGN="center">12</TD>
<TD ALIGN="center">13</TD>
<TD ALIGN="center">14</TD>
</TR>

<TR bgcolor="#AAAA00"> 
<TD ALIGN="center">15</TD>
<TD ALIGN="center">16</TD>
<TD ALIGN="center">17</TD>
<TD ALIGN="center">18</TD>
<TD ALIGN="center">19</TD>
<TD ALIGN="center">20</TD>
<TD ALIGN="center">21</TD>
</TR>

<TR bgcolor="#AAAA00"> 
<TD ALIGN="center">22</TD>
<TD ALIGN="center">23</TD>
<TD ALIGN="center">24</TD>
<TD ALIGN="center">25</TD>
<TD ALIGN="center">26</TD>
<TD ALIGN="center">27</TD>
<TD ALIGN="center">28</TD>
</TR>

</TABLE> 

 <!--  Text Box  -->
 <form name="myform">
    <input type="text" name="name" size="25">
 </form>

</html>

---

### Post by Wybiral on 2006-12-15
There are better ways to do it, I would suggest dynamically generating it if you are serious about this. Other than that, this would be an easier approach to making a static version more adjustable...

```

<html>

<style>
	.highlite{color: #FFFFFF;	background:#FF0000;}
	th{background:#AA7755; text-align: center; width: 30px;}
	td{text-align: center;}
</style>

<TABLE>
<TR bgcolor="#AAAAAA"><TD COLSPAN="7"><B>December 2006</B></TD></TR>
<TR><TH>Mon</TH><TH>Tue</TH><TH>Wed</TH><TH>Thu</TH><TH>Fri</TH><TH>Sat</TH><TH>Sun</TH></TR>
<TR bgcolor="#AAAA00">
	<TD onMouseOver="mOver(1 )" onMouseOut="mOut(1 )">1 </TD>
	<TD onMouseOver="mOver(2 )" onMouseOut="mOut(2 )" class = highlite>2 </TD>
	<TD onMouseOver="mOver(3 )" onMouseOut="mOut(3 )">3 </TD>
	<TD onMouseOver="mOver(4 )" onMouseOut="mOut(4 )">4 </TD>
	<TD onMouseOver="mOver(5 )" onMouseOut="mOut(5 )">5 </TD>
	<TD onMouseOver="mOver(6 )" onMouseOut="mOut(6 )">6 </TD>
	<TD onMouseOver="mOver(7 )" onMouseOut="mOut(7 )">7 </TD>
</TR>
<TR bgcolor="#AAAA00">
	<TD onMouseOver="mOver(8 )" onMouseOut="mOut(8 )">8 </TD>
	<TD onMouseOver="mOver(9 )" onMouseOut="mOut(9 )">9 </TD>
	<TD onMouseOver="mOver(10)" onMouseOut="mOut(10)">10</TD>
	<TD onMouseOver="mOver(11)" onMouseOut="mOut(11)" class = highlite>11</TD>
	<TD onMouseOver="mOver(12)" onMouseOut="mOut(12)">12</TD>
	<TD onMouseOver="mOver(13)" onMouseOut="mOut(13)">13</TD>
	<TD onMouseOver="mOver(14)" onMouseOut="mOut(14)">14</TD>
</TR>
<TR bgcolor="#AAAA00">
	<TD onMouseOver="mOver(15)" onMouseOut="mOut(15)">15</TD>
	<TD onMouseOver="mOver(16)" onMouseOut="mOut(16)">16</TD>
	<TD onMouseOver="mOver(17)" onMouseOut="mOut(17)">17</TD>
	<TD onMouseOver="mOver(18)" onMouseOut="mOut(18)">18</TD>
	<TD onMouseOver="mOver(19)" onMouseOut="mOut(19)">19</TD>
	<TD onMouseOver="mOver(20)" onMouseOut="mOut(20)">20</TD>
	<TD onMouseOver="mOver(21)" onMouseOut="mOut(21)">21</TD>
</TR>
<TR bgcolor="#AAAA00">
	<TD onMouseOver="mOver(22)" onMouseOut="mOut(22)">22</TD>
	<TD onMouseOver="mOver(23)" onMouseOut="mOut(23)">23</TD>
	<TD onMouseOver="mOver(24)" onMouseOut="mOut(24)">24</TD>
	<TD onMouseOver="mOver(25)" onMouseOut="mOut(25)">25</TD>
	<TD onMouseOver="mOver(26)" onMouseOut="mOut(26)">26</TD>
	<TD onMouseOver="mOver(27)" onMouseOut="mOut(27)">27</TD>
	<TD onMouseOver="mOver(28)" onMouseOut="mOut(28)">28</TD>
</TR>
</TABLE>
<input type="text" id=message size="25">
<script language = "javascript">
	var msg= new Array(29);
	for(var i=0; i<29; i++){msg[i] = "";}

	msg[2] = "2nd: New Album Released";
	msg[11] = "11th: Press Conference";

	function mOver(id){message.value=msg[id];}
	function mOut(id){message.value="";}
</script>
</html>

```

---

### Post by derby007 on 2006-12-16
Yeah, i was trying the dynamic approach, or at least i think i was, something like below maybe:

<!-- Function to display Calendar rows: 'length'=no of times;  'num'=starting point  -->
 function calendar(length,num) {
	for(i=0; i<length; i++) {
	     document.write("<td align='center'>"+(num+i)+"</td>");
   	}
 }

hense: after the HR tags just call this Function. I'll mess around with it a little more. Anymore help would be gratefully accepted.

---

### Post by Wybiral on 2006-12-16
Yeah, something like that... I would use style for the centering instead of the align tag. You can change the style of all of the "td" objects. You might want to use two for/loops so that it can be 7x4. It shouldn't be too bad. What are you writing this for anyway? It might help everyone know what you can change and how.

---

### Post by derby007 on 2006-12-16
For fun basically. Just gettin to know the language. 
Yeah, it can be changed to whatever, as long as it looks some-what similar....
Q. Do you not have to use a FORM tag around the 'Input' text box, or is this only for HTML editing?
& also:
Q. How is <table Cellspacing="15px">  done in CSS ?
Cheers....

---

### Post by Wybiral on 2006-12-16
Like this:
```

<style>
table{
	border-spacing: 15px;
}
</style>

```


No, if you aren't submitting the form to anything, you really don't need the form tags around the input. This is ONLY if you don't want to submit a form.

Something like this would work, but I'm sure there are more elegant ways of doing it:

```

<body onload="generate()">
<script language="javascript">
function generate(){
	var txt = new Array(
		["Mon","Tue","Wed","Thu","Fri","Sat","Sun"],
		["1"  ,"2"  ,"3"  ,"4"  ,"5"  ,"6"  ,"7"  ],
		["8"  ,"9"  ,"10" ,"11" ,"12" ,"13" ,"14" ],
		["15" ,"16" ,"17" ,"18" ,"19" ,"20" ,"21" ],
		["22" ,"23" ,"24" ,"25" ,"26" ,"27" ,"28" ]
	);	

	var mess = new Array(
		["1"  ,"2nd: New Album Released"  ,"3"  ,"4"  ,"5"  ,"6"  ,"7"  ],
		["8"  ,"9"  ,"10" ,"11th: Press Conference" ,"12" ,"13" ,"14" ],
		["15" ,"16" ,"17" ,"18" ,"19" ,"20" ,"21" ],
		["22" ,"23" ,"24" ,"25" ,"26" ,"27" ,"28" ]
	);	

	document.write("<style>td{text-align: center;} th{text-align: center; width: 30px; background: #AA7755}<\/style>");
	document.write("<table>");
	document.write("<TD COLSPAN='7' bgcolor='#FFFFFF'><B>December 2006<\/B><\/TD><tr>");
	for(var y=0; y<5; y++){
		for(var x=0; x<7; x++){
			if(y==0){document.write("<th>"+txt[y][x]+"<\/th>");}
			else{document.write("<td bgcolor='#AAAA00' onMouseOver=\"msg.value='"+mess[y-1][x]+"'\">"+txt[y][x]+"<\/td>");}
		}
		if(y<4){document.write("<tr>");}
	}
	document.write("<\/table>");
	document.write("<input type='text' id='msg' size='25'>");
}
</script>
</body>

```

---

### Post by derby007 on 2006-12-17
Cheers, i had a CSS reference document but it had no mention of the 'border-spacing:'. It must be OOD. 
I suppose there's a million diff ways of doing the same/similar thing, especially HTML, JavaScript, CSS. As for the 'best' way of doing it: what attributes/characteristics should a new 'coder' be looking at ?  :rolleyes: 
I ended up with 3 fn's in a .js file > like: (with ure previous help)

<!-- Function to display Calendar rows:                   -->
<!--  'length' @ no of times;  'num' @ starting point  -->
function cal(length,num) {
	for(i=0; i<length; i++) {
	     document.write("<td align='center'>"+(num+i)+"</td>");
	}
}

<!-- Function to display Mouse Over on Calendar   -->
  function mOver(id) { 
	var msg = new Array(2);
	msg[0] = "2nd: New Album Released";
	msg[1] = "11th: Press Conference";
	document.myform.name.value=(msg[id]);
}

<!-- Function to display Mouse Out on Calendar   -->
  function mOut() { document.myform.name.value=""; }

---

