---
title: "Change HTML Table Row Background Colour Using Button"
date: 2009-05-23
forum: Programming Talk
---

### Post by s.fox on 2009-05-23
Hi,

I am trying to change the background  colour of a table row using a button.  I have seen lots of examples where it can be achieved by clicking on the row,  but none using a button.   Is it possible?  I did a little coding,  but not sure where to begin with the javascript.  I imagine i will need to apply a css class to the row,  but i am not 100% sure.    Some direction would be welcomed.

```
<html>
<title>Test</title>
<head>
<script type="text/javascript">
function colourRow1(rowNumber) {
    //some code to change the colour of the row indicated by the number
    alert("change row 1 background colour");

}
</script>
</head>
<body>
<table name="table1" id="table1" border="1">
<thead>
<th>heading1</th>
<th>heading2</th>
<th>heading3</th>
</thead>
<tbody>
<tr id="row1">
<td>1,1</td>
<td>1,2</td>
<td>1,3</td>
</tr>
<tr id="row2">
<td>2,1</td>
<td>2,2</td>
<td>2,3</td>
</tr>
<tr id="row3">
<td>3,1</td>
<td>3,2</td>
<td>3,3</td>
</tr>
</tbody>
</table>
<button type="button" onClick="colourRow1(1)">Change Row 1</button>
</body>
</html>

```Thanks for looking.

-Ash R

---

### Post by odyniec on 2009-05-23
You can apply a class:
```
function colourRow1(rowNumber) {
    var tr = document.getElementById('table1')
                 .getElementsByTagName('tr')[rowNumber-1];
    tr.className += ' highlighted';
}
```

Or, you can just change the backgroundColor style property:
```
function colourRow1(rowNumber) {
    var tr = document.getElementById('table1')
                 .getElementsByTagName('tr')[rowNumber-1];
    tr.style.backgroundColor = 'blue';
}
```

---

### Post by s.fox on 2009-05-23
Hi,

Thank you odyniec.  That worked great.  Much appreciated. :D

-Ash R

---

