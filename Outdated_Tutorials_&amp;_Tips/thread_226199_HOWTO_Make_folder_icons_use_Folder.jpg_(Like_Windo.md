---
title: "HOWTO: Make folder icons use Folder.jpg (Like Windows XP My Music folder does)"
date: 2006-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by NinjitsuStylee on 2006-07-30
The purpose of this thread is to give you a quick and easy method to make your music folders use the Folder.jpg file to display album covers instead of the default folder icon.  Windows XP does this automatically for your folders if you have a Folder.jpg file in the folder.

Here is a screenshot:

[IMG]http://netfiles.uiuc.edu/adesai2/www/Screenshot.png[/IMG]

Now then...

This is actually not that great of a HOWTO, but it gives you some insight on how nautilus works :)

Here's a few things for you to learn:[LIST=1]
[*]Nautilus stores metadata (xml files) in a folder called ~/.nautilus/metafiles and the specific file we will be looking for will be the file that is associated with your music folder.  Also, the files' names are encoded using URI encoding so things are a bit goofy.  For example, I have my music folder in a folder called /media/fat/My Music (yea yea, I know, spaces are bad in unix filesystems, sue me :) ).  My .xml file is going to be called file:%2F%2F%2Fmedia%2Ffat%2FMy%2520Music.xml
[*]Basically this file needs to be edited appropriately to reflect whatever changes you want.  Make sure that all the edits are done on line 2 (for some reason nautilus likes to jumble up all the file data in one line).
[*]I used a PHP script to do this, but you can use any type of script to make the edits (details on how I did this below).
[*]**THE KEY:** Once you've made the edits, you need to restart nautilus with the following command:[/LIST]```
nautilus -q
``` 
Gnome will automatically restart nautilus for you.  Note:  When you go to your music folder to see the changes, it might eat up some of your CPU depending on how many folders you have....it has a lot of icons to display :)


[B]DETAILS:

[/B]Ok, here's what I did.  First I went to my music directory and made a text file of all of my folders using the following commands (things in capitals means use some common sense :) ):

```
cd /NAVIGATE/TO/YOUR/MUSIC/DIRECTORY
ls > music.txt
``` 
That should make a nice text file, seperated by linebreaks (\n) for the next step.

The next step:  Make your script.  Since I am comfortable with PHP I used PHP and executed the file using the command line (make sure you have the appropriate packages to run php files from the commandline......php-cli or something):

 ```
php icons.php > /home/aashay/.nautilus/metafiles/YOURMETAFILE.xml

``` Again, since my Directory is called /media/fat/My Music, my file was called file:%2F%2F%2Fmedia%2Ffat%2FMy%2520Music.xml

(Note: If you are having trouble finding your metafile, make some changes by hand to your music directory, ie maybe replace one of the folders, or change the view of it.....then navigate to the .nautilus/metafile directory and organize it by dates modifed, you should see the appropriate file as being one of the most recent ones modified)


Finally, here is my PHP code.  It's a bit disgusting and noob but that's because I catered it specifically to my own setup, so don't forget to tailor it to your own setup.  Again, you can use any sort of script that loops through a list of your music folders and outputs the data in the following format:

```
<file name="THE FOLDER WHOSE ICON YOU ARE MODIFYING" timestamp="UNIXTIMESTAMP" custom_icon="ICON NAME SUCH AS FOLDER.JPG"/>  
``` 
Again, use some common sense and replace all the appropriate stuff :)

So here is my code:
```

<?php

/*
    Used in conjunction with nautilus metafile for music folder Folder.jpg replacement!
*/

 $time = mktime();
$dir = "/media/fat/My Music/";

$filename = $dir . "music.txt";

$handle = fopen($filename, "r");
$contents = fread($handle, filesize($filename));
fclose($handle);

$lines = explode ("\n", $contents);



echo "<?xml version=\"1.0\"?>\n<directory>";
foreach ($lines as $value)
{
    if ($value)
    {
        //replace special characters.....this is kind of a dumb way to do things, I bet a more leet php coder would be able to find a better function to do this
        $newval = str_replace(" ", "%20", $value); //replace spaces
        $newval = str_replace(",", "%2C", $newval); //i have some commas in my album names
        $newval = str_replace("&", "%26", $newval); //i noticed an ampersand (&) in certain album titles such as Outkast - Speakerboxxx & The Love Below 
        
        
        $filename = $dir . $value . "/Folder.jpg";
        $time = mktime(); //Unix time!
        if (file_exists($filename)) //we only want to do this if there is actually a Folder.jpg file in there
        {
            $size = filesize($filename);
            if ($size && $size < 1048576) //if the Folder.jpg file is too big we might have problems, so lets limit it to 1 MB
            {
                echo "<file name=\"" . $newval . "\" timestamp=\"". $time . "\" custom_icon=\"Folder.jpg\"/>";
                        
            }
        }//end if statment: file_exists

    }
}  //end foreach

echo "</directory>\n";
clearstatcache(); //not really sure if we need this
exit ();

 ?>



``` 
Finally make sure to restart nautilus with:

```
nautilus -q
``` 
Load up your music directory and you should be good to go!  Again, sometimes it takes forever to load the directory (I do believe they are working on a fix that makes nautilus more efficient when it comes to icons).


If anyone wants more details or would like me to do more work for them along the lines of the php script and such, let me know and I'll make things more automagic when I have time.  Otherwise, have fun! ;-)

---

### Post by chikko on 2007-02-08
hey
i tried to follow your post, but couldn't make it..
is there any way you could (please) clearify the commands a total noobie should make in order to make my music folder much much nicer?..
i recently moved my music folder to a new USB external drive - and unfortunately everytime i plug it out and then in again the icons are resetted to the default one - and all of my work in changing them to the album covers is ruined.. :(

hopefully you could help :)
chikko.

---

### Post by spockrock on 2007-02-08
two things, you forgot to do;
```
chmod 755 icons.php 
```
to make it executable and;
```
sudo apt-get install php5-cli 
```
is that package required


Also can you make it so that its case insensitive like folder.jpg =! Folder.jpg, because other wise I have to go change alot of my Folder.jpg to folder.jpg.....just asking because I am lazy.....otherwise everything works perfectly.

---

### Post by MetalMusicAddict on 2007-02-08
Can this be cleaned up a little? Im having a time following it. Also does this work On subfolders?

Im actually surprised it took this long to get responses and me to see this thread. :)

EDIT: Yeah. Im sorry. This is really messy and I cant follow half of this.

[LIST]
[*]Where does the php code go? "music.txt" or "/home/user/.nautilus/metafiles/YOURMETAFILE.xml"
[/LIST]

I think this could be a awesome How-To it just needs some work on the order and locations of things.

---

### Post by spockrock on 2007-02-08
ok this is how I first did it.
open terminal, install the necessary php if you do not have it
```

sudo apt-get install php5-cli
gedit icons.php

```
and pasted the following into gedit;
```

<?php

/*
    Used in conjunction with nautilus metafile for music folder Folder.jpg replacement!
*/

 $time = mktime();
$dir = "/home/redemma/Multimedia/Music/Hardcore, Metal & Screamo/"; **//this is the music directory you wanna change**

$filename = $dir . "music.txt";

$handle = fopen($filename, "r");
$contents = fread($handle, filesize($filename));
fclose($handle);

$lines = explode ("\n", $contents);



echo "<?xml version=\"1.0\"?>\n<directory>";
foreach ($lines as $value)
{
    if ($value)
    {
        //replace special characters.....this is kind of a dumb way to do things, I bet a more leet php coder would be able to find a better function to do this
        $newval = str_replace(" ", "%20", $value); //replace spaces
        $newval = str_replace(",", "%2C", $newval); //i have some commas in my album names
        $newval = str_replace("&", "%26", $newval); //i noticed an ampersand (&) in certain album titles such as Outkast - Speakerboxxx & The Love Below 
        
        
        $filename = $dir . $value . "/folder.jpg"; **//changed Folder.jpg to folder.jpg**
        $time = mktime(); //Unix time!
        if (file_exists($filename)) //we only want to do this if there is actually a Folder.jpg file in there
        {
            $size = filesize($filename);
            if ($size && $size < 1048576) //if the Folder.jpg file is too big we might have problems, so lets limit it to 1 MB
            {
                echo "<file name=\"" . $newval . "\" timestamp=\"". $time . "\" custom_icon=\"folder.jpg\"/>"; **//again changed Folder.jpg to folder.jpg**
                        
            }
        }//end if statment: file_exists

    }
}  //end foreach

echo "</directory>\n";
clearstatcache(); //not really sure if we need this
exit ();

 ?>

```

note the difference in our folders, and I use folder.jpg instead of Folder.jpg. so make the appropriate changes, save and exit, ** I have put bold comments to areas of the script I have edited **

```
chmod 755 icons.php
```

Now cd to your music directory, and then create a list of folders, so I did this;
```
cd ./Multimedia/Music/Hardcore\,\ Metal\ \&\ Screamo/
ls > music.txt
```

this should create the music.txt in your music folder for me its just where I keep all my metal and hardcore cds. now the final step is to run icons.php so from here; or from home, thats what I did; just make sure you use your metafile, and not exactly what I do in the second line.  if your run from your music folder make sure you put the full path to icons.php!

```
cd ~/
php icons.php > /home/redemma/.nautilus/metafiles/file\:%2F%2F%2Fhome%2Fredemma%2FMusic%2FHardcore%252C%2520Metal%2520%2526%2520Screamo.xml
nautilus -q
```

go to the directory and viola!

---

### Post by MetalMusicAddict on 2007-02-08
Ok. I got it working. I need to make it work with subfolders somehow. I have my music organized "Artist/Album/file.mp3". So if theres nothing to /Artist I get no picture.

Is there a way to make subdirs also get scanned? So it picks up the image in "Artist/Album/cover.jpg"?

---

### Post by Ahriman on 2007-02-09
> **MetalMusicAddict said:**
> Ok. I got it working. I need to make it work with subfolders somehow. I have my music organized "Artist/Album/file.mp3". So if theres nothing to /Artist I get no picture.

Is there a way to make subdirs also get scanned? So it picks up the image in "Artist/Album/cover.jpg"?

There is a way to do it, but it involves making a function and doing recursive calling to that function if it detects a directory. Something like:

if (is_dir($value)){ cd_to_dir_and_call_function_again; }

might be needed. I'll work on this when I get home, and post my results (if I get any) :)


EDIT: also, this could be a slight problem. I have my music directories arranged similar to yours, and this is what I see when doing a list of them recursivley:

Korn
-- Life is Peachy
-- --  folder.jpg
-- -- (rest of songs)
-- Follow The Leader
-- -- folder.jpg
-- -- (rest of songs)
-- Take A Look In The Mirror
-- -- folder.jpg
-- (rest of songs)

so which folder.jpg do we use on the /Korn folder?

I think if we can get this script to be recursive, so that it would pick up into the .xml file the sub dirs like the three I list above, then all that needs doing is put an artist image into the /Artist dir, and go from there. Does that sound like a plan?

---

### Post by Ahriman on 2007-02-09
Below is my updated code. This version takes out the need for the first step (cd /YOUR/MUSIC/PATH | ls > music.txt) as it searches for all directories and finds the ones that contain a "folder.jpg" file inside. All that you need to do it change the $dir path as instructed in the first few lines.

This is only a change to the PHP code; all other steps remain the same.

It appears to create a proper xml listing, but for some reason I cannot get nautilus to show the folder icons correctly. I'm sure it's my setup, as the original instructions didn't work for me as well. Either way, let me know if there are any problems with the below code.

Also note: this assumes that the file name is "folder.jpg" I was unable to get it to differentiate between "Folder" and "folder". PHP sees both as the same o.O

[PHP]<?php
/*
	Used in conjunction with nautilus metafile for music folder folder.jpg replacement!
*/

$delim = strstr(PHP_OS, "WIN") ? "\\" : "/";
$time = mktime();
$dir = "/media/music"; // YOUR MUSIC PATH GOES HERE ... NO TRAILING SLASH 

echo "<?xml version=\"1.0\"?>\n<directory>\n";

function retrieveTree($path)  {
    global $delim;
    global $time;

    if ($dir=@opendir($path)) {
        while (($element=readdir($dir))!== false) {
            if (is_dir($path.$delim.$element) && $element!= "." && $element!= "..") {

					$newval = str_replace(" ", "%20", $element); //replace spaces
					$newval = str_replace(",", "%2C", $newval); //i have some commas in my album names
					$newval = str_replace("&", "%26", $newval); //i noticed an ampersand (&) in certain album titles such as Outkast - Speakerboxxx & The Love Below 

					$dirname = $path.$delim.$newval;
					
					$newdir = str_replace("/", "%2F", $dirname);
					
					if(file_exists($dirname.$delim.'folder.jpg') && (filesize($dirname.$delim.'folder.jpg') < 1048576)){
						echo "<file name=\"$newdir\" timestamp=\"$time\" custom_icon=\"folder.jpg\"/>\n";
					}

					$array[$element] = retrieveTree($dirname);
            }
        }
        unset($parent);
        closedir($dir);
    }
    return (isset($array) ? $array : false);
}
retrieveTree($dir);
echo "</directory>";

?> [/PHP]

---

### Post by MetalMusicAddict on 2007-02-09
Thanx for the effort. The new code didnt work for me. :( I hope we can get this sorted out. I think this is a great feature for music lovers if we can work it out. :)

Maybe this could even be made into a little app? I know a python programmer. :) Something simple like defining the root dir of your music and it does the rest?

---

### Post by Ahriman on 2007-02-09
I looked through my code and fixed the problems, however, there is something that I have found that makes my contribution abit pointless in the end.

I fixed up the output so that nautilus will actually find and use the folder.jpg files from the directories that are in the folder you define (in my example it is /media/music/). However, when I define in that .xml file a sub-dir, it doesn't work.

I think that in order to have the album covers on sub directories, the script needs to be run on each and every artist in your music collection, and for those with massive collections .... thats a loooooong time.

I'll keep trying to refine the code so that it will let nautilus use the folder.jpg's with sub directories. I post my current code below in case anyone smarter than me see's the problem :)

[PHP]<?php
/*
    Used in conjunction with nautilus metafile for music folder folder.jpg replacement!
*/

$delim = strstr(PHP_OS, "WIN") ? "\\" : "/";
$time = mktime();
$musicpath = "/media/music"; // YOUR MUSIC PATH GOES HERE ... NO TRAILING SLASH 
$dirstripcnt = strlen($musicpath)+1;
echo "<?xml version=\"1.0\"?>\n<directory>\n";

function retrieveTree($path)  {
    global $delim;
    global $time;
    global $dirstripcnt;

    if ($dir=@opendir($path)) {
        while (($element=readdir($dir))!== false) {
            if (is_dir($path.$delim.$element) && $element!= "." && $element!= "..") {

                    $newval = str_replace(" ", "%20", $element); //replace spaces
                    $newval = str_replace(",", "%2C", $newval); //i have some commas in my album names
                    $newval = str_replace("&", "%26", $newval); //i noticed an ampersand (&) in certain album titles such as Outkast - Speakerboxxx & The Love Below 

                    $dirname = $path.$delim.$newval;
                    
                    $newdir = substr($dirname,$dirstripcnt);
                    
                    if(file_exists($dirname.$delim.'folder.jpg') && (filesize($dirname.$delim.'folder.jpg') < 1048576)){
                    
                        echo "<file name=\"$newdir\" timestamp=\"$time\" custom_icon=\"folder.jpg\"/>\n";
                    }

                    $array[$element] = retrieveTree($dirname);
            }
        }
        unset($parent);
        closedir($dir);
    }
    return (isset($array) ? $array : false);
}
retrieveTree($musicpath);
echo "</directory>";

?>[/PHP]

The XML file that this creates looks like this:

```
<?xml version="1.0"?>
<directory>
<file name="Butterfingers" timestamp="1171060487" custom_icon="folder.jpg"/>
<file name="Vast" timestamp="1171060487" custom_icon="folder.jpg"/>
<file name="Zeromancer" timestamp="1171060487" custom_icon="folder.jpg"/>
<file name="Silverchair" timestamp="1171060487" custom_icon="folder.jpg"/>
<file name="Miscellaneous" timestamp="1171060487" custom_icon="folder.jpg"/>
<file name="Kittie" timestamp="1171060487" custom_icon="folder.jpg"/>
<file name="Korpiklaani" timestamp="1171060487" custom_icon="folder.jpg"/>
<file name="Godsmack" timestamp="1171060487" custom_icon="folder.jpg"/>
<file name="Prodigy/Miscellaneous" timestamp="1171060487" custom_icon="folder.jpg"/>
</directory>
```
In the above, only the last entry (Prodigy/Miscellaneous) does not have the image displayed.

---

### Post by MetalMusicAddict on 2007-02-09
Ill try it. Im not worried about the time. Ill let you know 1000 folders worth of CDs takes. :) Goes off to try.

---

### Post by MetalMusicAddict on 2007-02-09
I cant get it to work on the root music dir. Just for fun I ran it on a artists folder itself and it seems to choke on folders with spaces in them. Editing the .XML file to add the other folders doesnt work either.

```
<?xml version="1.0"?>
<directory>
<file name="Leviathan" timestamp="1171063155" custom_icon="cover.jpg"/>
<file name="Lifesblood" timestamp="1171063155" custom_icon="cover.jpg"/>
<file name="Remission" timestamp="1171063155" custom_icon="cover.jpg"/>
<file name="Blood Mountain" timestamp="1171063155" custom_icon="cover.jpg"/>
<file name="Call Of The Mastodon" timestamp="1171063155" custom_icon="cover.jpg"/>
<file name="Live 2003 Tilburg Netherlands" timestamp="1171063155" custom_icon="cover.jpg"/>
<file name="Live Club Quattro - Osaka, Japan" timestamp="1171063155" custom_icon="cover.jpg"/>
</directory> 
```

The the code might need something added for the spaces.

Something has changed between the original script and your last. I think the original one handled the spaces. I do have a couple of folders that do have a image in them. Before the ones with spaces showed. Now they do not. If I posted the .XML for the root folder of my music it would show this as well. Nothing with a space in it.

---

### Post by zerwas on 2007-02-09
I think we really need an easy way to do this! :)
Anyone has the same opinion? We should create a feature request for this.

---

### Post by spockrock on 2007-02-09
I am not surprised that it was not incorporated into gnome already.....

---

### Post by MetalMusicAddict on 2007-02-09
Maybe some crap IP infringement?

---

### Post by spockrock on 2007-02-10
I thought it was in mac osx as well cover.*, oh well.... btw so I had to go through about 500+ metal albums and fix the 100 something Folders.jpg to folder.jpg, so this would work, and damn it took a long time... hahahha, I am sure I could of wrote a script but meuh...

---

### Post by barney_1 on 2007-02-10
Hmmm... write a script or change 100 captial Fs by hand... it's a toss up.

I'm running Kubuntu and am new to the KDE desktop.  How much work do you think I'd have to go through to adapt this method for KDE?  It's a pretty nice feature, I appreciate the work you guys are putting in on it.

---

### Post by fifo on 2007-03-27
Well this is something that I'd quite like to do, but I can't stand php (sorry) and I wanted to have a go at fixing some of the shortcomings, so I've written my own version in python.

This should handle spaces in directory names (as well as other strange characters, but nautilus' quoting rules seem rather obscure, so maybe there are things I've missed here).

You can specify your own shell-type pattern (--names) for matching the image filename (the default is "[Ff]older.jpg").

There is also a switch (-R) to make it work recursively across nested directories.

Download: [ATTACH]28357[/ATTACH]

```
$ python custom_icon.py --help
usage: custom_icon.py [options] folder [folder2 ...]

options:
  --version        show program's version number and exit
  -h, --help       show this help message and exit
  --names=NAMES    specification to match image filenames [default:
                   "[Ff]older.jpg"]
  -R, --recursive  set icons for folders recursively

$ python custom_icon.py ~/music
/home/user/music ...
done.

$ nautilus -q
```

---

### Post by TeKniKal on 2007-06-07
> **fifo said:**
> Well this is something that I'd quite like to do, but I can't stand php (sorry) and I wanted to have a go at fixing some of the shortcomings, so I've written my own version in python.

This should handle spaces in directory names (as well as other strange characters, but nautilus' quoting rules seem rather obscure, so maybe there are things I've missed here).

You can specify your own shell-type pattern (--names) for matching the image filename (the default is "[Ff]older.jpg").

There is also a switch (-R) to make it work recursively across nested directories.

Download: [ATTACH]28357[/ATTACH]

```
$ python custom_icon.py --help
usage: custom_icon.py [options] folder [folder2 ...]

options:
  --version        show program's version number and exit
  -h, --help       show this help message and exit
  --names=NAMES    specification to match image filenames [default:
                   "[Ff]older.jpg"]
  -R, --recursive  set icons for folders recursively

$ python custom_icon.py ~/music
/home/user/music ...
done.

$ nautilus -q
```

Works quite well, but it doesn't work for folders with an exclamation mark in them, I guess. Anyhow, I ran it on my music folder, and the folder "Weird Al Yankovic - Polka Party!" didn't get a thumb. I will take a look at your source code when I have some time (and more experience with Python).

Already thanks for this script, ignoring this minor bug it works just great :-)

---

### Post by click4851 on 2007-08-04
I love this idea....but I have my collection setup using in WIN XP /media/artist/album/songs.xxx  with the album art in with the songs (folder.jpg style)  and the thumbs are sometimes 1,2,3, up to 4 little album covers per artist. If I were to move some to Ubuntu would these scripts duplicate that or would I just get 1 thumb per album ?

---

### Post by click4851 on 2007-08-05
bump

---

### Post by TeKniKal on 2007-10-21
> **click4851 said:**
> I love this idea....but I have my collection setup using in WIN XP /media/artist/album/songs.xxx  with the album art in with the songs (folder.jpg style)  and the thumbs are sometimes 1,2,3, up to 4 little album covers per artist. If I were to move some to Ubuntu would these scripts duplicate that or would I just get 1 thumb per album ?


You would get just one thumbnail (I also used similar schemes to group several volumes of the same album into one (when they all had different covers). But one could adapt this script to make it recognize such things, refactor a thumbnail and put output it as 'folder.jpg' (or folder.png to prevent interference with windows, as Windows only checks for JPG (and perhaps GIF, but certainly not PNG)).

Anyhow, I haven't taken the time yet to take a look at the script, but I feel I now have quite a steady base in Python to take a look at the litle bug I reported (and perhaps even take a look at your request, but I can't promise it will be soon).

For your problem I'd rather write a whole other script to combine different covers into one (my idea would be to extend the functionality of windows a bit: not limited to 4 covers, but certainly restrictable; ability to include or exclude certain files (e.g. allow 'folder01.jpg' but not 'disc.jpg' or 'back.jpg' and with other files the possibility to choose between an automatic-exclude, automatic-include). But hey, that's just me philosophizing :) I can promise you won't see such script from me before 2008.

---

### Post by Horizon on 2007-10-31
> **TeKniKal said:**
> You would get just one thumbnail (I also used similar schemes to group several volumes of the same album into one (when they all had different covers). But one could adapt this script to make it recognize such things, refactor a thumbnail and put output it as 'folder.jpg' (or folder.png to prevent interference with windows, as Windows only checks for JPG (and perhaps GIF, but certainly not PNG)).

Anyhow, I haven't taken the time yet to take a look at the script, but I feel I now have quite a steady base in Python to take a look at the litle bug I reported (and perhaps even take a look at your request, but I can't promise it will be soon).

For your problem I'd rather write a whole other script to combine different covers into one (my idea would be to extend the functionality of windows a bit: not limited to 4 covers, but certainly restrictable; ability to include or exclude certain files (e.g. allow 'folder01.jpg' but not 'disc.jpg' or 'back.jpg' and with other files the possibility to choose between an automatic-exclude, automatic-include). But hey, that's just me philosophizing :) I can promise you won't see such script from me before 2008. **OK. FInish reading this post and then see post below for a version that adds a "No Cover Art" icon to artist folders which contain no albums with cover art for consistency since it looks strange with dinky folder icons and colourful album art mixed in (it doesn't do it for the album folders inside though because since they'd all look like folders they'd already be consistent)**

I actually just had a go at this. It does Icons for both the albums and the artist folder. I don't really use bash much but I couldn't stand the thought of writing this kind of user script in PHP so here it is in bash. [color=blue][Preview image attached to this post][/color]

It's really basic and I only wrote it for my personal use. It won't destroy anything (only ever deleting the folder it created in /tmp), but I'd suggest backing up your ~/.nautilus/metafiles folder as it overwrites any files already existing for your music and artist folders (so any information for those folders like emblems or zoom memory will be overwritten).

It uses a tiny bit of perl to take advantage of Gnome VFS (because I couldn't figure out nautilus's way of escaping characters (it's not the same as normal URI escaping) so what better way than to tap into VFS directly) so make sure you have the libgnome2-vfs-perl package (Not sure if it's default or not but I'd be suprised if someone didn't already have this). You also need the imagemagick package. Because it uses VFS this means that it works on any folder nautilus can display, so basically every language you could possibly be using (which is the main reason I found myself writing this. the escaping in the howto totally ignored non-latin and even non-basic latin characters). 

So, if anyone wants to rewrite this script better, just steal the two lines of perl I used and get rid of any %0A (new line characters) VFS tries to add to the end of URIs as nautilus doesn't like those. It would probably be better if I had used perlmagick instead of the crippled command line tool but perl just looks like an even more evil version of C (well now I realise bash is evil...perl, not so much).

You basically run the script, passing it the path to your music folder [color=red]without the ending slash[/color]. Here's how it works:
> 
0. deletes any previous "/tmp/coverart_" folder

1. makes a list of every directory in your music folder and does a find inside them for folders which contain cover art meaning albums just sitting there in the music folder won't be recognised, they have to be inside another folder which the script will assume is an artist folder (defaults to cover.jpg, can change this near the top of the script, you'll see the comments)

2. creates hidden .icon.jpg thumbnails of your cover art in your album folders

3. generates the metafile for the artist folder in nautilus and saves it in /tmp, this holds a list of all album folders in it and the name of the icon file (.icon.jpg)

4. creates a ".icon.index" file in the artist directory which holds the paths for all the icon files in its sub-directories. In step 1 the script will skip directories with the .icon.index file inside them so if you need to redo a single folder just delete this file inside the artist folder to get the script to redo the folder. To redo all of them...well just do "for f in `find /<MUSICFOLDER HERE> -name .icon.index`; do rm "$f"; done" or something.

5. reads this file back in, counts how many there are and uses imagemagick to combine them into icons for the artist folder. If there are 4 or more it creates an icon of 4 tiled. If there are 2 or 3 it splits them vertically into strips starting from the left. And if there's one...well technically it does the same thing but since there's one it divides by 1 and you get the usual single image. Stores the full imagemagick command in .cmd files in the /tmp/coverart_ folder for debugging purposes.

6. generates and adds the xml file tag (i.e. the artist folder icons) to a file in /tmp for the artist folder

7. moves the metafile responsible for album icons to your ~/.nautilus/metafiles/ directory.

8. does steps 2 - 7  for every directory in your music folder.

9. moves the metafile for the artist icons into your ~/.nautilus/metafiles/


For anyone who happens to read this but didn't follow IT ONLY WORKS IF YOU HAVE THE FOLDER STRUCTURE "Artist/albums/".
```
So if your folder looks like:
/home/myuser/Music Folder/Artist Names
you would run:
/path/to/script/icongen "/home/myuser/Music Folder"
or:
/path/to/script/icongen ~/Music\ Folder
i.e. the usual bash escaping 
```

Here it is. Save it into a file and go nuts. Don't cringe too much, and I can't see how this script could go wrong but test it on something not your music folder first. It's pretty straight forward with the basic settings near the top so go wild :D
```


[color=red]**The code is in the next post**[/color]


```
THis is only tested with English, Chinese, Japanese and Korean. But the characters in those languages are pretty wild so I wouldn't worry too much.

---

### Post by Horizon on 2007-10-31
New version which adds a "No Cover Art" icon for artist folders with no albums with cover art so the music folder looks more consistent.

The old one wiped your old music folder configuration when you did as I suggested and deleted the .icon.index file for it to redo a folder (it appeared to work but then you'd get a music folder with only that one icon the next time nautilus restarted).That's fixed in this version (it uses the index file placed in the music folder which is what I meant to do in the first pace but forgot :p ).

With this one it has to redo the metafile for the root music folder every time it is run even if you're only redoing a single folder so don't think it is hanging or something, it is converting every folder name into a valid nautilus URI. Here it is for anyone who wants to try it or just take a look, it is quite a nest:
```
#!/bin/bash
ORIGIFS=$IFS
IFS=`echo -en "\n\b"`
UTIME=$(date "+%s") #unix time
TAB="	"
LINEBREAK="
"


########GENERAL SETTINGS

TMPDIR="/tmp/coverart_" #temporary folder used to store xml file and error log
BLANKIMG="$TMPDIR/blank.jpg"

LOGFILE="$TMPDIR/error.log" #error log file
touch $LOGFILE

OUTPUTDIR=~/.nautilus/metafiles/ #target directory for the resulting xml file
COVERFILE="cover.jpg" #cover image filename
ICONFILE=".icon.jpg" #folder icon file
INDEXFILE=".icon.index"

GENERAL_ICONSIZE=256 #standard dimension of all icons generated
ICONSPACING=0

FILEHEADER="<?xml version=\"1.0\"?>$LINEBREAK	<directory>$LINEBREAK"
FILEFOOTER="	</directory>\n"
LINESTART="		<file"
LINEEND="/>"
CODE_HANDLE="$FILEHEADER" #handle where generated album xml is stored
CODE="$CODE_HANDLE" #the generated album xml
CODE_HANDLE_="$FILEHEADER" #handle where generated artist xml is stored
CODE_="$CODE_HANDLE_" #the generated artist xml

SUCCESS=0
OUTPUT_DIV="------------------------------------------------"

######
#Make temporary directory
rm -R $TMPDIR
mkdir $TMPDIR

convert -background black -fill white -pointsize 45 -size 256x256 -gravity Center caption:'No Cover Art' "$BLANKIMG"

#Sanitise directory Path
TMPVAR=$*
FULLPATH="$TMPVAR/" #full path to root directory

######ROOT MUSIC FOLDER CODE INITIALISATION#########

TMPVAR_1=${FULLPATH%%/}
MUSICPATH="$TMPVAR_1"

TMPVAR_1=$(echo "$MUSICPATH" | perl -e 'use Gnome2::VFS; $path = <STDIN>; $uri = Gnome2::VFS -> make_uri_from_input($path); $escaped_uri = Gnome2::VFS -> escape_slashes($uri); print $escaped_uri;')
CLEANURI_="$TMPVAR_1" #full path to root in URI format

#Create temporary files
TMPXML_="$TMPDIR/$UTIME${MUSICPATH##\/*\/}.xml"
touch "$TMPXML_"

INDEXPATH_="$MUSICPATH/$INDEXFILE"

#######################

#Loop through
ARTISTLIST=$(find $FULLPATH* -maxdepth 0 -type d)
for ARTISTPATH in $ARTISTLIST
do
		if [ ! -e "$ARTISTPATH/.icon.index" ] #if index file doesn't exist
		then

	UTIME_=$(date "+%s") #unix time
	CODE_HANDLE="$FILEHEADER"

	TMPVAR_1=${ARTISTPATH%%/}
	CLEANPATH="$TMPVAR_1"
	
	TMPVAR_1=$(echo "$CLEANPATH" | perl -e 'use Gnome2::VFS; $path = <STDIN>; $uri = Gnome2::VFS -> make_uri_from_input($path); $escaped_uri = Gnome2::VFS -> escape_slashes($uri); print $escaped_uri;')
	CLEANURI="$TMPVAR_1" #full path to root in URI format
	
	#Create temporary files
	TMPXML="$TMPDIR/$UTIME_${CLEANPATH##\/*\/}.xml"
	TMPCMD="$TMPDIR/$UTIME_${CLEANPATH##\/*\/}.cmd"
	if [ -e "$CLEANPATH/.icon.index" ]; then rm "$CLEANPATH/$INDEXFILE";	fi
	#touch "$CLEANPATH/.icon.index"
	
	
	#Get list of image paths
	IMGLIST=$(find $CLEANPATH -maxdepth 2 -mindepth 2 -name "$COVERFILE")
	INDEXPATH="$CLEANPATH/$INDEXFILE"
	
	if [ "$IMGLIST" != "" ]
	then
		touch "$TMPXML"
		touch "$TMPCMD"
		chmod +x "$TMPCMD"
		#Generate XML and icon images
		for cover in $IMGLIST
		do
			#echo $cover
			TMPVAR_0=${cover%%"/$COVERFILE"}
			ICONPATH="${cover//$COVERFILE/$ICONFILE}" #path to new icon file
			#convert $IMGSETTINGS $cover $ICONPATH
			convert -thumbnail $GENERAL_ICONSIZEx$GENERAL_ICONSIZE ${cover// /\ } ${ICONPATH// /\ }
	
			TMPVAR_1=${TMPVAR_0##'/'*'/'}
			TMPVAR_2=${TMPVAR_1##'/'*}
			TMPVAR_3=$(echo "$TMPVAR_2" | perl -e 'use URI::Escape; $path = <STDIN>; $escaped_uri = uri_escape($path); print $escaped_uri;')
			TMPVAR_4=${TMPVAR_3%%%0A}
			SHORTURI="$TMPVAR_4" #uri to album directory from the root directory
			TMPVAR_5="$LINESTART name=\"$SHORTURI\" timestamp=\"$UTIME_\" custom_icon=\"$ICONFILE\"$LINEEND$LINEBREAK"

			if [ -e $ICONPATH ] #check if the icon was created successfully
			then
				CODE_HANDLE="$CODE_HANDLE$TMPVAR_5"
			else
				QUITMSG="$QUITMSG[$UTIME_]  -  ERROR:Failed to create $ICONFILE file.  -  [$CLEANPATH] \n"
			fi
			echo "$ICONPATH" >> "$INDEXPATH" #add icon path to icon index file
		done
		
		ICONPATH_="$CLEANPATH/$ICONFILE" #build artist icon path
		
		INDEXCONTENT=$(cat $INDEXPATH) #extract index file contents into variable

		IMGNUM=$(echo "$INDEXCONTENT" | wc -l) #count index entries
		#while [ "$IMGNUM" -gt 4 ]; do INDEXCONTENT=${INDEXCONTENT%"$LINEBREAK"*}; let IMGNUM--; done
		if [ "$IMGNUM" -lt 4 ] #if less than for tile horizontally
		then
			IMGCMD="convert -size ${GENERAL_ICONSIZE}x${GENERAL_ICONSIZE} xc:none \\
	"
			let "ICONSIZE=$GENERAL_ICONSIZE/$IMGNUM" #figure out how to divide images
			ICONSIZE=$(printf %.0f $ICONSIZE)
			ICONPOS=-$ICONSIZE
			for path in $INDEXCONTENT
			do
				path=${path//\'/\\\'}
				if [ "$IMGNUM" -eq 1 ] #calculate icon position
				then
					ICONPOS=0
				else
					let "ICONPOS=$ICONPOS+$ICONSIZE" #update overlay position
				fi
				#path=${path//' '/'\ '}
				IMGCMD="$IMGCMD-draw \"image over $ICONPOS,0 $ICONSIZE,$GENERAL_ICONSIZE '$path'\" \\
	"
			done
		else #else let montage command handle it
			IMGCMD="montage "
			while [ "$IMGNUM" -gt 4 ]; do INDEXCONTENT=${INDEXCONTENT%"$LINEBREAK"*}; let IMGNUM--; done
			for path in $INDEXCONTENT
			do
				IMGCMD="$IMGCMD\"$path\" "
			done
			let "ICONSIZE=$GENERAL_ICONSIZE/($IMGNUM/2)"
			IMGCMD="$IMGCMD-geometry ${ICONSIZE}x${ICONSIZE}+${ICONSPACING}+${ICONSPACING} "
		fi
			#ICONPATH_=${ICONPATH_//\'/\\\'}
			IMGCMD="$IMGCMD\"$ICONPATH_\""
		echo -en "$IMGCMD" >> $TMPCMD
		$($TMPCMD) #execute generated .cmd file
		IMGCMD=""

		CODE="$CODE_HANDLE$FILEFOOTER" #append footer xml for final code string
		echo -en "$CODE" >> "$TMPXML" #write the code to the temporary xml file
		XMLFILE="$CLEANURI.xml" #prepare the metafile filename
		CODE_HANDLE=""
		
		cp "$TMPXML" "$OUTPUTDIR$XMLFILE" #move temporary xml to metafile directory
		
		if [ "$QUITMSG" == "" ]
		then
			echo -en "\033[0;36mSUCCESS! Metafile created for: $ARTISTPATH\033[0m\n\bdebug:\tURI: $CLEANURI\n$OUTPUT_DIV\n"
		else
			ERRORMSG="$ERRORMSG$QUITMSG"
			QUITMSG=""
		fi
	else
		ICONPATH_="$CLEANPATH/.icon.jpg" #build artist icon path to blank image
		cp "$BLANKIMG" "$CLEANPATH"
		mv "$CLEANPATH/blank.jpg" "$ICONPATH_"
	fi
	
	echo "$ICONPATH_" >> "$INDEXPATH_" #add icon path to icon index file
			fi #end of if index file doesn't exist
done

#generate metafile entry for artist directory
INDEXCONTENT=$(cat $INDEXPATH_) #extract index file contents into variable
for path in $INDEXCONTENT
do
	TMPVAR_0=${path%%"/$ICONFILE"}
	TMPVAR_1=${TMPVAR_0##'/'*'/'}
	TMPVAR_2=${TMPVAR_1##'/'*}
	TMPVAR_3=$(echo "$TMPVAR_2" | perl -e 'use URI::Escape; $path = <STDIN>; $escaped_uri = uri_escape($path); print $escaped_uri;')
	TMPVAR_4=${TMPVAR_3%%%0A}
	SHORTURI="$TMPVAR_4" #uri to artist directory from the root directory
	TMPVAR_5="$LINESTART name=\"$SHORTURI\" timestamp=\"$UTIME_\" custom_icon=\"$ICONFILE\"$LINEEND$LINEBREAK"

	if [ -e $path ] #check if the icon was created successfully
	then
		CODE_HANDLE_="$CODE_HANDLE_$TMPVAR_5"
	else
		QUITMSG="$QUITMSG[$UTIME_]  -  ERROR:Failed to create $ICONFILE file.  -  [$MUSICPATH] \n"
	fi

done

if [ "$CODEHANDLE_" != "$FILEHEADER" ]
then
	CODE_="$CODE_HANDLE_$FILEFOOTER" #append footer xml for final code string
	echo -en "$CODE_" >> "$TMPXML_" #write the code to the temporary xml file
	XMLFILE_="$CLEANURI_.xml" #prepare the metafile filename
	CODE_HANDLE_=""

	cp "$TMPXML_" "$OUTPUTDIR$XMLFILE_" #move temporary xml to metafile directory
fi

if [ "$ERRORMSG" != "" ]
then
	echo -en "$ERRORMSG"
	echo -en "$ERRORMSG" >> "$LOGFILE"
	ERRORMSG=""
fi

IFS=$ORIGIFS



```

---

### Post by dysphasi on 2007-12-06
To be honest, I think this script suits me best, I want to be able to apply folder icons for my video folders etc as well regardless of folder structure.

My only issue, as someone else said was the '!'s stop it working if in the folder name, is there a workaround for this?

One other thing I found was that nautilus -q would close all my windows and would have to issue a 'nautilus' command from the terminal to fire things up again, 'killall nautilus' is more consistent in its behaviour and opens the window again after closing to refresh. I found the most convenient thing to do was ad this command via Nautilus Actions Configuration, allowing me to right click anywhere in the folder and refresh. 
Thanks guys for what you've come up with so far :D

> **fifo said:**
> Well this is something that I'd quite like to do, but I can't stand php (sorry) and I wanted to have a go at fixing some of the shortcomings, so I've written my own version in python.

This should handle spaces in directory names (as well as other strange characters, but nautilus' quoting rules seem rather obscure, so maybe there are things I've missed here).

You can specify your own shell-type pattern (--names) for matching the image filename (the default is "[Ff]older.jpg").

There is also a switch (-R) to make it work recursively across nested directories.

Download: [ATTACH]28357[/ATTACH]

```
$ python custom_icon.py --help
usage: custom_icon.py [options] folder [folder2 ...]

options:
  --version        show program's version number and exit
  -h, --help       show this help message and exit
  --names=NAMES    specification to match image filenames [default:
                   "[Ff]older.jpg"]
  -R, --recursive  set icons for folders recursively

$ python custom_icon.py ~/music
/home/user/music ...
done.

$ nautilus -q
```

---

### Post by Lothas on 2007-12-07
This is a very interesting thread. Does this code you've posted search for any .jpeg or do you have to create an image for each folder? Could this be used for pictures folders as well?

I'm looking for a feature like in windows where you can see which pics are in which folder just by looking at the icon.

Also, it would be nice, since apparently some work has been put into this script, to update the first post on the thread with the newest working code.

Thanks for everything!

---

### Post by NinjitsuStylee on 2007-12-08
Wow, it's been a long time since I've even visited this thread.  Just yesterday I was thinking about my music collection and how I managed to get all them folder.jpg files working. I had completely forgotten that I was the one who started the ubuntuforums thread about it!  xD

Long story short, I suck at maintaining my own threads.  :(

Lothas does bring up a good point:  a good handful of people have posted scripts for this issue, and it would be nice to include them in the original post.  However, for the sake of sanity, I'd like to only include the ones that people have had the most luck with.

Would you guys mind "voting" on which ones have worked best?

My original PHP script was not meant to be a silver bullet, rather it was just a quick hackup to automate changing the XML.  I'm glad people have found this thread useful.

And just in case you're curious, I've since moved on to Python myself ;-)

So that's it...a handful of votes on which scripts are most effective, and I'll update the original thread with links.  

Boy I love open-source :D

---

### Post by adrianmak on 2007-12-08
does the script run manually for new album added ???

---

### Post by dysphasi on 2007-12-08
> **adrianmak said:**
> does the script run manually for new album added ???

You need to run the script when you want to update folderart, basically it's ideal if you've got a large collection that you want to update all at once, otherwise I find myself doing it manually more often than not.

Could someone give me a bit of a hand though, I'm using the script fifo posted: custom_icon.py.

Probably due to my inept use of the linux terminal (only a recent convert, I'm too used to DOS terminology), but I do struggle to get the script to work on the one folder consistently.

 For example if I'm in my videos folder with all my videos in their own respective folders containing the avi and folder.jpg and I run the script as follows: ```
custom_icon.py ./*
``` it doesn't always alter all the folder images, if I use the -R switch, it'll add art to the subfolders of each folder but won't change the image of the main folders directly within the videos folder.

However, if I run:```
custom_icon.py ../*
``` it will change the images of the folders within videos no problem...but also changes the images of any other folders in my home directory (i.e. ~/Music/<ALL FOLDERS HERE and ~/Documents/<ALL FOLDERS HERE)

Probably as clear as mud, but basically I want the script to work for all my folders and subdirectories in the videos folder, not all my other folders, but can't get this behaviour.

Also is there a way the script could be altered to refresh nautilus and open up the windows I'm currently viewing?
[color=blue]
**EDIT:** 
Ok, sorted out the problem with my terminal use it appears....still not sure on the correct switches, but I've just used Nautilus Actions Configuration to add a right-click option with
Path: custom_icon.py
Parameters: -R %d

Now all I want to do is refresh nautilus and have it open up again in the folder I've been working in
[/color]

---

### Post by PiK4cHu on 2008-10-18
[CENTER][[IMG]http://brainstorm.ubuntu.com/idea/279/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/279/)

**Go stand for your ideas boys !** :KS[/CENTER]

---

### Post by amaasbier on 2009-01-05
Hi there,
I'm new to this forum and this is my first post (yay!).

Didn't see that there already was a bash and python version, so I did it myself. Though it may be not be the best script, I share it with you:

```
#!/bin/bash

if [ $# = 1 ]; then

	# define variables
	folder=$1
	cfolder=file:%2F%2F${folder//\//%2F}
	timestamp=$(date +%s)
	ofile=$HOME/.nautilus/metafiles/$cfolder.xml

	# create xml-file header
	echo '<?xml version="1.0"?>' > $ofile
	echo '<directory>' >> $ofile

	find $folder -name '* *' -type d | while read ifolder
	do
		if [ -e "$ifolder/folder.jpg" ]; then
			icfolder=${ifolder//$folder\/}
			icfolder=${icfolder//\ /%20}
			icfolder=${icfolder//\&/\&amp\;}
			echo '	<file name="'$icfolder'" timestamp="'$timestamp'" custom_icon="folder.jpg"/>' >> $ofile
		fi
	done

	# create xml-file footer
	echo '</directory>' >> $ofile
	
	nautilus -q
	
	echo $ofile

else
    echo "Usage: $0 [FOLDER]"
fi
```

Please tell me what you think of it. I'm sure there are things that could be improved.
I don't think I did escape every special character needed, but it works with all of my folders.

EDIT:
If it's not clear: the script is used correctly by calling "script.sh /your/folder". It will then scan all subfolders of /your/folder.

It may be useful if someone can share a way to quit nautilus and then reopen the same windows.
'nautilus --help' tells me that there is a way to load a session. Unfortunately I don't know how to save a session.

---

### Post by Niko_K on 2009-01-06
> **fifo said:**
> Well this is something that I'd quite like to do, but I can't stand php (sorry) and I wanted to have a go at fixing some of the shortcomings, so I've written my own version in python.

This should handle spaces in directory names (as well as other strange characters, but nautilus' quoting rules seem rather obscure, so maybe there are things I've missed here).

You can specify your own shell-type pattern (--names) for matching the image filename (the default is "[Ff]older.jpg").

There is also a switch (-R) to make it work recursively across nested directories.

Download: [ATTACH]28357[/ATTACH]

```
$ python custom_icon.py --help
usage: custom_icon.py [options] folder [folder2 ...]

options:
  --version        show program's version number and exit
  -h, --help       show this help message and exit
  --names=NAMES    specification to match image filenames [default:
                   "[Ff]older.jpg"]
  -R, --recursive  set icons for folders recursively

$ python custom_icon.py ~/music
/home/user/music ...
done.

$ nautilus -q
```

I really like this script best, because it is able to generate folder icons not only from folder.jpg files, but also from any filename pattern (i personally use '*.png').

However, it does not work for folders, that contain a & in the folder's name (for me it works for folders like "Music/Pop", but not for folder lik "Music/Blues & Jazz").

I am not that familiar with python (and i can't find the problem)...
... can someone please fix this issue?

---

### Post by wadeo on 2009-01-07
This was an excellent idea - always wanted an easier way to do this to my rather large music collection and this works wonders.

If the php method were as easily and clearly setup and ran as the python script I believe it would be worth looking at. Just some constructive criticism.

\\:D/

---

### Post by KhaaL on 2009-02-12
while this script is handy for many, it made my head dizzy. Also i'm not sure if it will fill my needs, i'd like to have a custom icon in many of my folders in order to recognise them more quickly since emblems are so limited in number and variety...

EDIT: saw that what i'm looking for [has already been suggested]("http://brainstorm.ubuntu.com/idea/279/").

---

### Post by lesqueFM on 2009-04-06
(sorry for being absolutely dumb on this)

Where do I save the code file? Do I have to edit specific parts of it (where do I "tell" the code the location I use)? And then make it operational with the command at the end of quote?

> **fifo said:**
> Well this is something that I'd quite like to do, but I can't stand php (sorry) and I wanted to have a go at fixing some of the shortcomings, so I've written my own version in python.

This should handle spaces in directory names (as well as other strange characters, but nautilus' quoting rules seem rather obscure, so maybe there are things I've missed here).

You can specify your own shell-type pattern (--names) for matching the image filename (the default is "[Ff]older.jpg").

There is also a switch (-R) to make it work recursively across nested directories.

Download: [ATTACH]28357[/ATTACH]

```
$ python custom_icon.py --help
usage: custom_icon.py [options] folder [folder2 ...]

options:
  --version        show program's version number and exit
  -h, --help       show this help message and exit
  --names=NAMES    specification to match image filenames [default:
                   "[Ff]older.jpg"]
  -R, --recursive  set icons for folders recursively

$ python custom_icon.py ~/music
/home/user/music ...
done.

$ nautilus -q
```

---

### Post by Keith Hedger on 2009-04-10
This is a script I used when setting the album art for my music collection, just copy it to your music folder and run it, it is fully recursive, you may want to change line 4 to use whatever file name you use for your albumart, this should set the thumbnail regardless of Artist/Album structure, running this on Hardy 8.04
[php]
#!/bin/bash

MAINWD=$PWD
JPEGNAME="albumart.jpg"

find  . -type d | while read FOLDER
	do
		if [ -e "${FOLDER}/${JPEGNAME}" ];then

			cd "${FOLDER}/../"
			FILENAME="$PWD"
			FILENAME="file:%2F%2F"${FILENAME// /%2520}
			FILENAME=${FILENAME//\//%2F}
			XMLFILE=~/.nautilus/metafiles/${FILENAME}.xml
			BASE=$(basename "$FOLDER")

			if [ ! -e $XMLFILE ];then
				echo "<?xml version=\"1.0\"?>" > $XMLFILE
				echo "<directory>" >> $XMLFILE
				echo "</directory>" >> $XMLFILE
			fi

			CNT=$(wc -l $XMLFILE | awk '{ print $1 }')
			CONTENTS=$(head -n $(( $CNT - 1 )) $XMLFILE)
			BASE=${BASE// /%20}
			BASE=${BASE//&/%26}

			echo "$CONTENTS" > $XMLFILE
			echo "<file name=\"${BASE}\" custom_icon=\"${JPEGNAME}\"/>" >> $XMLFILE
			echo "</directory>" >> $XMLFILE

			cd "$MAINWD"
		fi
	done

killall nautilus

exit 0

[/php]

---

### Post by lilo_booter on 2009-06-01
Here is my python effort for custom folders on albums - it's a bit dumb and probably needs a little work :-).

You will probably need to run:

```
sudo apt-get install python-beautifulsoup
```

before attempting to run this script.

It assumes that you run it in the directory above your Music dir (so if you use $HOME/Music, run it from $HOME). 

It further assumes you use an Artist/Album subdirectory structure and if it finds multiple files in any Music/<dir1>/<dir2>/ directory and no folder.jpg, it'll use the dir1 and dir2 values to query albumart.org - if that returns nothing, then it uses dir1 alone.

Finally, if you arbitrarily and manually place folder.jpg files in any subdirectory, then this is used in preference to the albumart.org query.

```
#!/usr/bin/env python

import BeautifulSoup
import urllib
import os
import xml.dom
import xml.dom.minidom
import time

def albumart( path, query ):
	"""Fire query at albumart.org"""
	base = 'http://www.albumart.org/index.php?srchkey=%s&itempage=1&newsearch=1&searchindex=Music'
	result = ''
	try:
		url = base % urllib.quote( query )
		connection = urllib.urlopen( url )
		tree = BeautifulSoup.BeautifulSoup( connection )
		incidents = tree('div', id = 'main_left' )
		if len( incidents ) == 1:
			images = incidents[ 0 ]( 'img' )
			if len( images ):
				result = images[ 0 ][ 'src' ]
			else:
				print 'No images for', path
		else:
			print 'No div for', path
	except Exception, e:
		print 'Malformed result from', path
	return result

def save_as( url, file ):
	"""Save a url to a file"""
	fd = open( file, 'w' )
	connection = urllib.urlopen( url )
	while True:
		data = connection.read( 16384 )
		if len( data ) == 0: break
		fd.write( data )

def metaname( path ):
	"""Probably broken - attempts to map the path given to the nautilus weirdisms..."""
	full = os.path.dirname( os.path.join( os.getcwd( ), path ) )
	result = ( 'file://' + full ).replace( ' ', '%2520' ).replace( '/', '%2F' )
	return result

# Iterate through the Music subdirectory
for path, dirs, files in os.walk( 'Music' ):

	# Split our path (assumption is that we have a Music/Artist/Album combo for albumart usage
	tokens = path.split( '/' )

	# This is the file we will use
	cover = os.path.join( path, 'folder.jpg' )

	# Crappy check to see that we have some files in this dir - assumption is
	# if files exists, and we have at least 3 levels of subdir, then we have an
	# album in the form 'Music/Artist/Album/' or if the current dir contains
	# a folder.jpg we will use it
	
	if len( files ) == 0:
		continue

	# Obtain an image if one is not available
	if len( tokens ) == 3 and not os.path.exists( cover ):
		url = albumart( path, ( tokens[ 1 ] + ' ' + tokens[ 2 ] ).replace( '\'', '' ) )
		if url == '':
			url = albumart( path, ( tokens[ 1 ] ).replace( '\'', '' ) )
		if url != '':
			save_as( url, cover )

	# If we have no cover image for this dir, continue to the next
	if not os.path.exists( cover ):
		continue

	# Obtains the nautilus metadata file name
	directory = os.path.join( os.getenv( 'HOME' ), '.nautilus', 'metafiles' ) + '/' + metaname( path ) + '.xml'

	# Following are populated below
	exists = False
	doc = None
	dir = None

	# Update or create nautilus metafile for icons
	if os.path.exists( directory ):
		doc = xml.dom.minidom.parse( open( directory, 'r' ) )
		elements = doc.getElementsByTagName( 'directory' )
		if len( elements ) == 1:
			dir = elements[ 0 ]
			files = dir.getElementsByTagName( 'file' )
			for file in files:
				name = file.getAttribute( 'name' )
				if name == urllib.quote( os.path.basename( path ) ):
					file.setAttribute( 'custom_icon', os.path.basename( cover ) )
					exists = True
		elif len( elements ) == 0:
			dir = doc.createElement( 'directory' )
			doc.appendChild( dir )
		else:
			print "Umm - don't think this is supposed to happen"
	else:
		dom = xml.dom.minidom.getDOMImplementation( )
		doc = dom.createDocument( None, None, None )
		dir = doc.createElement( 'directory' )
		doc.appendChild( dir )

	# Create the new file if necessary
	if not exists:
		element = doc.createElement( 'file' )
		element.setAttribute( 'name', urllib.quote( os.path.basename( path ) ) )
		element.setAttribute( 'custom_icon', os.path.basename( cover ) )
		element.setAttribute( 'timestamp', str( int( time.time( ) ) ) )
		dir.appendChild( element )

	# Save the document
	output = open( directory, 'w' )
	doc.writexml( output )
	output.close( )
```

---

### Post by jlaroche on 2009-06-22
I tried the following code and got it working, but I don't like the way the bare jpg files look. In short, I'd like to have the normal folder icons back. How would one do this?

Python Code Used:

<?php

/*
    Used in conjunction with nautilus metafile for music folder Folder.jpg replacement!
*/

 $time = mktime();
$dir = "/media/500gb/My Music/"; //this is the music directory you wanna change

$filename = $dir . "music.txt";

$handle = fopen($filename, "r");
$contents = fread($handle, filesize($filename));
fclose($handle);

$lines = explode ("\n", $contents);



echo "<?xml version=\"1.0\"?>\n<directory>";
foreach ($lines as $value)
{
    if ($value)
    {
        //replace special characters.....this is kind of a dumb way to do things, I bet a more leet php coder would be able to find a better function to do this
        $newval = str_replace(" ", "%20", $value); //replace spaces
        $newval = str_replace(",", "%2C", $newval); //i have some commas in my album names
        $newval = str_replace("&", "%26", $newval); //i noticed an ampersand (&) in certain album titles such as Outkast - Speakerboxxx & The Love Below 
        
        
        $filename = $dir . $value . "/folder.jpg"; //changed Folder.jpg to folder.jpg
        $time = mktime(); //Unix time!
        if (file_exists($filename)) //we only want to do this if there is actually a Folder.jpg file in there
        {
            $size = filesize($filename);
            if ($size && $size < 1048576) //if the Folder.jpg file is too big we might have problems, so lets limit it to 1 MB
            {
                echo "<file name=\"" . $newval . "\" timestamp=\"". $time . "\" custom_icon=\"folder.jpg\"/>"; //again changed Folder.jpg to folder.jpg
                        
            }
        }//end if statment: file_exists

    }
}  //end foreach

echo "</directory>\n";
clearstatcache(); //not really sure if we need this
exit ();

 ?>

---

### Post by Horizon on 2009-06-22
You'll need to go into ```
~/.nautilus/metafiles
``` and delete the lines from the metafile. There should be one named after your music folder. You can delete the whole thing but then you'll lose anything like emblems and settings you had stored on it. If you want to keep them then inside it should have a file element per folder with an icon inside your music folder, so just delete the lines that you want.

If you want a smarter version then try my bash version on page 1 (read my [first post](http://ubuntuforums.org/showthread.php?t=226199#23), then use the code in my [second post](http://ubuntuforums.org/showthread.php?t=226199#24) which is just below). It resizes the images to the right size (not the actual cover art, it creates a copy first), creates collages of multiple album covers, and creates a "no cover art" image for folders without it because otherwise your folder looks ugly with images and normal folder icons mixed together. Also handles any language, and any characters that nautilus can display.

I also have a version that adds a border and a shadow (like in the attachment to my post on page 1) if you want it.

---

### Post by JasperK on 2009-07-26
[FONT=Verdana][COLOR=Black]The newer versions of nautilus as available in Karmic don't store the[/COLOR][/FONT][FONT=Verdana][COLOR=Black] metadata in xml files anymore. Instead nautilus now uses the new gio [/COLOR][/FONT]abstraction layer to give files a "metadata::custom_icon" attribute. This attribute contains a filename of a picture that should be used as the file icon.

I changed the python script that was posted before to use gio attributes. I have only tested this on  karmic(Nautilus 2.27.4).
****

---

### Post by AFU_Ra on 2009-10-11
> **JasperK said:**
> [FONT=Verdana][COLOR=Black]The newer versions of nautilus as available in Karmic don't store the[/COLOR][/FONT][FONT=Verdana][COLOR=Black] metadata in xml files anymore. Instead nautilus now uses the new gio [/COLOR][/FONT]abstraction layer to give files a "metadata::custom_icon" attribute. This attribute contains a filename of a picture that should be used as the file icon.

I changed the python script that was posted before to use gio attributes. I have only tested this on  karmic(Nautilus 2.27.4).
****

I've tried your script with Nautilus 2.28.0 on Karmic but it didn't work for me :(. Do you have any suggestions? This is what i get: ```
Traceback (most recent call last):
  File "custom_icon_gio.py", line 48, in <module>
    main()
  File "custom_icon_gio.py", line 42, in main
    gioFile.set_attribute_string("metadata::custom_icon", sd[1])
gio.Error: Error setting file metadata: No such file or directory

 
```

---

### Post by qos on 2009-10-31
Try mine ... :)

```
#!/usr/bin/python

import sys
from optparse import OptionParser
import os
import fnmatch
from urllib import quote

def main():
    parser = OptionParser(usage="usage: %prog [options] folder [folder2 ...]",
                          version="%prog 0.1")
    parser.add_option("", "--names", dest="names",
                      default="[Ff]older.[Jj][Pp][Gg]",
                      help='specification to match image filenames [default: "%default"]')
    parser.add_option("-R", "--recursive", dest="recursive", action="store_true", default=False,
                      help="set icons for folders recursively")

    (options, folders) = parser.parse_args(sys.argv)
    folders = folders[1:]

    if not folders:
        parser.error("no folders specified")

    noquote = "()'*"

    for folder in folders:
        for root, dirs, files in os.walk(folder):
            print root, "..."
            subdirs = []
            for d in dirs:
                images = fnmatch.filter(os.listdir(os.path.join(root, d)), options.names)
                if images:
                    path  = os.path.join(root, d)
                    image = os.path.basename(images[0])
                    os.system('gvfs-set-attribute "%s" metadata::custom-icon "%s"' % (path, image))
                else:
                    print "no image found for %s/%s" % (root, d)
            if not options.recursive:
                dirs[:] = []
    print "done."

if __name__ == "__main__":
    main()
```

---

### Post by linux4all on 2009-11-22
Tanks qos!!!!! this works well for me! hope some day nautilus will do this by default or at least give the optiom...

C.

---

### Post by Patapalo on 2009-12-10
> **qos said:**
> Try mine ... :)

```
#!/usr/bin/python

import sys
from optparse import OptionParser
import os
import fnmatch
from urllib import quote

def main():
    parser = OptionParser(usage="usage: %prog [options] folder [folder2 ...]",
                          version="%prog 0.1")
    parser.add_option("", "--names", dest="names",
                      default="[Ff]older.[Jj][Pp][Gg]",
                      help='specification to match image filenames [default: "%default"]')
    parser.add_option("-R", "--recursive", dest="recursive", action="store_true", default=False,
                      help="set icons for folders recursively")

    (options, folders) = parser.parse_args(sys.argv)
    folders = folders[1:]

    if not folders:
        parser.error("no folders specified")

    noquote = "()'*"

    for folder in folders:
        for root, dirs, files in os.walk(folder):
            print root, "..."
            subdirs = []
            for d in dirs:
                images = fnmatch.filter(os.listdir(os.path.join(root, d)), options.names)
                if images:
                    path  = os.path.join(root, d)
                    image = os.path.basename(images[0])
                    os.system('gvfs-set-attribute "%s" metadata::custom-icon "%s"' % (path, image))
                else:
                    print "no image found for %s/%s" % (root, d)
            if not options.recursive:
                dirs[:] = []
    print "done."

if __name__ == "__main__":
    main()
```

Don´t work for me.

This what i get:

Usage: albumart [options] folder [folder2 ...]

albumart: error: no folders specified

---

### Post by qos on 2009-12-19
I cleaned up the code, and fixed a potential bug.
So, give it a new try... :)

```
#!/usr/bin/python

import sys
from optparse import OptionParser
import os
import fnmatch
from urllib import quote


def setattrib(root, directory, names):
    path   = os.path.join(root, directory)
    images = fnmatch.filter(os.listdir(path), names)
    if images:
        image = os.path.basename(images[0])
        os.system('gvfs-set-attribute "%s" metadata::custom-icon "%s"' % (path, image))
    else:
        print "no image found for %s/%s" % (root, directory)

def main():
    parser = OptionParser(usage="usage: %prog [options] folder [folder2 ...]",
                          version="%prog 0.2")
    parser.add_option("", "--names", dest="names",
                      default="[Ff]older.[Jj][Pp][Gg]",
                      help='specification to match image filenames [default: "%default"]')
    parser.add_option("-R", "--recursive", dest="recursive", action="store_true", default=False,
                      help="set icons for folders recursively")

    (options, folders) = parser.parse_args(sys.argv)
    folders = folders[1:]

    if not folders:
        parser.error("no folders specified")

    noquote = "()'*"

    for folder in folders:
        setattrib('', folder, options.names)
        for root, dirs, files in os.walk(folder):
            for d in dirs:
                setattrib(root, d, options.names)
            if not options.recursive:
                dirs[:] = []
    print "done."

if __name__ == "__main__":
    main()
```

---

### Post by user333 on 2009-12-19
Why don't you just edit an icon theme?

---

