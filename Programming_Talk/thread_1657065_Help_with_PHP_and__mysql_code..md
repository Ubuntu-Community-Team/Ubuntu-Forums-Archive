---
title: "Help with PHP and  mysql code."
date: 2010-12-31
forum: Programming Talk
---

### Post by BillyHoppe14843 on 2010-12-31
I am working with PHP and mysql and need some help in figureing out the code to select data from a data base by states and it needs to display a message when there is no listing for that state. My email is     [EMAIL="bghoppe@stny.rr.com"]bghoppe@stny.rr.com[/EMAIL], my aim is [EMAIL="billyghoppe@aim.com"]billyghoppe@aim.com[/EMAIL],  thank you for your time in this matter.
 
Billy Hoppe.

---

### Post by muaaz007 on 2011-01-01
It is simple what i understand what you wrote

<?php
         $sql = "Select * from states where `statename` = `PostedStateName`; ";
         $rs = mysql_query($sql);
         $row = mysql_fetch_array($rs);
         if($row == NULL)
             echo "No Data in State"
         //Display the names
?>

---

### Post by epicoder on 2011-01-02
A couple of syntax corrections to muaaz007's otherwise correct solution:

[PHP]<?php
$sql = "Select * from states where `statename` = `PostedStateName`"; // mysql_query doesn't need a semicolon on the end of the query.
$rs = mysql_query($sql);
$row = mysql_fetch_array($rs);
if($row == NULL) {
    echo "No Data in State"
} else {
    //Display the names
}
?>     [/PHP]

@OP: Generally it's not a good idea to post your email address openly on a site. You'll get a ton of spam.

---

