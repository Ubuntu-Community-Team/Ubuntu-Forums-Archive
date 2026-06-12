---
title: "mysql..unble to connect to DB..."
date: 2010-01-17
forum: Programming Talk
---

### Post by LumbeeNDN on 2010-01-17
I had this code running on a Windows box, and I moved the DB over to Ubuntu, and its not working any more. Its failing on the

 $result = mysqli_query($dbc, $query) 
            or die ('Error connecting to DB'); 

..which is odd, because the mysqli_connect line is OK...any ideas?

```
<!--    Author: 
        Date: 
        File:    vieworgs.php 
        Purpose: 
--> 
 
<html> 
<head> 
    <title>Speech In Progress</title> 
    <link rel ="stylesheet" type="text/css" href="style.css" > 
</head> 
 
<body> 
<h1>View Organizations</h1> 
<table> 
<p> 
    <?php 
         
        $dbc = mysqli_connect('localhost', 'root', '', 'speechnprogress') 
            or die ('Error connecting to DB'); 
             
        $query = "SELECT * FROM ORGANIZATIONS"; 
                 
        $result = mysqli_query($dbc, $query) 
            or die ('Error connecting to DB'); 
             
            while($row = mysqli_fetch_array($result)) 
            { 
                echo $row['orgName'] . " " . $row['orgContact']; 
                echo "<br />"; 
            } 
 
             
        mysqli_close($dbc); 
         
    ?> 
    <td><a href="/snp/admin.html">Back to Admin Page</a></p> 
</p> 
</tr> 
</form> 
</table> 
</body> 
</html>
```

---

### Post by Black Mage on 2010-01-17
Is the database on the Linux machine?

Are the ports open?

Can you connect to the database from the command line?

---

### Post by LumbeeNDN on 2010-01-17
...thanx for the reply Black...yep, I am x/lampp installed on my linux box. Xampp control panel says its running, and I can get to phpmyAdmin. However I cannot run "mysql" from the command line...says it can't find it.  May be a separate issue??? Not sure about the ports...like I said, localhost, and phpmyAdmin are accessible...

---

### Post by LumbeeNDN on 2010-01-17
...I figured it out black...had some upper case table names that were lower case. Odd becuase it worked on the windows box.  At any rate, I could still use help with running "mysql" from the command line if you know anything about that...

---

