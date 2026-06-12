---
title: "Need PHP help"
date: 2006-12-02
forum: Programming Talk
---

### Post by votresivain on 2006-12-02
I don't know if this is the right place for this, but I have had terrible luck with any forums on any topic other than ubuntuforums.org so I thought I'd give it a try, so if this is not topic-worthy, feel free to discard.

I am trying to write a PHP image gallery for my uncle's website. I am using the [Hoverbox Gallery]("http://sonspring.com/journal/hoverbox-image-gallery"), adding [Lightbox v2]("http://www.huddletogether.com/projects/lightbox2/"), and implementing the [Slim PHP script]("http://slim.climaxdesigns.com/tutorial.php?section=slim&id=12") that makes the gallery dynamic by searching a directory and automatically generating the images. I got all of the above working together without any problem.

Unfortunately the dynamic script only works well with a small amount of images. I have approximately 200 images and want to break it down to 15 images per page. The second bad thing is I am very new to PHP and am really just learning as I go along and looking at other people's scripts and reading the PHP manual. So this is proving to be a very difficult project.

Here's the Slim script, if there are any PHP gurus out there with some free time, please feel free to take it and implement automatic pagination. I have no access to MySQL or any other databases so that is out of the question as well.

[php]
<?php 
function createGalleryPage($path){
echo "<ul class=\"gallery\">";
  if (($dir = opendir("$path"))){
  // loops through while the readdir function returns true.
    while (false !== ($file = readdir($dir))){
    // picks only valid filenames
      if ($file != "." && $file != ".." && !is_dir($file)){
      // echos to the client a nice unordered list of images
      echo
      "<li>".
      // using the rel=lightbox is optional
      "<a href=\"".$path."/".$file."\" rel=\"lightbox\">
      <img src=\"".$path."/".$file."\" alt=\Generic alt description\" 
      width=\"40\" border=\"0\" />
      </a>".
      "</li>";
      }
    }
  }
echo "</ul>";
}
?>
[/php]

I appreciate any suggestions, thoughts, questions, etc. Thanks!

---

### Post by Verminox on 2006-12-03
It will be very easy to this via MySQL... and I'm no expert with filesystems.

However, I can suggest a method that will work, but it won't save any resources, i.e it will display only 15 per page... but each search will have to go through all 200 images in the script anyway.

The trick is... instead of a while loop... make it a for loop.

```
for ( $i=1; false !== ($file = readdir($dir)); $i++ ){ 
```

The loop will function the same, but now in each iteration you can associate the file with a unique id. To avoid this ID being given to the '.' and '..', just decrement the iterator ($i--;) during that loop so that the next iteration will contain the same unused ID.


Now that you have an ID for each file... it will be very easy to customize the list according to a page number variable, which is probably got via $_GET. 

eg. for Page 3... you only have to show items 31-45... 

```
$last = $page_no * 15;
$first = $last - 14;
```

Now only echo those with IDs such that $first <= $i <= $last.

---

### Post by votresivain on 2006-12-03
Thank you very much for your reply! I will definitely give that script a try and report back with my results.

Another question is if I do choose to switch hosts and get access to MySQL, can that be as dynamic? How do I go and get the images from the directory into the database? Usually I am a Google Guru with questions I have but this problem has really been eluding me, due greatly to my lack of general knowledge of PHP.

If there are any decent PHP/MySQL image gallery tutorials that you could link me to, that would be a great help. Thanks again.

---

### Post by johnnymac on 2006-12-03
So if your going to make this dynamic with MySQL you'd simply create table(s) of the images locations and keep it up to date.  In the PHP code you'd simply query the database however you wanted to for a given page, get the result-set returned and display the images - thus dynamic display of images.  There's a TON of examples|how-to's on there but report back if you need any further help.

---

### Post by votresivain on 2006-12-03
Johnny, thanks for the input as well, I will look further into how to use this method. Unfortunately my knowledge of MySQL is even less than that of PHP and though I love scraping Google and finding out all I can, any tips in the right direction (tutorials, sample scripts I can analyze, etc.) would be appreciated!

---

### Post by johnnymac on 2006-12-03
Here you go...

One stop shopping for enough PHP|MySQL tutorials to get you into trouble.

Welcome to the land of PHP|MySQL - the world couldn't exist without it :mrgreen: 

[http://www.php-mysql-tutorial.com/](http://www.php-mysql-tutorial.com/)

---

### Post by slavik on 2006-12-03
Or you can read the images in as a string of bytes (or hex) and store that as a varchar in MySQL, then read it back and convert it.

---

### Post by Verminox on 2006-12-04
slavik: That will be an utter waste of resources. Why increase the size of the database and make it hard to query... when you can easily just store filenames in the database and only open the images as required?

votresivian: Yes MySQL will indeed make life much easier for you. Organizing your data into databases is much easier to work with than raw files.

[Hudzilla](http://hudzilla.org/phpwiki/index.php?title=Databases) was where I picked up PHP and MySQL so you can give that a try.

---

### Post by votresivain on 2006-12-04
How would be the easiest way to get the filenames of 200 images into a table? Would I use a PHP script for this? If so, what might that look like? 

Despite the very helpful links provided (I have bookmarked both of them) I can't find a simple way of doing it without using albums/subdirectories.

I am just looking for a way to store individual images and now since I will be using a database maybe a description and image name as well.

I am going to continue looking and see if I can find an example tat I can modify as well. Thank you.

---

### Post by Verminox on 2006-12-04
You will need to make a database table... with fields such as ID, filename, description, etc.

Take a look at the ORDER BY and LIMIT keywords in SQL queries to find out how to sort items and limit to only a few.

I had posted a tutorial on simple MySQL pagination on [this site](http://pixeldepth.net/tutorials/2/1156944241/Simple_Pagination_with_MySQL/)... but if you are enthusiastic about learning then try figuring it out yourself after learning to query with SQL.

---

### Post by votresivain on 2006-12-04
I am very interested in learning on my own and am actually discovering quite a bit so far.  I have read several things about how to query and limity from the images I will store in the table. The one thing I am having trouble finding is how to go through my directory and stash the image names in a table in my database.

Would you do this through usage of PHP's opendir and readdir functions and with each result, use an insert command for MySQL? I am trying to think of the most efficient way to construct this.

All the articles I have read are how to create a PHP upload page which is fine, but not very efficient with 200+ images. So I tried searching for how to upload an entire directory but could not find out how to do that either. I have gathered quite a lot of info regarding how to display and limit and page my results but cannot find anything suitable for inserting my large amount of images into the database.

---

### Post by Verminox on 2006-12-04
Yeah you can run a script like "UpdateTable.php" which basically goes through your image dir and adds all the images to the table by using INSERT queries inside a loop.

If you are going to be adding images to that directory yourself by hand, it may be a good idea to save this script to run it later each time you edit the directory.

If you are going to have an upload form later on, make sure to ad d an entry to the database each time an image is uploaded successfully.

---

