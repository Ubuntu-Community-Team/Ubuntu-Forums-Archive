---
title: "Plz post a basic simple PHP code to upload a file onto website?"
date: 2010-10-30
forum: Programming Talk
---

### Post by honeybear on 2010-10-30
Hello,

I would like that my friend has a very simple php page to post a file. 


I knwo that it can be done since I am using a php code to post some text into a sort of online notepad.

Anyone has the code for that ? 
that woudl help a lot
(I cannot do PHP sorry)

---

### Post by gerahmartinez on 2010-10-31
You could try something simple like

```

<form method='post' action='uploadfile.php' enctype='multipart/form-data'>
File: <input type='file' name='filename' />
<input type='submit' value='Upload File' />
</form>
<?php
if ($_FILES)
{[INDENT]$name= $_FILES['filename']['name'] ;
move_upload_file($_FILES['filename']['tmp_name'], $name);
[/INDENT]}
?>

```This will save the file in the directory your php script is located. Hope it helps

---

### Post by honeybear on 2010-10-31
> **gerahmartinez said:**
> You could try something simple like

```

<form method='post' action='uploadfile.php' enctype='multipart/form-data'>
File: <input type='file' name='filename' />
<input type='submit' value='Upload File' />
</form>
<?php
if ($_FILES)
{[INDENT]$name= $_FILES['filename']['name'] ;
move_upload_file($_FILES['filename']['tmp_name'], $name);
[/INDENT]}
?>

```This will save the file in the directory your php script is located. Hope it helps

- well, I am sorry but it is not working it gives error of the provider :(
> 
<form method='post' action='uploadfile.php' enctype='multipart/form-data'>
File: <input type='file' name='filename' />
<input type='submit' value='Upload File' />
</form>
<?php
if ($_FILES)
{

    $name= $_FILES['filename']['name'] ; move_upload_file($_FILES['filename']['tmp_name'], $name); 

}
?>



this one is not working too:
> 
<?php

if(isset($_FILES['uploaded'])){
$target = "galleries/".basename($_FILES['uploaded']['name']) ;
print_r($_FILES);

if(move_uploaded_file($_FILES['uploaded']['tmp_name'],$target)) echo "OK!";//$chmod o+rw galleries

}
else{
 echo "<form enctype='multipart/form-data' action='CodeTool.php' method='POST'>";
 echo "File:<input name='uploaded' type='file'/><input type='submit' value='Upload'/>";
 echo "</form>";
}

?>




It returned an error of provider. However thanks so much. 

With the command I tried several and found that this one works:
there is some generated text but well it works (not nice , but it works fine)
DEMO.PHP
```

<?php // RAY_temp_upload_example.php
error_reporting(E_ALL);
echo "<pre>" . PHP_EOL;

// IF A FILE HAS BEEN UPLOADED
if (!empty($_FILES))
{
    // SHOW THE UPLOADED FILES
    print_r($_FILES);

    // TRY TO MOVE THE FILE TWICE - SECOND MOVE RETURNS FALSE
    if (!move_uploaded_file($_FILES["userfile"]["tmp_name"], $_FILES["userfile"]["name"])) echo "CANNOT MOVE {$_FILES["userfile"]["name"]}" . PHP_EOL;
    if (!move_uploaded_file($_FILES["userfile"]["tmp_name"], $_FILES["userfile"]["name"])) echo "CANNOT MOVE {$_FILES["userfile"]["name"]}" . PHP_EOL;

    // SHOW THE UPLOADED FILES AFTER THE MOVE - NO VISIBLE CHANGE
    print_r($_FILES);
}

// END OF PHP, PUT UP THE HTML FORM TO GET THE FILE
?>
<!-- The data encoding type, enctype, MUST be specified as below -->
<form enctype="multipart/form-data" method="POST">
    <!-- MAX_FILE_SIZE must precede the file input field -->
    <input type="hidden" name="MAX_FILE_SIZE" value="300000" />
    <!-- Name of input element determines name in $_FILES array -->
    Send this file: <input name="userfile" type="file" />
    <input type="submit" value="Send File" />
</form>




```

I try to avoid : $dir_base = "/your/file/location/";   
so that it works anywhere and all the time

I have found this : 
[http://php.net/manual/en/function.move-uploaded-file.php](http://php.net/manual/en/function.move-uploaded-file.php)
but have no ideas how to make how to join the HTML and the PHP functions, ie. to use both the array input type="submit" & php functions, well, some could look nice





--

For instance this code:
DEMO.PHP
> 
<?php // RAY_temp_upload_example.php

// IF A FILE HAS BEEN UPLOADED

$uploaddir = '';
$uploadfile = $uploaddir . basename($_FILES['upfile']['name']);
echo '<pre>';
if (move_uploaded_file($_FILES['upfile']['tmp_name'], $uploadfile)) {
   echo "File is valid, and was successfully uploaded.\n";
} else {
   echo "Possible file upload attack!\n";
}
echo 'Here is some more debugging info:';
print_r($_FILES);
print "</pre>";

// END OF PHP, PUT UP THE HTML FORM TO GET THE FILE
?>
<!-- The data encoding type, enctype, MUST be specified as below -->
<form enctype="multipart/form-data" method="POST">
    <!-- MAX_FILE_SIZE must precede the file input field -->
    <input type="hidden" name="MAX_FILE_SIZE" value="300000" />
    <!-- Name of input element determines name in $_FILES array -->
    Send this file: <input name="userfile" type="file" />
    <input type="submit" value="Send File" />
</form>


returns an error but NOT uploads well:
(not uploading/not working)
> Possible file upload attack!
Here is some more debugging info:Array
(
    [userfile] => Array
        (
            [name] => apple_netbook.jpg
            [type] => image/jpeg
            [tmp_name] => /var/tmp/multiserv/users/542256/projects/232138/phpsseuve
            [error] => 0
            [size] => 27366
        )

)

Send this file

---
* EDIT * 
--- 
I made a code example split in two : html and php also 
as indication
file is: working_uploader_php_code_example_HB.zip


a best move would be in one file surely

---

