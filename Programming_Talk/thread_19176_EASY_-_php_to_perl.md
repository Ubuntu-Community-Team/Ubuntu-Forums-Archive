---
title: "EASY - php to perl??"
date: 2005-03-10
forum: Programming Talk
---

### Post by mangotext on 2005-03-10
Hi all 
I'm only a beginner in perl. Easy if you know how I suppose! Need to change this insert php script to perl.....

include ("detail.php"); 

$db = mysql_connect("$host", $user, $password );
mysql_select_db("$database",$db);

$q  = "INSERT INTO tablename (";
$q .= "DBfield1, DBfield2, DBfield3";
$q .= ") VALUES (";
$q .= "'$formfield1', '$formfield2', '$Formfield3')";

mysql_query($q,$db);

?>
<script language="javascript">	

	document.location.replace("thankYou.htm");

</script>

can anyone help?

---

