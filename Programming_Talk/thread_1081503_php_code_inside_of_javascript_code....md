---
title: "php code inside of javascript code..."
date: 2009-02-26
forum: Programming Talk
---

### Post by qmqmqm on 2009-02-26
Hi

I have the following line of javascript code:

url=url+"?profile_name=" + <?php echo $name;?>;

This line of code is in an external .js file that an html file links to. However it is causing error.

Does anyone has any suggestions on how to pass a variable from php to javascript?

Thanks,

Tom

---

### Post by smani on 2009-02-26
Assuming the php variable contains an arbitrary string and not the name of a javascript variable you want to use, you need to enclose the <?php .. ?> part into quotes too.

---

### Post by qmqmqm on 2009-02-26
> **smani said:**
> Assuming the php variable contains an arbitrary string and not the name of a javascript variable you want to use, you need to enclose the <?php .. ?> part into quotes too.

Hi smani

I tried this:

url=url+"?profile_name=" + "<?php echo $name;?>";

However it seems that javascript just treats the php part as a normal string and does not try to interpret it with php.

Does anyone have any suggestions?

Thanks,

Tom

---

### Post by smani on 2009-02-26
Stupid question, but is the extension of the file actually php and on a webserver with php support?

---

### Post by qmqmqm on 2009-02-26
Hi Smani

The file is a .js file, on a server that supports php.

The line of code that I provided in the first message is in a js function in the .js file.

There is an html file that refers to the .js file by:
<script type="text/javascript" src="my.js"></script>

Thanks,

Tom

---

### Post by simeon87 on 2009-02-26
This isn't going to work because PHP is executed by the webserver while JavaScript is executed by the webbrowser, so you can't use PHP in a JavaScript file.

What is exactly the problem you're trying to solve? You could let PHP generate the JavaScript and embed that in the webpage if you want to pass values from PHP to JavaScript.

---

### Post by smani on 2009-02-26
You need to rename the file as .php and then declare the content-type as text/javascript, otherwise the webserver will not interpret anything in the page and simply send it to the client as-is.

---

### Post by qmqmqm on 2009-02-26
> **smani said:**
> You need to rename the file as .php and then declare the content-type as text/javascript, otherwise the webserver will not interpret anything in the page and simply send it to the client as-is.

could you please give a simple example code?

Thanks,

Tom

---

### Post by qmqmqm on 2009-02-26
> **smani said:**
> You need to rename the file as .php and then declare the content-type as text/javascript, otherwise the webserver will not interpret anything in the page and simply send it to the client as-is.

Does this mean that the javascript code is generated only once when the page is loaded. When the content of the php variable changes after that, the javascript code will not update that value?

Thanks,

Tom

---

### Post by cerealtx on 2009-02-26
php dosn't change on a page, its all done pefore it gets to your browser its a server side language, u might want too look into ajax

---

### Post by simeon87 on 2009-02-26
> **qmqmqm said:**
> Does this mean that the javascript code is generated only once when the page is loaded. When the content of the php variable changes after that, the javascript code will not update that value?

Thanks,

Tom

The PHP code will generate the JavaScript and send that to the user. After that, it's not "updated" because PHP is executed per page view, so only when the user refreshes and requests a new page, the PHP code can send an updated script.

But, like cerealtx said, you may want to look into Ajax which allows you to send requests from the JavaScript to the webserver which can reply by sending new data back.

---

### Post by smani on 2009-02-26
To explain it a bit more in detail: the purpose of php (and any server-side scripting language) is to generate a file (html, css, js, etc) BEFORE sending it to the client, and then it will send a what-appears-to-be normal html,css,js or whatever page, which then is static as any other page. Once the file is transfered, the connection with the server is interrupted, that is, you cannot simply change a variable on the server side and see it updated on the client side. If you want to keep the connection between server and client open to exchange data even when the page is loaded, AJAX is what you are looking for, as stated above. If you are happy with "statically-generated pages", an example code would be:
```

<?php
header("Content-type: "."text/javascript");
$var=$_GET['var'];
?>
document.onload=function(){alert("<?php echo $var;?>");}

```
This file would be generated based upon the GET variable var, i.e. .../js_script.php?var=SomeValue.

---

### Post by Reiger on 2009-02-26
What you are looking for is something to the effect of

[X]HTML doc:
[code]
<head>
<script type="text/javascript" src="http://your-domain/path/to/js/script.php" />
<!-- some more stuff here -->
[code]

PHP file:
[php]
<?php
header("Content-type: text/javascript");
/*
With your coding style you'd probably do all your includes/requires here...
*/
?>
/*
Some fixed JavaScript here
*/
<?php echo $variable_js_content;
?>
/*
And possibly more JavaScript here...
*/
[/php]

---

### Post by qmqmqm on 2009-02-28
Thank you everyone. Studied all your replies, and I think I know what to do now - and understand how php works much better :)

---

### Post by qmqmqm on 2009-03-03
Hi Reiger

I implemented your code however it did not work for me...
Does anyone know why this would not work:

HTML doc:
<head>
<script type="text/javascript" src="http://your-domain/path/to/js/script.php" />
<!-- some more stuff here -->
... ...

PHP file:
<?php
header("Content-type: text/javascript");
?>
function foo(){
    alert ("hi");
}



Thanks,

Tom

---

