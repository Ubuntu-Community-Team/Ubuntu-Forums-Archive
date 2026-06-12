---
title: "HTML help passing variable value to a script."
date: 2009-12-28
forum: Programming Talk
---

### Post by hasan1 on 2009-12-28
I want to make a  web page that has a text box with a send button.

How should the html line be edited to ***send the text to the script as a variable 'a'*** and then store it in a variable in the script located at /usr/lib/cgi-bin?

_HTML_

<textarea name="comments" cols="50" rows="6">
Enter text here...
</textarea><br>
<input type="submit" value="send" >
**<form action="/usr/lib/cgi-bin/s1.sh" method="post">**    
</form>

 To execute s2 what changes should be made to the following code/tag.
s2 will print the first line to the screen.

**action="/usr/lib/cgi-bin/s2.sh" method="post"**
[B]

*_Scripts_*:

s1)[/B]. After entering text and  clicking the send button  the web page should send the text lines as a variable i.e '**a**' to a script s1 which would store the text to a file.


     #!/bin/sh
     a                                //for this I think a has to be declared in html tag.  
     $a>/home/../f1



**s2)** The script s2 will take the first line from the file f1 , display it on screen.

    a=`head -n 1 f1`
    echo $a

---

### Post by hasan1 on 2009-12-30
Or execute s1 while the user is typing by the code
'read a' but thats not what I want and  even that doesnt work.something might be wrong with the html tag.

Btw here is what happens after I type text and press the enter code
[IMG]http://ubuntuforums.org/%3Ca%20href=http://img109.imageshack.us/i/screenshotui.png/%20target=_blank%3E[IMG]http://img109.imageshack.us/img109/7418/screenshotui.th.png[/IMG]
[[IMG]http://img109.imageshack.us/img109/7418/screenshotui.th.png[/IMG]]("http://img109.imageshack.us/i/screenshotui.png/")

It simply opens the form_reader script(the s1 script with a changed name)  and  there isn't  anything written to tf as well.
 this is with the following edited html code/tag.


<html>
    <head><title>Title</title></head>
    <body>
        <form action="/usr/lib/cgi-bin/form_reader" method="post">
            Enter data:<input type="text" name="data"><br>
            <input type="submit">
        </form>
    </body>
</html>

---

