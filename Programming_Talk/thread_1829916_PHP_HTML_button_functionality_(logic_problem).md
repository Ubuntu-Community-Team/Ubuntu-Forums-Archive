---
title: "PHP HTML button functionality (logic problem)"
date: 2011-08-20
forum: Programming Talk
---

### Post by bneva on 2011-08-20
Sorry for the weird name, I wasn't really sure what to call this!

Basically I have a folder with a bunch of files and I want to be able to delete them by pressing a button.  The page looks like this..

video link | DELETE
video link | DELETE
etc... each file has a delete button beside it.

My question is, I am not sure how to link the button with the actual file.  Like when I press delete next to file 1, how can I associate that button ONLY with file 1?  I can't think of how to keep track of which button I pressed so I know which video to delete.

OR if anyone has a better solution speak up by all means lol

this is my code so far.
```
<?php
		$dir = "pictures/";
		$vid = "swf";
		$dirhandler = opendir($dir);
	
		$fc = 0;
		while ($file = readdir($dirhandler))
		{

			if ($file != '.' && $file != '..')
		    {
		    	if((strpos($file, $vid) == false))
		    	{
		    		continue;
		    	}
		    	else
		    	{
					$files[$fc]=$file;
					$fc++;
				}
		    }
		}
		$length = $fc;
		$count = 0;
		
		echo "<table border=1>";
		for ($fc = 0; $fc < $length; $fc++)
		{
			$count++;
			$dir2 = $dir;
			$dir2 .= $files[$fc];
			
			echo "<tr><td>";
			echo "<a href= \"$dir2\"/> $files[$fc] </a> <br /> ";
			echo "</td>";
			echo "<td>";
			echo "<button type=\"button\">Delete</button>";
			echo "</td></tr>";
		}
		echo "</table>";
	?>
```

---

### Post by Bachstelze on 2011-08-21
You could make each button a link to page.php?action=delete+filename=blah

Of course you will probably need some sort of authentication mechanism to make sure people can't delete files just by entering the URL.

---

### Post by bneva on 2011-08-21
ok I found out I can give the button an ID so I am going to just use an incrementing variable so the ID is simple (1,2,3 etc).  So each time I add a new link, the counter goes up.

Now my question is, how do I actually get the ID from the button when it's pressed?

---

### Post by bneva on 2011-08-21
> **Bachstelze said:**
> You could make each button a link to page.php?action=delete+filename=blah

Of course you will probably need some sort of authentication mechanism to make sure people can't delete files just by entering the URL.

But what I can't figure out is like, when I press the delete in row 1, how do I identify I pressed the button in row 1, so I know to delete the file name in row 1 as well?

edit: if you look at the post before this I am adding an ID to the button, but I"m not sure how to get the ID when I actually press the button itself.

---

### Post by Bachstelze on 2011-08-21
You would create your buttons like that:

```
<?php
echo "<a href=\"{$_SERVER['PHP_SELF']}?action=delete+filename={$file[$fc]}\">
          <button type=\"button\">Delete</button>
      </a>";
?>
```

---

### Post by fdrake on 2011-08-21
would be easier to just give as ID of the button the name or url of the file?

second do you want to detele files one by one or select the delete button of eny file and delete them all at once? that an important issue because making a $_POST insteat of a $_GET request may be easier and more functional.

---

### Post by Bachstelze on 2011-08-21
> **fdrake said:**
> would be easier to just give as ID of the button the name or url of the file?

Depends. Then you would need a way to match the ID to the actual file to be deleted.

---

### Post by v8YKxgHe on 2011-08-21
Go simpler and just make each its own HTML form, with 1 hidden input being the identifier for the file and 1 submit button per form. Of course, validate the values server-side for security reasons.

---

### Post by bneva on 2011-08-22
> **Bachstelze said:**
> You would create your buttons like that:

```
<?php
echo "<a href=\"{$_SERVER['PHP_SELF']}?action=delete+filename={$file[$fc]}\">
          <button type=\"button\">Delete</button>
      </a>";
?>
```

sorry it took so long to reply, this doesn't work.  It just goes to the same page, but action "action=delete+filename=" at the end of the URL.  It doesn't actually delete anything.

I changed it to $dir2 which holds the path (/picture/videoname.swf) and still doesn't work, it just does the same thing as before but adds the path to the link.

---

### Post by bneva on 2011-08-22
I guess something I should mention is.......

The page will be dynamically adding videos to the page.  I'm using the program "motion" which is like a motion detection via webcam program.  When it detects motion it makes a video file of the images it stores.

Basically this part of my project I am trying to make a video.php page and dynamically add videos to the table.  So if they refresh the page and more motion was detected, they will be added.  That's why it's basically impossible (or at least I think) to hardcode the filename at least as an ID.

---

### Post by bneva on 2011-08-22
> **AlexC_ said:**
> Go simpler and just make each its own HTML form, with 1 hidden input being the identifier for the file and 1 submit button per form. Of course, validate the values server-side for security reasons.

I'm trying this approach right now...I'm not sure if I am calling the function right because its not working.  I did chmod 777 the video files just to make things easier for now.  I think I need to somehow pass the button ID into the function but I don't know how to do that.
```
	<?php
	
		function delete_video($path)
		{
			unlink($path);
		}
	?>

	 <?php
		$dir = "pictures/";
		$vid = "swf";
		$dirhandler = opendir($dir);
	
		$fc = 0;
		while ($file = readdir($dirhandler))
		{

			if ($file != '.' && $file != '..')
		    {
		    	if((strpos($file, $vid) == false))
		    	{
		    		continue;
		    	}
		    	else
		    	{
					$files[$fc]=$file;
					$fc++;
				}
		    }
		}
		$length = $fc;
		$count = 0;
		
		echo "<table border=1>";
		for ($fc = 0; $fc < $length; $fc++)
		{
			$count++;
			$dir2 = $dir;
			$dir2 .= $files[$fc];
			
			echo "<tr><td>";
			echo "<a href= \"$dir2\"/> $files[$fc] </a> <br /> ";
			echo "</td>";
			echo "<td>";
			
			echo "<form>
				  <input type=\"button\" id=\"$files[$fc]\" value=\"Delete\" onClick=\"delete_video($files[$fc])\" />
				  </form>";

			#echo "<button type=\"button\" id=\"$count\">Delete</button>";
			echo "</td></tr>";
		}
		echo "</table>";
	?>
```

---

### Post by v8YKxgHe on 2011-08-23
You're mixing server side (PHP) with client side (JavaScript). You can not call PHP functions from within JavaScript.

You don't need any JavaScript for this to work. That HTML form will POST to another URL, that can then use PHP to delete the provided file name (but be careful, you will need to secure this).

---

### Post by bneva on 2011-08-23
> **AlexC_ said:**
> You're mixing server side (PHP) with client side (JavaScript). You can not call PHP functions from within JavaScript.

You don't need any JavaScript for this to work. That HTML form will POST to another URL, that can then use PHP to delete the provided file name (but be careful, you will need to secure this).

so I have to send it to another page to handle this?  How do I actually get the ID from the button though.  I gave each button the filename of the current rows video as an ID.  So when I send this to another page, how do I get the button's ID stored to say a variable or something so I can unlink() it.

---

### Post by v8YKxgHe on 2011-08-23
```
<form action="foo.php" method="post">
    <input type="hidden" name="file" value="myfile">
    <input type="submit" value="Delete">
</form>
```

[PHP]<?php
if (isset($_POST['file'])) {
   /** Add security logic here as this code is very insecure, example only */
   unlink($_POST['file']);
} else {
   /** Error handling for when the key does not exist */
}
?>
[/PHP]

---

### Post by bneva on 2011-08-23
> **AlexC_ said:**
> ```
<form action="foo.php" method="post">
    <input type="hidden" name="file" value="myfile">
    <input type="submit" value="Delete">
</form>
```

[PHP]<?php
if (isset($_POST['file'])) {
   /** Add security logic here as this code is very insecure, example only */
   unlink($_POST['file']);
} else {
   /** Error handling for when the key does not exist */
}
?>
[/PHP]

wow thanks I will try that out.  By security do you mean I should add like encryption stuff etc..

---

### Post by fdrake on 2011-08-23
> **bneva said:**
> wow thanks I will try that out.  By security do you mean I should add like encryption stuff etc..

for security you can create a varaiable (or set of random caracters) to be stored in the client's session(saved in the server) and inside the $_post globale array (saved in the client session).And double check if the variable from the session is the same as the the othe one sent to to the $_post array. This way people cannot send at free will random $_post requests to your server.

---

### Post by bneva on 2011-08-24
It's still not deleting, am I doing it wrong?  It prints foo everytime.  I tried giving it just the filename as the value as well as the path (pictures/filename) and neither of them work.

[PHP]			echo "<form action=\"handle.php\">	  
				  <input type=\"hidden\" name=\"file\" value=\"$files[$fc]\" />
				  <input type=\"submit\" value=\"Delete\" />
				  </form>";[/PHP]
[PHP]<?php
	if (isset($_POST['file'])) {
	   unlink($_POST['file']);

	}
	else
	{
		echo "foo";
	}
?> [/PHP]

---

### Post by fdrake on 2011-08-24
can you do:
```

<?php
    if (isset($_POST['file'])) {
       unlink($_POST['file']);

    }
    else
    {
        print_r($_POST);

    }
?> 

```

and post here the results of the array. maybe your pat is wrong.

---

### Post by bneva on 2011-08-24
lol all it says is Array ( )

edit: doh forgot to put method=post oops!

Ok it's still not deleting, I made the array print before unlink and it prints out if I give it the path.....I think I need the path because the php files aren't in the picture folder.

```
Array ( [file] => pictures/01-20110814190142.swf )
```


Also, is there any way I can send the handle.php right back to the previous page?  As in, I click delete, it goes to handle.php, deletes the file and goes back to videos.php

---

### Post by fdrake on 2011-08-24
> **bneva said:**
> lol all it says is Array ( )

edit: doh forgot to put method=post oops!

Ok it's still not deleting, I made the array print before unlink and it prints out if I give it the path.....I think I need the path because the php files aren't in the picture folder.

```
Array ( [file] => pictures/01-20110814190142.swf )
```


Also, is there any way I can send the handle.php right back to the previous page?  As in, I click delete, it goes to handle.php, deletes the file and goes back to videos.php

```
ls -al /etc/www/pictures
```
or wherever you keep the pics folder
what's the output.

to redurect google "php redirect function" there is more than 1 way to do that.

---

### Post by bneva on 2011-08-24
> **fdrake said:**
> ```
ls -al /etc/www/pictures
```
or wherever you keep the pics folder
what's the output.

to redurect google "php redirect function" there is more than 1 way to do that.

bolded the ones of importance

```
drwxr-xr-x 2 root root  4096 2011-08-22 20:27 .
drwxr-xr-x 3 root root  4096 2011-08-24 15:57 ..
-rwxr-xr-x 1 root root  3490 2011-08-06 15:41 01-20110805195931-01.jpg
-rwxr-xr-x 1 root root  3779 2011-08-06 15:41 01-20110805195932-00.jpg
-rwxr-xr-x 1 root root  3483 2011-08-06 15:41 01-20110805195933-00.jpg
-rwxr-xr-x 1 root root  3418 2011-08-06 15:41 01-20110805195933-01.jpg
-rwxr-xr-x 1 root root  3287 2011-08-06 15:41 01-20110805195934-00.jpg
-rw-r--r-- 1 root root  3486 2011-08-14 19:01 01-20110814190142-00.jpg
-rw-r--r-- 1 root root  2815 2011-08-14 19:01 01-20110814190142-01.jpg
**-rwxrwxrwx 1 root root 39497 2011-08-14 19:02 01-20110814190142.swf**
-rw-r--r-- 1 root root  2965 2011-08-14 19:01 01-20110814190143-00.jpg
-rw-r--r-- 1 root root  2815 2011-08-14 19:01 01-20110814190151-01.jpg
-rw-r--r-- 1 root root  2898 2011-08-14 19:01 01-20110814190152-00.jpg
-rw-r--r-- 1 root root  2920 2011-08-14 19:01 01-20110814190152-01.jpg
-rw-r--r-- 1 root root  2933 2011-08-14 19:01 01-20110814190153-00.jpg
-rw-r--r-- 1 root root  2786 2011-08-14 19:02 01-20110814190209-00.jpg
-rw-r--r-- 1 root root  2872 2011-08-14 19:02 01-20110814190209-01.jpg
-rw-r--r-- 1 root root  2914 2011-08-14 19:02 01-20110814190210-00.jpg
-rw-r--r-- 1 root root  2895 2011-08-14 19:02 01-20110814190210-01.jpg
-rw-r--r-- 1 root root  2875 2011-08-14 19:02 01-20110814190211-00.jpg
-rw-r--r-- 1 root root  2872 2011-08-14 19:02 01-20110814190211-01.jpg
-rw-r--r-- 1 root root  2885 2011-08-14 19:02 01-20110814190212-00.jpg
-rw-r--r-- 1 root root  2885 2011-08-14 19:02 01-20110814190212-01.jpg
-rw-r--r-- 1 root root  2902 2011-08-14 19:02 01-20110814190213-00.jpg
-rw-r--r-- 1 root root  2892 2011-08-14 19:02 01-20110814190213-01.jpg
-rw-r--r-- 1 root root  2885 2011-08-14 19:02 01-20110814190214-00.jpg
-rw-r--r-- 1 root root  2879 2011-08-14 19:02 01-20110814190214-01.jpg
-rw-r--r-- 1 root root  2676 2011-08-14 19:02 01-20110814190257-01.jpg
-rw-r--r-- 1 root root  2834 2011-08-14 19:02 01-20110814190258-00.jpg
-rw-r--r-- 1 root root  2913 2011-08-14 19:02 01-20110814190258-01.jpg
**-rwxrwxrwx 1 root root 13770 2011-08-14 19:03 01-20110814190258.swf**
-rw-r--r-- 1 root root  2724 2011-08-14 19:03 01-20110814190302-00.jpg
-rw-r--r-- 1 root root  2827 2011-08-14 19:03 01-20110814190302-01.jpg
-rw-r--r-- 1 root root  2774 2011-08-14 19:03 01-20110814190336-00.jpg
-rw-r--r-- 1 root root  2643 2011-08-14 19:03 01-20110814190336-01.jpg
**-rwxrwxrwx 1 root root 13959 2011-08-14 19:03 01-20110814190336.swf**
-rw-r--r-- 1 root root  2774 2011-08-14 19:03 01-20110814190337-00.jpg
-rw-r--r-- 1 root root  2858 2011-08-14 19:03 01-20110814190345-01.jpg
-rw-r--r-- 1 root root  2941 2011-08-14 19:03 01-20110814190346-00.jpg
-rw-r--r-- 1 root root  5657 2011-08-14 20:08 01-20110814200801-01.jpg
-rw-r--r-- 1 root root  5263 2011-08-14 20:08 01-20110814200802-00.jpg
-rw-r--r-- 1 root root  5085 2011-08-14 20:08 01-20110814200802-01.jpg
**-rwxrwxrwx 1 root root 50214 2011-08-14 20:08 01-20110814200802.swf**
-rw-r--r-- 1 root root  5158 2011-08-14 20:08 01-20110814200803-00.jpg
-rw-r--r-- 1 root root  5055 2011-08-14 20:08 01-20110814200803-01.jpg
-rw-r--r-- 1 root root  5137 2011-08-14 20:08 01-20110814200804-00.jpg
-rw-r--r-- 1 root root  5032 2011-08-14 20:08 01-20110814200804-01.jpg

```

---

### Post by fdrake on 2011-08-24
i am assuming that the php file and the pictures folder are in the /etc/www folder.

---

### Post by bneva on 2011-08-24
> **fdrake said:**
> i am assuming that the php file and the pictures folder are in the /etc/www folder.

they are in /var/www and the pictures/video are in /var/www/pictures

---

### Post by fdrake on 2011-08-24
> **bneva said:**
> they are in /var/www and the pictures/video are in /var/www/pictures

try not to apply the redirection function yet since we need to see the erro msg to resolve the problems.

do you see any erro msg showing or not?
can you change your code to this:

```

<?php
    
   echo "<html><head><title>Deleting File!</title></head><body>"

    if (isset($_POST['file'])) {
       echo "file selected:$_POST['file']</br>";
       if (!unlink($_POST['file']))
           {
             echo ("Error deleting $_POST['file']</br>");
            }
       else
            {
        echo ("Deleted $_POST['file']</br>");
             }

    }
    else
    {
        echo "no file selected!";

    }

   echo "</body></html>"
?>

```

---

### Post by bneva on 2011-08-24
nothing prints at all, must be something wrong with a statement.  It doesn't like echo with $_POST['file'] if I get rid of the ['file'] part it will print the words Array, but gives an error regardless.

---

### Post by fdrake on 2011-08-24
> **bneva said:**
> nothing prints at all, must be something wrong with a statement.  It doesn't like echo with $_POST['file'] if I get rid of the ['file'] part it will print the words Array, but gives an error regardless.

try to save the value into a variable first of all:
```

$file=$_POST['file']

```

probably the original problem for the unlink function not to wrok was the string structure of the array (maybe). and then use the $file instead of $_POST['file'] in the code

---

### Post by bneva on 2011-08-24
> **fdrake said:**
> try to save the value into a variable first of all:
```

$file=$_POST['file']

```

probably the original problem for the unlink function not to wrok was the string structure of the array (maybe). and then use the $file instead of $_POST['file'] in the code

file selected:pictures/01-20110814190142.swf
Error deleting pictures/01-20110814190142.swf

---

### Post by fdrake on 2011-08-25
ok the problem is that unlink cannot find the file. why? because it thinks that "pictures/video.swf" is the name of the file!

edit:  Sorry, do not change the first file!!!! It's fine the way it was before!

Change the $file variable to:
```

$file = basename($_POST['file']]); 

```
try again.

ps can you change your ini file so it displays an error msg! will make the developmend easier. see the how to [http://php.about.com/od/troubleshooting/qt/php_error_reporting.htm](http://php.about.com/od/troubleshooting/qt/php_error_reporting.htm)

---

### Post by dazman19 on 2011-08-25
1) it cant unlink the file because its owned by root.

try this:
```
sudo chown -R www-data:www-data /var/www/pictures 
```
this will recursively change the owner to the web server user.

2) I cant see how this will work 
[PHP]
    if(!unlink($_POST['file']))
[/PHP]

I am going to assume your server root is /var/www/
meaning that [http://localhost/](http://localhost/) or [http://(your.servers.ip.address)/](http://(your.servers.ip.address)/) is the root.

In most cases you will post the file name. I suggest printing out the value of $_POST or use a tool like firebug to see what is being posted.

also find out what this returns 
echo getcwd(); 

it probably wont be /pictures, and it will more than likely return /var/www so you will have to unlink it using

unlink("pictures/".$_POST['file']);

Hope it helps.

EDIT: its probably not a good idea to chmod 777 anything in general.

---

### Post by fdrake on 2011-08-25
@dazman
chown will not make the difference because he wants to delete only the .swf file in  the picture folder. and those files have already an full permisssion:rwx for everyone.

---

### Post by dazman19 on 2011-08-25
nothing was printing from the code above because it was not compiling by the pre-processor properly.

inside the echo, when dealing with object member functions or arrays you need to use the {} around.

e.g. 

[PHP]echo "file selected:{$_POST['file']}</br>";[/PHP]

that is why your screen is coming up blank. 

Here I added in what you needed to fdrake's code so the syntax is correct. So assuming your $_POST array has the right data in the file key then it should be sweet.


[PHP]
   echo "<html><head><title>Deleting File!</title></head><body>";

    if (isset($_POST['file'])) 
    {
       echo "file selected:{$_POST['file']}</br>";
       if (!unlink($_POST['file']))
       {
            echo ("Error deleting {$_POST['file']}</br>");
       }
       else
       {
            echo ("Deleted {$_POST['file']}</br>");
       }
    }
    else
    {
        echo "no file selected!";
    }

   echo "</body></html>"
[/PHP]

@fdrake 
Yeh you are right he can delete the file, but if he adds more files later and doesn't change the permissions he will wonder why they are not deleting. So its best to set the permissions/owners correctly.

Once you get this working you can do a header re-direct:

[PHP]
    if (isset($_POST['file'])) 
    {
       try 
       {
            unlink($_POST['file']);
            
       } catch (Exception $e)
       {
           echo "File failed to delete".$e->getMessage();
       }
    }
    header('videos.php'); //for the redirect. NOTE: that if it does throw an error, then you will see the error, and it wont re-direct to the videos.php
[/PHP]

---

### Post by kunal00731 on 2011-08-25
Hi bneva,
I think the best way to do this is to make a form, an action class  and a dao (if u r making any queries form DB) , but u must have an action and a form class definitely. This will easily help you to perform any operation you want based on a html document.

Hope this helps.
__

---

### Post by v8YKxgHe on 2011-08-26
bneva; there seems to be a lot of misinformation being handed to you here so I'll try and clear a few things up.

The code I gave you will work, the reason you're running into issues is that the permissions on the file you're trying to delete are denying you from doing so.

The files are owned by root; therefor your PHP script is going to have to be ran as root for those files to be deleted - however, this is a **bad idea.** I'm going to assume you're using Apache2 and the mod_php extension, of which by default you're PHP scripts will be executed as the 'www-data' user. So, the files you want to delete need to be owned by 'www-data'.

As for security, no I don't mean "encryption stuff" ;). What happens if I was to pass my own filename to your script, say "/var/www/file_you_dont_want_me_to_delete"?

This will work and do what you need:

```
<form action="foo.php" method="post">
    <input type="hidden" name="file" value="myfile">
    <input type="submit" value="Delete">
</form>
```

[PHP]<?php
header('Content-Type: text/plain; charset=utf-8'); # This is here as I CBA to use HTML.

if (isset($_POST['file'])) {
   $photo_dir = '/var/www/cake/';
   $file_path = $photo_dir.$_POST['file'];
   if (strpos(realpath($file_path), $photo_dir) === 0) {
       // We should be safe to remove the file, but more checks can be added for security
       if (is_file($file_path) && unlink($file_path)) {
           header('Location: http://example.com/alldone.php');
       } else {
           echo 'Oh noes, could not delete: ', $file_path;
       }
    } else {
        echo 'no malicious activity please :)';
    }
} else {
   echo 'Please provide a file name to delete';
}
?>[/PHP]

Note that this is untested, but should work.

dazman19: PHP does not throw exceptions for error handling with functions such 'unlink'.

kunal00731: Eh? Why would any classes need to be used here? That's just overcomplicating a situation. Keep it simple.

---

### Post by bneva on 2011-08-26
holy crap this thread has been busy sorry for not updating you guys, I am working on it now!

---

### Post by bneva on 2011-08-26
ALRIGHT!!! it works!!

Thank you everyone for all the help, I feel stupid sometimes asking these questions but I have never used PHP in my life until now!

---

### Post by bneva on 2011-08-31
Actually I have one more question.  For the Header() function, is there a way I can get it to go to my servers ip address/whatever.php.  Like I have this on other pages

$ip = $_SERVER[SERVER_ADDR]; but I can't seem to put $ip inside the header function.

I'm only asking this because when I demo this project I have to go to school so my IP will be different and I would rather the server just give me the IP address instead of hard coding it in.

---

### Post by dazman19 on 2011-09-01
I believe you can use it in the header(); function

$ip = $_SERVER[SERVER_ADDR];
header('Location: http://'.$ip.'/folder/');

The thing that will throw you off with headers is that you can only use a header re-direct if there has been nothing written to standard out.. in this case no echo's or anything printed.

If you are seeing something like "content encoding error" i think firefox says.. then it will often be because you have output before a header re-direct.

---

