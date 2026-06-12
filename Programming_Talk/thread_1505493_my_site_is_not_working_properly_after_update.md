---
title: "my site is not working properly after update"
date: 2010-06-09
forum: Programming Talk
---

### Post by Iuliux on 2010-06-09
So, I have a page for uploading some files on the server and marking the upload into a db:

index.php is
```
<table width="500" border="0" align="center" cellpadding="0" cellspacing="1" bgcolor="#CCCCCC">
<tr>
<form action="mupload.php" method="post" enctype="multipart/form-data" name="form1" id="form1">
<td>
<table width="100%" border="0" cellpadding="3" cellspacing="1" bgcolor="#FFFFFF">
<tr>
<td><strong>uploadeaza tema</strong></td>
</tr>
<tr>
<td>numarul 1
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 2
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 3
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 4
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 5
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 6
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 7
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 8
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 9
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td>numarul 10
<input name="ufile[]" type="file" id="ufile[]" size="50" /></td>
</tr>
<tr>
<td align="center"><input type="submit" name="Submit" value="Upload" /></td>
</tr>
</table>
</td>
</form>
</tr>
</table>
```

and mupload.php is
```
<?php
include 'config.php';
include 'opendb.php';

$user = "ovidiu.pop";

$res = mysql_query("SELECT id FROM useri WHERE username = '$user'");
if (mysql_num_rows($res) > 0) {
   $row = mysql_fetch_row($res);
 //  echo $row[0];
}

$comanda= "mkdir ".$user;
shell_exec($comanda);

for ($i=1;$i<11;$i++){
$comanda= "mkdir ".$user."/"."tema".$i;
shell_exec($comanda);
}

$path1= $user."/tema1/".$HTTP_POST_FILES['ufile']['name'][0];
$path2= $user."/tema2/".$HTTP_POST_FILES['ufile']['name'][1];
$path3= $user."/tema3/".$HTTP_POST_FILES['ufile']['name'][2];
$path4= $user."/tema4/".$HTTP_POST_FILES['ufile']['name'][3];
$path5= $user."/tema5/".$HTTP_POST_FILES['ufile']['name'][4];
$path6= $user."/tema6/".$HTTP_POST_FILES['ufile']['name'][5];
$path7= $user."/tema7/".$HTTP_POST_FILES['ufile']['name'][6];
$path8= $user."/tema8/".$HTTP_POST_FILES['ufile']['name'][7];
$path9= $user."/tema9/".$HTTP_POST_FILES['ufile']['name'][8];
$path10= $user."/tema10/".$HTTP_POST_FILES['ufile']['name'][9];

//copiaza fisierele in locul de stocare de pe server
//fisierul 1
$filesize1=$HTTP_POST_FILES['ufile']['size'][0];
if($filesize1!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][0], $path1);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema1')");}

//fisierul 2
$filesize2=$HTTP_POST_FILES['ufile']['size'][1];
if($filesize2!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][1], $path2);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema2')");}

//fisierul 3
$filesize3=$HTTP_POST_FILES['ufile']['size'][2];
if($filesize3!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][2], $path3);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema3')");}
//fisierul 4
$filesize4=$HTTP_POST_FILES['ufile']['size'][3];
if($filesize4!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][3], $path4);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema4')");}
//fisierul 5
$filesize5=$HTTP_POST_FILES['ufile']['size'][4];
if($filesize5!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][4], $path5);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema5')");}

//fisierul 6
$filesize6=$HTTP_POST_FILES['ufile']['size'][5];
if($filesize6!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][5], $path6);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema6')");}

//fisierul 7
$filesize7=$HTTP_POST_FILES['ufile']['size'][6];
if($filesize7!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][6], $path7);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema7')");}

//fisierul 8
$filesize8=$HTTP_POST_FILES['ufile']['size'][7];
if($filesize8!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][7], $path8);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema8')");}

//fisierul 9
$filesize9=$HTTP_POST_FILES['ufile']['size'][8];
if($filesize9!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][8], $path9);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema9')");}

//fisierul 10
$filesize10=$HTTP_POST_FILES['ufile']['size'][9];
if($filesize10!= 0)
{
copy($HTTP_POST_FILES['ufile']['tmp_name'][9], $path10);
mysql_query("INSERT INTO `licenta`.`tabela_teme` (`id` ,`tema`)VALUES ('$row[0]', 'tema10')");}

//header("Location: rezultate.php");
?>
```

The code was working great until I've updated the server to 10.4. Now I can't upload any more files.
Can someone help me with this?

P.S. the folder I'm uploading to has permissions set to 777.

---

