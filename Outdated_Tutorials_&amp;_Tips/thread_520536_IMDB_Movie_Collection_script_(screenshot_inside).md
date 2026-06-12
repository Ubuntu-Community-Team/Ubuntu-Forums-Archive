---
title: "IMDB Movie Collection script (screenshot inside)"
date: 2007-08-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Yuzem on 2007-08-08
This script will automatically generate a shelf from your imdb firefox bookmarks and it will create categories from the respective folders.

Here is the screenshot:
[[IMG]http://img461.imageshack.us/img461/6500/imdbmoviecollectionwl9.th.png[/IMG]](http://img461.imageshack.us/my.php?image=imdbmoviecollectionwl9.png)


**Installation and Usage**
It only needs image-magick:
```
sudo apt-get install imagemagick
```
Then uncompress it and from the terminal run the file "imdb-movie-collection" It will generate the html file in the same folder.

To run the script you can drag it to the terminal and press enter or from the terminal, go to the script folder and type:
```
./imdb-movie-collection
```

To set a custom cover for a movie run the script with the movie URL as the fist argument and the path to the image as the second.
Example:
```
./imdb-movie-collection http://www.imdb.com/title/tt0093437/ /path2image/image.jpg
```


**Uninstall**
Just delete the script folder.

---

### Post by pt123 on 2007-08-11
Thanks that is very neat.

Do you have links to other places where one might find useful scripts that use the imagemagick libraries.

---

### Post by Yuzem on 2007-08-11
I have one to another script that I made:
[http://ubuntuforums.org/showthread.php?t=486359](http://ubuntuforums.org/showthread.php?t=486359)
I hope you like it.

---

### Post by Yuzem on 2007-08-14
Ok, the script wasn't working... at least for me.
Now it is fixed, I hope...
Please report if there is any problem.

---

### Post by nikoPSK on 2007-11-12
cool! Thanks alot.

---

