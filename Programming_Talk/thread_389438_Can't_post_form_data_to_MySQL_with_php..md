---
title: "Can't post form data to MySQL with php."
date: 2007-03-20
forum: Programming Talk
---

### Post by nucklebone on 2007-03-20
Apache2
PHP5
MySQL5
GNU/Linux Ubuntu 6.10
___________________________

I am having a problem posting data to a MySQL database using a PHP script. This server/php/mysql is a fresh install.

I am able to insert data into the MySQL database via the PhpMyadmin interface and that information can be read by my PHP scripts and displays fine on a web page. The problem is when I try to insert or update via a PHP script, it fails to do so. I don't get an error, just simply doesn't work.

I'm error checking with an if/else statement in the script. If success... print success, else print failed. It does neither, it just does nothing.

CAVEAT: This is the same generic script I have used on 3 other commercial sites and it works fine (difference being Apache1.3, PHP4.x and Mysql4.x). Also, the script is connecting to the database perfectly fine. I know this because elements on the page are databased elements and they show up on the page.

Without posting my script here first, does this sound familiar to anyone? I'm slightly newbish about PHP/MySQL so if the default is to not accept post data then I don't know how to turn it on.

Thanks!

---

### Post by Mirrorball on 2007-03-20
Maybe error reporting is off. Turn it on to see the error messages.

---

### Post by nucklebone on 2007-03-21
error reporting is turned on. when i break the script (in the step that updates the database) the script fails and spits out an error to the web browser.

and like i said, i know the script is reading the database because it displays the information it is supposed to be updating

---

### Post by Mirrorball on 2007-03-21
You wrote: "I'm error checking with an if/else statement in the script. If success... print success, else print failed. It does neither, it just does nothing." If it did nothing, either the script died before it had a chance to print something or that query that updates the database wasn't executed. If the script had died, you would have seen an error message, unless error reporting was turned off and you said it wasn't. Therefore the query that updates the database isn't being executed.

---

### Post by nucklebone on 2007-03-21
> **Mirrorball said:**
> If it did nothing, either the script died before it had a chance to print something or that query that updates the database wasn't executed. If the script had died, you would have seen an error message, unless error reporting was turned off and you said it wasn't. Therefore the query that updates the database isn't being executed.

ok, that was good. so i followed your suggested line of inquiry.

still nothing though. error reporting is on and i get nothing. actually, i broke the script to actually get an error to make sure it was on, but other than that i get no on-screen errors nor do i get anything in my php.log file.

you can see the script in "action" by going here:

[http://xx.xx.xx.xx/cp/edit_style.php](http://xx.xx.xx.xx/cp/edit_style.php)

when you enter values into that form you should see the results after hitting Update, since the style of that page is reading the database where you are inputting the values (which is how i am certain that the php script is actually accessing the database in the first place). FYI, i connect to the databse from an external script which has been commented out here in the code.

here is my actual php script:

```
<?PHP
include ("/path/to/my/connection/script.php");
include ("/path/to/my/header/script.php");

echo "<p class=\"normbod\"><a href=\"index.php\">{Back to the Control Panel}</a></p>";

/////////////// SECTION 2 (processform==1)
/////////////// run ONLY if form was submitted - see SECTION 1 BELOW

// this line added for register_globals
$processform = $_POST['processform'];

if ($processform == 1) {

$style_id = $_POST['style_id'];
$body_color = $_POST['body_color'];
$table_color = $_POST['table_color'];
$table_border = $_POST['table_border'];
$table_border_color = $_POST['table_border_color'];
$table_border_size = $_POST['table_border_size'];
$cellcolor = $_POST['cellcolor'];
$cellpadding = $_POST['cellpadding'];
$nav_cell_color = $_POST['nav_cell_color'];
$nav_cell_padding = $_POST['nav_cell_padding'];
$bodyfont = $_POST['bodyfont'];
$bodyfont_color = $_POST['bodyfont_color'];
$bodyfont_size = $_POST['bodyfont_size'];
$bodyfont_weight = $_POST['bodyfont_weight'];
$bodyfont_style = $_POST['bodyfont_style'];
$headerfont = $_POST['headerfont'];
$headerfont_color = $_POST['headerfont_color'];
$headerfont_size = $_POST['headerfont_size'];
$headerfont_weight = $_POST['headerfont_weight'];
$headerfont_style = $_POST['headerfont_style'];
$weefont = $_POST['weefont'];
$weefont_color = $_POST['weefont_color'];
$weefont_size = $_POST['weefont_size'];
$weefont_weight = $_POST['weefont_weight'];
$weefont_style = $_POST['weefont_style'];
$alink_font = $_POST['alink_font'];
$alink_decoration = $_POST['alink_decoration'];
$alink_weight = $_POST['alink_weight'];
$alink_color = $_POST['alink_color'];
$alink_size = $_POST['alink_size'];
$avisited_font = $_POST['avisited_font'];
$avisited_decoration = $_POST['avisited_decoration'];
$avisited_weight = $_POST['avisited_weight'];
$avisited_color = $_POST['avisited_color'];
$avisited_size = $_POST['avisited_size'];
$aactive_font = $_POST['aactive_font'];
$aactive_decoration = $_POST['aactive_decoration'];
$aactive_weight = $_POST['aactive_weight'];
$aactive_color = $_POST['aactive_color'];
$aactive_size = $_POST['aactive_size'];
$ahover_font = $_POST['ahover_font'];
$ahover_decoration = $_POST['ahover_decoration'];
$ahover_weight = $_POST['ahover_weight'];
$ahover_color = $_POST['ahover_color'];
$ahover_size = $_POST['ahover_size'];

$query = "UPDATE $tb_sty1 SET
('style_id','body_color','table_color','table_border','table_border_color','table_border_size','cellcolor','cellpadding','nav_cell_color','nav_cell_padding','bodyfont','bodyfont_color','bodyfont_size','bodyfont_weight','bodyfont_style','headerfont','headerfont_color','headerfont_size','headerfont_weight','headerfont_style','weefont','weefont_color','weefont_size','weefont_weight','weefont_style','alink_font','alink_decoration','alink_weight','alink_color','alink_size','avisited_font','avisited_decoration','avisited_weight','avisited_color','avisited_size','aactive_font','aactive_decoration','aactive_weight','aactive_color','aactive_size','ahover_font','ahover_decoration','ahover_weight','ahover_color','ahover_size')

VALUES

('$style_id','$body_color','$table_color','$table_border','$table_border_color','$table_border_size','$cellcolor','$cellpadding','$nav_cell_color','$nav_cell_padding','$bodyfont','$bodyfont_color','$bodyfont_size','$bodyfont_weight','$bodyfont_style','$headerfont','$headerfont_color','$headerfont_size','$headerfont_weight','$headerfont_style','$weefont','$weefont_color','$weefont_size','$weefont_weight','$weefont_style','$alink_font','$alink_decoration','$alink_weight','$alink_color','$alink_size','$avisited_font','$avisited_decoration','$avisited_weight','$avisited_color','$avisited_size','$aactive_font','$aactive_decoration','$aactive_weight','$aactive_color','$aactive_size','$ahover_font','$ahover_decoration','$ahover_weight','$ahover_color','$ahover_size') WHERE style_id = 0";

// error check the database query
if (mysql_query($query)) {
	echo "<meta http-equiv=\"Refresh\" content=\"0; url=index.php\">";
	} else {
	echo "WARNING! An error occurred, hit refresh to submit it again. Or if you like you can <a href='$PHP_SELF'>return to the form</a> and try again.";
	}

}
/////////////// end of the form processor
/////////////// end of SECTION 2 




/////////////// SECTION 1 
/////////////// by default display this

if (!$processform) {
//connect to the database and define this database connection as query.
$query = "SELECT * FROM $tb_sty1 WHERE style_id = 0";
//quantify the results
$result = mysql_query($query);
//display data
  {
     $row = mysql_fetch_array($result);
			echo "<form action=\"$PHP_SELF\" method=\"POST\" name=\"style_editor\">
			<input type=\"hidden\" name=\"processform\" value=\"1\" />";
			echo "<input type=\"hidden\" name=\"style_id\" value=\"0\" />";
			echo "<hr />
			<p class=\"boldbod\">Backgrounds and Borders</a></p>";
			echo "<p class=\"normbod\">
			<input type=\"text\" name=\"body_color\" value=\"";
			echo stripslashes($row["body_color"]);
			echo "\" tabindex=\"1\" size=\"6\" maxlength=\"6\"> Background color of entire page.<br />";
// table color
			echo "<input type=\"text\" name=\"table_color\" value=\"";
			echo stripslashes($row["table_color"]);
			echo "\" tabindex=\"2\" size=\"6\" maxlength=\"6\"> Main table background color.<br />";
// table border
			echo "<select size=\"1\" name=\"table_border\">
			<option value=\"";
			echo stripslashes($row["table_border"]);
			echo "\" selected=\"selected\">";
			echo stripslashes($row["table_border"]);
			echo "</option>
			<option value=\"none\">none</option>
			<option value=\"solid\">solid</option>
			<option value=\"dashed\">dashed</option>
			<option value=\"dotted\">dotted</option>
			</select> Border style of the main table.<br />";
// table border color
			echo "<input type=\"text\" name=\"table_border_color\" value=\"";
			echo stripslashes($row["table_border_color"]);
			echo "\" tabindex=\"3\" size=\"6\" maxlength=\"6\"> Main table border color.<br />";
// table border size
			echo "<input type=\"text\" name=\"table_border_size\" value=\"";
			echo stripslashes($row["table_border_size"]);
			echo "\" tabindex=\"4\" size=\"6\" maxlength=\"6\"> Main table border size.<br />";
// cell background
			echo "<input type=\"text\" name=\"cellcolor\" value=\"";
			echo stripslashes($row["cellcolor"]);
			echo "\" tabindex=\"5\" size=\"6\" maxlength=\"6\"> Cell background color.<br />";
// cell padding
			echo "<input type=\"text\" name=\"cellpadding\" value=\"";
			echo stripslashes($row["cellpadding"]);
			echo "\" tabindex=\"6\" size=\"6\" maxlength=\"6\"> Cell padding.<br />";
// navigation cell color
			echo "<input type=\"text\" name=\"nav_cell_color\" value=\"";
			echo stripslashes($row["nav_cell_color"]);
			echo "\" tabindex=\"7\" size=\"6\" maxlength=\"6\"> Navigation bar color.<br />";
// navigation cell padding
			echo "<input type=\"text\" name=\"nav_cell_padding\" value=\"";
			echo stripslashes($row["nav_cell_padding"]);
			echo "\" tabindex=\"8\" size=\"6\" maxlength=\"6\"> Navigation bar padding.</p>";
// ------ fonts section ------
			echo "<hr />
			<p class=\"boldbod\">Fonts</a></p>";
// body font family
			echo "<p class=\"normbod\"><input type=\"text\" name=\"bodyfont\" value=\"";
			echo stripslashes($row["bodyfont"]);
			echo "\" tabindex=\"9\" size=\"15\" maxlength=\"100\"> Caption font - 3 seperated by a comma. (ex: helvetica, arial, san-serif).<br />";
// body font color
			echo "<input type=\"text\" name=\"bodyfont_color\" value=\"";
			echo stripslashes($row["bodyfont_color"]);
			echo "\" tabindex=\"10\" size=\"6\" maxlength=\"6\"> Caption font color.<br />";
// body font size
			echo "<input type=\"text\" name=\"bodyfont_size\" value=\"";
			echo stripslashes($row["bodyfont_size"]);
			echo "\" tabindex=\"11\" size=\"6\" maxlength=\"6\"> Caption font size. (1 is normal size, 1.5 is one and a half size, etc...)<br />";
// body font weight
			echo "<input type=\"text\" name=\"bodyfont_weight\" value=\"";
			echo stripslashes($row["bodyfont_weight"]);
			echo "\" tabindex=\"12\" size=\"6\" maxlength=\"6\"> Caption font weight. (400, 500, 600 or 700 --- 400 is normal, 700 is bold)<br />";
// body font style
			echo "<select size=\"1\" name=\"bodyfont_style\">
			<option value=\"";
			echo stripslashes($row["bodyfont_style"]);
			echo "\" selected=\"selected\">";
			echo stripslashes($row["bodyfont_style"]);
			echo "</option>
			<option value=\"none\">normal</option>
			<option value=\"solid\">itallic</option>
			</select> Caption font style.<br />";
// header font family
			echo "<br />";
			echo "<input type=\"text\" name=\"headerfont\" value=\"";
			echo stripslashes($row["headerfont"]);
			echo "\" tabindex=\"9\" size=\"15\" maxlength=\"100\"> Headline font - 3 seperated by a comma. (example: helvetica, arial, san-serif).<br />";
// header font color
			echo "<input type=\"text\" name=\"headerfont_color\" value=\"";
			echo stripslashes($row["headerfont_color"]);
			echo "\" tabindex=\"10\" size=\"6\" maxlength=\"6\"> Headline font color.<br />";
// header font size
			echo "<input type=\"text\" name=\"headerfont_size\" value=\"";
			echo stripslashes($row["headerfont_size"]);
			echo "\" tabindex=\"11\" size=\"6\" maxlength=\"6\"> Headline font size. (1 is normal size, 1.5 is one and a half size, etc...)<br />";
// header font weight
			echo "<input type=\"text\" name=\"headerfont_weight\" value=\"";
			echo stripslashes($row["headerfont_weight"]);
			echo "\" tabindex=\"12\" size=\"6\" maxlength=\"6\"> Headline font weight. (400, 500, 600 or 700 --- 400 is normal, 700 is bold)<br />";
// header font style
			echo "<select size=\"1\" name=\"headerfont_style\">
			<option value=\"";
			echo stripslashes($row["headerfont_style"]);
			echo "\" selected=\"selected\">";
			echo stripslashes($row["headerfont_style"]);
			echo "</option>
			<option value=\"none\">normal</option>
			<option value=\"solid\">itallic</option>
			</select> Headline font style.<br />";

// small font family
			echo "<br />";
			echo "<input type=\"text\" name=\"weefont\" value=\"";
			echo stripslashes($row["weefont"]);
			echo "\" tabindex=\"9\" size=\"15\" maxlength=\"100\"> Small font - 3 seperated by a comma. (ex: helvetica, arial, san-serif).<br />";
// small font color
			echo "<input type=\"text\" name=\"weefont_color\" value=\"";
			echo stripslashes($row["weefont_color"]);
			echo "\" tabindex=\"10\" size=\"6\" maxlength=\"6\"> Small font color.<br />";
// small font size
			echo "<input type=\"text\" name=\"weefont_size\" value=\"";
			echo stripslashes($row["weefont_size"]);
			echo "\" tabindex=\"11\" size=\"6\" maxlength=\"6\"> Small font size. (1 is normal size, 1.5 is one and a half size, etc...)<br />";
// small font weight
			echo "<input type=\"text\" name=\"weefont_weight\" value=\"";
			echo stripslashes($row["weefont_weight"]);
			echo "\" tabindex=\"12\" size=\"6\" maxlength=\"6\"> Small font weight. (400, 500, 600 or 700 --- 400 is normal, 700 is bold)<br />";
// small font style
			echo "<select size=\"1\" name=\"weefont_style\">
			<option value=\"";
			echo stripslashes($row["weefont_style"]);
			echo "\" selected=\"selected\">";
			echo stripslashes($row["weefont_style"]);
			echo "</option>
			<option value=\"none\">normal</option>
			<option value=\"solid\">itallic</option>
			</select> Small font style.<br /></p>";
// ------ link section ------
			echo "<hr />
			<p class=\"boldbod\">Links</a></p>";
// alink font family
			echo "<p class=\"normbod\"><input type=\"text\" name=\"alink_font\" value=\"";
			echo stripslashes($row["alink_font"]);
			echo "\" tabindex=\"9\" size=\"15\" maxlength=\"100\"> Link font - 3 seperated by a comma. (ex: helvetica, arial, san-serif).<br />";
// alink font decoration
			echo "<select size=\"1\" name=\"alink_decoration\">
			<option value=\"";
			echo stripslashes($row["alink_decoration"]);
			echo "\" selected=\"selected\">";
			echo stripslashes($row["alink_decoration"]);
			echo "</option>
			<option value=\"none\">none</option>
			<option value=\"solid\">underline</option>
			</select> Link font decoration. (the link as it appears by default)<br />";
// alink font weight
			echo "<input type=\"text\" name=\"alink_weight\" value=\"";
			echo stripslashes($row["alink_weight"]);
			echo "\" tabindex=\"12\" size=\"6\" maxlength=\"6\"> Link font weight. (400, 500, 600 or 700 --- 400 is normal, 700 is bold)<br />";
// alink font color
			echo "<input type=\"text\" name=\"alink_color\" value=\"";
			echo stripslashes($row["alink_color"]);
			echo "\" tabindex=\"10\" size=\"6\" maxlength=\"6\"> Link font color.<br />";
// alink font size
			echo "<input type=\"text\" name=\"alink_size\" value=\"";
			echo stripslashes($row["alink_size"]);
			echo "\" tabindex=\"11\" size=\"6\" maxlength=\"6\"> Link font size. (1 is normal size, 1.5 is one and a half size, etc...)<br />";
// avisited font family
			echo "<br />";
			echo "<input type=\"text\" name=\"avisited_font\" value=\"";
			echo stripslashes($row["avisited_font"]);
			echo "\" tabindex=\"9\" size=\"15\" maxlength=\"100\"> Visited link font - 3 seperated by a comma. (ex: helvetica, arial, san-serif).<br />";
// avisited font decoration
			echo "<select size=\"1\" name=\"avisited_decoration\">
			<option value=\"";
			echo stripslashes($row["avisited_decoration"]);
			echo "\" selected=\"selected\">";
			echo stripslashes($row["avisited_decoration"]);
			echo "</option>
			<option value=\"none\">none</option>
			<option value=\"solid\">underline</option>
			</select> Visited link font decoration. (the link as it appears by default)<br />";
// avisited font weight
			echo "<input type=\"text\" name=\"avisited_weight\" value=\"";
			echo stripslashes($row["avisited_weight"]);
			echo "\" tabindex=\"12\" size=\"6\" maxlength=\"6\"> Visited link font weight. (400, 500, 600 or 700 --- 400 is normal, 700 is bold)<br />";
// avisited font color
			echo "<input type=\"text\" name=\"avisited_color\" value=\"";
			echo stripslashes($row["avisited_color"]);
			echo "\" tabindex=\"10\" size=\"6\" maxlength=\"6\"> Visited link font color.<br />";
// avisited font size
			echo "<input type=\"text\" name=\"avisited_size\" value=\"";
			echo stripslashes($row["avisited_size"]);
			echo "\" tabindex=\"11\" size=\"6\" maxlength=\"6\"> Visited link font size. (1 is normal size, 1.5 is one and a half size, etc...)<br />";
// aactive font family
			echo "<br />";
			echo "<input type=\"text\" name=\"aactive_font\" value=\"";
			echo stripslashes($row["aactive_font"]);
			echo "\" tabindex=\"9\" size=\"15\" maxlength=\"100\"> Active link font - 3 seperated by a comma. (ex: helvetica, arial, san-serif).<br />";
// aactive font decoration
			echo "<select size=\"1\" name=\"aactive_decoration\">
			<option value=\"";
			echo stripslashes($row["aactive_decoration"]);
			echo "\" selected=\"selected\">";
			echo stripslashes($row["aactive_decoration"]);
			echo "</option>
			<option value=\"none\">none</option>
			<option value=\"solid\">underline</option>
			</select> Active link font decoration. (the link as it appears by default)<br />";
// aactive font weight
			echo "<input type=\"text\" name=\"aactive_weight\" value=\"";
			echo stripslashes($row["aactive_weight"]);
			echo "\" tabindex=\"12\" size=\"6\" maxlength=\"6\"> Active link font weight. (400, 500, 600 or 700 --- 400 is normal, 700 is bold)<br />";
// aactive font color
			echo "<input type=\"text\" name=\"aactive_color\" value=\"";
			echo stripslashes($row["aactive_color"]);
			echo "\" tabindex=\"10\" size=\"6\" maxlength=\"6\"> Active link font color.<br />";
// aactive font size
			echo "<input type=\"text\" name=\"aactive_size\" value=\"";
			echo stripslashes($row["aactive_size"]);
			echo "\" tabindex=\"11\" size=\"6\" maxlength=\"6\"> Active link font size. (1 is normal size, 1.5 is one and a half size, etc...)<br />";
// ahover font family
			echo "<br />";
			echo "<input type=\"text\" name=\"ahover_font\" value=\"";
			echo stripslashes($row["ahover_font"]);
			echo "\" tabindex=\"9\" size=\"15\" maxlength=\"100\"> Hover link font - 3 seperated by a comma. (ex: helvetica, arial, san-serif).<br />";
// ahover font decoration
			echo "<select size=\"1\" name=\"ahover_decoration\">
			<option value=\"";
			echo stripslashes($row["ahover_decoration"]);
			echo "\" selected=\"selected\">";
			echo stripslashes($row["ahover_decoration"]);
			echo "</option>
			<option value=\"none\">none</option>
			<option value=\"solid\">underline</option>
			</select> Hover link font decoration. (the link as it appears by default)<br />";
// ahover font weight
			echo "<input type=\"text\" name=\"ahover_weight\" value=\"";
			echo stripslashes($row["ahover_weight"]);
			echo "\" tabindex=\"12\" size=\"6\" maxlength=\"6\"> Hover link font weight. (400, 500, 600 or 700 --- 400 is normal, 700 is bold)<br />";
// ahover font color
			echo "<input type=\"text\" name=\"ahover_color\" value=\"";
			echo stripslashes($row["ahover_color"]);
			echo "\" tabindex=\"10\" size=\"6\" maxlength=\"6\"> Hover link font color.<br />";
// ahover font size
			echo "<input type=\"text\" name=\"ahover_size\" value=\"";
			echo stripslashes($row["ahover_size"]);
			echo "\" tabindex=\"11\" size=\"6\" maxlength=\"6\"> Hover link font size. (1 is normal size, 1.5 is one and a half size, etc...)<br /><br />";
			echo "<input name=\"submit\" type=\"submit\" value=\"Update\" /></form>";
	}
}
/////////////// end of SECTION 1

include ("/path/to/my/footer/script.php");

?>

```

as far as I can tell, this is exactly what happens: i click the "Update" button, the script does something, then the page refreshes with the old values from the database in the form field. it never passes the variables from the form in section 1 (see script) to the query in section 2 (see script).

---

### Post by Mirrorball on 2007-03-21
I bet $processform != 1. Before
```

if ($processform == 1) {

```
write:
```

echo (int) $processform;
exit();

```
See what will be printed.

---

### Post by nucklebone on 2007-03-21
[SIZE="4"]**0**[/SIZE]

so... yeah, $processform !=1

now, i am very confused. mostly due to my limited knowledge of php, but why wouldn't that script work? i'm certainly passing 1 as the variable. obviously, the obvious is escaping me.

p.s. thanks for your help, we'll get your ubuntu bean count up to 350 beans before this is over. ;)

EDIT (3:15pm): Since putting that code where you told me to put it resulted in getting "0" before the form, i redirected the form to a simple file based on your suggestion:
```
<?PHP
echo (int) $processform;
exit();
?>
```

and still got "0"

---

### Post by Mirrorball on 2007-03-21
I think I know what's wrong. This code relies on the register_globals setting being on and it's off. Write
```
$processform = $_POST['processform'];
```
before
```
if ($processform == 1) {
```
With register_globals turned off, POST (form) data will be only in $_POST, $processform hasn't even been initialized.
You could also turn register_globals on, but it's not recommended for security purposes.

---

### Post by nucklebone on 2007-03-21
That was it.

Now mysql is reporting an error in my syntax. But at least now I know once I fix my syntax it will work.

I re-tried the very original code (not the one posted above) I used when I first posted, along with the fix you just mentioned and was able to make it work. Now that I am using my new code in the example above(re-posted to reflect most current version) I'm getting a MySQL syntax error.

[COLOR="DarkRed"]You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '('style_id','body_color','table_color','table_border','table_border_color','tabl' at line 2[/COLOR]

But that was the problem with PHP. Thanks for the help.

---

### Post by nucklebone on 2007-03-21
nevermind...

never send insert syntax to do update's job.

thanks!

---

