---
title: "Need another  pair of eyes to see javascript error."
date: 2010-03-29
forum: Programming Talk
---

### Post by hockey97 on 2010-03-29
Fixed

---

### Post by Reiger on 2010-03-29
Apart from lacking proper indentation? Possibly a dodgy \"read_delete_messages.php\"?
Did you by any chance copy and paste that code?

---

### Post by Hellkeepa on 2010-03-29
HELLo!

Don't escape the quotes when trying to create a string, and the filename/URL to call in a AJAX request is a string. That is your problem.

Happy codin'!

---

### Post by hockey97 on 2010-03-30
Fixed

---

### Post by Compyx on 2010-03-30
Separate the javascript from the PHP code by putting all javascript into *.js files and loading those with <script type="text/javascript" src="blabla.js"></script>.
That'll make stuff a lot more readable and thus easier to debug.

And isn't 'http://www.domain.com' an example URL? I think you're supposed to install jQuery in your own domain. You didn't provide the error message, but I'm guessing it has something to do with '$' not being defined.

---

### Post by hessiess on 2010-03-30
> **hockey97 said:**
> oh, forgot to tell you this is in php. The javascript code above is inside a echo in a php file.

in the read_delete_messages.php file inside code is here:[PHP]<?php
session_start();
$user=$_SESSION["username"];
$app_name=$_POST["app_name"];
$message=$_POST["message1"];
$db=$_POST["db1"];
$action=$_POST["name1"];
$db_database ="Market" or die("Could not select database");
mysql_select_db ($db_database);
switch ($action){
case "Delete":
$query="DELETE FROM $app_name WHERE id ='$message'";
$query2="SELECT * FROM $app_name WHERE id = '$message'";
$result = mysql_query($query)or die(mysql_error());
$result2 = mysql_query($query2)or die(mysql_error());
if($result2!=""){
return true;}
else{
return false;}
break;
}
?>
[/PHP]

The code I posted in the original post is in a php file inside a echo.

here is the whole code from the original post.

[PHP]echo"<script type=\"text/javascript\" src=\"http://www.domain.com/pngFix/jquery-1.3.2.min.js\"></script>  
<script type=\"text/javascript\" src=\"http://www.domain.com/pngFix/jquery.pngFix.js\"></script>
<script type=\"text/javascript\">
$(document).ready(function(){
function market_messages(name ,db ,app){
$.post(\"market_app_messages.php\", { name1:name , db1:db, app_name:app }, 
function(html){
         $('#app_content').html(html);});}

function read_delete_messages(action ,database ,datatable ,message){
var html='<a>Loading....</a>';
$('#app_content').html(html);
$.post(\"read_delete_messages.php\", { name1:action , db1:database, app_name:datatable, message1:message }, 
function(data){
        if(data == ''){
           var html='<a>Error:Faied to process your request please try again.</a>';
           $('#app_content').html(html);}
       else{
         html='<a>Message:You suceeded on deleting the message.</a>';
           $('#app_content').html(html);}
         var count = '100';
         while(count > '0'){
         count--;}
        if (count=='0'){
        market_messages('Interested_people','Market','Market_messages');}
});
}});
</script>";[/PHP]

hope this helps.

Don't mix up everything into one file, its a sure fire way to produce an unmaintainable mess... as you have already discovered. HTML should be kept out of your business logic using a MVC framework or a templating language(which can be done using only plain PHP). Javascript is best kept out of the HTML in its own file, then loaded with a <script type="text/javascript" src="file.js"></script>. Frameworks like JQuery allow JavaScript to be applied using CSS style selectors, keeping it completely separate from the HTML.

---

### Post by Hellkeepa on 2010-03-30
HELLo!

In addition to what **Compyx** already has said, please use proper indentation when posting code that other people is meant to read. In fact, you'll do yourself a favour by using it regardless; It makes the code *much* easier to read.
The same goes for comments, btw.

**hessiess**: While a full-fledged MVC framework has it place in some bigger projects, recommending it to someone just learning the ropes (and a small project like this) is not only a waste, but rather counter-productive. If you ask me, at least.
Besides this, we are in complete agreement about the separation of the different types of code.

Happy codin'!

---

### Post by hessiess on 2010-03-30
> **Hellkeepa said:**
> HELLo!
**hessiess**: While a full-fledged MVC framework has it place in some bigger projects, recommending it to someone just learning the ropes (and a small project like this) is not only a waste, but rather counter-productive. If you ask me, at least.
Besides this, we are in complete agreement about the separation of the different types of code.


Hence the suggestion of using a templating language, plain PHP can be used as a perfectly usable templating language [http://thephppro.com/articles/pte.php](http://thephppro.com/articles/pte.php)

For example, the common procedure of displaying an array of items into HTML:

echo method
[php]
<ul>
<?php
foreach($items as $item)
{
    echo "<li><a href=\"" . $item['something'] . "\">" . $item['something-else'] . "<\a></li>";
}
?>
</ul>
[/php]

template method
[php]
<ul>
<?php foreach($items as $item): ?>
    <li><a href="<?php echo $item['something']; ?>"><?php echo $item['something-else']; ?></a></li>
<?php endforeach; ?>
</ul>
[/php]

The template method produces simpler code as there is no need to escape anything, its also a lot easier to read as your code gets more complicated.

---

### Post by hockey97 on 2010-03-30
> **Compyx said:**
> Separate the javascript from the PHP code by putting all javascript into *.js files and loading those with <script type="text/javascript" src="blabla.js"></script>.
That'll make stuff a lot more readable and thus easier to debug.

And isn't 'http://www.domain.com' an example URL? I think you're supposed to install jQuery in your own domain. You didn't provide the error message, but I'm guessing it has something to do with '$' not being defined.


the domain.com is a example. I have my own domain name and it's hosted on my own server. I took the domain out because in the past I had trouble. 

I am not a newb to php. I am new to ajax and intermediate level of jquery.

I gave you the whole code as you can see there is a function before the function that is having the errors and that function runs fine.

I was told if you make new files for each javascript code and load it in just like how I loaded the jquery in. They said it would eat up more hard drive space. They suggested me to write the code in the php with the html.
They claim it will lower the amount of space it takes up on a hard drive.

that is why I did what I did. Right now it's really too late to fix those. I might fix the neatness later since I already wrote a bunch of code this way.

---

### Post by hockey97 on 2010-03-30
Fixed.... I found the problem and fixed it. It's too complex.
Now the code works.

---

### Post by hessiess on 2010-03-30
> **hockey97 said:**
> They claim it will lower the amount of space it takes up on a hard drive.

Who cares about a few k/m bytes these days, maintaining readable code is far more important.

---

### Post by Compyx on 2010-03-30
Here's the code, properly indented, could do with a bit more whitespace though:

[php]
$(document).ready(
    function ()
    {
        function market_messages(name ,db ,app)
        {
            $.post("market_app_messages.php",
                { name1:name , db1:db, app_name:app },
                function (html)
                {
                    $('#app_content').html(html);
                }
            );
        }

        function read_delete_messages(action ,database ,datatable ,message)
        {
            var html = '<a>Loading....</a>';
            $('#app_content').html(html);
            $.post("read_delete_messages.php",
                { name1:action , db1:database, app_name:datatable,
                  message1:message },
                function (data)
                {
                    if (data == '') {
                        var html = '<a>Error:Faied to process your request please try again.</a>';
                        $('#app_content').html(html);
                    } else {
                        html = '<a>Message:You suceeded on deleting the message.</a>';
                        $('#app_content').html(html);
                    }
                    var count = '100';
                    while (count > '0') {
                        count--;
                    }
                    if (count == '0') {
                        market_messages('Interested_people','Market','Market_messages');
                    }
                }
            );
        }
    }
);
[/php]

Now, if you could post the exact error message by copying and pasting it, I might be able to be of further assistance.

---

