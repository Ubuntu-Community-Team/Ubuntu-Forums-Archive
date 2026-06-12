---
title: "javascript remove onChange on a form select item"
date: 2007-04-21
forum: Programming Talk
---

### Post by mrpeenut24 on 2007-04-21
Ok, so here's the progress thus far on [this]("http://ubuntuforums.org/showthread.php?t=354454") post for my networking project:

I've created the calendar, and the page for adding classes, professors, and everything else.  On the page where I'm adding classes, there is a form that has a select box with a javascript function called with an onchange().  Basically what it does is add another select box.  What I want to do, is add into the javascript function to delete the onchange() for the first select box.

Here's the html code:

```

          <tr>
            <td>Interferences</td>
            <td><select name="int1" value="0" onchange="addRow(1);">
              <option value="">Interference 1</option>
              <option value="1">CSC320A</option>
              <option value="2">CSC320B</option>
              </select>
            </td>
          </tr>
```and here's the javascript function:

```

function addRow(i)
{
var text = " \
<td><select name=\"int"+(i+1)+"\" value=\"0\" onchange=\"addRow("+(i+1)+");\"> \
<option value=\"\">Interference "+(i+1)+"</option> \
              <option value=\"1\">CSC320A</option>\
              <option value=\"2\">CSC320B</option>\
";


myRow = document.getElementById("table").insertRow(11 + i);
var col1 = myRow.insertCell(-1);
var col2 = myRow.insertCell(-1);
col1.innerHTML = "&nbsp;";
col2.innerHTML = text;
}

```This shouldn't be hard, I just can't find how to do it.  I've tried removeChild, but I can't get it to work.  This is due in 4 days, so I need this as soon as possible, so if anyone can help, that would be GREATLY appreciated!

Thanks.

---

### Post by Mirrorball on 2007-04-21
Select the first select box and do:
```

first_select_box.onchange = null;

```

---

### Post by mrpeenut24 on 2007-04-21
hrm... ok here's the php (the js is partially php...):

```

function addRow(i)
{
var text = " \
<td><select name=\"int"+(i+1)+"\" value=\"0\" onchange=\"addRow("+(i+1)+");\"> \
<option value=\"\">Interference "+(i+1)+"</option> \

<?php
include "settings.php";
$query_class = "select * from classes";
$result_class = $db->query($query_class);
$num_results_class = 0 + $result_class->num_rows;

for($i=0; $i < $num_results_class; $i++)
{
  $row_class = $result_class->fetch_assoc();
  $query_dept = "select deptCode from departments where deptID=".$row_class['classDept'];
  $result_dept = $db->query($query_dept);
  $row_dept = $result_dept->fetch_assoc();
  echo "              <option value=\\\"".$row_class['classID']."\\\">".$row_dept['deptCode'].$row_class['classCode'].$row_class['classSection']."</option>\\\n";
}

?>
";

myRow = document.getElementById("table").insertRow(11 + i);
var col1 = myRow.insertCell(-1);
var col2 = myRow.insertCell(-1);
col1.innerHTML = "&nbsp;";
col2.innerHTML = text;
int1.onchange = null;

}

```If I put the 'int1.onchange = null;' line any higher, it doesn't do anything below it.  Also, no matter where it is, it doesn't stop the select from calling the addRow function when changed.  :-/  Another thing I'd like to do, instead of calling just int1.onchange, is to call int'i'.onchange where the i variable passed is tacked onto the variable name.  (In php this would be something like ${'int'.$i}, except the i and $i are different variables...)

---

### Post by Mirrorball on 2007-04-21
This doesn't make any sense, because you are adding a select box with an onchange event and the next thing you do is to delete the onchange event...

---

### Post by mrpeenut24 on 2007-04-22
Oh!  Duh... :-D.  Thanks.  Hrm.. I thought if I just put getElementById('int'+i).onchange it would work for them all, but it's not.  (the id's are set now.)  Do you know how to make it concatenate the 'int'+i(variable).  The id's are int1, int2, int3...etc.

---

### Post by Mirrorball on 2007-04-22
I have edited my message above, I'm trying to understand why you are adding a select box with an onchange event and deleting it immediately. Why put it there in the first place?
And I think this code is not working because the DOM tree is not updated immediately.

---

### Post by mrpeenut24 on 2007-04-22
If you look at the thread I had mentioned in the first post, you can see an ascii-resemblance of what I'm working on.  I want to allow the user to create a class and have a select bar to allow the user to select interferences in schedules with this class.  The onChange function creates a second select box with the exact same values as the first one to allow for multiple interferences.  However in it's current state, the user is able to select the first interference and have the second box show up, and if they change the first interference, another box pops up with the same name as the second one.  This makes the url passed via the POST option 'http://website/add_class.php?(...)&int1=9&int2=3&int2=&int3=26&int4=12&int4=13&int5=...etc.
See where the problem is?  I want the onchange option removed after it is done once to prevent for multiple int2's so the variable is not overwritten when I implement it.

Hrm...I think I could just change it to plain text and have a remove button to get rid of it...but if possible, I'm now curious about this, and would really like to get this to work.

---

### Post by Mirrorball on 2007-04-22
Try creating the select box with the createElement() method.

---

### Post by mrpeenut24 on 2007-04-22
I could, and for better programming practices probably should.  But I'm on a tight schedule and don't see how this will help with removing the onchange action.  If the DOM doesn't update, should I just forget trying to remove it, and change it to a normal text with a remove button?

---

### Post by Mirrorball on 2007-04-22
Then you could just do:
```

var select1 = document.createElement('select');
[...]
select1.onchange = null;

```

---

