---
title: "extract data from http sorce using bash"
date: 2008-10-11
forum: Programming Talk
---

### Post by marli2 on 2008-10-11
Hi im pretty new to linux and therin bash.

ive knocked to gether this script
> 
while read inputline
do
  youtube_url="$(echo $inputline)"
  youtube-dl $youtube_url

done < videos.txt



# Convert the flv files to mpg and mp3 files

for i in *.flv
do
  ffmpeg -i $i $i.mpg
  # comment out the next line if you don't want MP3's extracted
  mplayer -dumpaudio $i -dumpfile $i.mp3
  # The next line deletes all FLV files in the current directory to cleanup
  rm $i
rm $i.mpg

done

its not all my own work BTW.
it extracts the youtube urls from videos.txt and dl and coverts them, im sure it can be optimised however i need to add somthing.
I want to extract the title from the page and rename the mp3. I am doing this to learn bash, I have only used the above code becuase I understand it. Ive found lots of ways of doing it but i dont understand it, and if i dont understand code i wont learn or be able to optimise it.

could sombody post the needed commands and what is actully happening

---

### Post by drubin on 2008-10-11
You are going to have to use wget to get hold of the web page.
[http://linux.byexamples.com/archives/302/how-to-wget-flv-from-youtube/](http://linux.byexamples.com/archives/302/how-to-wget-flv-from-youtube/) 

This might help

---

### Post by marli2 on 2008-10-11
> do
  youtube_url="$(echo $inputline)"
  wget -O test $youtube_url
  TITLE = grep "id=\"video_title\"" test | cut -d">" -f2 | cut -d"<" -f1
  youtube-dl -O $TITLE.flv $youtube_url

done < videos.txt

but i get the following error

/home/simon/Downloads/flv/youtube2mp3.sh: 27: TITLE: not found

---

### Post by calraith on 2008-10-11
> **marli2 said:**
> but i get the following error

/home/simon/Downloads/flv/youtube2mp3.sh: 27: TITLE: not found

This is subtle.  You have a space on either side of the equal sign when you're assigning a value to $TITLE.  Bash is very picky about spaces.  Don't use spaces when you're assigning values.  Do use spaces separating arguments within the brackets of if statements.  For example:
```
foo="bar"
if [ "$bar" = "baz" ]; then
/usr/bin/lulz
fi
```There are little idiosyncrasies that you learn to expect after a couple of BASH scripts (such as learning to enclose each argument in that if statement in quotation marks if you're comparing strings -- to prevent the script from erroring in case $bar evaluates to a null value).

While I'm making suggestions, you could get rid of the "test" file you download by having wget download to stdout.
```
TITLE=`wget "$youtube_url" -O- -q | grep -i 'id="video_title"' | cut -d">" -f2 | cut -d"<" -f1`
```

---

### Post by marli2 on 2008-10-11
> while read inputline
do
  youtube_url="$(echo $inputline)"
fname=`wget "$youtube_url" -O- -q | grep -i 'id="video_title"' | cut -d">" -f2 | cut -d"<" -f1`
echo $fname
  youtube-dl $youtube_url -O $fname

done < videos.txt

great now i dont even get errors!!

---

### Post by ghostdog74 on 2008-10-11
this is a simple PHP script to download youtube video. Doesn't take care of login to youtube.
```


<?php
$youtube_url = $argv[1];
$result = file_get_contents($youtube_url);
// get the flash video id and params
if ( (strpos($result,"var swfArgs") !==FALSE ) ){
    $swf = strstr($result,"var swfArgs");
    $swf = substr( $swf,0,strpos($swf,";"));
    $swfitems = explode(",",$swf);
    foreach($swfitems as $key => $val){
        list($name,$param)= explode(":",$val);
        $name = str_replace('"',"",trim($name));
        $param = str_replace('"',"",trim($param));
        $components[$name]=trim($param);        
    }
}
    
$download_url = "http://www.youtube.com/get_video?video_id=" . $components['video_id'] . "&t=" . $components['t'];

// output file name of flash file    
$newfile = "output.flv";
$fh = fopen($newfile,"w");
    
    
//prepare to download
$headers = array(
       "Host: www.youtube.com",
       "Accept-Encoding: gzip,deflate",
       "Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5"
    );
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,$download_url)    ;
curl_setopt($ch, CURLOPT_FILE,$fh)    ;
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_HTTPGET, 1);
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);       
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);    

$result = curl_exec($ch);
curl_close($ch);
// save the flv file
fwrite($fh,$result);    
fclose($fh);
    

```


Just give the script a url eg usage in shell
```

#!/bin/bash

url="http://www.youtube.com/watch?v=HQEtnDLv0XI&feature=dir"
php5 test.php "$url" 


```

it will create an output file called "output.flv".you can after that use your tools to convert your flv.

---

### Post by calraith on 2008-10-11
> **ghostdog74 said:**
> this is a simple PHP script to download youtube video. Doesn't take care of login to youtube.

Wow, that was... random.  This thread is called "extract data from http sorce(sic) using bash."  Now I'm not positive what language he had in mind, but I'm pretty sure it wasn't PHP.  Maybe COBOL? #-o

---

### Post by ghostdog74 on 2008-10-11
> **calraith said:**
> Wow, that was... random.  This thread is called "extract data from http sorce(sic) using bash."  Now I'm not positive what language he had in mind, but I'm pretty sure it wasn't PHP.  Maybe COBOL? #-o
that was modified from a script i did for a client long ago. its up to OP if he wants to use it. I leave the bash problem solving to enthusiastic guys like you :)

---

### Post by marli2 on 2008-10-11
WHAT??
did you not read the question??
you script does what i CAN do in a different way but fails to do what i CANT do.
BTW the changes i didnt hasn't soved the problem

---

### Post by calraith on 2008-10-11
Well, I hate to give you the answer outright when I know you're trying to teach yourself.  But perhaps seeing it done with Youtube might help you figure out how to make yet another one for Google Video or Metacafe or something, to further your teaching yourself.  :)

Anyway, instead of using any sort of Youtube leeching howtos, I used a Firefox extension (Video DownloadHelper) to see what gets passed in the URL to initiate the download.  Apparently it's the "video_id=" and the "t=" parameters.  That has nothing to do with BASH scripting, though -- only with how to leech from Youtube.

With that in mind, I set out to download the HTML from Youtube, scrape that HTML for video_id=, t=, and the video's title.  Then use that info to download the videos and save them as $title.flv.  Finally, $title.flv is converted directly to $title.mp3 and the flv file is deleted.  Here's what I came up with:

```
#!/bin/bash

while read line; do
    YTPAGE=`wget "$line" -O- -q`
    TITLE=`echo "$YTPAGE" | grep -E -m 1 -o -e 'meta name="title" content="[^"]+"' | awk -F\" '{ print $4 }'`
    VIDEO_ID=`echo "$YTPAGE" | grep -E -m 1 -o -e '[\?&]video_id=[^&]+' | awk -F\= '{ print $2 }'`
    T=`echo "$YTPAGE" | grep -E -m 1 -o -e '&t=[^&]+' | awk -F\= '{ print $2 }'`
    VIDURL="http://www.youtube.com/get_video?video_id=$VIDEO_ID&t=$T"
    if [ "$VIDEO_ID" != "" ] && [ "$T" != "" ] && [ ! -f "$TITLE.mp3" ]; then
        echo "Downloading $VIDURL ($TITLE)"
        wget -c "$VIDURL" -O "$TITLE.flv"
        echo "Converting flash video to $TITLE.mp3..."
        mplayer -dumpaudio "$TITLE.flv" -dumpfile "$TITLE.mp3"
        if [ -f "$TITLE.mp3" ]; then rm -f "$TITLE.flv"; fi
    fi
done < videos.txt
```My only complaint is that wget's output is either obnoxious, or it doesn't provide a progress bar.  There is no progress-bar-only option for wget.

I hope you can follow the logic I used.

[LIST]
[*]capture the HTML downloaded by wget into $YTPAGE, then do my parsing on that variable
[*]grep args:
[LIST]
[*]**-E**: The expression to be matched will be a regular expression.
[*]**-m 1**: Grab one matching line, then stop looking for more.
[*]**-o**: Grab only the part of the line matching the expression.
[*]**-e** **'&t=[^&]+'**: This is a regular expression meaning, "Look for the characters ampersand-t-equals, then whatever isn't an ampersand, for one or more characters."  Basically everything from &t= up to, but not including, the next &.
[/LIST]
 
[*]awk args:
[LIST]
[*]**-F\"**: Use a quotation mark as a delimiter.
[*]**'{ print $4 }'**: This is basically like splitting the line into an array along whatever delimiter specified with -F and popping out only the 4th element.
[/LIST]
 
[/LIST]
If you don't know how to use regular expressions, I suggest you concentrate your learning there.  Regular expressions are useful for parsing HTML, XML, log files, conf files, and other text files when lines can contain complex information.  The nice thing about regular expressions is that they're used in so many languages.  As a general rule, they're slower to process than static text -- so if you can avoid them, by all means, do.  However, they're pretty much indespensible when parsing HTML from BASH.  I learned regular expressions using [this tutorial]("http://www.regular-expressions.info/tutorial.html").  Bear in mind that not all languages use all the conventions described in that tutorial.  For instance, [0-9] can be written in shorthand as \d in JavaScript, but perhaps not in ASP.  JavaScript also supports lookahead (?=something), whereas other languages might not.  You might have to play with your regexps a few times before they behave the way you intend, even after you're comfortable with working with them in general.

There are probably 20 different ways to accomplish what this script does.  So if your answer is different from mine, it's probably correct as well, as long as you avoid some [common mistakes]("http://partmaps.org/era/unix/award.html").  (Note: I know I violate at least one or two of these.)

---

### Post by marli2 on 2008-10-12
great...thanks.
exactly what i need.
well head down...brain on...
i guess theres enough here for me to work it out.

---

