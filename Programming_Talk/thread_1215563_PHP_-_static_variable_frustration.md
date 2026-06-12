---
title: "PHP - static variable frustration"
date: 2009-07-17
forum: Programming Talk
---

### Post by akvino on 2009-07-17
Someone please tell me why is this wrong and how it should be done:

[php]
function get_value()
{
    STATIC $bandName;
    
    if (!isset($_POST["bandfield"]))
    {
        $bandName = $_POST["bandfield"];
        return $bandName;
    }
    else return $bandName;

}
[/php]


HOW would you do that?



My second question has to do with forms - I have a requirement to take form's input - based on input query the Database, provide output that requires input - and then process the input. In other words:
I have a band_name entry that has collection of albums. I want user to select a band, and then I display the albums for that band, then user selects the ablum - and I process his request.

My current design 
select_band.php (user selects band) -> select_album.php (captures $_POST and displays albums available for the band, also little javascript confirms the selection) -> db_process_request.php (I call the album class that interacts with the database)......

---

### Post by akvino on 2009-07-17
I hate to bump my threads but any opinions on this are welcomed!

---

### Post by hessiess on 2009-07-17
Your code is trying to return a variable which would be uninitialised if the post variable is not set, try:

```

function get_value()
{
    if (!isset($_POST["bandfield"]))
    {
        return $_POST["bandfield"];
    }
    else
    {
        return NULL;
    }
} 

```

You should also use curly braces on any else if or else statements if you have used them previously, it makes the code easer to read.

---

### Post by akvino on 2009-07-17
> **hessiess said:**
> Your code is trying to return a variable which would be uninitialised if the post variable is not set, try:

```

function get_value()
{
    if (!isset($_POST["bandfield"]))
    {
        return $_POST["bandfield"];
    }
    else
    {
        return NULL;
    }
} 

```

You should also use curly braces on any else if or else statements if you have used them previously, it makes the code easer to read.

I am trying to return value in the variable even if $_POST["bandfield"] is not set. In other words, I want to store the value of $_POST["bandfield"] in the variable. Reason for this is when form one is completed and calls form two - form two will take input and process SQL call to the second page $_SERVER[PHP_SELF], based on it - then I will capture its $_POST variable and make a call to function. So I need both variables - the one selected in the first form, and the one selected in the second form.

---

### Post by tyfius on 2009-07-17
> **hessiess said:**
> Your code is trying to return a variable which would be uninitialised if the post variable is not set, try:

```

function get_value()
{
    if (!isset($_POST["bandfield"]))
    {
        return $_POST["bandfield"];
    }
    else
    {
        return NULL;
    }
} 

```

You should also use curly braces on any else if or else statements if you have used them previously, it makes the code easer to read.Shouldn't that be the other way around? Now you are checking whether the variable is not set, then returning it, and returning NULL when the variable is set.

[PHP]
function get_value()
{
    if (isset($_POST["bandfield"]))
    {
        return $_POST["bandfield"];
    }
    else
    {
        return NULL;
    }
}
[/PHP]

Or, as the OP had because I assume he wants to return the last known value:

[PHP]
function get_value()
{
    static $bandName = NULL;

    if (isset($_POST["bandfield"]))
    {
        $bandName = $_POST['bandfield'];
    }

    return $bandName;
}
[/PHP]

For the second part, you will need to use some form of AJAX. Have a look at the following example, it basically does and describes what you want: [http://www.w3schools.com/PHP/php_ajax_database.asp](http://www.w3schools.com/PHP/php_ajax_database.asp)

---

