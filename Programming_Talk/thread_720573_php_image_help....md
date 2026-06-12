---
title: "php image help..."
date: 2008-03-10
forum: Programming Talk
---

### Post by hockey97 on 2008-03-10
HI  me and another guy are having trouble with grabbing images from a mysql database,  I mean multiple we can do only one, we can't figure out how to display many images from one user.


ok well I have made the upload script which it uploads the image to a folder and then I grab the url of that image and save it in mysql, I also grab the user name to be saved in the database.

so I limit the user 12 pics max.  


What I want to do is to display each image that users has on my server onto a html table.

I have used mysql fetched.

but nothing is happing.

Can someone give me an example or explain to me methods you would use the diplay more than one, I even tried out the foreach loop ect but failed.

---

### Post by mike_g on 2008-03-10
> HI me and another guy are having trouble with grabbing images from a mysql database, I mean multiple we can do only one, we can't figure out how to display many images from one user.
You might want to look at using a relational database, that way it would be able to deal with each user having a variable amount of pictures, or other elements on their page.

Or, an alternative would be to put each image link together in a string seperated by a delimeter, then split the string when you get it from the database.

---

### Post by mssever on 2008-03-10
It's hard to help you without seeing some code.

---

### Post by hockey97 on 2008-03-11
Deleted!!! 

CLosed!!!

---

### Post by Zugzwang on 2008-03-11
The normal way of doing so is to use a SELECT statement in SQL:
```

SELECT image from Images where user="<yourusername>";

```
And then generate a table with all you the links you got.

Note that that code appears to be vulnerable to SQL-injection since "$_SESSION["username"]" is used without the necessary encoding.

---

### Post by mssever on 2008-03-11
A couple comments about your code: First, it's very difficult to read, because it's incorrectly indented. Every time you type a {, indent the next line and all following lines. Just before typing }, dedent. For example: [php]if(foo) {
    statement_1();
    $do_something = 6;
    if($here_is_another_block) {
        //I'm indenting even more
    }
}[/php]
Maybe you should hit the pause button on PHP and learn Python; Python will force you to indent correctly. Why is indentation so important? Because sometime someone (maybe even you) will have to look at that code after you've forgotton exactly how it works. Unindented code is disorienting. Wrongly indented code--as in the example you posted--is actively deceptive. Before I can figure out what your code is doing, I have to completely read it and parse it, because the visual clues are wrong.

Second, always assume that any data coming from the user (e.g., $_GET, $_POST, $_COOKIE, $_SESSION, etc.) is potentially malicious. Program as if you know that a team of talented crackers will be trying to exploit your site to incite World War III. That means that you need to always validate all input in some way. Part of that is to use mysql_real_escape_string() on every such variable that you include in a MySQL query. If that's too much typing, make a shortcut: [php]function esc($str) {
    return mysql_real_escape_string($str);
}[/php]

As to your main question, Zugzwang answered it. But don't overlook the things I've pointed out. They're basic to all programming.

---

### Post by hockey97 on 2008-03-12
Closed!!!!

---

### Post by mssever on 2008-03-12
> **hockey97 said:**
> 
this is what I have so far on the script this was what the one guy suggested from another fourm.
You still need to indent your code properly, so that people can understand it.
[php]<?php 
session_start();
$_SESSION['firsttimeupload']= "ok";
require_once("/home/linuxuser/WebPages/mydomain.com/DbConnector.php");
$db = new DbConnector();
$db->connect();
$query = "SELECT image FROM Images WHERE username='$username'";
$result = $db->query($query);
$rows = $db->fetchArray($result);
$nrow = mysql_num_rows($result);  
while ($row = $db->fetchArray($result))
{
    $A=$row['image'];
}
?>[/php]
Note that $A will get overwritten every iteration through the while loop. If you do [php]$a = array();
if($nrow >= 1) { //You aren't doing anything with $nrow in your code
    while($row - $db->fetchArray($result)) {
        $a[] = $row['image'];
    }
}[/php] you'll have an array of all the images. Variables with names beginning with a capital letter are, in most languages, constants or environment variables. (By convention, if not by syntax rules.) So you should use $a, not $A. Even better, use a meaningful name for your variable, such as $images.

To make a table, simply loop through your images array.

---

### Post by hockey97 on 2008-03-12
ok thanks for all the replies so far, I used that array techeak and I was not able to display the image. 


What do you mean by You aren't doing anything with $nrow in your code???

are you just explaining me about the if statement ??  or are you saying that $nrow  
isn't doing anthing in the script at all??

---

### Post by mssever on 2008-03-13
> **hockey97 said:**
> ok thanks for all the replies so far, I used that array techeak and I was not able to display the image. 
Techeak? I don't understand what you're saying. It is frequently helpful to dump the contents of a variable so you can see what its value is. That keeps you from just taking stabs in the dark. The print_r function is ideal for this, but I prefer to use the following wrapper to make more readable output:
[php]function dump($var, $tag=false) {
    echo "<pre>";
    // If an optional tag is specified, print it before the
    // variable. Tags can be anything that can be
    // converted to a string, such as the name of the
    // variable or the line number (__LINE__).
    if($tag !== false) {
        echo "<b>$tag</b>:\n";
    }
    echo htmlspecialchars(print_r($var, true));
    echo "</pre>";
}[/php]Then, to see the value of any variable at any point in your code, write dump($that_variable), specifying an optional tag to help you locate what's producing that output. If you dump the array at various points in its life, you'll likely experience enlightenment. :)

> What do you mean by You aren't doing anything with $nrow in your code???

are you just explaining me about the if statement ??  or are you saying that $nrow  
isn't doing anthing in the script at all??As you had it written, you assigned the number of rows returned to $nrow, but you didn't do anything with that information. I incorporated it into the test in my code because it's important info. You have quite a bit more unused code in an earlier post: [php]$_SESSION['firsttimeupload']; // Since you aren't assigning this variable
                              // to anything, you might as well remove it.
$n=$_FILES['user_file']['name']; // Here you set $n (see four lines below)
$type=$_FILES['user_file']['type']; // You aren't doing anything with this.
$size=$_FILES['user_file']['size']; // ditto
$time=time();
$n=$time; // Here you change $n before doing anything with the old value.[/php]

---

### Post by hockey97 on 2008-03-13
thanks for your guys help so far.  I have been checking ech line of code to see what it's getting.

everything to me seems good but I am not user about the $a .

The $a  gets array1 assigned to it after those while loops, should I be getting that for $a? 

or should I be getting the url content from the database?

---

### Post by mssever on 2008-03-13
$a should be an array of URLs from the database. Since you've got more than one picture per user, using a normal variable would only give you the last picture, since every time you step through the database result, you overwrite the previous value.  If you use an array, ou can store all the URLs you want.

---

### Post by hockey97 on 2008-03-13
ok well I used echo and also print and also the stuff (print_r)you suggested and what I get on the screen is  array1    that's what I get, no image just a test saying array1.

I am going to do another check all over. 

So I right now just got to find out why $a isn't getting the urls it's just getting array1   which I echo $a and that spit out text (array1) on the page.

Thanks for the help.

---

### Post by hockey97 on 2008-03-13
ok I got the $a to get the url .

now another problem the script works but apache is giving errors of 404 would that mean it's a permission issu??

---

### Post by mssever on 2008-03-13
> **hockey97 said:**
> ok I got the $a to get the url .

now another problem the script works but apache is giving errors of 404 would that mean it's a permission issu??

404 Not Found means that the file wasn't found. The paths are probably wrong. Check that a) the URL is correct and b) the image actually exists at that location. 

Permissions issues produce 403 Forbidden errors. (Other things can also cause 403 errors, as well.)

---

### Post by hockey97 on 2008-03-14
Ok I found out the problem my apache2 server didn't have the a image pinted there.

but now it acts as a binary file, I think I should store also the file type in the database right?

---

### Post by mssever on 2008-03-14
> **hockey97 said:**
> Ok I found out the problem my apache2 server didn't have the a image pinted there.

but now it acts as a binary file, I think I should store also the file type in the database right?

I don't understand you. If you're storing the image as a file, then all you need in the database is a URL, because Apache will automatically send the correct content-type header (provided you use the correct extension on your filename).

If you're storing the image itself in the database, then yes, you need the filetype. You also need it in one of the blob type columns. And you need a script to output the image and set the proper headers.

---

### Post by hockey97 on 2008-03-14
Closed!

---

### Post by mssever on 2008-03-14
> **hockey97 said:**
> The problem is that I get Array1 from $a not the url in the database.

at the end I print/echo out what was in $a and I got Array1.

Please, indent your code properly!

Are you echoing $a? As I said in post 10 above, the proper function is print_r (or the dump function I gave you). PHP isn't smart enough to echo arrays.

---

### Post by hockey97 on 2008-03-14
yes I done that and I got this printed in the screen:  
Array
(
)

that's what I got .

---

### Post by mssever on 2008-03-14
> **hockey97 said:**
> yes I done that and I got this printed in the screen:  
Array
(
)

that's what I got .

Have you checked that your query actually returned anything? You've got an empty array, which suggests that $nrow is probably 0.

You might want to echo/dump mysql_error(). You probably have a syntax error in your query (such as a missing semicolon).

---

### Post by hockey97 on 2008-03-15
Closed!!!

---

### Post by mssever on 2008-03-15
> **hockey97 said:**
> when I check the query with echo and the other ones the dump function I get this:
SELECT image FROM Images WHERE username=''1 

That's what gets printed on the screen.

I assume that you can see the syntax errors in your query. 
[LIST]
[*]username=''1 is invalid. The value belongs inside the quotes.
[*]You're missing a semicolon at the end of the query.[/LIST]

---

### Post by hockey97 on 2008-03-15
Closed!!!

---

### Post by hockey97 on 2008-03-15
Closed!!!!

---

### Post by mssever on 2008-03-15
> **hockey97 said:**
> no there is a semicolon ; at the end.

this is the query I have : [php]$query = "SELECT image FROM Images WHERE username='$user'"; [/php]
Actually, there isn't a semicolon at the end of the *query*. Yes, there's one at the end of the line, but that doesn't help your query any. Try something like [php]$query = "SELECT image FROM Images WHERE username = '".mysql_real_escape_string($user)."';";[/php]> When I use my test user and login and still echo and do what you asked dump ect I get  (SELECT image FROM Images WHERE username=hockey97'1)   I get that printedThere's some information missing here. The result you just gave isn't possible, given the query you gave earlier in your post. What happened to the other single quote? Where did the 1 come from? What code aren't you showing me?

I've given you a number of debugging tips, such as print_r and mysql_error(), and explained code indentation. You don't seem to have availed yourself of my help. Your code still isn't indented properly, and you're reporting results that aren't possible. print_r never prints [FONT=Courier New]Array1[/FONT]. Your SQL has problems, but if you've checked mysql_error(), you haven't mentioned it. mysql_error() will give you some indication of the problem.

If you're going to succeed in programming, you have to be able to debug your code. I can give you some tools, but it's up to you to use them. In another thread, I questioned whether you have what it takes to become a programmer. If you can't use debugging tools, then you don't have what it takes. If you've just been mindlessly taking what I've posted and using it without understanding it, you need to take a step back and figure out or ask what something does. If I were to debug your code for you, I'd be doing you a disservice, because you wouldn't learn to debug.

---

### Post by hockey97 on 2008-03-15
Closed!!!!

---

### Post by mssever on 2008-03-15
OK, so now you know where the problem is. Apply the tools you have, and see if you can fix it.

---

### Post by hockey97 on 2008-03-16
I  got that problem fixed now I know the $a is now getting all the urls needed.

now  I been playing around in the html area to try getting the thing to show up.

so html  part I have  [html]<img src="<?php $a;?>">[/html] 

however I still get the borken image icon. I see no pictures.

did I do the html thing right?

---

### Post by mssever on 2008-03-16
Another debugging tool is your browser's view source command. If you look at the source there, you'll see why you're getting a broken image icon.

---

### Post by pacofvf on 2008-03-16
an fancy way to show anything in the html code is:
example:
```
<a src="<?=$link?>">
```
and about your problem :
check this things
1.- the image is in its place
2.- check if the correct path is stored in mysql
select * from Images;
(the * means everything)
3.- when you do the query in php just do this, to see what a variable contain:
```
echo $array;
```
(yes!!! you can print an array.)
if the correct path is in your query then you will see an image on your website.
:)

---

### Post by hockey97 on 2008-03-16
Closed!!!

---

### Post by mssever on 2008-03-16
Well, think this through. What is an array? How would you then get the necessary info from it?

This is obvious. If you don't know this already, and can't figure it out on your own (or with the help of the PHP manual), then you shouldn't be programming.

I'm not trying to be rude, but you need to think about your problems a little before asking for help. Try this: Before asking, search the PHP manual. And Google. Also, read this: [http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html)

---

### Post by CptPicard on 2008-03-16
I think this is an excellent real life exmple of this... [http://en.wikipedia.org/wiki/Cargo_cult_programming](http://en.wikipedia.org/wiki/Cargo_cult_programming)... or maybe more accurately, [http://en.wikipedia.org/wiki/Voodoo_programming](http://en.wikipedia.org/wiki/Voodoo_programming)

---

### Post by mssever on 2008-03-16
@CptPicard:

Congrats on the new avatar. The old one was disturbing...

---

### Post by LaRoza on 2008-03-16
> **mssever said:**
> @CptPicard:

Congrats on the new avatar. The old one was disturbing...

[http://ubuntuforums.org/showthread.php?t=725662&page=2](http://ubuntuforums.org/showthread.php?t=725662&page=2)

---

### Post by hockey97 on 2008-03-18
Closed!!!

---

### Post by mssever on 2008-03-18
> **hockey97 said:**
> my question is  what is the max you can assing to  a variable?
You can assign anything to a variable.

As to the rest of your post, I can't answer it because you couldn't be bothered to give correct information. You gave your code twice, but both times were different (and incorrect). How can I know what your code really looks like? Also, remember that I'm finished debugging your code for you. I'm willing to help you learn the tools, but you need to debug your code yourself. If you use your debugging tools, you should be able to determine what your problem is.

---

### Post by hockey97 on 2008-03-18
Closed!!!!

---

### Post by mssever on 2008-03-18
> **hockey97 said:**
> I have the code of the variables like this $path=$path.$filename.$format;

Well, now you at least gave some more concrete info (remember, no one can read your mind).

So, your variables aren't returning what you expect them to return. How do you debug that? Use your tools.

Currently, my ignore list is empty. I'm considering adding you to it, though, unless you start thinking your problems through. How many times have I suggested that you use your tools to solve a problem? And apparently, you eventually manage to do so. Yet you keep asking questions that you could answer yourself without asking other people to waste their time, if you only tried before asking.

I'm willing to help with genuine problems, but few of yours have been in that category. Note also that I've been the only one here trying to help you. If I add you to my ignore list...

> the reason I asked about the variables if there is a max becuse I notics mysql I can adjust the size of the field.

MySQL != PHP. Fields in MySQL have a maximum length. If you had read the PHP manual, you would have known that your limits in PHP are memory and time, not data length.

---

### Post by hockey97 on 2008-03-18
Closed!!!!

---

### Post by CptPicard on 2008-03-18
> **hockey97 said:**
> 
according to many websites that gives examples...

That is the problem with you.

You copy examples, without understanding what is going on, and not even making a fair attempt at "getting it".

Certainly, blind copying and "bind-eval" is one strategy. I made use of that at uni when I was totally short on time and just had to pass the class... sometimes it worked, sometimes it didn't. The more competent I became, the better the strategy worked (after all, in pure-functional languages, it works all the way).

But alas, for you, it's not The Way To Do It. You really need to go back all the way, for as many times as it takes... really.

---

### Post by mssever on 2008-03-19
> **hockey97 said:**
> To me looks like you were trying to help me at first then you turn 360 and then started fighting against me.
Contrary to how it may seem, I haven't been fighting against you. I'd love for you to succeed, and that's why I "turned 360." Initially, I did my best to help debug your code for you. But after a while, it became evident that you weren't learning from my help; you were merely using it to solve a particular problem. There's a difference. As I see it, learning how to write better programs is more important than the particular program at hand.

So since you weren't learning from my help, I decided that I needed to change my approach. I decided to stop debugging your code for you to push you toward applying the tools you have. Why did I do this? As I've said before, your success as a programmer depends on your ability to solve these kinds of problems. And I thought you need a bit of a kick in the pants to move you in that direction.

When that didn't work, I decided to provide more incentive for you to start thinking about your problems and applying the tools. That's when I threatened to ignore you. Now, I didn't have to threaten anything; I could have simply done it. But I hoped to get your attention. I still stand by my threat, but if this discussion proves fruitful, then that's awesome. I want you to succeed, but by simply debugging your code for you as I did at first, I believe I was actually hurting you and robbing you of a valuable learning experience.

You might disagree with me, but I'm writing as someone who has more experience than you do. I know what I'm talking about.

> $path=$filepath . $filename . $format;To illustrate what I've been saying about using your tools, I'll provide a hint about this problem. This expression isn't providing the results you expect. If you were using your debugging tools, you would examine the contents of $filename and $format (and maybe $filepath, if necessary). You would find that one or more of them contains incorrect data. So, you would trace that variable back to where it gets set and find out where the data went bad. Then you would examine the code and find out what the problem was.

If you really pondered this problem, and the method above (or some approximation) never occurred to you, then you're in way over your head. In such a case, you need to step back, and start over with learning programming, making sure that you understand everything before going on. If you don't understand something, ask, but show to whoever reads your question that you've done your homework. If I didn't explain how to use the debugging tools I recommended well enough, ask me for further clarification. But you need to provide evidence that you're actually thinking about things and trying to understand them, rather than simply copying and pasting.

Finally, if you have already used a method similar to what I outlined, great. Sometimes the most difficult problems are the ones that should be the most obvious, and having an extra pair of eyes helps a lot. But in this case, you need to provide evidence of what you've tried.
>  what is your definition of genuine problems??For example, you could say something like, "When I try to set the filename (on line such and such), I'm getting such an such a result, instead of thus and so, which I expect. I've discovered that $foo is the problem, as its value at this point is bar, instead of baz. I traced it back to line some_line, but I can't figure out how it's getting set incorrectly. What am I missing?"

Then, be sure to include ALL the relevant code (but still the minimum possible), PROPERLY INDENTED. (Note also that you should use clear, correct English. I don't know whether English is your native language, but regardless, you need to make an effort to write clearly and accurately. Given how often you've altered details, I don't think that you pay sufficient attention to accuracy.)

Such a question would appear a whole lot more like a genuine problem, and less like someone who's just looking for a copy-and-paste answer. (If you're observant, you'll notice that what I've just said is very similar to ESR's article I gave you a link to earlier (post 33) about how to ask questions the smart way. I hope you read it.)

Wow. This is quite a long post. I hope that I haven't been wasting my time by writing it. I hope that you actually learn something from it.

---

