---
title: "remove space from file written"
date: 2012-04-10
forum: Programming Talk
---

### Post by cj13579 on 2012-04-10
Hi all,

I have a php script that writes to a file but I am having some problems with it. The file that I am writing is highly sensitive YML file and it breaks every time I edit it using my web editor. What happens is the script seemingly appends a space on the first line every time the file is opened and then saved. I have tried changing the fopen mode.

Any help greatly appreciated:

[PHP]		$filename = "../config.yml"; 
		$newdata = $_POST['newd']; 
		
		if(isset($_POST['submit1']))
		{
			header("location:config.php");
		}
		if ($newdata != '') 
		{ 
			// open file  
			$fw = fopen($filename, 'w') or die('Insufficent permissions to open file with write access!'); 
			// write to file 
			// added stripslashes to $newdata 
			$fb = fwrite($fw,stripslashes($newdata)) or die('Could not write to file'); 
			// close file 
			fclose($fw); 
		}

		$fh = fopen($filename, "r") or die("Could not open file!"); 
		$data = fread($fh, filesize($filename)) or die("Could not read file!"); 
		fclose($fh); 
		
		echo "<h3>Contents of File</h3> ";
		echo "<form method=\"post\" action=\"$_SERVER[php_self]\">";
		echo "<input type=\"submit\" value=\"Change\"> ";	
		echo "<input type=\"hidden\" name=\"cancel\" value=\"cancel\">";
		echo "<input type=\"submit\" name=\"submit1\"value=\"Cancel\">";
		echo "<textarea name='newd' cols='100%' rows='50'> $data </textarea> ";
		echo "<input type='submit' value='Change'> ";
		echo "<input type=\"hidden\" name=\"cancel\" value=\"cancel\">";
		echo "<input type=\"submit\" name=\"submit1\"value=\"Cancel\">";		
		echo "</form>"; [/PHP]

Thanks in advance.

---

### Post by wallaroo on 2012-04-11
If you mean that the first character of the first line is always a space, then yes, your html code is inserting it.

All the text between <textarea></textarea> tags is taken literally so by having a space before and after your '$data' variable is in fact inserting a space before and after your text when you read back the data in $_POST['newd'].

So the line should be ..
```
<textarea name='newd' cols='100%' rows='50'>$data</textarea> 
```

---

### Post by cj13579 on 2012-04-11
I was sure that it was going to be something simple but that really is annoying!!

Thank you very much sir, you are a gent! Will mark solved.

---

