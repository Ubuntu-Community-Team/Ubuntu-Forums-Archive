---
title: "AJAX Variable Problems"
date: 2007-05-10
forum: Programming Talk
---

### Post by JNowka on 2007-05-10
I have tried figuring out what my problem with some variables could possibly be.  I have yet to figure it out.  Perhaps someone here could point me in the right direction.

I have the following AJAX code in a web based IM I am creating for a Web Development class I am taking.  I have asked my teacher who is currently just as unsure as me, more so because I have been studying a little bit of AJAX on my own, where he has never used it before.

So here is the problem code:

```

            if("chatclear" != ajaxRequest.responseText) {
                alert("Error! Please contact site admin!");
            }

```

This to me seems simple.  If ajaxRequest.responseText is not equal to chatclear throw up an alert box.

Here is the php code associated with the value returned for the ajaxRequest itself.

```

if($row[0] != "") {
    echo $row[0];
}
else {
    echo "chatclear";
}

```

I am making sure that it is sending chatclear by using a text field and changing the value in it using the following code:

```

document.getElementById("ctxt").value = ajaxRequest.responseText;

```

because it makes the text fields value read "chatclear" I know that the value is correct.

So to make a long story short it is showing the alert box, stating that the value isn't equal to "chatclear", then makes the text field read "chatclear".  Any one have a suggestion of what can be done.  I am currently debating using a hidden field, but I like keeping my code a bit less repetitive that this.  Thank you in advance for any help forthcoming.

---

### Post by chris1974 on 2007-05-11
Hmmm, it's a stumper alright.

In my experience, when an if statement fires the conditional code despite what appears to be a false comparison, I have made a syntax error.  For example, I might add an extra semi colon or leave out a curly brace.  The error causes the browser to not evaluate the expression and instead execute the condition code as if it were the next statement.

The javascript syntax in your example looks fine to me, but there may be a small error in the lines prior to your if statement.  

That's the only thing I can think of at the moment.  Javascript is difficult to debug.  Sometimes it just takes a little experimentation.  For example, change the comparison to "==" test for equality, and see if the condition code does not fire.  Or, your could have the alert function display the value of ajaxRequest.responseText instead of assigning it to a text field.

Sorry I can't give you anything more specific.

---

### Post by Blacktalon on 2007-05-11
Hmm...could you post your whole code in your html, javascript,and php.  This way I can see what exactly you are trying to do and with what.   But as far as I can tell it looks like a variable problem with you using 
>  if("chatclear" != ajaxRequest.responseText) {
                alert("Error! Please contact site admin!");
            }

with the "chatclear", and it looks like you aren't setting any variable to anything so as to equal or not equal anything.

Definately post the rest of your code for at least the php file, I really would need to see it to determine, mainly really need to see the methods and paramaters being applied!


:)

---

### Post by yaaarrrgg on 2007-05-11
Could be a browser bug.  Could be comparingt he object references instead of the values?

Or possibly there could be some extra chars in the string ... like  \0 or \n?

a couple of things to try:

```

var someVariable = ajaxRequest.responseText;  //assign to a variable
if ( someVariable.indexOf("chatclear")  == -1 ){   // test if it's not a substring
   alert( "contact admin" );
}

```

---

### Post by Mirrorball on 2007-05-11
A few ways to debug: Make the alert box show the value of ajaxRequest.responseText too. Count the number of characters, compare character by character, print the numeric value of each character.

---

### Post by JNowka on 2007-05-12
Here is the code that I have written to check to see if anyone has sent an IM Request.  If there is an IM request then it will open up a IM window so that you and the other user can chat back and forth.

I have changed the below code already so that I could at least start working on and testing the send and receive functions in the chat box.  I find that if I store the information in a hidden field that it still has the same problem.  but if I use a text field then it works just fine.

I might have to try out checking out the length of each item.

```

function startCheck() {
    setTimeout("checkChat()", 5000);
    setTimeout("startCheck()", 6000);
}

function checkChat(){
    var ajaxRequest;  // The variable that makes Ajax possible!
    try{
        // Opera 8.0+, Firefox, Safari
        ajaxRequest = new XMLHttpRequest();
    } catch (e){
        try{
            // Internet Explorer Browsers
            ajaxRequest = new ActiveXObject("Msxml2.XMLHTTP");
        } catch (e) {
            try{
                ajaxRequest = new ActiveXObject("Microsoft.XMLHTTP");
            } catch (e){
                // Something went wrong
                alert("Your browser does not support AJAX!\n\nEither upgrade your browser or\nupdate your settings to allow AJAX!");
                return false;
            }
        }
    }
    ajaxRequest.onreadystatechange = function(){
        if(ajaxRequest.readyState == 4) {
            document.getElementById("ctxt").value = ajaxRequest.responseText;
             if("chatclear" != document.getElementById("ctxt").value) {
                window.open("./chat.php?login=<?= $login ?>&other=primary&chat=" + ajaxRequest.responseText, ajaxRequest.responseText, "height=680, width=500, scrollbars=no, menubar=no resizeable=no");
            }
        }
        
    }
    ajaxRequest.open("GET", "checkChat.php?login=<?= $login ?>", true);
    ajaxRequest.send(null);
}

``````

<?php
$conn = mysql_connect("localhost", "user", "password");
mysql_select_db("user", $conn);

$sql = <<<HERE
SELECT chat FROM JMap_Users WHERE login='$login';
HERE;

$result = mysql_query($sql, $conn);
$row = mysql_fetch_row($result);

$sql = <<<HERE
UPDATE JMap_Users SET chat ='' WHERE login = '$login';
HERE;

mysql_query($sql, $conn);

if($row[0] != "") {
    echo $row[0];
}
else {
    echo "chatclear";
}
?>

```

---

### Post by Mirrorball on 2007-05-12
Try removing the ?> from the PHP script. It's not necessary and it may be adding a newline character.

---

### Post by zephyrcat on 2009-06-05
EDIT: see here:

[http://stackoverflow.com/questions/958798/ajax-returns-random-values/](http://stackoverflow.com/questions/958798/ajax-returns-random-values/)

Was a solution found? I am having what appears to be the exact same issue. My code is below. I will update this if I find a solution.

```
WAITING FOR MATCH
<html><head><title>Waiting...</title></head><body>
<?php
echo "Your match id is: " . $_GET[id]; // No, this will not be passed as GET, but it works for now.
?>

<script type="text/javascript">
function update(id)
{
   var xmlhttp;
   if (window.XMLHttpRequest){
         // code for IE7+, Firefox, Chrome, Opera, Safari
         xmlhttp=new XMLHttpRequest();
   }else if (window.ActiveXObject){
      // code for IE6, IE5
      xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
   }else{
      alert("Your browser does not support XMLHTTP!");
   }

   xmlhttp.onreadystatechange=function(){
      if(xmlhttp.readyState==4){
         if(xmlhttp.responceText==1){
            document.write("Ready!");
         }
         document.myForm.status.value=xmlhttp.responseText;
      }
   }

   var i = 0;
   while(i<1){
      var requesturl = "t1_checkMatch.php?id="+id;
      document.write("- ");
      xmlhttp.open("GET",requesturl,true);
      xmlhttp.send(null);
      i=i+1;
      
      // delay for 1 sec
      var date = new Date();
      var curDate = null;
      do { curDate = new Date(); }
      while(curDate-date < 1000);
   }

}

<?php
   echo "update(".$_GET['id'].");";
?>

</script>


<form name="myForm">
Status: <input type="text" name="status" />
</form>

</body></html>
```
```
<?php
$db_user = "wikirunner";
$db_pass = "wiki";
$db_name = "wikirunnert1";
mysql_connect(localhost,$db_user,$db_pass);
@mysql_select_db($db_name) or die("Unable to select database");

$match_id = $_GET['id'];

$match_info = mysql_query("SELECT * FROM wikiracet1 WHERE id=".$match_id);
if(mysql_result($match_info,0,"usr2")==-1){
   echo 1;
}else{
   echo 0;
}
?>
```

---

