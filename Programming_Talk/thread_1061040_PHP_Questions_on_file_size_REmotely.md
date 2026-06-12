---
title: "PHP Questions on file size REmotely"
date: 2009-02-05
forum: Programming Talk
---

### Post by cerealtx on 2009-02-05
im trying to check the files size of a remote video file to see if i want it, from what i have searched i have found something like this 
```
 				$handle = fopen($vidmatch[1], "r");
				$contents = fread($handle, filesize($vidmatch[1]));
				fclose($handle);
```
but all i get is Warning: fread(): Length parameter must be greater than 0 in /home/cereal/Documents/HubVideoGrab/HubVid.php on line 25
 what am i missing? or is there a better way to do this
or if i do it like this, it has to download the whole video file so it can then check the file size there has to be a better way
```
	$handle = fopen($vidmatch[1], "rb");
	$contents = stream_get_contents($handle);
	fclose($handle);
	echo filesize($handle);
```

---

### Post by drubin on 2009-02-05
Take a look here [http://php.mirrors.ilisys.com.au/manual/en/features.remote-files.php](http://php.mirrors.ilisys.com.au/manual/en/features.remote-files.php)

---

### Post by cerealtx on 2009-02-05
couldn't get it from that site, and or was slow, found a diff one tho [http://codesnippets.joyent.com/posts/show/1214](http://codesnippets.joyent.com/posts/show/1214), your my hero drubin helped me ask google the right question :)

---

### Post by drubin on 2009-02-05
hehe often you have to change the wording for google to understand what you mean.

If it isn't on the first page try another combination of words. :)

---

