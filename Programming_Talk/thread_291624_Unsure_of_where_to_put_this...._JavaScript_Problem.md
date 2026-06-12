---
title: "Unsure of where to put this.... JavaScript Problems"
date: 2006-11-02
forum: Programming Talk
---

### Post by Dark_Dragon on 2006-11-02
Hey all ( I appologise if this is in the wrong Forum was unsure of where to put it),

Im putting together some javascript to make the background for the bowser to automaticly change colour but I have hit a snag...

When i run the code *ill post a copy of the code below for you to view* it comes up with this error: Line 94, Char: 1, Error: Expected ')', Code: 0, URL: (obscured).

:START CODE:

<html>

	<head>
		<title></title>

		<script language="javascript">

	var shade;

	var r1 = 0, r2 = 0, g1 = 0, g2 = 0, b1 = 0, b2 = 0;
	var R1, R2, G1, G2, B1, B2;

	function shade_bg()
		{
			alert("r1 is " + r1 + "| r2 is " + r2); 
			alert("g1 is " + g1 + " g2 is " + g2);
			alert("b1 is " + b1 + "| b2 is " + b2);

			r1 = 0;
			r2 = r2 + 1;
	
			b1 = 0;
			b2 = 0;
	
			g1 = 0;
			g2 = 0;

			// Return
			R1 = toHex(r1);
			R2 = toHex(r2);

			G1 = toHex(g1);
			G2 = toHex(g2);

			B1 = toHex(b1);
			B2 = toHex(b2);

			alert("r1 is " + r1 + "| r2 is " + r2); 
			alert("g1 is " + g1 + " g2 is " + g2);
			alert("b1 is " + b1 + "| b2 is " + b2);

		shade = "#" + R1 + R2 + G1 + G2 + B1 + B2;	

			alert("shade is " + shade);

			document.bgColor = shade;
		}

	function toHex(innum)
		{
			var outmun;

		if (innum <= 9)
			{
				outnum = innum;
			}

		else if (innum == 10)
			{
				outnum = "A";
			}

		else if (innum == 11)
			{
				outnum = "B";
			}

		else if (innum == 12)
			{
				outnum = "C";
			}

		else if (innum == 13)
			{
				outnum = "D";
			}

		else if (innum == 14)
			{
				outnum = "E";
			}

		else if (innum == 15)
			{
				outnum = "F";
			}

			return outnum;
		}
		</script>
	</head>

	<body onload=setInterval("shade_bg()" 100)>
		<center><h1>Auto Background</h1></center>
	</body>

</html>

:END CODE:

I have tryed debuging the code myself but to no avail, if anyone that knowes javascript can help id be verry gratefull.

thanks

-- DD

---

### Post by PriceChild on 2006-11-02
*thread moved*

---

### Post by raul_ on 2006-11-02
can u post the line numbers? i don't want to count 94 lines =\ and maybe ident it...gvim auto idents

---

### Post by po0f on 2006-11-02
Dark_Dragon,

I don't know JavaScript, but this line looks funny:
```
<body onload=setInterval("shade_bg()" 100)>
```
Shouldn't it be something more like this:
```
<body onload=setInterval("shade_bg()", 100)>

OR

<body onload=setInterval("shade_bg(100)")>
```

---

### Post by raul_ on 2006-11-02
not necessarily...i don't work with javascript either but that can be something like 
```

<body onload= setinterval(name interval)>

```
or something like that. 
anywayz, u said u debugged it so i'll assume it's not a missing ")" (it IS what the error says)

---

### Post by Dark_Dragon on 2006-11-02
Those actualy look alot better than what ive got ill try those, thanks ill let u know how i go

-- DD

---

### Post by Dark_Dragon on 2006-11-02
> **raul_ said:**
> u said u debugged it so i'll assume it's not a missing ")" (it IS what the error says)

I did try to debug it but as im only learning JS atm my knowledge is rather limited to what i can do... and as i was 'debugging' i took note at every '(' & ')' and ther is a pair for each i cannot find where the error is generatign from... *and neitehr of your suggestions worked im afraid po0f :( thanks for ur input tho....*

i am at the moment tryign to find HTML and JS syntax referances to see where i went wrong with it... ill keep u posted with what i find as it might help others l8er on...

-- DD

---

### Post by Vex on 2006-11-02
You need to change line 93 (the body tag) to the following:

```

<body onload="setInterval('shade_bg()', 100)">

```

**HOWEVER!!!** - I wouldn't run the code as it currently stands. You'll want to remove the 'alerts' from the script. Otherwise you'll end up with message alerts popping up continuously! Making it difficult to do anything else!

---

