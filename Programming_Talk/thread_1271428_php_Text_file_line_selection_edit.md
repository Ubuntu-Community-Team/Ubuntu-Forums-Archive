---
title: "php Text file line selection edit?"
date: 2009-09-20
forum: Programming Talk
---

### Post by hockey97 on 2009-09-20
Hi, I want to know how to use php to delete or add a line in a text file. 

For example, I want to create a html file. Lets say their is 15 lines of html code in this file. I would like to  be able to delete lets say line 6 and add line 16 which is an extra line of code. Then lets say a month goes by and I want to put data back in line 6. How can you add or delete code on each lines in the file?

---

### Post by CyberJack on 2009-09-21
html files are just plain text files so you can read them with the file(), fread() or file_get_contents() functions.
When using the file() function you will get an array (each line is an element) the other functions will get you a string which you can convert to an array (explode() function).

Then when you have read the file into an array, create a new array while looping the original array.
If you want to remove a line just don't add it to the new array.
If you want to keep or modify a line add the original or the modified version to the new array.

When you are done changing the content, convert the new array back to a string (implode() function) and write to the file with the file_put_contents() or the fwrite() functions.


Instead of changing html files with php you could also let php generate the html output.
Changing files is always a risk. If a write action goes wrong you could lose the complete file.
So generating output with php is a safer option.

---

