---
title: "displaying images stored in a mysql blob via php"
date: 2007-03-24
forum: Programming Talk
---

### Post by nandasunu on 2007-03-24
Hi, I have a database with images stored as blobs. I want to be able to download them and display them as a part of a webpage (in <img> tags).

So far I have figured out how to download and create the jpeg, but how do I get this to display as part of a webpage? The code I have displays the image, but doesn't give me any control over it, it stops anything else being displayed and just shows the image.

Heres my code:

[PHP]$result = mysql_query("select cover from Movies where movie_id=4");
$row = mysql_fetch_row($result);
		
$data = base64_decode($row[0]);
		
$im = imagecreatefromstring($row[0]);
imagejpeg($im);[/PHP]

and here is a live example of it: [http://uae-eyes.com/efilm/test.php](http://uae-eyes.com/efilm/test.php)

Also, I would like to be able to resize the image and create thmbnails, if possible.

---

### Post by Mirrorball on 2007-03-24
Just output the correct headers and the image:
```

header('Content-type: ' . $mime); // 'image/jpeg' for JPEG images
echo $data;

```Suppose this code is in image.php. On the page you want to display the image:
```

<img src="image.php" alt="cover" />

```

---

### Post by nandasunu on 2007-03-24
thanks for the help :)

---

