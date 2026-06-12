---
title: "Beginner PHP question"
date: 2009-12-15
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2009-12-15
Hello All

I'm just starting to learn php and have encountered a problem.  I'm trying to read lines from a file, check their values, then update those values.  Here's what I have:
```

	$idFile = "id.txt";
	$id = 0;
	if (file_exists($idFile)) {
		$t = fopen($idFile, 'w');
		$id = fgets($t) + 1;
		// Check the year to make sure we don't need to reset...
		if (trim(fgets($t)) != date("Y")) $id = 0;	
		
		fwrite($t, $id);
		fwrite($t, "\r\n");
		fwrite($t, date("Y"));
		fclose($t);
	}

```

It appears that the values are being read and written correctly, but all the boolean conditions always fail, and the first line in the file (the id line) is never overwritten unless there's nothing there.  Can anyone tell me what I'm doing wrong?

Thanks a lot.

---

### Post by travmanx on 2009-12-15
```

  $file = fopen('id.txt', 'a');
  while (!feof($file)) {
    $line = fgets($file);
    if(trim($line) !=  date("Y"))
    {
         $id = 0;
  }
  fwrite($file, str_replace($line, ' ', $id . "\r\n" . date("Y"));
  fclose($file);

```
Hopefully its what you need.

---

### Post by the_real_fourthdimension on 2009-12-16
Thanks for the reply.  I am only reading the only two lines from this file, so I don't see why any looping constructs are necessary...  I think I'm just doing something wrong with how I'm using or accessing the variables in my expressions.

---

### Post by Hellkeepa on 2009-12-16
HELLo!

First off we need to know how the data in that file is stuctured, in order to give you accurate assistance on this. Secondly, you seem to be using the old method of reading and writing to files. "file_get_contents()" and "file_put_contents()" are the recommended method of doing this.

What you are doing wrong is almost certainly tied with the data structure in the file, and as such I cannot say for certain. However, you might want to take a closer look at how "[fgets()](http://no.php.net/fgets)" works. The missing length is most likely the issue here.
That said, this is how I'd do it:
```
<?php

$idFile = "id.txt";

// First off, check if the file is write- and readable.
if (!is_writable ($idFile) || !is_readable ($idFile)) {
	die ("Cannot read/write to the data file");
}

// Read the contents of the entire file and add into an array.
if (!$data = file ($idFile)) {
	die ("Could not read the contents of the data file");
}

// If data is not from current year, set ID to 0. (Why?)
if (trim ($data[1]) != date ('Y')) {
	$data[0] = "0\n";
}

// Implode the contents of the array to a string.
$data = implode ('', $data);

// Write to the file.
if (!file_put_contents ($idFile, $data)) {
	die ("Could not write to the file");
}

?>
```
PS: You can, and probably should, replace the "die()" calls with your own error handling methods.

Happy codin'!

---

### Post by travmanx on 2009-12-16
> **Hellkeepa said:**
> HELLo!

First off we need to know how the data in that file is stuctured, in order to give you accurate assistance on this. Secondly, you seem to be using the old method of reading and writing to files. "file_get_contents()" and "file_put_contents()" are the recommended method of doing this.



Wow didn't know about file_put/get_contents... always just used fwrite, ect. Learn something new everyday lol
:)

---

### Post by the_real_fourthdimension on 2009-12-16
Thanks.  that general idea worked just fine. :)

---

### Post by Hellkeepa on 2009-12-16
HELLo!

You're welcome, both of you. :-)

Happy codin'!

---

