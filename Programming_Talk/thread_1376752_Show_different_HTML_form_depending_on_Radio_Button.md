---
title: "Show different HTML form depending on Radio Button selection"
date: 2010-01-09
forum: Programming Talk
---

### Post by dmillerw on 2010-01-09
As the title suggests, I'm trying to get certain forms to show depending on which Radio button is selected.

I'm attempting to base it of this..
```
<html>
<head>
<script>
function RadioGroup1_toggle(c)
{
   if (c.value == 'yes')
      document.getElementById('hideme').style.visibility='visible';
   else
      document.getElementById('hideme').style.visibility='hidden';
}
</script>
</head>
<body>
<table width="551" border="0" cellpadding="5" cellspacing="0">
  <tr>
    <th valign="top"><div align="left">label1</div></th>
    <td>
      <input name="RadioGroup1" type="radio" id="yes" onClick="RadioGroup1_toggle(this);" value="yes" />
      <label>Yes</label>
      <input name="RadioGroup1" type="radio" id="no" onClick="RadioGroup1_toggle(this);" value="no" checked />
      <label>No</label>
      </td>
  </tr>
  <tr id="hideme" style="visibility:hidden;">
    <th valign="top">label2:</th>
    <td><input name="text2" type="text" id="text2" size="50" /></td>
  </tr>
</table>
</body>
</html>
```

But can't get past only have two options.

Using this...
```
<html>
<body>
<form action="insert.php" method="post">
First name: <input type="text" name="FName" />
<br>
Last name: <input type="text" name="LName" />
<br>
Username: <input type="text" name="UName" />
<br>
Student ID: <input type="text" name="StuID" />
<br>
Category:
<br>
<input type="radio" name=Cat value="School" >School
<br>
<input type="radio" name=Cat value="Facebook">Facebook
<br>
<input type="radio" name=Cat value="MySpace">MySpace
<br>
<input type="radio" name=Cat value="Other">Other
<br>
<input type="submit" value="Update Database" />
</form>

</body>
</html> 
```

I'm trying to make it so if "School" is selected, then it shows the "FName" "LName" "UName" and StuID" forms, and if Facebook or MySpace is selected to show "FName" "LName" "UName" "PWord" "E-Mail".

Anyone?

---

### Post by The Secret on 2010-01-09
JavaScript / DIVs [COLOR=Green]display[/COLOR] property ( block, none ).

---

### Post by dmillerw on 2010-01-09
> **The Secret said:**
> JavaScript / DIVs [COLOR=Green]display[/COLOR] property ( block, none ).
Sorry, what?

---

### Post by dmillerw on 2010-01-09
The best I've been able to do so far is to toggle the fields, and that obviously isn't what I'm after, any ideas?

---

### Post by shadylookin on 2010-01-10
You need to use javascript to hide or make visible the forms that you want

[PHP]
<?xml version = "1.0"?>

<html xmlns="http://www.w3.org/1999/xhtml">
	<head>
		<script type="text/javascript">
			function displayForm(c){
				if(c.value == "1"){
					document.getElementById("form1").style.visibility='visible';
					document.getElementById("form2").style.visibility='hidden';
				}
				else if(c.value =="2"){
					document.getElementById("form1").style.visibility='hidden';
					document.getElementById("form2").style.visibility='visible';
				}
				else{
				}
			
			}		
		</script>	
	</head>
	<body>
		<form>
			<label>Form 1<input value="1" type="radio" name="formselector" onclick="displayForm(this)"></label>	
			<label>Form 2<input value="2" type="radio" name="formselector" onclick="displayForm(this)"></label>	
		</form>
	
		<form style="visibility:hidden" id="form1"><label>Form 1<input type="text"/> </label></form>	
		
		<form style="visibility:hidden" id="form2"><label>Form 2<input type="text"/> </label></form>	
	
	</body>

</html>

[/PHP]

depending on which choice you select you get a different form displayed. That should get you in the right direction

---

### Post by dmillerw on 2010-01-10
Ah, thank you, I knew it was something like it

---

### Post by djRobbieF on 2010-07-21
This was a helpful bit of code; thanks!

I didn't realize this was in the Ubuntu forums until a while after utilizing the code; so just wanted to make a mention that once again, the Ubuntu community proves awesome, even in something totally unrelated to Ubuntu (although, I'm on Ubuntu as I type this).  :)

---

