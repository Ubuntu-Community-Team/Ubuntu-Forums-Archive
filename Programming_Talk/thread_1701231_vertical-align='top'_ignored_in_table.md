---
title: "vertical-align='top' ignored in table"
date: 2011-03-06
forum: Programming Talk
---

### Post by sdowney717 on 2011-03-06
vertical-align:top is also ignored
it does respond to width and also does respond to align
I put some data in a table with 2 columns
when ever the second column overruns the width so the text wraps, the first column text centers in the table cell.
I want it to pin itself to the top of the cell.
this is it here.

[PHP]       echo " <td WIDTH='350';vertical-align='top'; align='right'>$mdata[$loop600]</td>"; //the names of the numbered fields
       echo " <td WIDTH='600';vertical-align='top'; align='left'>$arr[2]</td>"; //the first data of the subfield of the tag[/PHP]

this is the whole routine

[PHP]//print array here, split off chr(29)
echo "<table width='952' border='0'>";

//$mdata holds the tag names with each number corresponding to the text name

$loop600 = 1;
while ($loop600 < 900)//dont show local LOC tags
{
if (!empty($taggs[$loop600]))
{
$arr = explode(chr(29),$taggs[$loop600]);
//if ($loop600 == 650) {print_r ($arr);}
echo " <tr>";
echo " <td WIDTH='350';vertical-align='top'; align='right'>$mdata[$loop600]</td>"; //the names of the numbered fields
echo " <td WIDTH='600';vertical-align='top'; align='left'>$arr[2]</td>"; //the first data of the subfield of the tag
echo " </tr>";
for ($i = 3; $i < count($arr); $i += 2)
{
echo " <tr>";
echo " <td>"." "."</td>";
echo " <td>".$arr[($i+1)] ."</td>";
echo " </tr>";
}
$arr = array();
}
$loop600 = ($loop600 +1);
} [/PHP]

---

### Post by n~kf)}BW% on 2011-03-06
The HTML syntax is wrong...

This is how it should look in HTML:
[PHP]
echo " <td WIDTH='350' VALIGN='top' align='right'>$mdata[$loop600]</td>"; //the names of the numbered fields
echo " <td WIDTH='600' VALIGN='top' align='left'>$arr[2]</td>"; //the first data of the subfield of the tag  
[/PHP]
And here by using CSS:
[PHP]
echo " <td style="width:350px;vertical-align:top;text-align:right;">$mdata[$loop600]</td>"; //the names of the numbered fields
echo " <td style="width:600px;vertical-align:top;text-align:left;">$arr[2]</td>"; //the first data of the subfield of the tag  
[/PHP]

Best regards

---

### Post by sdowney717 on 2011-03-06
Hi, thank you!
I plugged it in and worked.
I changed " to ' in php or you need to use a \ to escape the "

[PHP]echo " <td style='width:350px;vertical-align:top;text-align:right;'>$mdata[$loop600]</td>"; //the names of the numbered fields
echo " <td style='width:600px;vertical-align:top;text-align:left;'>$arr[2]</td>"; //the first data of the subfield of the tag  [/PHP]

---

