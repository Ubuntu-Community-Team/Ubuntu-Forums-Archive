---
title: "Extracting variables from banshee database"
date: 2011-08-24
forum: Programming Talk
---

### Post by db579 on 2011-08-24
I'm trying to write a script that will take all the album cover art from banshee, which stores it all in one general folder (.cache/media-art) and uses the database banshee-1.db, and copy it into the appropriate folder in my actual music collection. 

I will probably attempt this in java and I basically want it to work like this:

```


START PROGRAM copyalbumart

$folderName
$albumArt
$bandName

openfolder .cache/media-art

foreach ($albumArt as $picture){
	$bandName =
	$folderName = 
	copy $albumArt
	open Music/$bandName/$folderName
	paste $albumArt
	close Music/$bandName/$folderName}

closefolder .cache/media-art

END PROGRAM copyalbumart


```

But I have no idea how to get the band name and album name variables from the banshee database. I think banshee uses sqlite3. How would I access the information? Thanks

---

### Post by dethorpe on 2011-08-24
Can't give a full solution but a few ideas, banshee does use sqlite3 for the database.
 
1) Could use sqlite3 command line to run queries against the database from within your program. 
 
2) Use java JDBC and a SQLlite driver/wrapper in your program (see here for a list: [http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers](http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers))
 
3) Use perl instead and DBI & DBD::SQLite CPAN modules for whole script to scan art directory and query database to do what you want. (my personal favorite option)
 
 
This blog has a bit of info on the database structure: [http://isching.wordpress.com/2009/07/27/howto-export-ratings-information-from-banshee/](http://isching.wordpress.com/2009/07/27/howto-export-ratings-information-from-banshee/)
 
Should be able to google for more info on the DB structure to figure out the querys you will need to get the band and album names.
 
Hope that helps get you started.

---

### Post by aeiah on 2011-08-24
use java's sqlite stuff. ive done a similar thing for xbmc's database using python to generate an html film library list.

you might find it useful to poke around in the database with sqlitebrowser whilst you write your program so you can see how things are layed out in the db.

---

### Post by db579 on 2011-08-25
Thanks for both your responses that's pretty much what I want to do I don't really have any experience using databases though. aeiah, any chance you still have the code you wrote for that library list and don't mind sharing? Would probably help me get started.

Thanks

---

### Post by DouglasAWh on 2011-12-16
> **aeiah said:**
> use java's sqlite stuff. ive done a similar thing for xbmc's database using python to generate an html film library list.

you might find it useful to poke around in the database with sqlitebrowser whilst you write your program so you can see how things are layed out in the db.

I too would be interested in seeing this code. I don't want to do pictures, I want to extract licence info but I still think it would get me going. I would be happy to start my own thread if that is best (and will likely end up doing that in a couple weeks if not response here).

---

