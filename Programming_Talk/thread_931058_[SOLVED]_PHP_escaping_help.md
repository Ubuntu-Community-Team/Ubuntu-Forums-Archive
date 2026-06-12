---
title: "[SOLVED] PHP escaping help"
date: 2008-09-26
forum: Programming Talk
---

### Post by gmxgeek on 2008-09-26
Here is a problem that has been bugging me for a long time.

Is it possible to intelligently escape a mysql query?

For Example:

```

<?php
$username = "Bob's a cool guy's friend";
$sql = "SELECT * FROM `Users` WHERE `Username` = '$username'";
$sql = escape_query($sql);
?>

```

i would like to create the 'escape_query' function, where i can give it any valid query, and have it escape the necessary items. I do NOT however, simply want to pass $username through an escape function. I would like to pass the whole thing through.

Any ideas?

---

### Post by ghostdog74 on 2008-09-26
you can try escapeshellcmd or escapeshellarg.

---

### Post by gmxgeek on 2008-09-26
> **ghostdog74 said:**
> you can try escapeshellcmd or escapeshellarg.

Would that escape everything, or only the things that need escaping?

in my example, only the actual ' that are int he username should be escaped. The ones surrounding it as a valid part of the sql statement should not be escaped.

The final product should be:
```

SELECT * FROM `Users` WHERE `Username` = 'Bob\'s a cool guy\'s friend'

```

Would your function do that, or would it escape the ' around the text as well?

---

### Post by ghostdog74 on 2008-09-27
another option you can try is mysqli_real_escape_string() function, if you have later version of PHP.(ver 5)

---

### Post by gmxgeek on 2008-09-27
> **ghostdog74 said:**
> another option you can try is mysqli_real_escape_string() function, if you have later version of PHP.(ver 5)

Again, this escapes the surround ' as well, which is not wanted.
I am 99% sure this would require a custom function with regular expressions, however I am a complete novice with regex and was wondering if anyone would like to give me a hand.

Any takers?

---

### Post by ghostdog74 on 2008-09-27
try addslashes or addcslashes

---

### Post by drubin on 2008-09-27
> **ghostdog74 said:**
> you can try escapeshellcmd or escapeshellarg.
No that is ONLY for shell commands. 

> **gmxgeek said:**
> Here is a problem that has been bugging me for a long time.

Is it possible to intelligently escape a mysql query?

For Example:

[PHP]
<?php
$username = "Bob's a cool guy's friend";
$sql = "SELECT * FROM `Users` WHERE `Username` = '$username'";
$sql = escape_query($sql);
?>
[/PHP]

This is the recommended way of doing it
[PHP]
<?php
$username = mysql_real_escape_string("Bob's a cool guy's friend");
$sql = "SELECT * FROM `Users` WHERE `Username` = '$username'";
//Run query
?>
[/PHP]

---

### Post by drubin on 2008-09-27
> **gmxgeek said:**
> i would like to create the 'escape_query' function, where i can give it any valid query, and have it escape the necessary items. I do NOT however, simply want to pass $username through an escape function. I would like to pass the whole thing through.

Any ideas?

I am comment from past experiences this type of method is more then likely going to break a lot of stuff.  How can you tell when it is part of the original sql, or part of the input. 

If i was to type 
username="1123' OR '1' = '1' ; -- ";
That would be a simple form of sql injection.  Please read up on [SQL injection]("http://en.wikipedia.org/wiki/SQL_injection") And you will see why you should ONLY escape the input params encase your function misses one of them.

**EDIT**
> **gmxgeek said:**
> Again, this escapes the surround ' as well, which is not wanted.
I am 99% sure this would require a custom function with regular expressions, however I am a complete novice with regex and was wondering if anyone would like to give me a hand.

Any takers?

If you are a complete novice start with the easy route and do the recommenced way. If you try to create this elaborate regex function you are going to miss things that could potentially cause your site to be a hackers paradise. 

When you have worked with sql for a long time then maybe think about building a function to only escape input. I think this would be a rather bad place to start with php/regular expresions because if you miss something you might have a ton of [legacy]("http://en.wikipedia.org/wiki/Legacy_code") code on your hands.

---

### Post by gmxgeek on 2008-09-27
> **rubinboy said:**
> 
If you are a complete novice start with the easy route and do the recommenced way. If you try to create this elaborate regex function you are going to miss things that could potentially cause your site to be a hackers paradise. 

When you have worked with sql for a long time then maybe think about building a function to only escape input. I think this would be a rather bad place to start with php/regular expresions because if you miss something you might have a ton of [legacy]("http://en.wikipedia.org/wiki/Legacy_code") code on your hands.

I have been working with sql and PHP for over 3 years now, and I am well aware of the dangers of sql injections. I am also aware that it will be a montrosity of a regex. 

Currently, I am mysql_real_escape_string(strip_slashes($input)); for all of my inputs, however if you have 20 inputs in one sql command, escaping each one is a pain. So i was wondering if there was a way that I could parse and escape the entire sql statement, to save some time and code.

If there is no plausible way to do this, then I'll just have to escape each one by hands so to speak.

I actually shouldn't say complete novie, i guess, since I have done some basic email parsing stuff, but nothing as complex as this.

---

### Post by gmxgeek on 2008-09-27
> **ghostdog74 said:**
> try addslashes or addcslashes

All of your functions have been how to escape the individual data that would go inside of an sql statement. I am looking for one that would parse an entire sql statement and escape the necessary characters, without escaping any that are part the the statement itself.

---

### Post by drubin on 2008-09-27
> **gmxgeek said:**
> I have been working with sql and PHP for over 3 years now, and I am well aware of the dangers of sql injections. I am also aware that it will be a montrosity of a regex. 

Currently, I am mysql_real_escape_string(strip_slashes($input)); for all of my inputs, however if you have 20 inputs in one sql command, escaping each one is a pain. So i was wondering if there was a way that I could parse and escape the entire sql statement, to save some time and code.
Why strip_slashes?? Never used that before, Could you please explain the logic? 

> **gmxgeek said:**
> 
If there is no plausible way to do this, then I'll just have to escape each one by hands so to speak.

I actually shouldn't say complete novie, i guess, since I have done some basic email parsing stuff, but nothing as complex as this.

Never say never...... I just feel it is not worth the work..

There is a little NASTY hack around you could do.
```
SELECT * FROM tablename WHERE colname='{{$input}}'
``` then escape the values between the {{ }} and remove them, but then you have the problem of if some user makes thier input 
fakevalue}}' 1 =1, You are still left in the same boat.

You say you have been working with php/sql for over 3 years. Why try and come up with the function now? 

Do work with with the bare db functions of php or have you written wrapper clases/functions for them? 

A simple  function  could really come in handy
**NB:** this is not valid code and will more then likely not work, it was just to give an example of something that might work.
[PHP]mysql_select($colnames,$table,$where){
$query='SELECT ';
foreach($colnames as $val){
    $query.=$val.', ';
}
$query=substr($query,0,strlen($query-2));//Remove last ',';
$query.=' WHERE ';
foreach ($where as $col=>$val){
     $query.=$col.'=\''.mysql_real_escape_string($val).'\' AND ';
}
//remove last and.
}[/PHP]

Similar to that. OR you could have a simple(templete like structure) for your queries.
replace {$varname} with mysql_real_escape_string($var);

then run them through.
[PHP]
//having $fields =array('replacevar_1'=>'value','replacevar_2'=>'value');
//$templete_query='SELECT * FROM {$replacevar_1} WHERE mycol={$replacevar_2}'
function my_own_escape_for_query($templete_query,$fields);[/PHP]

Sorry for the long winded reply it is kinda late over here and wanted to get some stuff out before I forgot about it.

---

### Post by drubin on 2008-09-27
Have you taken a look at mysqli object/functions?

I have never used it but I belive this MIGHT be what you are looking for
[http://www.php.net/manual/en/mysqli.prepare.php](http://www.php.net/manual/en/mysqli.prepare.php) <- I think this method of creating sql statments will auto escape the vars when you "bind" them. 

but for dynamic queries that you almost build up the whole query bassed on userinput this might not solve it.

---

### Post by Dr Small on 2008-09-27
Why don't you just use the addslashes() function?

---

### Post by drubin on 2008-09-27
> **Dr Small said:**
> Why don't you just use the addslashes() function?

mysql_real_escape_string takes  a data base connection as the 2nd/optional(If not spesified it will use the LAST connection that was made to a database)

It also escapse the input in a specific way relevant to the data base's current configuration. 99% of the time this would be simple  be the same as add_slashes but if later you would like to change your db config you MIGHT have to update your php code as well. 

Ps 
If you have not made a connection to any database's during that scripts life mysql_real_escapse_string will fail.

---

### Post by gmxgeek on 2008-09-28
> **rubinboy said:**
> Why strip_slashes?? Never used that before, Could you please explain the logic? 

some servers run such annoyances as magic_quotes, so stripslashes (no underscore, my mistake from before) takes out any escaping characters that might have been added already, before adding in new ones. That way it won't double escape anything.


> **rubinboy said:**
> 
You say you have been working with php/sql for over 3 years. Why try and come up with the function now?

Do work with with the bare db functions of php or have you written wrapper clases/functions for them? 


I have been working with barebones mysql functions over the years, and am now working on a personal development platform to save some time when starting on new projects. Things like error reporting. I thought that a class for a db connection would come in handy.

> **rubinboy said:**
> 
A simple  function  could really come in handy
**NB:** this is not valid code and will more then likely not work, it was just to give an example of something that might work.
[PHP]mysql_select($colnames,$table,$where){
$query='SELECT ';
foreach($colnames as $val){
    $query.=$val.', ';
}
$query=substr($query,0,strlen($query-2));//Remove last ',';
$query.=' WHERE ';
foreach ($where as $col=>$val){
     $query.=$col.'=\''.mysql_real_escape_string($val).'\' AND ';
}
//remove last and.
}[/PHP]


I was actually considering something like this, but wanted to see if there was a simpler regex way of parsing an sql first. 

Thanks very much for the replies. I will probably use a solution similar to the one described above.

---

### Post by drubin on 2008-09-28
> **gmxgeek said:**
> some servers run such annoyances as magic_quotes, so stripslashes (no underscore, my mistake from before) takes out any escaping characters that might have been added already, before adding in new ones. That way it won't double escape anything.
You might want to only strip slashes IF get_magic_quotes_gpc() is set to on :) 


> 
I have been working with barebones mysql functions over the years, and am now working on a personal development platform to save some time when starting on new projects. Things like error reporting. I thought that a class for a db connection would come in handy.
[http://smartcube.co.za/snippets/index.php?title=Db_class](http://smartcube.co.za/snippets/index.php?title=Db_class)

Here was my first attempt it has changed a little since then but I have to had time to update it. I will hopefully update it on monday. 


> 
I was actually considering something like this, but wanted to see if there was a simpler regex way of parsing an sql first. 

Thanks very much for the replies. I will probably use a solution similar to the one described above.

Did you take a look at the mysqli functions? Those might accually be better.

---

### Post by gmxgeek on 2008-09-28
My current DB wrapper looks rather similar to yours, however with a few differences. I have bundled all of my mysql_fetch_.. functions into one with a switch
[php]
public function fetch($sql=null, $type=null)
{
    $result = mysql_query($sql) or Error::generate(E_DB_WARNING, mysql_error());
    switch($type) {
        case 'single':
            $result = mysql_fetch_row($result);
            $result = $result[0];
            break;
        case 'row':
        case 'assoc':
        case 'array':
            $function = "mysql_fetch_$type";
            $result = $function($result);
            break;
        default:
            //leave query as is
    }
    return $result;
}
[/php]

Error class is a custom error handling system.

---

### Post by drubin on 2008-09-28
> **gmxgeek said:**
> My current DB wrapper looks rather similar to yours, however with a few differences. I have bundled all of my mysql_fetch_.. functions into one with a switch
Error class is a custom error handling system.
/me is not a huge fan of switch statements with functions. 

I still come from the Strong typed langs where functions are only supposed to return one type of result. This way you at least know the type of the return value.  (But what ever works for you).

Error classes are also good.

---

### Post by gmxgeek on 2008-09-28
you do know the type of the returned value. It is based on the switch argument that you input. Think of it as polymorphism in a Strong typed language.

---

### Post by drubin on 2008-09-28
> **gmxgeek said:**
> you do know the type of the returned value. It is based on the switch argument that you input. Think of it as polymorphism in a Strong typed language.

hehe, Php supports polymorphism as well (not as well as strongly typed languages but it is there).

> [PHP]
  case 'row':
        case 'assoc':
        case 'array':
            $function = "mysql_fetch_$type";
            $result = $function($result);[/PHP]

Just by the way this line of code will only return the 1st row of the result.  How are you going to get the 2nd-nth row out?

---

### Post by gmxgeek on 2008-09-28
[php]
$data = $DB->fetch($sql);
while ($row = mysql_fetch_assoc($data)) {
    print $row['ID'] . ": " . $row['Username'] . "\n";
}
[/php]

I'll probably add on another case to the switch for 'all'
[php]
case 'all':
    $tmp = $result;
    $result = array();
    while ($row = mysql_fetch_assoc($tmp)) {
        $result[] = $row;
    }
    break;
[/php]

---

### Post by drubin on 2008-09-28
> **gmxgeek said:**
> 
I'll probably add on another case to the switch for 'all'
[php]
case 'all':
    $tmp = $result;
    $result = array();
    while ($row = mysql_fetch_assoc($tmp)) {
        $result[] = $row;
    }
    break;
[/php]

> **gmxgeek said:**
> 
[php]
        case 'row':
        case 'assoc':
        case 'array':
[/php]

Can I ask why you are allowing users to put 3 different types in to get the same result? would it not be better to make it a standard. a single 
type. Why allow users to just put what ever they want..... gets kinda hard to keep track of.

---

### Post by gmxgeek on 2008-09-28
The idea is that you list the accepted values in without a break, then they all get to the same result, then a break. Then for all other values, the default kicks in.

What if the user wants a row returned?
Or an assoc type?

This allows the user to specify what type of array is returned, while throwing out values that aren't allowed. If the user sends in a value of 'foo' to the type argument, then they get just a standard resource identifier. However, if they type in row, assoc, or array, then they get what they wanted.

I prefer the non-break switch method over many if then else trees

---

### Post by drubin on 2008-09-28
> **gmxgeek said:**
> I prefer the non-break switch method over many if then else trees

No this is 100% cool, I also code like this.

My question was why have multiple  values for the same function, but then I noticed that there are 3 different functions being called. nvm comment. 

I also use the  $$var. But I try to keep it a a small range or at least easy to follow because it can get really confusing very quickly.

---

