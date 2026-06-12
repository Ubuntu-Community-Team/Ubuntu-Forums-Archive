---
title: "Html form submission problem"
date: 2011-05-31
forum: Programming Talk
---

### Post by zobayer1 on 2011-05-31
I am trying to build a simple page that can post to another page (not from my server). Here is what I am doing to submit data:
[HTML]<html>

<body>

<form id="submitcode" action="process.php" method="post" enctype="multipart/form-data">
<table border="0">
<tr>
    <td>Username:</td>
    <td><input name="username" type="text" maxlength="20" id="username" /></td></tr>
<tr>
    <td>Password:</td>
    <td><input name="password" type="password" id="password" /></td>
</tr>
<tr>
    <td><br />Select Language:<br />
        <select name="language" id="language">
            <option value="62" >Text (plain text)</option>
            <option value="11" >C (gcc 4.3.2)</option>
            <option value="1" >C++ (g++ 4.0.0-8)</option>
            <option value="41" >C++ (g++ 4.3.2)</option>
            <option value="34" >C99 strict (gcc 4.3.2)</option>
            <option value="10" >Java (JavaSE 6)</option>
            <option value="2" >Pascal (gpc 20070904)</option>
            <option value="22" >Pascal (fpc 2.2.4)</option>
            <option value="4" >Python (python 2.5)</option>
            <option value="116" >Python 3 (python 3.1.2)</option>
        </select>
    </td>
    <td><br />Problem Code:<br />
        <input type="text" name="probcode" id="probcode" maxlength="8">
    </td>
</tr>
<tr>
    <td colspan="2"><br />Paste your souce code here:</td>
</tr>
<tr>
    <td colspan="3"><textarea id="srcecode" name="srcecode" rows="20" style="width: 600px; overflow: auto;" wrap="off"></textarea></td>
</tr>
<tr>
    <td colspan="2"><br />Or, Upload your source code:<br /><input id="srcefile" name="srcefile" type="file" size="32" /></td>
    <td align="right"><br /><br /><input id="submit" name="submit" type="submit" value="Submit" /></td>
</tr>
</table>
</form>

</body>

</html>[/HTML]Here, process.php is the script that processes form data before posting to the target page. I used cURL library to do this. Everything is working fine except for file upload.

What I am doing here is, sending the file according to the flow below:
from client ---> my server ---> their server
I mean, this file submits to process.php and process.php submits to another page which is not in my server.

Now, I understand that "file" type input can carry my file to my server, how can I resend to their server?

---

### Post by Petrolea on 2011-06-01
You can do it with cURL via FTP (and many other protocols). It's not hard and tutorials on this are great. I'd recommend doing it by this tutorial: [http://www.web-development-blog.com/archives/tutorial-ftp-upload-via-curl/](http://www.web-development-blog.com/archives/tutorial-ftp-upload-via-curl/)

Since you came that far already, this will not be a problem for you to implement. If something won't work, report back to us :)

---

### Post by zobayer1 on 2011-06-01
Hi Petrolea, thanks for replying, I have read the link you posted, but I don't have any actual server yet, I test everything on Apache Server set up on my localhost, (my os is Ubuntu 11.04, incase if it matters). I have no idea on how I can do ftp on my localhost :(

Meanwhile, I tried php uploading but went in vain, here is what I tried:
```
    if($_FILES["srcefile"]["error"] > 0) {
        echo "Error: " . $_FILES["srcefile"]["error"] . "<br />";
    }
    else {
        echo "Upload: " . $_FILES["srcefile"]["name"] . "<br />";
        echo "Type: " . $_FILES["srcefile"]["type"] . "<br />";
    }
    if(file_exists("upload/" . $_FILES["srcefile"]["name"])) {
        echo $_FILES["srcefile"]["name"] . " already exists. ";
    }
    else {
        if(move_uploaded_file($_FILES["srcefile"]["tmp_name"],"upload/" . $_FILES["srcefile"]["name"])) {
            echo "Stored in: " . "upload/" . $_FILES["srcefile"]["name"];
        }
        else {
            echo "Something wrong happened that I could not understand<br />";
        }
    }
```

I suspect, tmp_name tries to acces /tmp which is not permitted, am I correct? Is there any way I can choose some other temporary target? Changing something in ini file doesn't seem a good idea to me as I am not sure whether actual servers will allow me to do so. Same reason, I think changing permission on other folders may not be a good idea. What is the way out from here?

Thanks in advance.

---

### Post by zobayer1 on 2011-06-01
Seems like I was wrong, it is not about permission, then whats going wrong? However, I did this to get the work done:
```

    if(isset($_POST['submit'])===true) {
        if($_FILES["srcefile"]["error"] > 0) {
            echo "Error: " . $_FILES["srcefile"]["error"] . "<br />";
        }
        else {
            echo "Upload: " . $_FILES["srcefile"]["name"] . "<br />";
            echo "Type: " . $_FILES["srcefile"]["type"] . "<br />";
            $fp = fopen($_FILES["srcefile"]["tmp_name"], "r");
            $srcecode = fread($fp, filesize($_FILES["srcefile"]["tmp_name"]));
            fclose($fp);
        }
    }

```

That is, I manually read the file and later I write it to somewhere else. This is working :D
I am eager to know, why the previous one fails...
:popcorn:

---

### Post by Petrolea on 2011-06-01
> **zobayer1 said:**
> Seems like I was wrong, it is not about permission, then whats going wrong? However, I did this to get the work done:
```

    if(isset($_POST['submit'])===true) {
        if($_FILES["srcefile"]["error"] > 0) {
            echo "Error: " . $_FILES["srcefile"]["error"] . "<br />";
        }
        else {
            echo "Upload: " . $_FILES["srcefile"]["name"] . "<br />";
            echo "Type: " . $_FILES["srcefile"]["type"] . "<br />";
            $fp = fopen($_FILES["srcefile"]["tmp_name"], "r");
            $srcecode = fread($fp, filesize($_FILES["srcefile"]["tmp_name"]));
            fclose($fp);
        }
    }

```

That is, I manually read the file and later I write it to somewhere else. This is working :D
I am eager to know, why the previous one fails...
:popcorn:

Most likely it is because of permissions or non-existing directories. 
If it would be a permissions issue it would throw a 'Permission denied' error.

Usually it's because the directories aren't correct. You should debug your code by echoing the variables and see where it is going wrong. 
Because now you have a huge mess of $_FILES I would recommend that you save paths to 1 variable and then give them to functions (it will be way easier to track down and fix bugs in your code). 

Also make sure that your file is in the same directory as 'upload'. 

I can't test your example because the rest of the code is missing & I'm not really in a mood to do this so any more info would be great (errors, anything suspicious happening there?).

EDIT: I'm talking about your previous post.

---

### Post by zobayer1 on 2011-06-01
I am confused actually. As I can read tmp_file, so I think I have permissions to do so.
Next, yes, I have my process.php and 'upload' in the same directory. So I tried applying chmod() before using move_uploaded_file() but no luck so far...
```

    if(isset($_POST['submit'])===true) {
        if($_FILES["srcefile"]["error"] > 0) {
            echo "Error: " . $_FILES["srcefile"]["error"] . "<br />";
        }
        else {
            $name = $_FILES["srcefile"]["name"];
            $type = $_FILES["srcefile"]["type"];
            $size = $_FILES["srcefile"]["size"];
            $temp = $_FILES["srcefile"]["tmp_name"];
            /*
            $fp = fopen($temp, "r");
            $srcecode = fread($fp, filesize($temp));
            fclose($fp);
            echo "<pre>".$srcecode."</pre>";
            */
            chmod("upload", 0777);
            move_uploaded_file($temp, "upload/".$name);
            exit();
        }
    }

```Am I doing anything wrong here... :(

---

### Post by zobayer1 on 2011-06-01
YaY... finally It worked, I had to set chmod from root before using it.
```

sudo chmod 777 /var/www/test/upload

```

Then I use the above php code removing the chmod() function (it did nothing at all x-( )

Thanks for helping :)

---

### Post by Petrolea on 2011-06-02
> **zobayer1 said:**
> YaY... finally It worked, I had to set chmod from root before using it.
```

sudo chmod 777 /var/www/test/upload

```

Then I use the above php code removing the chmod() function (it did nothing at all x-( )

Thanks for helping :)

No problem, that's what we do :). If you have any more questions, make sure to ask.
Just a side note: You don't have to compare function return to TRUE. If it returns TRUE, if statement will get automatically executed (example: if(isset($_POST['something'])) is the same as if you add '== true' (or triple equals as in your code)).

---

### Post by zobayer1 on 2011-06-02
> **Petrolea said:**
> No problem, that's what we do :). If you have any more questions, make sure to ask.
Just a side note: You don't have to compare function return to TRUE. If it returns TRUE, if statement will get automatically executed (example: if(isset($_POST['something'])) is the same as if you add '== true' (or triple equals as in your code)).

Ow, I always do that in C++ but for PHP I have read somewhere that it is always good to check using triple === , so I thought it might be a good practice. Thanks for clarifying ... :)

---

### Post by Petrolea on 2011-06-02
> **zobayer1 said:**
> Ow, I always do that in C++ but for PHP I have read somewhere that it is always good to check using triple === , so I thought it might be a good practice. Thanks for clarifying ... :)

Well, it worked for me, maybe it is better but I can't find a reason why. 

Anyways, have fun in programming :)

---

