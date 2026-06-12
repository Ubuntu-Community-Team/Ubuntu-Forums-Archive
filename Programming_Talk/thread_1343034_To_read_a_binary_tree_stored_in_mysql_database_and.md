---
title: "To read a binary tree stored in mysql database and display it in tabular format"
date: 2009-12-01
forum: Programming Talk
---

### Post by pnewbie on 2009-12-01
Hi,
I am working on a project in which the name of people are stored in a binary tree. the names are stored in a mysql database. they are store in the following format
 
**node** **left** **right**
root A B
A C D
B E F
C G NULL
D H I
E J NULL
F NULL K 
 
I have to show the tree structure under any particular person entered by the user. The output has to be shown on a html page in a tabular format. We are using php language. I am very new to php so please help me.
 
Thanks

---

### Post by escapee on 2009-12-01
You should review the Guidelines sticky about posting homework questions.  No one is going to do the work for you, but if you ask the right questions we are more likely to nudge you in the right direction.

To start, how do you think you should do this?  Since you're new to PHP, feel free to use pseudocode or something.  Also, the PHP.net manual will become your best friend.

---

### Post by pnewbie on 2009-12-02
Sorry for that. 
 
I will try to explain what i am doing. Suppose some one want to check the tree structure below A. In the first step I will directly find the row where node is = A. Using mysql_fetch_assoc() function i will be able to find whether the left or right column of A contains any value other than NULL. if its not NULL then i will fetch the row corresponding to that value from the database and so on untill we get a NULL. I am trying to first retrieve all left values then the right values. But the problem is i don't know how/where to store the results at one place so that once this searching process is complete i can display the output in a tabular format, showing node, left and right values. 
 
thanks again

---

### Post by ib.lundgren on 2009-12-02
Not certain I understood exactly what you are trying to do but with storing the result, do you mean as in....

[PHP]$query = "SELECT node, left_column, right_column FROM example_table"; 
$result = mysql_query($query) or die(mysql_error());

while($row = mysql_fetch_array($result))
{
    echo $row['node'];
    echo $row['left_column'];
    echo $row['right_column'];
}
[/PHP]

Because then it might be a good time to google "PHP + MySQL" tutorial.

---

