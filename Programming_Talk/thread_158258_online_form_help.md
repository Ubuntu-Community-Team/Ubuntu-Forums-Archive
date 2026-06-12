---
title: "online form help"
date: 2006-04-10
forum: Programming Talk
---

### Post by morphodone on 2006-04-10
I am trying to develope an online (intranet) form that my wife and I can use to 
document when we paid a bill last.

I coded a basic form with html but I do not know how to implement it.
I assume I need to use php and mysql.  Is there a good site or tutorial
on how to do this?

I tried using openoffice base but it doesn't allow online form entry from what I can tell.

Any suggestions are greatly appreciated.

source code of form:

<form action="billpay.php" method="post">

<p>date: (mm.dd.yy)<input type="text" name="date" /></p>

<p>amount:<input type="text" name="amount"></p>

<p>Please choose from the following bills:</p>
<p><input type="radio" name="which bill" value="bill_one" /> bill_one</p>
<p><input type="radio" name="which bill" value="bill_two" /> bill_two</p>
<p><input type="radio" name="which bill" value="bill_three" /> bill_three</p>

<p><input type="radio" name="which bill" value="bill_four" checked="bill_four" />bill_four</p>

<select>
	<option value="first option">check </option>
	<option value="second option">credit card </option>
	<option value="third option">debit </option>
</select>

<p><input type="submit" value="Submit"/></p>
<p>or </p>

<p><input type="reset" /></p>


</form>

---

