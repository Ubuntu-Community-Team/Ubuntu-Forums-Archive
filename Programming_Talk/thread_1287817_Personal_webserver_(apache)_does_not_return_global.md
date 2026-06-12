---
title: "Personal webserver (apache) does not return global variables"
date: 2009-10-10
forum: Programming Talk
---

### Post by darkchest on 2009-10-10
Hi all,

I installed php, apache and mysql on my ubuntu laptop and I am going thru some tutorial files. I run one of the php files on my localhost but it does not return any variables as explained.

The code is as below:
=========================================================
```

<html>

<head>

<title>Untitled Document</title>

<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">

</head>



<body bgcolor="#FFFFFF">

<table width="95%" border="1" bordercolorlight="#0000CC" bordercolordark="#0000CC">

  <tr> 

    <td width="30%" valign="top" bgcolor="EEEEFF"> 

      <p><font face="Arial, Helvetica, sans-serif"><b>Code File 02 01-2 - External 

        Variables</b></font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1"><b>Scenario:</b></font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1">You need to gather 

        variables from the user's request, the HTTP request, or from the environment 

        to manage interactions with the user. The solution demonstrates how to 

        use external variables available in Php to access these variables.</font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1"><br>

        <b>Coding Solution:</b></font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1">Php automatically 

        provides several external variables in the form of SuperGlobal arrays 

        (SuperGlobals are variables that can automatically be accessed from anywhere 

        in a script without identifying them as Global variables). The names/methods 

        used to access these variables has changed in more recent versions of 

        Php.</font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1">In order to demonstrate 

        accessing these variables, we'll simply print them to the screen using 

        the print_r function, along with HTML &lt;PRE&gt; tags to preserve the 

        formatting and spacing. Like any other array, Php variables that are arrays 

        can be accessed by their names and any index or name associated with a 

        particular slot in the array.</font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1"><b>Code:</b></font></p>

      <table width="100%" border="1" cellpadding="2">

        <tr>

          <td> <code> echo "&lt;pre&gt;";<br>

            print_r($GLOBALS);<br>

            echo "&lt;/pre&gt;";</code></td>

        </tr>

      </table>

      <p><font face="Arial, Helvetica, sans-serif" size="-1">Php &lt;pre&gt; provides 

        the following external variables as SuperGlobals:</font></p>

      <ul>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$GLOBALS (part 

          of Php since Php 3.0) This displays all the arrays for all the variables 

          that are available within the global scope of the script you are running.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_SERVER (use 

          $HTTP_SERVER_VARS for older versions of Php). Includes variables from 

          the Web server, such as CONTENT_LENGTH, HTTP_HOST, and so forth.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_GET (use $HTTP_GET_VARS). 

          Includes variables provided as part of a query string.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_POST (use $HTTP_POST_VARS). 

          Includes variables provided as part of a form post.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1"> $_COOKIE (use 

          $HTTP_COOKIE_VARS). Includes cookies sent with a request.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_FILES (use HTTP_POST_FILES). 

          Includes variables from post file uploads. </font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_ENV (use $HTTP_ENV_VARS). 

          Includes variables from the environment, such as PATH. </font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_REQUEST Includes 

          variables provided by any user input method. There is no similar array 

          available before Php 4.1.0. </font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_SESSION (use 

          $HTTP_SESSION_VARS). Includes variables that are part of the current 

          user session</font></li>

      </ul>

    </td>

    <td width="70%" valign="top"> 

      <form method="post" action="0201_2.php">

        <font face="Arial, Helvetica, sans-serif" size="-1"> 

        <input type="hidden" name="posted" value="True">

        </font> 

        <p><font face="Arial, Helvetica, sans-serif" size="-1">Please pick an 

          external variable to display: 

          <select name="external_variable">

            <option value="GLOBALS">GLOBALS</option>

            <option value="_SERVER">_SERVER</option>

            <option value="_GET">_GET</option>

            <option value="_POST">_POST</option>

            <option value="_COOKIE">_COOKIE</option>

          </select>

          </font></p>

        <p> <font face="Arial, Helvetica, sans-serif" size="-1"> 

          <input type="submit" name="pick" value="Pick">

          </font></p>

      </form>

      <font face="Arial, Helvetica, sans-serif"><?

if (isset($posted)) {



	if ($external_variable == "GLOBALS") {

		echo "<PRE>";

		print_r($GLOBALS);

		echo "</PRE>";

	} elseif ($external_variable == "_SERVER") {

		echo "<PRE>";

		print_r($_SERVER);

		echo "</PRE>";

	} elseif ($external_variable == "_GET") {

		echo "<PRE>";

		print_r($_GET);

		echo "</PRE>";

	} elseif ($external_variable == "_POST") {

		echo "<PRE>";

		print_r($_POST);

		echo "</PRE>";

	} elseif ($external_variable == "_COOKIE") {

		echo "<PRE>";

		print_r($_COOKIE);

		echo "</PRE>";

	}

}

?></font></td>

  </tr>

  <tr>

    <td width="30%" valign="top" bgcolor="EEEEFF"><img src="spacer.gif" width="360" height="1"></td>

    <td width="70%" valign="top">&nbsp;</td>

  </tr>

</table>

</body>

</html>

```
====================================================

Can you please tell me why? I checked to see if my server was started and it was. Thank you.

---

### Post by NoaHall on 2009-10-10
```

<html>

<head>

<title>Untitled Document</title>

<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">

</head>



<body bgcolor="#FFFFFF">

<?php
if (isset($pick))
{
	if ($external_variable == "GLOBALS")
	{
		echo "<PRE>";
		print_r($GLOBALS);

		echo "</PRE>";
	}
	elseif ($external_variable == "_SERVER") 
	{
		echo "<PRE>";
		print_r($_SERVER);
		echo "</PRE>";
	} 
	
	elseif ($external_variable == "_GET") 
	{
		echo "<PRE>";
		print_r($_GET);
		echo "</PRE>";
	} 
	elseif ($external_variable == "_POST") 
	{
		echo "<PRE>";
		print_r($_POST);
		echo "</PRE>";
	} 
	
	elseif ($external_variable == "_COOKIE") 
	{
		echo "<PRE>";
		print_r($_COOKIE);
		echo "</PRE>";
	}
}

?>

<table width="95%" border="1" bordercolorlight="#0000CC" bordercolordark="#0000CC">

  <tr> 

    <td width="30%" valign="top" bgcolor="EEEEFF"> 

      <p><font face="Arial, Helvetica, sans-serif"><b>Code File 02 01-2 - External 

        Variables</b></font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1"><b>Scenario:</b></font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1">You need to gather 

        variables from the user's request, the HTTP request, or from the environment 

        to manage interactions with the user. The solution demonstrates how to 

        use external variables available in Php to access these variables.</font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1"><br>

        <b>Coding Solution:</b></font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1">Php automatically 

        provides several external variables in the form of SuperGlobal arrays 

        (SuperGlobals are variables that can automatically be accessed from anywhere 

        in a script without identifying them as Global variables). The names/methods 

        used to access these variables has changed in more recent versions of 

        Php.</font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1">In order to demonstrate 

        accessing these variables, we'll simply print them to the screen using 

        the print_r function, along with HTML &lt;PRE&gt; tags to preserve the 

        formatting and spacing. Like any other array, Php variables that are arrays 

        can be accessed by their names and any index or name associated with a 

        particular slot in the array.</font></p>

      <p><font face="Arial, Helvetica, sans-serif" size="-1"><b>Code:</b></font></p>

      <table width="100%" border="1" cellpadding="2">

        <tr>

          <td> <code> echo "&lt;pre&gt;";<br>

            print_r($GLOBALS);<br>

            echo "&lt;/pre&gt;";</code></td>

        </tr>

      </table>

      <p><font face="Arial, Helvetica, sans-serif" size="-1">Php &lt;pre&gt; provides 

        the following external variables as SuperGlobals:</font></p>

      <ul>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$GLOBALS (part 

          of Php since Php 3.0) This displays all the arrays for all the variables 

          that are available within the global scope of the script you are running.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_SERVER (use 

          $HTTP_SERVER_VARS for older versions of Php). Includes variables from 

          the Web server, such as CONTENT_LENGTH, HTTP_HOST, and so forth.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_GET (use $HTTP_GET_VARS). 

          Includes variables provided as part of a query string.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_POST (use $HTTP_POST_VARS). 

          Includes variables provided as part of a form post.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1"> $_COOKIE (use 

          $HTTP_COOKIE_VARS). Includes cookies sent with a request.</font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_FILES (use HTTP_POST_FILES). 

          Includes variables from post file uploads. </font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_ENV (use $HTTP_ENV_VARS). 

          Includes variables from the environment, such as PATH. </font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_REQUEST Includes 

          variables provided by any user input method. There is no similar array 

          available before Php 4.1.0. </font></li>

        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_SESSION (use 

          $HTTP_SESSION_VARS). Includes variables that are part of the current 

          user session</font></li>

      </ul>

    </td>

    <td width="70%" valign="top"> 

      <form method="post" >

        <font face="Arial, Helvetica, sans-serif" size="-1"> 

        <input type="hidden" name="posted" value="True">

        </font> 

        <p><font face="Arial, Helvetica, sans-serif" size="-1">Please pick an 

          external variable to display: 

          <select name="external_variable">

            <option value="GLOBALS">GLOBALS</option>

            <option value="_SERVER">_SERVER</option>

            <option value="_GET">_GET</option>

            <option value="_POST">_POST</option>

            <option value="_COOKIE">_COOKIE</option>

          </select>

          </font></p>

        <p> <font face="Arial, Helvetica, sans-serif" size="-1"> 

          <input type="submit" name="pick" value="Pick">

          </font></p>

      </form>

      <font face="Arial, Helvetica, sans-serif"><?


</font></td>

  </tr>

  <tr>

    <td width="30%" valign="top" bgcolor="EEEEFF"><img src="spacer.gif" width="360" height="1"></td>

    <td width="70%" valign="top">&nbsp;</td>

  </tr>

</table>

</body>

</html>

```

---

### Post by darkchest on 2009-10-10
I tried your code, but it still didnt work. (I removed the <? on line 124)

---

### Post by NoaHall on 2009-10-10
Let me take a look at it then. brb.

A lot of it needs changing. Brb.

---

### Post by darkchest on 2009-10-10
Thanks

---

### Post by -grubby on 2009-10-10
I hate to provide a post that doesn't actually help, but looking at your HTML, it would be much more efficient if you used [CSS](http://www.w3schools.com/css/)...

---

### Post by NoaHall on 2009-10-10
+1 for CSS, and I'd get rid of the tables.

Almost there, just got to work out why it won't choose something.

---

### Post by darkchest on 2009-10-10
Well grubby, thanks for the advice. But i actually got it from a tutorial file. Im learning PHP and that was one of the work files. I was wondering why what they were explaining was not working on my ubuntu laptop.

I still need to practice CSS also. So thanks for the link.

Umm NoaHall, how else would you arrange stuff on a webpage without tables? I may find that out with time but im trying to create a webpage soonest, thats why any information that would get me on the right track will be helpful.

---

### Post by NoaHall on 2009-10-10
I use things called <div> to declare individual pieces of html. I then set the layout in the CSS, using the <div> name.

Done.

```

<html>
<head>
<title>Untitled Document</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>
<body bgcolor="#FFFFFF">
<?php
$external_variable=$_POST['external_variable'];
if (isset($_POST['pick']))
{
	if ($external_variable == "GLOBALS")
	{
		echo "<PRE>";
		print_r($GLOBALS);
		echo "</PRE>";
	}
	elseif ($external_variable == "_SERVER")
	{
		echo "<PRE>";
		print_r($_SERVER);
		echo "</PRE>";
	}

	elseif ($external_variable == "_GET")
	{
		echo "<PRE>";
		print_r($_GET);
		echo "</PRE>";
	}
	elseif ($external_variable == "_POST")
	{
		echo "<PRE>";
		print_r($_POST);
		echo "</PRE>";
	}

	elseif ($external_variable == "_COOKIE")
	{
		echo "<PRE>";
		print_r($_COOKIE);
		echo "</PRE>";
	}
	else
	{
		echo "Error";
		echo $external_variable;
	}
}

?>

<table width="95%" border="1" bordercolorlight="#0000CC" bordercolordark="#0000CC">
  <tr>
    <td width="30%" valign="top" bgcolor="EEEEFF">
      <p><font face="Arial, Helvetica, sans-serif"><b>Code File 02 01-2 - External
        Variables</b></font></p>
      <p><font face="Arial, Helvetica, sans-serif" size="-1"><b>Scenario:</b></font></p>
      <p><font face="Arial, Helvetica, sans-serif" size="-1">You need to gather
        variables from the user's request, the HTTP request, or from the environment
        to manage interactions with the user. The solution demonstrates how to
        use external variables available in Php to access these variables.</font></p>
      <p><font face="Arial, Helvetica, sans-serif" size="-1"><br>
       <b>Coding Solution:</b></font></p>
      <p><font face="Arial, Helvetica, sans-serif" size="-1">Php automatically
        provides several external variables in the form of SuperGlobal arrays
        (SuperGlobals are variables that can automatically be accessed from anywhere
        in a script without identifying them as Global variables). The names/methods
        used to access these variables has changed in more recent versions of
        Php.</font></p>
      <p><font face="Arial, Helvetica, sans-serif" size="-1">In order to demonstrate
        accessing these variables, we'll simply print them to the screen using
        the print_r function, along with HTML &lt;PRE&gt; tags to preserve the
        formatting and spacing. Like any other array, Php variables that are arrays
        can be accessed by their names and any index or name associated with a
        particular slot in the array.</font></p>
      <p><font face="Arial, Helvetica, sans-serif" size="-1"><b>Code:</b></font></p>
      <table width="100%" border="1" cellpadding="2">
        <tr>
          <td> <code> echo "&lt;pre&gt;";<br>
            print_r($GLOBALS);<br>
            echo "&lt;/pre&gt;";</code></td>
        </tr>
      </table>
      <p><font face="Arial, Helvetica, sans-serif" size="-1">Php &lt;pre&gt; provides
        the following external variables as SuperGlobals:</font></p>
      <ul>
        <li><font face="Arial, Helvetica, sans-serif" size="-1">$GLOBALS (part
          of Php since Php 3.0) This displays all the arrays for all the variables
          that are available within the global scope of the script you are running.</font></li>
        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_SERVER (use
          $HTTP_SERVER_VARS for older versions of Php). Includes variables from
          the Web server, such as CONTENT_LENGTH, HTTP_HOST, and so forth.</font></li>
        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_GET (use $HTTP_GET_VARS).
          Includes variables provided as part of a query string.</font></li>
        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_POST (use $HTTP_POST_VARS).
          Includes variables provided as part of a form post.</font></li>
        <li><font face="Arial, Helvetica, sans-serif" size="-1"> $_COOKIE (use
          $HTTP_COOKIE_VARS). Includes cookies sent with a request.</font></li>
        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_FILES (use HTTP_POST_FILES).
          Includes variables from post file uploads. </font></li>
        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_ENV (use $HTTP_ENV_VARS).
         Includes variables from the environment, such as PATH. </font></li>
        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_REQUEST Includes
          variables provided by any user input method. There is no similar array
          available before Php 4.1.0. </font></li>
        <li><font face="Arial, Helvetica, sans-serif" size="-1">$_SESSION (use
          $HTTP_SESSION_VARS). Includes variables that are part of the current
          user session</font></li>
      </ul>
    </td>
    <td width="70%" valign="top">
      <form method="post" >
        <font face="Arial, Helvetica, sans-serif" size="-1">
        <input type="hidden" name="posted" value="True">
        </font>
        <p><font face="Arial, Helvetica, sans-serif" size="-1">Please pick external variable to display:
          <select name="external_variable">
            <option value="GLOBALS">GLOBALS</option>
            <option value="_SERVER">_SERVER</option>
            <option value="_GET">_GET</option>
            <option value="_POST">_POST</option>
            <option value="_COOKIE">_COOKIE</option>
          </select>
          </font></p>
        <p> <font face="Arial, Helvetica, sans-serif" size="-1">
          <input type="submit" name="pick" value="Pick">
          </font></p>
      </form>
      <font face="Arial, Helvetica, sans-serif">
</font></td>
  </tr>
  <tr>
    <td width="30%" valign="top" bgcolor="EEEEFF"><img src="spacer.gif" width="360" height="1"></td>
    <td width="70%" valign="top">&nbsp;</td>
  </tr>
</table>
</body>
</html>

```

edit - try it now! I put two "==" by mistake.

---

### Post by darkchest on 2009-10-10
Thank you. I tried the code and it worked. I will study it and find out what was wrong with mine. I guess im reading an old school version of php.

About the <div> tags. I will read more about it. Thank you all

---

