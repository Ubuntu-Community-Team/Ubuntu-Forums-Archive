---
title: "[SOLVED] HTML file upload not working"
date: 2008-09-25
forum: Programming Talk
---

### Post by balagosa on 2008-09-25
I am going to make this short and informative.

I have two JSP pages namely view_image.jsp, and image.jsp. In view_image.jsp there is a **<input type="file" name="uploadfile" />** and a **Submit Button.** So I test the file upload by clicking on the Browse... and selecting a File, e.g. "/home/daniel/Pictures/dark_knight.jpeg". This file is printed on the textbox of the **<input type="file" name="uploadfile" />**. So I click submit which is directed to image.jsp. In image.jsp, the whole name of the file is supposed to be printed via **request.getParameter("uploadfile")**, which is **"/home/daniel/Pictures/dark_knight.jpeg"** but only **dark_knight.jpeg** is retrieved. 

Secondly to this, I have tried [w3school's File Example]("http://www.w3schools.com/TAGS/tryit.asp?filename=tryhtml_input_type_file") and I still get the same results. I edited their code, and Printed the Text Field's value in a message Box via javascript. I still get the undesired output even though the value in the text field is the **full URL**. There is also a [Note From w3schools.com]("http://www.w3schools.com/TAGS/att_input_type.asp#table30") that the**<input type="file" />** is poorly supported in all major browsers.

Thirdly, I asked my friend to try the link and we have the same problem. He Uses Windows.

[It seems that I am not alone on my dilemma.]("http://stackoverflow.com/questions/81180/how-to-get-the-file-path-from-html-input-form-in-firefox-3") This problem is due to the web browser, simply FF3. It is a new security issue they have implemented.

Can anyone help me?

Using:
a)Webserver: Tomcat5.5
b)Internet Browser: Mozilla Firefox 3.02

---

### Post by cdenley on 2008-09-25
I think most (if not all) web browser will not post the full path to the file being uploaded. I wrote a php script once that needed the path, and I ended up with what sounds like a similar solution to yours. I used javascript to change the value of a hidden input every time a new file is selected.

---

### Post by balagosa on 2008-09-25
> **cdenley said:**
> I think most (if not all) web browser will not post the full path to the file being uploaded. I wrote a php script once that needed the path, and I ended up with what sounds like a similar solution to yours. I used javascript to change the value of a hidden input every time a new file is selected.

hmm...mind showing me that script you made? The Javascript one.

What Irritates me is that **[www.friendster.com](www.friendster.com)** also uses **<input type="file">** but their File upload works well. They will even show you the size of the file, therefore I can say that they have located the file perfectly.

---

### Post by cdenley on 2008-09-25
> **balagosa said:**
> hmm...mind showing me that script you made? The Javascript one.

What Irritates me is that **[www.friendster.com](www.friendster.com)** also uses **<input type="file">** but their File upload works well. They will even show you the size of the file, therefore I can say that they have located the file perfectly.

Actually, I just looked at it, and it doesn't seem to work anymore. Maybe firefox3 works differently. I'll have to test other browsers.

---

### Post by balagosa on 2008-09-25
I have seen an alternative:

[Alternative 1]("http://www.javazoom.net/jzservlets/uploadbean/uploadbean.html"), but I do not know what to do with it. :) I have an idea of turning the indicated file to a Stream for Blob Operations.

Sorry for being a noob.

---

### Post by cdenley on 2008-09-25
I tested it, and it seems I was correct in assuming this behavior was changed in Firefox 3.0. Firefox 2.0, IE7, and Safari all worked correctly with the javascript trick, but firefox 3.0 only uses the file name as the input file's "value", not the full path.

If you figure out a workaround, let me know. This change breaks a small part of my system for FF3 users. This change makes since, because there is typically no reason for javascript to be aware of the local paths of any files. The only reason I need to know the path is to append it to a windows executable which verifies the md5 checksum of the user's original file, or give non-windows users a command to copy/paste to do the same.

[HTML]
<html><head>
<script type="text/javascript">
function GetPath() {
    var file=document.getElementById('file');
    var text=document.getElementById('text');
    var hidden=document.getElementById('hidden');
    text.value=file.value;
    hidden.value=file.value;
}
</script>
</head>
<body>
<form action="#" method="GET">
<input type="file" id="file" onChange="GetPath()" /><br/>
<input type="text" id="text" name="text" /><br/>
<input type="hidden" id="hidden" name="hidden" />
<input type="submit" />
</form>
</body></html>
[/HTML]

---

### Post by balagosa on 2008-09-26
*bump*

---

### Post by davidryder on 2008-09-26
Are you willing to use PHP to upload the file?

```
<form enctype="multipart/form-data" name="upload" action="confirm.php" method="post">
<p>
       <label>Enter file:</label><br>

       <input name="fileup" type="file"><br><br>
       
       <br>
       
       <label>Please enter description:</label><br>
       <textarea name="desc" cols="25" rows="3"></textarea>
       <br><br><br>
       
       <input value="Upload File" type="submit">
       <br><br>
</p>
</form>

```

You could use a simple form like that and the confirm.php would have the code to upload the file (using PHP). 

I could write up some simple code if you are interested.

---

### Post by Zugzwang on 2008-09-26
> **balagosa said:**
> This problem is due to the web browser, simply FF3. It is a new security issue they have implemented.


So they turned off transmitting the whole path to the server for security reasons (i.e. knowledge about your path organisation might give the attacker information that can be used). If there was a way to circumvent this, that change wouldn't strengthen security very much, wouldn't it?

So all in all I would say that you better forget the idea of getting the full path except if you used some Applet run at the client computer or such for uploading.

---

### Post by cdenley on 2008-09-26
> **davidryder said:**
> Are you willing to use PHP to upload the file?

```
<form enctype="multipart/form-data" name="upload" action="confirm.php" method="post">
<p>
       <label>Enter file:</label><br>

       <input name="fileup" type="file"><br><br>
       
       <br>
       
       <label>Please enter description:</label><br>
       <textarea name="desc" cols="25" rows="3"></textarea>
       <br><br><br>
       
       <input value="Upload File" type="submit">
       <br><br>
</p>
</form>

```

You could use a simple form like that and the confirm.php would have the code to upload the file (using PHP). 

I could write up some simple code if you are interested.

If you can write some simple php code to retrieve the full path to the original file on the ff3 user's computer, I would appreciate it. I am assuming you didn't read the thread closely enough, because I don't think this is possible.

---

### Post by cdenley on 2008-09-26
I found a different way to accomplish what I need. I still have to find a way to make it work with large files, and I'm not sure it will work on all browsers.
[HTML]<html><head>
<script src="md5.js" type="text/javascript"></script>
<script type="text/javascript">
function GetPath() {
    var file=document.getElementById('file');
    var text=document.getElementById('text');
    var hidden=document.getElementById('hidden');
    var md5=document.getElementById('md5');
    text.value=file.value;
    hidden.value=file.value;
    md5.value=hex_md5(file.files.item(0).getAsBinary());
}
</script>
</head>
<body>
<form action="#" method="GET">
<input type="file" id="file" onChange="GetPath()" /><br/>
path: <input type="text" id="text" name="text" /><br/>
md5 checksum: <input type="text" id="md5" name="md5" size="32" /><br/>
<input type="hidden" id="hidden" name="hidden" />
<input type="submit" />
</form>
</body></html>[/HTML]
[http://pajhome.org.uk/crypt/md5/](http://pajhome.org.uk/crypt/md5/)

Maybe you can accomplish what you need to with javascript read access to the local file?

---

### Post by balagosa on 2008-09-26
as for me, I have already found a solution to my problem.

[Tomcat's FileUpload]("http://www.developershome.com/wap/wapUpload/wap_upload.asp?page=jsp2").

I am still not closing this thread for cdenley's sake, he also needs help. I give him permission to hijack this thread. :popcorn:

next problem, Printing that Image. I will just hook up with you guys if I will bump into some trouble again. But just for a short intro, When to use **Output Stream**, and **InputStream**? As stated [here]("http://commons.apache.org/fileupload/apidocs/org/apache/commons/fileupload/FileItem.html"), OutputStream is supposed to be used for storing the contents of the file. But I used InputStream to store the contents. (Am I doing it wrong?)

---

### Post by cdenley on 2008-09-26
That solution isn't going to work either. The user's are usually going to be uploading large files. If I compute an md5 hash for the file with javascript, it would have to be a buffered read. It seems the only methods available to read a selected file load the entire file's contents into memory. This wouldn't work too well if the user is uploading a 500MB file, and has 256MB of memory.

---

### Post by balagosa on 2008-09-26
I was going to suggest storing the data in memory but I guess you beat me to it. that is bad news...

---

### Post by Reiger on 2008-09-26
Well it is sneaky, of course. But you can try setting a cookie (full_path) with the value of your full_file_path using JavaScript (onsubmit=func(); ) which gets sent to your server... And then retrieve it using the usual cookie content inspection methods... ;)

---

### Post by balagosa on 2008-09-26
> **Reiger said:**
> Well it is sneaky, of course. But you can try setting a cookie (full_path) with the value of your full_file_path using JavaScript (onsubmit=func(); ) which gets sent to your server... And then retrieve it using the usual cookie content inspection methods... ;)

What if the user/client has disabled cookies? It is funny how other people believe that you can acquire virus from cookies. (I maybe wrong with this info)

---

### Post by cdenley on 2008-09-26
> **Reiger said:**
> Well it is sneaky, of course. But you can try setting a cookie (full_path) with the value of your full_file_path using JavaScript (onsubmit=func(); ) which gets sent to your server... And then retrieve it using the usual cookie content inspection methods... ;)

How do you get the full file path from FF3 with javascript? I don't think it's possible, that is why my page is broken for FF3.

---

### Post by Reiger on 2008-09-26
FF3 *did* show the full path in the input box right? Just that it didn't sent the whole thing... Should be interesting to see what's possible with:

```

var myVar=document.getElementById('the_thing').value;

```

But if not... *shrugs*

---

### Post by cdenley on 2008-09-26
> **Reiger said:**
> FF3 *did* show the full path in the input box right? Just that it didn't sent the whole thing... Should be interesting to see what's possible with:

```

var myVar=document.getElementById('the_thing').value;

```

But if not... *shrugs*

Try reading the thread. That line was in my example. The full path is displayed, but the value is only the filename.

---

### Post by Reiger on 2008-09-26
Ok, then not...

---

### Post by balagosa on 2008-09-28
still no luck huh?

---

### Post by Zugzwang on 2008-09-28
> **balagosa said:**
> still no luck huh?

...as already mentioned: If the Firefox developers did there homework, you won't get the full path, whatever you may try (except if you used applets or such).

---

### Post by cdenley on 2008-09-28
I gave up. I don't think it's possible. I'm modifying my windows program to use a file selection dialog if the file does not exist in the current working directory, and I guess I will simply have to warn non-windows users using FF3 that they may have to add the path to the file.

---

### Post by balagosa on 2008-09-29
> **Zugzwang said:**
> ...as already mentioned: If the Firefox developers did there homework, you won't get the full path, whatever you may try (except if you used applets or such).

yep, I read about it in the FF3 forums. My problem was already solved though with the help of Tomcat's FileUpload class.

cdenley, I think that is a bad idea but you have no choice. What would be more horrible is Netscape, IE, etc would be following FF3's security feature such as the problem-at-hand. Firefox now, tomorrow who knows.

---

### Post by cdenley on 2008-09-29
> **balagosa said:**
> yep, I read about it in the FF3 forums. My problem was already solved though with the help of Tomcat's FileUpload class.

cdenley, I think that is a bad idea but you have no choice. What would be more horrible is Netscape, IE, etc would be following FF3's security feature such as the problem-at-hand. Firefox now, tomorrow who knows.

If there is no way for me to retrieve the local path, I have no choice but to require the user to specify the path to the file they uploaded after the upload is completed. Either that, or I force them to upload each file twice, then compare the two uploads. I really wish there were a buffered read for nsIDOMFile, because that would be the perfect solution.

---

### Post by cdenley on 2008-10-02
I now generate scripts like these when users finish uploading files.
```

#!/bin/sh
ALGORITHM=md5
show_msg() {
    if [ $ZENITY -eq 1 ]; then
        if [ $2 -eq 1 ]; then
            zenity --error --text "$1"
        else
            zenity --info --text "$1"
        fi
    else
        echo $1
    fi
}
get_file() {
    if [ $ZENITY -eq 1 ]; then
        zenity --info --text "Select the file \"$1\""
        UPLOAD=`zenity --file-selection`
    else
        echo Enter the path to the file \"$1\".
        echo -n path:\ 
        read UPLOAD
    fi
}
check_file() {
    UPLOAD=$1
    SCHECKSUM=$2
    while [ ! -f $UPLOAD ] && [ -n $UPLOAD ] ; do
        get_file $UPLOAD
    done;
    if [ -z $UPLOAD ]; then show_msg "The uploaded file was not found!" 1 & exit 1; fi
    CCHECKSUM=`openssl $ALGORITHM $UPLOAD|cut -d ' ' -f 2`
    if [ $SCHECKSUM = $CCHECKSUM ]; then
        show_msg "The file \"$UPLOAD\" has been verified." 0
    else
        show_msg "The uploaded copy of \"$UPLOAD\" is corrupt or incomplete!

original checksum:
$CCHECKSUM

uploaded checksum:
$SCHECKSUM" 1
    fi
}
openssl version 1>/dev/null 2>/dev/null
if [ $? -ne 0 ]; then show_msg "Unable to run openssl. This command is required." 1 & exit 1; fi
openssl list-message-digest-commands|grep $ALGORITHM>/dev/null
if [ $? -ne 0 ]; then show_msg "The algorithm \"$ALGORITHM\" is not supported by openssl." 1 & exit 1; fi
ZENITY=0
zenity --version 1>/dev/null 2>/dev/null
if [ $? = 0 ]; then ZENITY=1; fi
check_file 'test1.txt' 3e7705498e8be60520841409ebc69bc1
check_file 'test2.txt' 126a8a51b9d1bbd07fddc65819a542c3

```
On any other browser, the last two lines would be
```

check_file '/path/to/test1.txt' 3e7705498e8be60520841409ebc69bc1
check_file '/path/to/test2.txt' 126a8a51b9d1bbd07fddc65819a542c3

```
For windows users, an executable is generated which does something similar. This is necessary because of the way FF3 works, and even if they change it back, I have to assume some people will still be using an affected version of FF3.

---

