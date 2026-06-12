---
title: "Youtube-dl + ffmpeg and exec php script"
date: 2010-03-01
forum: Programming Talk
---

### Post by Kemon on 2010-03-01
I have made a youtube downloading script you my server/desktop that download the flw file and convert it to mp3, I want to make a php script that download and convert it so I can download just the mp3-file.

youtube.sh with user:www-data and 755 access:
```
#! /etc/bach
if [ "$1" ]; then

        cd "/var/www/youtube/mp3"
        youtube-dl $1
        ffmpeg -i "$1.flv" -ab 128k "$1.mp3"
        mv "$1.mp3" "$2.mp3"
        rm "$1.flv"
fi
```

/var/www/youtube/index.php:
[PHP]<?

$dl = $_POST['dl'];
$new_name = $_POST['new_name'];
if($dl && $new_name){
if(exec("sh ./yt.sh $dl '$new_name'", $out)) {
        echo "<a href='http://WEBADDRESS.com/youtube/mp3/$new_name.mp3'>[RightClick, save as]</a>";
        print_r($out);
}
}
?>
<form method="post" action="">
Youtube link: <input type="text" name="dl"><br>
Nytt navn: <input type="text" name="new_name"><br>
<input type="submit" value="Convert and download">
</form>
[/PHP]
My problem is that the script is not "loading" long enugh to download and convert the file so I made a output var $out that says:
```
Array ( [0] => Retrieving video webpage... done. [1] => Extracting URL "t" parameter... done. [2] => Requesting video file... done. [3] => Video data found at http://v16.lscache2.c.youtube.com/videoplayback?ip=0.0.0.0&sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor&fexp=905210%2C900022%2C904704%2C906103&algorithm=throttle-factor&itag=5&ipbits=0&burst=40&sver=3&expire=1267146000&key=yt1&signature=834FB7D42000C8CA343C9905197E95AF477CEF0A.22DAEAB6E74D6B330D634F55BDA50CF511A4E22A&factor=1.25&id=d999a4b16c9a7090 )
```

It works in shell/putty but not on the webpage..
Any ide?

Thanks

---

### Post by dragos2 on 2010-03-01
php.ini has a setting maximum execution time for a script.

Try that, maybe it works.

---

### Post by Kemon on 2010-03-01
Not working =( I have to run the script in background, but dont know how I can do it.

---

### Post by Rany Albeg on 2010-03-01
Hello ,
I actually did the same thing using bash and c++.
It could be written only in bash but i decided that i want to write a simple link-parser in c++ and use youtube-dl and ffmpeg in a bash script.
Sorry , but , can you be more specific when you say "long enough"?
This is my piece of code.It may be of help.

Have a nice day.

```
#!/bin/bash

var=$(echo "$1"|tr ' ' '+')
url='http://www.google.co.il/search?hl=en&q='"$var"'&btnG=Google+Search&meta=&aq=f&oq='
wget -q -U "" "$url" -O sourcefile.txt
sleep 2
./linkParser
sleep 2
wantedLink=`cat links.txt`

rm sourcefile.txt links.txt
echo "Downloading..."
youtube-dl -q http://www.youtube.com/"$wantedLink"
echo "Done."
echo "Converting sound track to mp3."
ffmpeg -i *.flv -vn "$1".mp3
echo "Done."
echo
exit 0
```

---

### Post by Kemon on 2010-03-01
I think the script stops at "youtube-dl $1" around 3sec and it don't start to download the flv file.

---

### Post by Rany Albeg on 2010-03-01
Of curse it stops.
That because you don't have the executable of 'linkParser.cpp' i mentioned before.
So here is its source code:

```
#include <iostream>
#include <cstring>
#include <fstream>
#include <cstdlib>

using namespace std;

string get_watch_link(string passedStr);

int main()
{
	ifstream file;
	ofstream links;
	string line;

	file.open("sourcefile.txt");

	if(!file.is_open())
	{
		cout<<"can not open sourcefile.txt\n";
 		return (EXIT_FAILURE);
	}

	links.open("links.txt");

	if(!links.is_open())
	{
		cout<<"can not open links.txt\n";
 		return (EXIT_FAILURE);
	}

	while(!file.eof())
	{
	     getline(file,line);
	     line=get_watch_link(line);
             if(line.length() != 0)links<<line<<endl;
        }

	file.close();
	links.close();

        return (EXIT_SUCCESS);
}
string get_watch_link(string passedStr)
{
	string answer; 
        string toFind="watch?v=";
        size_t pos = passedStr.find(toFind);
	int i;

	if(pos!=string::npos)
        {
		answer=passedStr.substr(pos);
                for(i=1;answer[i]!='\"';i++);
                answer=answer.substr(0,i);
	}
	return (answer);
}
```

Compile it and place it in the same directory with the script i posted earlier.
EDIT: The function get_watch_link can be implemented in bash , therefore the whole program could have been written in bash.

---

### Post by Hellkeepa on 2010-03-02
HELLo!

Here's what I've done to ensure that the script runs in the background, in a similar system I wrote a year back.
[php]// Run command, and make sure no output is displayed.
$Command = "php -q encode.php $Filename > /dev/null 2> /dev/null &";
system ($Command);[/php]
The important bit is everything after the filename variable, that ensure that "system ()" won't wait for output, and PHP will thus continue to run the script in the background. I've used a PHP script here, but you could just as easily use a bash-script.

Happy codin'!

---

