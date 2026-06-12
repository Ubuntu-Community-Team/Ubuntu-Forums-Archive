---
title: "PHP: How do I put a variable into an include argument?"
date: 2007-05-18
forum: Programming Talk
---

### Post by dccmyst on 2007-05-18
Its quite simple, I would like to include a variable within an include argument.
like so:

[HTML]<?php include('forum/viewTopic.php?id='$id);?>[/HTML]

Of course this doesn't work, I've tried playing around with quotes to no avail.
Does anyone know the correct syntax

Kind Regards
David

---

### Post by FuriousLettuce on 2007-05-18
It's been a while since I did PHP properly, but in general the correct syntax for concatenation (connecting two strings together) is
```
$myvar = 'random';
echo 'MyVar = '.$myvar; // prints "MyVar = random"
```
You can also use this to insert a variable inside a block of text:
```
echo 'My name is '. $name .' and I am a Ubuntu user.';
```
Thus, your code would be
```
include ('forum/viewTopic.php?id='.$id);
```
Shout me if there's any problems, although it ought to work fine.

---

### Post by dodgePT on 2007-05-18
Make a print/echo of the variable and check if the value is being passed, maybe that's your problem.
Something like this: echo "$id";
Or a condition:
if ($id = "")
{
return an error message...
}

How are you passing the variable anyway?

---

### Post by bunker on 2007-05-18
You do not need to append a query string to an included file unless you are using an include wrapper (like including from a remote location via http).  Simply:

```
<?php
$id = "whatever";
include('thefile.php');
?>
```

However, judging by what you posted, what you really want to do is display the page at form/viewtopic.php?id=whatever.  In this case you should use a http redirect - the script probably won't work anyway if you include it since you are executing it from a directory that it is not expecting to be in.

```
<?php header("location: http://yourdomain/form/viewtopic.php?id=whatever"); ?>
```

I would advise you to read the PHP docs on header() redirecting, because I vaguely remember there being some issues with certain browsers and versions not interpreting the redirect correctly.

---

### Post by dccmyst on 2007-05-19
Thank you for all the replies, I think I know what's going wrong. 

The value is definitely being passed.

I corrected the syntax as suggested by FuriousLettuce and got the following error:

[HTML]
Warning: include(D:\www\index.php?id=3) [function.include]: failed to open stream: Invalid argument in D:\www\index.php on line 69

Warning: include() [function.include]: Failed opening 'D:\www\index.php?id=3' for inclusion (include_path='.;C:\php5\pear') in D:\www\index.php on line 69[/HTML]

as bunker said, I think I need to use header() somehow, although I have tried, but get the error:

header has already been sent.

You see I'm trying to get the topic link in http//www.minnesotatwins.co.uk/forum to open **within** the content window. Which I do by using switch like so:

[HTML]case 'createTopic':
				include('forum/createTopic.php');
			break;
			case 'addTopic':
				include('forum/addTopic.php');
			break;
			case 'viewTopic':
				include('D:\www\index.php?id='.$id);  
			break;
			case 'addAnswer':
				include('forum/addAnswer.php');
			break;[/HTML]

This works fine, as long as an or a value has to be posted, like so index?location=forum?&id=1.

Anyone have any suggestions?

Kind Regards
David

---

### Post by winch on 2007-05-19
Read the php docs on the [include]("http://php.net/include") command.

> When a file is included, the code it contains inherits the variable scope of the line on which the include occurs. Any variables available at that line in the calling file will be available within the called file, from that point forward.

The included file doesn't need to be passed $id it can just use it.

```

case 'viewTopic':
    include('forum/viewtopic.php');
break;

```

Then viewtopic.php could be something like this.
```

$result = mysql_query("SELECT * FROM posts WHERE id='$id'");
if ($result)
{
    //loop over rows and display posts
}

```

---

### Post by bunker on 2007-05-19
[HTML]
Warning: include(D:\www\index.php?id=3) [function.include]: failed to open stream: Invalid argument in D:\www\index.php on line 69

Warning: include() [function.include]: Failed opening 'D:\www\index.php?id=3' for inclusion (include_path='.;C:\php5\pear') in D:\www\index.php on line 69[/HTML]

Include simply means 'get some code and put it in this document'.  Therefore, when you try to open 'index.php?id=3', it'll look for a file called 'index.php?id=3'.  This of course does not exist ;).

To clarify, suppose I have two files, a.php and b.php.

b.php:
```
<?php echo "I am b.php\n";?>
```

a.php:
```
<?php echo "I am a.php\n";
include('b.php');?>
```

Output of running a.php:
```
I am a.php
I am b.php
```

As I said before, I'm not sure this is the effect you were aiming for.

--

The error you're getting on header() means that you've printed some characters already.  Normally php does not buffer the page before sending it.  Obviously you need to send headers before any content so make sure there is no stray html or any echo statements before you call header().  You can get around this by using ob_start() (turns on output buffering), but it's better to avoid printing stuff if you're not ever going to display it.  Check for newlines at the start and end of your php files - this counts as outputted data.

---

### Post by qix on 2007-05-20
As said, your file does not exist where you said it should. If it really IS placed in D:\www\blabla, then maybe try reverting your \ to / and see if it works. Eg.
include("D:/www/viewtopic.php");

---

### Post by dccmyst on 2007-05-20
Finally got the topic to load within the content table. All I did was remove the $_GET(id) from viewTopic.As you said all previous variables will be visible within the included page.

Thank you loads.

While I'm on a roll, how might I get paragraphing to work in my forum, [www.minnesotatwins.co.uk](www.minnesotatwins.co.uk). For some reason, each topic is displayed as one long string?

Kind Regards
David

---

### Post by qix on 2007-05-20
Use nl2br() on the variable containing the post. It should convert lineshifts to <br> elements.

---

