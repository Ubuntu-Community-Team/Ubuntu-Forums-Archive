---
title: "[SOLVED] help with HTML's pre tag"
date: 2008-11-22
forum: Programming Talk
---

### Post by rbprogrammer on 2008-11-22
Ok, so I have this code in a PHP script on my server:
[PHP]
$body = $_GET['body'];
if( $body == "source" )
{
    println("<html>");
    println("<head>");
    println("<title>Website Source Code</title>");
    println("</head>");
    println("<body>");
    println("<pre>");
    $file = $_SERVER["SCRIPT_NAME"];
    $break = Explode('/', $file);
    $pfile = $break[count($break) - 1]; 
    $lines = file($pfile);
    if( $lines != false )
    {
        $numbers = "";
        $codelines = "";
        foreach ($lines as $line_num => $line)
        {
            $numbers = $numbers . ($line_num+1) . " : <br/>\n";
            $codelines = $codelines . htmlspecialchars($line) . "<br/>\n";
        }
        println("<table>");
        println("  <tr>");
        println("    <td>" . $numbers . "</td>");
        println("    <td>" . $codelines . "</td>");
        println("  </tr>");
        println("</table");
    }
    println("</pre>");
    println("</body>");
    println("</html>");
    exit;
}
[/PHP]
Basically, when the variable body equals "source", I want to display the source code of that PHP script.  But, for some reason, whitespace is not being displayed in the browser.  Meaning all the code is at one level with no indentations.  Looking at the source code, there are the spaces there.  But for some reason, firefox is not showing it.  What am I doing wrong?  I though the pre tage was supposed to preserve white space and display it....

---

### Post by slavik on 2008-11-23
do you know about <? ?> ? they show where PHP code is and where it is not.

---

### Post by drubin on 2008-11-23
> **slavik said:**
> do you know about <? ?> ? they show where PHP code is and where it is not.

Simple example of that.
[PHP]<html>
        <head>
                <title<?php echo $title;?></title>
        </head>
        <body>
                <?php echo 'This is some random text;'?>
        </body>
<html>[/PHP]

This will show what is php code and what is html code. It makes your code easier to read and follow.

---

### Post by drubin on 2008-11-23
> **rbprogrammer said:**
> 
[PHP]
$body = $_GET['body'];
if( $body == "source" )
{
    println("<html>");
    println("<head>");
    println("<title>Website Source Code</title>");
    println("</head>");
    println("<body>");
 // println("<pre>"); << HERE
    $file = $_SERVER["SCRIPT_NAME"];
    $break = Explode('/', $file);
    $pfile = $break[count($break) - 1]; 
    $lines = file($pfile);
    if( $lines != false )
    {
        $numbers = "";
        $codelines = "";
        foreach ($lines as $line_num => $line)
        {
            $numbers = $numbers . ($line_num+1) . " : <br/>\n";
            $codelines = $codelines . htmlspecialchars($line) . "<br/>\n";
        }
        println("<table>");
        println("  <tr>");
        println("    <td>" . $numbers . "</td>");
        println("    <td><pre>" . $codelines . "</pre></td>");// << HERE
        println("  </tr>");
        println("</table");
    }
   // println("</pre>");<< HERE
    println("</body>");
    println("</html>");
    exit;
}
[/PHP]
Basically, when the variable body equals "source", I want to display the source code of that PHP script.  But, for some reason, whitespace is not being displayed in the browser.  Meaning all the code is at one level with no indentations.  Looking at the source code, there are the spaces there.  But for some reason, firefox is not showing it.  What am I doing wrong?  I though the pre tage was supposed to preserve white space and display it....

So I have re-looked at it. I think you have the pre in the wrong place. try move it to where I suggested. The pre tags wont exactly work when you have html code in side them.

---

### Post by rbprogrammer on 2008-11-26
Ok, that worked perfectly.  For the record, this is what I will be using:
[PHP]
$COURSE = "HIST/STS::151";
$BODY = $_GET['body'];
function println( $str )
{
    echo $str . "\n";
}
if( $BODY == "source" )
{
    println("<html>");
    println("<head>");
    println("<title>" . $COURSE . " - Website Source Code</title>");
    println("</head>");
    println("<body>");
    $file = $_SERVER["SCRIPT_NAME"];
    $break = Explode('/', $file);
    $pfile = $break[count($break) - 1]; 
    $lines = file($pfile);
    if( $lines != false )
    {
        $numbers = "";
        $codelines = "";
        foreach ($lines as $line_num => $line)
        {
            $numbers = $numbers . ($line_num+1) . ": \n";
            $codelines = $codelines . htmlspecialchars($line);
        }
        println("<table>");
        println("  <tr>");
        println("    <td><pre>" . $numbers . "</pre></td>");
        println("    <td><pre>" . $codelines . "</pre></td>");
        println("  </tr>");
        println("</table");
    }
    println("</body>");
    println("</html>");
    exit;
}
[/PHP]

Among other things, this is just the source code part that I will be using to display the source code of the php page.  Obviously there are other parts to my file.

---

