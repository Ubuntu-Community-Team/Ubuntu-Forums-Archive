---
title: "[SOLVED] xkcd downloader"
date: 2008-07-23
forum: Programming Talk
---

### Post by king vash on 2008-07-23
so I make a sh script to download all the xkcd webcomics, but it only downloaded by file name so I added a counter in front of the file name.
I really want the format to be 1_name_morename.jpg but to get the number and file name I use ```
mv $name $i.$name 
``` if i use ```
mv $name $i_$name
``` it thinks it is one variable name. Help, suggestions, comments anything. 



ORIGINAL CODE
```
#!/bin/sh

cd /home/king3/Pictures/webcomics/XKCD/

i=1;
while [ $i -lt 450 ]
do
	wget http://xkcd.com/$i/
	url=`grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f2`	
	name=`grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f2 | cut -d\/ -f5`
        alttext=`grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f6`
	wget -N $url

	mv $name "$i"_"$name"+"$alttext"
	rm index.html
	i=`expr $i + 1`
done

```

Explanation of the grep | head | cut
[CODE]# the grep return the entire <img src=" line

# <img src="http://imgs.xkcd.com/comics/tree_cropped_(1).jpg" title="'Petit' being a reference to Le Petit Prince, which I only thought about halfway through the sketch" alt="Petit Trees (sketch)" /><br/> <h3>Image URL (for hotlinking/embedding): http://imgs.xkcd.com/comics/tree_cropped_(1).jpg</h3>

#by adding the "| head -1" we get one line of html

#<img src="http://imgs.xkcd.com/comics/tree_cropped_(1).jpg" title="'Petit' being a reference to Le Petit Prince, which I only thought about halfway through the sketch" alt="Petit Trees (sketch)" /><br/>

#by adding the "cut -d\" -f2" we find the second instance of text seperated by two quote marks

#http://imgs.xkcd.com/comics/tree_cropped_(1).jpg

#the second cut filters to the image name

#tree_cropped_(1).jpg[

#to get the alt text  "cut cut -d\" -f6" will probable work
/CODE]

---

### Post by ad_267 on 2008-07-23
You can use:
```
mv $s "$i"_"$s"
```

And can you post the final script when you're done? That could come in handy.

---

### Post by Tuna-Fish on 2008-07-23
Do remember that the tagline in many xkcd comics is in the alt-text. How do you plan to package that with the images?

---

### Post by blackaj on 2008-07-23
if u use FF3 try OutWit Hub (its an addon)
it automatically detects the next pages and you can download pictures in a bunch (i have just tried on xkcd.com and it really works!!!^^) or if u want there is also a scraper widget
[https://addons.mozilla.org/en-US/firefox/addon/7271](https://addons.mozilla.org/en-US/firefox/addon/7271) or [www.outwit.com](www.outwit.com)

---

### Post by king vash on 2008-07-23
thank you ad_267 I will try that and see if it works.

Tuna-Fish - I would really like a tuna fish sandwich right now. I can use a different grep \ head \ cut for that it would be pretty easy to as alt text are between quotes


blackaj - I have used an add-on similar to the one your describing but my real purpose is to make about ten of these that download all my favorite webcomics once a week, and having to do any work other than type something like "sh sh\UpdateComics" in console sounds to hard.

next question 


you might notice that the variable "name" is similar to "url" but with a second cut command. this next command will spit out the name of the file 
```

echo $url | cut -d\/ -f5

```
but when I try to set the variable "name" equal to that it always fail
```

echo this doesn't work
name=`$url | cut -d\/ -f5`
echo $name
echo neither does this
name=$($url | cut -d\/ -f5)
echo $name

```
what is the proper formatting syntax to get the command substitution to work?

---

### Post by king vash on 2008-07-23
Almost final code
it is worth a cookie if someone can merge the two name= lines togethor
```
#!/bin/sh

cd /home/king3/Pictures/webcomics/XKCD/

i=1;
while [ $i -lt 453 ]
do
	wget http://xkcd.com/$i/
	url=$(grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f2)	
	file=$(echo $url | cut -d\" -f2 | cut -d\/ -f5)
	alttext=$(grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f6)	
	name=${file%_(1).jpg}
	name=${name%.jpg}.jpg
	wget $url
	mv $file "$i"_"[""$alttext""]"_$name
	rm index.html
	i=`expr $i + 1`
done

```

---

### Post by nanotube on 2008-07-23
a somewhat off-topic comment: thanks for reminding me to catch up on some xkcd :)

---

### Post by blackaj on 2008-07-24
king vash, it was just that there is nothing to type in the consol, just tell the program save the files in ur harddisk and browse till the end, you'll see it's better than programming(anyway it's my opinion)

---

### Post by Yannick Le Saint kyncani on 2008-07-24
> **king vash said:**
> my real purpose is to make about ten of these that download all my favorite webcomics once a week, and having to do any work other than type something like "sh sh\UpdateComics" in console sounds to hard.

I use dailystrips, it knows how to download 676 strips (count made just now in hardy), xkcd being one of them.

The config file is especially easy, I call it once a day in cron and it makes a single html page with my daily strips (about ten of them).

It also keeps archive of previously downloaded strips, setup convenient links, ...

If you've been offline for an extensive period, it has a --date option so you can download the strips for that specific date. You just have to setup a loop to download the last ten days strips.

I've been using it since many years and am very happy about it :)

---

### Post by lobner on 2009-08-12
Slightly improved:
```
#!/bin/sh

cd /home/lobner/Desktop/XKCD/

i=1;
while [ $i -lt 623 ]
do
	wget http://xkcd.com/$i/
	url=$(grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f2)	
	file=$(echo $url | cut -d\" -f2 | cut -d\/ -f5)
	ext=$(echo $file | cut -d\. -f2)
	alttext=$(grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f6)
	titletext=$(grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f4)
	wget $url
	mv $file "$i"_"[""$alttext""] - [""$titletext""]".$ext
	rm index.html
	i=`expr $i + 1`
done
```

---

### Post by bmiller on 2010-07-08
A version in PHP (automatically displays today's XKCD on load). I modified a Dilbert version from TechDose.com


```

<?php
 // Define the URL we'll be pulling from
 $URL = "http://www.xkcd.com/";

 // Grab the full contents of the web page, 8192 bytes at a time until done
 $file = fopen("$URL", "r");
 $r = "";
 do {
    $data = fread($file, 8192);
    if (strlen($data) == 0) {
        break;
    }
    $r .= $data;
 } while (true);

// Define a Start & End location for the regular expression
$Start = 'imgs.xkcd.com/comics/';
$End = 'title';

// Grab the text between the Start & End location (ie. The picture name)
$stuff = eregi("$Start(.*)$End", $r, $content);

$todaysxkcd = "\"http://imgs.xkcd.com/comics/$content[1]";
echo "<center><img src=$todaysxkcd></center>";
?>

```

---

