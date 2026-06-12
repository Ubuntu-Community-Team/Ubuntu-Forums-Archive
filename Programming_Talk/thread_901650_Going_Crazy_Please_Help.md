---
title: "Going Crazy Please Help"
date: 2008-08-26
forum: Programming Talk
---

### Post by abhik.chakraborty on 2008-08-26
Hi All I have recently got some code from 
[http://dojotoolkit.org/book/dojo-book-0-9/part-2-dijit/form-validation-specialized-input/textbox-validating-currency-number](http://dojotoolkit.org/book/dojo-book-0-9/part-2-dijit/form-validation-specialized-input/textbox-validating-currency-number)

For the Currency Number.

I have taken the code from the above link and added to a file in kate.

Here is the code below:

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
            "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>CurrencyTextBox Demo</title>
    <style type="text/css">
        @import "http://o.aolcdn.com/dojo/1.0/dijit/themes/tundra/tundra.css";
        @import "http://o.aolcdn.com/dojo/1.0/dojo/resources/dojo.css"
    </style>
    <script type="text/javascript" src="http://o.aolcdn.com/dojo/1.0/dojo/dojo.xd.js"
        djConfig="parseOnLoad: true"></script>
    <script type="text/javascript">
       dojo.require("dojo.parser");
       dojo.require("dijit.form.CurrencyTextBox");
    </script>
</head>
<body class="tundra">
    <form method="post">
        <input type="text" name="income1" value="54775.53"
                dojoType="dijit.form.CurrencyTextBox"
                required="true"
                constraints="{fractional:true}"
                currency="USD"
                invalidMessage="Invalid amount.  Include dollar sign, commas, and cents." />
    <input type="submit" value="Go!"/>
    </form>
</body></html>


I have the file as .php extension and while I run the file I get a special character before the $ in the text box.

I saw that with .html file on works fine. 

I am really not sure why this is happening.

I further checked that my kate is using utf-8 encoding.

If anyone have got some idea of that. Please let me know.

Thanks in advance.

---

### Post by rogeriopvl on 2008-08-26
I've tested it here in my system, saved it has .php and got nothing wrong. I used Gedit.

Have you tried other editors?

---

