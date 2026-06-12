---
title: "PHP Object Orientated"
date: 2008-05-27
forum: Programming Talk
---

### Post by thenetduck on 2008-05-27
Hi 
I am developing my first online app. I know object orientated concepts. Here is my question. 

There are three parts to my site (four maybe).... Gui/Screens ... Database... and Contol that interacts the two. I am assuming if I do it OOP I will have my classes interact with my Database and use my control to create objects etc. 

My question is... How does this work? Is this the right way to do it? Or should I be doing it a different way? Also, say I have a new user, do I create a new User object every time he logs in? or does that object now always exist some how? I am a little confused on how to make Objects work with a database as in the past, I have not used databases with objects. 

Thanks for any help
The Net Duck

---

### Post by CptPicard on 2008-05-27
Look up the Model-View-Controller pattern.

Your Model is usually the database and associated classes, maybe through some kind of an ORM layer. Your Controllers are typically hooked to URLs that are yanked in response to user clicking links, posting forms etc... the View are templates the Controllers forward to, and that render what the user sees.

Mind you, Python+TurboGears makes this so much more obvious than PHP ever could...

---

### Post by LaRoza on 2008-05-27
> **CptPicard said:**
> 
Mind you, Python+TurboGears makes this so much more obvious than PHP ever could...

Or a PHP MVC framework ;)

---

### Post by Ann.A on 2008-05-27
We used [ezsql]("http://www.woyano.com/jv/ezsql") at my last company for a side project.  

You should find the answers to your questions, by seeing how ezsql works along with the other good advice here :)

---

### Post by mssever on 2008-05-27
For PHP, I heartily recommend [Code Igniter]("http://www.codeigniter.com"). It's one of several MVC frameworks for PHP. Its biggest advantage is that it's documented much better than most frameworks.

---

### Post by The Titan on 2008-05-28
> **thenetduck said:**
> Hi 
I am developing my first online app. I know object orientated concepts. Here is my question. 

There are three parts to my site (four maybe).... Gui/Screens ... Database... and Contol that interacts the two. I am assuming if I do it OOP I will have my classes interact with my Database and use my control to create objects etc. 

My question is... How does this work? Is this the right way to do it? Or should I be doing it a different way? Also, say I have a new user, do I create a new User object every time he logs in? or does that object now always exist some how? I am a little confused on how to make Objects work with a database as in the past, I have not used databases with objects. 

Thanks for any help
The Net Duck
objects work with a database just like any other script would in php.  Here is an example:

connecting to database WITHOUT using objects:
[php]

<?php

//connecting to mysql
mysql_connect("server", "mysl username", "mysql password");

//selecting database
mysql_select_database("database");

//rest of code, ready to pass querys

$result = mysql_query("SOME MYSQL query HERE");
$resArray = mysql_fetch_array($result);

?>
[/php]
And here is how you would do it in OO:

[php]

<?php

class Mysql{
    
    public function __construct(){
        /*
       Connect to mysql like above
        Using mysql connect
        */
    }


    public function do_query($query){
    
        /*
        Set up a function to do querys for you, all you have to do is
        pass a query string and have it return the result.
        */

        return $result;
    }


}

/*
The class would generally be located in a different file, 
like mysql.class.php or something.  And then included
when you need it.

then you can use it like this
*/

$Mysql = new Mysql();

$result = $Mysql->query("SOME MYSQL query HERE");

$resArray = mysql_fetch_array($result);



?>


[/php]


So in conclusion, if you plan on using MySQL alot in your PHP application then it is likely that OOP is a good way to go.  It allows you to organize everything that you need to do with MySQL with functions which can lead to more secure and faster development.    

you can learn more about PHP and OOP in the manual at the php website, my examples were very crude and slim and are strictly for example but i hope it gets the point across.

---

