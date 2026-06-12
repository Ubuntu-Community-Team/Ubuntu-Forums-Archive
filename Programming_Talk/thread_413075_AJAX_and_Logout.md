---
title: "AJAX and Logout"
date: 2007-04-18
forum: Programming Talk
---

### Post by JNowka on 2007-04-18
Hello, I am in a web development class, and I am trying to make a web based instant messanger using JavaScript, MySql, PHP, and AJAX.  My teacher has no idea what the hell AJAX is or what to do with it.  I have been studying it for a few weeks on my own time.


My major problem is that I am trying to get the page to run a logoff php script using onunload.  I can get the ajax code to run, but when it gets to the point where it is supposed to open the ajax request it never does it.  I have been working on this bit for a few hours, and still have not been able to get it to run the ajax request.  I will list my code below and if you will please give me some pointers, or an idea on where to go from here.

main.php:
> 
<SCRIPT language="JavaScript">
function goodbye(){
    var ajaxReq;  // Variable to store ajax call.
    
    try{
        // Opera 8.0+, Firefox, Safari
        ajaxRequest = new XMLHttpRequest();
    } catch (e){
        // Internet Explorer Browsers
        try{
            ajaxRequest = new ActiveXObject("Msxml2.XMLHTTP");
        } catch (e) {
            try{
                ajaxRequest = new ActiveXObject("Microsoft.XMLHTTP");
            } catch (e){
                // Something went wrong
                alert("Your browser broke!");
                return false;
            }
        }
    }
    ajaxReq.open("GET", "logout.php?login=<?= $login ?>");
}
</SCRIPT>

<frameset rows="20%,80%" border="0" onunload='goodbye()'>
    <frame src="header.html" name="header" marginwidth="10" marginheight="10" noresize>
    <frameset cols="20%,80%">
        <frame <?php print'src="friends.php?login=' . $login . '"';?> name="friends" marginwidth="10" marginheight="10" noresize>
        <frame <?php print'src="welcome.php?login=' . $login . '"';?> name="welcome" marginwidth="10" marginheight="10" noresize>
    </frameset>
</frameset>


logout.php
> 
<html>
<BODY>
<form name="logout" method="POST" action="./index.html" target="main">
<?php
$conn = mysql_connect("localhost", "user", "password");
mysql_select_db("nowka", $conn);

$sql = 'DELETE FROM JMap_Login WHERE login = "' . $login . '" LIMIT 1';

mysql_query($sql, $conn);
?>

<script type="text/javascript" language="JavaScript">
alert("Log Out!");
document.logout.submit();
</script>

</form>
</BODY>
</html>


Thank you for any help in advance.

---

