---
title: "PHP linking an image"
date: 2011-08-06
forum: Programming Talk
---

### Post by bneva on 2011-08-06
I feel pretty stupid asking this question but I haven't ever used php and I am sure it's just a easy fix.

I'm just making a simple website for a class and I am trying to link images I have in a folder.

My code thus far

```
  <?php
	$dir = "/var/www/pictures/";
	$dirhandler = opendir($dir);
	
	$fc = 0;
	while ($file = readdir($dirhandler))
	{

		if ($file != '.' && $file != '..')
        {
			$files[$fc]=$file;
			$fc++;                
        }
	}
	$length = $fc;
	for ($fc = 0; $fc < $length; $fc++)
	{
		
		$dir2 = $dir;
		$dir2 .= $files[$fc];
		echo "$dir2 <br />";
		echo "<IMG SRC = \"$dir2\"/><br /> ";
	}
?>
```

Now when I echo $dir2 it prints out all of the /var/www/pictures/filename.jpg but I'm not sure why the images aren't actually showing.  What am I missing or overlooking in my image tag?

Thanks

---

### Post by Bachstelze on 2011-08-06
In IMG tags you must use the path of the image relative to the root of the webserver, not of the filesystem.

---

### Post by bneva on 2011-08-06
> **Bachstelze said:**
> In IMG tags you must use the path of the image relative to the root of the webserver, not of the filesystem.

so would I just need pictures/, or am I misunderstanding?

---

### Post by Bachstelze on 2011-08-06
If the root of your webserver is /var/www (which it probably is), yes. Basically the filename in the IMG tag must match what you would type in a browser to access the image, minus the host part.

---

### Post by bneva on 2011-08-06
> **Bachstelze said:**
> If the root of your webserver is /var/www (which it probably is), yes. Basically the filename in the IMG tag must match what you would type in a browser to access the image, minus the host part.

alright thanks I will try it out

---

### Post by unknownPoster on 2011-08-07
> **Bachstelze said:**
> If the root of your webserver is /var/www (which it probably is), yes. Basically the filename in the IMG tag must match what you would type in a browser to access the image, minus the host part.


I don't think "must" is the right choice. Links can be absolute, rather than relative as you're describing.

---

### Post by Bachstelze on 2011-08-07
> **unknownPoster said:**
> I don't think "must" is the right choice. Links can be absolute, rather than relative as you're describing.

Yes sorry, poor choice of words. Though honestly, who uses absolute paths for images on the same site?

---

### Post by unknownPoster on 2011-08-07
> **Bachstelze said:**
> Yes sorry, poor choice of words. Though honestly, who uses absolute paths for images on the same site?

No one other than beginners, assuming proper site structure. 

At my old job about 3 years ago I remember explicitly having to use absolute links because relative would fail but we were also working with a web CMS which has never received positive reviews from my coworkers. 

I still have access to it as they just transferred me to a "sister" department. I'll have to look and see if it still forces the absolute links.

---

