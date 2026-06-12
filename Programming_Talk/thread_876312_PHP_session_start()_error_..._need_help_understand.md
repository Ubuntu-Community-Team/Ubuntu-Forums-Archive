---
title: "PHP session_start() error ... need help understanding error"
date: 2008-07-31
forum: Programming Talk
---

### Post by thenetduck on 2008-07-31
```

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /opt/lampp/htdocs/development/Piles/Piles/start.php:2) in /opt/lampp/htdocs/development/Piles/Piles/verify_user.php on line 2

```


that is the error I get. 

Ok so I can create this error when I add .... include "verify_user.php" to my "start.php" file. This is what I have in my verify_user.php script 

```

<?php
session_start();
/**
 *  Summary: 
 *  This script will be added at the top of each page 
 *  and will check to make sure the user can access
 *  this page. If he can, the script simply does nothing allowing
 *  you to continue veiwing the page you intended to view. If 
 *  you are not logged in, it will redirect you to the login page 
 *  and that page will tell you to login. 
 */
if (isset($_SESSION['logged_user']) && $_SESSION['logged_user'] !="" || 
    isset($_SESSION['logged_password']) && $_SESSION['logged_password'] !="")
{
    // Does nothing and continues with the script.
}
else
{
    // Send them to the attempted login page. 
    header("Location:tried.log.php");
}
?>


```

this is what start.php looks like

```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<?php
    include "verify_user.php"; // make sure this is a user
?>
<html>
    <link rel="stylesheet" type="text/css" href="css/style.css" />
  <head>
    <title>Welcome to Piles</title>
    <h1>Wecome to Piles </h1>
  </head>
  <body>
      <appnav><a href = ""> <img src = "img/create_project_btn.png" border=0> </a></appnav>
      <br />
      <form action="control.php" method="POST">
          New Project Name: 
      <input type="text" name="new_project_name" value="Enter project name here" size="25" />
      <input type="submit" value="create" name="main_btn" />
</form>
      OR
      <br />
      <h1> view previously created projects </h1>
<?php
    
	// Code here will populat projects that all ready exist and allow the user to click on them. 
        function displayProjects()
        {
            $project_list = "<br />";
            $project_list = $project_list. "1) This is an example of a project that could be here.";
            return $project_list;
        }
    echo displayProjects();
?>
  </body>
</html>


```

I can't figure out why it gives me this error or what I am doing wrong. I have looked into ob_start() thingy but it doesn't make sense to me and I don't know how to use it. Does anyone have a solution? 

Thanks for any help
The Net Duck

---

### Post by drubin on 2008-07-31
> **thenetduck said:**
> ```

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /opt/lampp/htdocs/development/Piles/Piles/start.php:2) in /opt/lampp/htdocs/development/Piles/Piles/verify_user.php on line 2

```
[QUOTE]
That error explains that your headers where already sent to the browser ie Your php script has already outputted some text.. 

If you look at the first line of your php script it is sending the doc type.

[QUOTE=thenetduck;5498210]
```

<?php
session_start();
/**
 *  Summary: 
 *  This script will be added at the top of each page 
 *  and will check to make sure the user can access
 *  this page. If he can, the script simply does nothing allowing
 *  you to continue veiwing the page you intended to view. If 
 *  you are not logged in, it will redirect you to the login page 
 *  and that page will tell you to login. 
 */
if (isset($_SESSION['logged_user']) && $_SESSION['logged_user'] !="" || 
    isset($_SESSION['logged_password']) && $_SESSION['logged_password'] !="")
{
    // Does nothing and continues with the script.
}
else
{
    // Send them to the attempted login page. 
    header("Location:tried.log.php");
}
?>


```

this is what start.php looks like

```

<?php
    include "verify_user.php"; // make sure this is a user
?>
**<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">**
<html>
    <link rel="stylesheet" type="text/css" href="css/style.css" />
  <head>
    <title>Welcome to Piles</title>
    <h1>Wecome to Piles </h1>
  </head>
  <body>
      <appnav><a href = ""> <img src = "img/create_project_btn.png" border=0> </a></appnav>
      <br />
      <form action="control.php" method="POST">
          New Project Name: 
      <input type="text" name="new_project_name" value="Enter project name here" size="25" />
      <input type="submit" value="create" name="main_btn" />
</form>
      OR
      <br />
      <h1> view previously created projects </h1>
<?php
    
	// Code here will populat projects that all ready exist and allow the user to click on them. 
        function displayProjects()
        {
            $project_list = "<br />";
            $project_list = $project_list. "1) This is an example of a project that could be here.";
            return $project_list;
        }
    echo displayProjects();
?>
  </body>
</html>


```


Try what i changed to bold. You might also want to take a look at ob_start() ob_end(); ob_flush_end();  They buffer out put until such time as you chose to output it. You could use  ob_start() as the first line of your script that then no matter where in the file you call "header()" it should work. just remember to call the flush method.

---

### Post by drubin on 2008-08-02
Just remembered this thread. Any one else that is having the same error should also remember.

If your files end like this it could break your  session/headers
[PHP]
?>

[/PHP]
Notice the trailing new lines... That could also cause issues with sessions as the file is included and the last line is outputted as html, or at least a new line. (Still output from the file)

---

### Post by thenetduck on 2008-08-03
Your first suggestion fixed my problem. I have been looking into ob_start() a little more and looks like it should work, I have however been playing it safe for now and not echoing anything after headers. so far is been working because everything goes threw a "contro.php" type script. Thanks for the help, 

The Net Duck

---

### Post by drubin on 2008-08-04
> **thenetduck said:**
> Your first suggestion fixed my problem. I have been looking into ob_start() a little more and looks like it should work, I have however been playing it safe for now and not echoing anything after headers. so far is been working because everything goes threw a "contro.php" type script. Thanks for the help, 

The Net Duck

I am not a HUGE fan of ob_start() functions unless you need them for some reason, as they remove output to the user until the very end, It may some times look as if your website is not loading. I am a fan of displaying what you have to the user when you have it.

---

