---
title: "need to move the text input box to end of echo $page_pagination; line"
date: 2011-03-01
forum: Programming Talk
---

### Post by sdowney717 on 2011-03-01
I assume it does this because of the <FORM method
How can i simply put the input box at the end of echo $page_pagination;
instead of dropping down to a new line.


[PHP]
echo $page_pagination;

echo '<FORM NAME="Library Search" ACTION="z3950get.php" METHOD="POST">';
echo '&nbsp&nbsp&nbsp&nbsp Or go to page number ';
echo '<input type="text"SIZE="5" name="pageinput2" value="'. $page_num.'">';
echo '<input type="hidden" name="recordcount" value="'.$recordcount.'"/>'; 
echo '<button type="submit" name="pageinput1" value="search">Search</button>';
echo '</FORM>';

echo '<BR><BR>';
echo 'Showing Page Number -> '.$page_num. ' | Total number of results -> '.$numrows . ' | Total number of pages -> '.$numofpages.'<BR><BR>';
[/PHP]

---

