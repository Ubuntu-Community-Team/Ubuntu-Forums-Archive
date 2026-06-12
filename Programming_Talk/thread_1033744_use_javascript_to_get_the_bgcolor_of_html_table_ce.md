---
title: "use javascript to get the bgcolor of html table cell"
date: 2009-01-07
forum: Programming Talk
---

### Post by zpzpzp on 2009-01-07
Hi

An html table cell is defined as follows:
<td rowspan="2" bgcolor="red" width="10"></td>

Does anyone know how to use javascript to get the bgcolor of this table cell?

I tried this following code, but in the popup window there is nothing displayed (not "undefined".)

[INDENT]	var table = document.getElementById("automationTestResults");
	var tableBody = table.getElementsByTagName("tbody")[0];
	var rows = tableBody.getElementsByTagName("tr");
	var cellsInARow = rows[1].getElementsByTagName("td");
	
	alert (cellsInARow[3].style.backgroundColor);[/INDENT]

Thanks,

Paul

---

### Post by myrtle1908 on 2009-01-07
bgcolor is an attribute NOT a style property ...

[PHP]<table>
<tr><td bgcolor="red" id="blah">Blah</td></tr>
</table>

<script>
var td = document.getElementById("blah");
alert(td.bgColor);
</script>[/PHP]

---

