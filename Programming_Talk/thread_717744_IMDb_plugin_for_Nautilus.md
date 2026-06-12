---
title: "IMDb plugin for Nautilus"
date: 2008-03-07
forum: Programming Talk
---

### Post by graabein on 2008-03-07
Hi, I had an idea for a hobby project to learn some programming on GNU/Linux. I don't know if such a thing exists already. It probably does. Anyhow I don't have the time to start it off so I'd just like to air the idea here.

I'm thinking of when you've got a bunch of movies on your harddrive in directories with the title as directory name, and you'd like to get the IMDb information for that particular release. Like they have for the XBOX media center. 

Wouldn't it be great to right click the directory and choose get IMDb information from the popup menu? Then a new Gtk window appears with the information somewhat formatted nicely (HTML) right there. If the search gives more than one hit you'd get a choice what title matches the best. No results just gives a "no results" message box. Or let's you input what title you'd like to search for.

Does anybody know if something like this exists? Not necessarily for Nautilus but for Gtk or command line perhaps? Sounds like something you'd find useful?

---

### Post by nanotube on 2008-03-07
most people's movie directories are not nearly as organized as you imagine. :)

---

### Post by nhandler on 2008-03-07
I could probably implement something like this. I'm not that great at GUIs, but I could definitely create a CLI for this. Let me just make sure I understand what you are proposing:

You want a script to scan all the movie files in a directory. It then assumes the filename is the title of the movie. Using the title, it searches IMDB and retrieves all the relevant information. If there is more than 1 result for the title, it displays a list and allows the user to select the one they want.

My only question is what information should be retrieved? I personally don't think it should get the entire page. Is there some specific info you want?

---

### Post by kool_kat_os on 2008-03-07
either im retarded or you avatar looks like Borat (no offense intended:-) )

---

### Post by nhandler on 2008-03-07
Well, I've started working on the script. It is a CLI. Right now, it searches the movie folder (the current directory or you can pass it to the script as an argument) for any .mp4 movies (Eventually, it will find movies based on mime-type). Once it finds an mp4, it downloads [http://www.imdb.com/find?q=FILENAME](http://www.imdb.com/find?q=FILENAME). That is the search results page on IMDB. The script then displays all of the "Popular Titles" in the terminal. The user is then prompted to select which title is the one they were looking for. After they select a title, the url for the movie's page on imdb is displayed in the terminal.

Once I decide (or you guys suggest) what information about the movie should be displayed, I will implement it. If anyone is interested in the script (it is written in perl), send me an email/pm. I would post it here, but a) It is incomplete and b) It is EXTREMELY sloppy, and if I were to post it here, it would come back to haunt me later.

---

### Post by graabein on 2008-03-08
OK thanks for the input. Here are some corrections. 

It's the actor Tom Selleck as [Thomas Magnum]("http://en.wikipedia.org/wiki/Thomas_Magnum"). He lived in Hawaii and drove a Ferrari and had a bunch of friends and girlfriends. :)

I'm thinking of right clicking either a directory or a movie file, both named somewhat close to the title of the movie, and then activating the plugin on the directory/file name. Nothing a little string parsing won't solve. Replace . and _ with white space and search for the longest words in the title and so on.

---

### Post by graabein on 2008-03-08
> **Cheater said:**
> Well, I've started working on the script. It is a CLI. Right now, it searches the movie folder (the current directory or you can pass it to the script as an argument) for any .mp4 movies (Eventually, it will find movies based on mime-type). Once it finds an mp4, it downloads [http://www.imdb.com/find?q=FILENAME](http://www.imdb.com/find?q=FILENAME). That is the search results page on IMDB. The script then displays all of the "Popular Titles" in the terminal. The user is then prompted to select which title is the one they were looking for. After they select a title, the url for the movie's page on imdb is displayed in the terminal.

Once I decide (or you guys suggest) what information about the movie should be displayed, I will implement it. If anyone is interested in the script (it is written in perl), send me an email/pm. I would post it here, but a) It is incomplete and b) It is EXTREMELY sloppy, and if I were to post it here, it would come back to haunt me later.

Sounds good Cheater! Can you break it up into parts so you have the option to search for a specific filename also? And forcing mp4 is a bit unnecessary don't you think? It should look for all typical movie files like mpg, avi and such.

---

### Post by graabein on 2008-03-08
> **Cheater said:**
> I could probably implement something like this. I'm not that great at GUIs, but I could definitely create a CLI for this. Let me just make sure I understand what you are proposing:

You want a script to scan all the movie files in a directory. It then assumes the filename is the title of the movie. Using the title, it searches IMDB and retrieves all the relevant information. If there is more than 1 result for the title, it displays a list and allows the user to select the one they want.

My only question is what information should be retrieved? I personally don't think it should get the entire page. Is there some specific info you want?

Cool! Okay I've not put much thinking into that, but looking at a movie page on IMDb:
[LIST]
[*]Correct title and release year (main header)
[*]Director
[*]Writer
[*]Genre
[*]Plot summary (there's a link there)
[*]User rating (x out of 10 stars)
[*]Also known as (for those foreign movies)
[*]Runtime
[*]Country
[*]Language
[*]Color
[*]Aspect ratio
[*]Sound mix
[*]Certification
[/LIST]

Another function to rename directory or filename to the correct title of the movie would be sweet. Maybe with director and release year in parenthesis, like: 
"This Is The Title (Some Director, 2000)"

---

### Post by nhandler on 2008-03-08
I currently have it only analyzing the .mp4 files in the folder for testing purposes. It would be easy to add other file extensions to analyze as well. My real goal is to have it use the mime-type to determine if the file is a movie. That way, it will work on movies with any extension (or no extension).

I could probably make the script check if the argument passed to it is a file or folder. If it is a folder, it will analyze all of the movies in it. If it is a file, it will check if it is a movie, and then it will analyze it.

I should be able to have it get most of the information you want. By "Plot Summary", do you mean the Plot Synopsis or Plot Outline. Personally, I think the Plot Outline would be a better choice since the Plot Synopsis is very long.

I might implement the rename function later. For now, I just want to get the actual script working. My goal is to have it done by the end of the weekend, but it might take a little longer depending on whether or not I run into problems.

---

### Post by nhandler on 2008-03-08
I got the script working! It will successfully download all the movie info from imdb and display it in the terminal. I also expanded the list of file extensions that it considers as movies. I still have not implemented the rename feature. It also still doesn't check the mime type of the file to check if it is a movie. This script currently must be run from the terminal. I will try and make it a nautilus script (that will appear in the right click menu) for the next version. The URL of the script can be found below. Please remember, I have not had a chance to clean up the code. It is extremely sloppy. However, it *does* work. I am open to any suggestions.

[http://paste.ubuntu-nl.org/58934/](http://paste.ubuntu-nl.org/58934/)

P.S. You had suggested renaming the file to MovieName(Director,Year).extension. For movies that have more than one director, should it include all of them? If not, what should it include?

---

### Post by graabein on 2008-03-10
Wow, cool that you're picking up on this! 

I'd figure just use the first director named if there's more than one. You'd have to try out different test cases. Too bad if one of the Coen brothers got snubbed every time though, LOL. 

Supplying both plot outline and plot summary would be nice. The summary is usually under the *more* button. I agree that the synopsis is far too much. 

I probably don't have time to try out the script just yet, but keep up the good work! Have you looked at the [g-scripts page]("http://g-scripts.sourceforge.net/") for Nautilus?

---

### Post by meastp on 2008-03-10
I have done something similar for the tv-show section of imdb. This is not a nautilus script, though, but a program written in python/gtk+.

The program will correct file names such as hustle.s01e01.avi to Hustle - S01E01 - The Con Is On.avi

information about where to get the episode information, and different ways to spell the show, is stored in a xml file.

meastp

---

### Post by nhandler on 2008-03-10
> **graabein said:**
> Wow, cool that you're picking up on this! 

I'd figure just use the first director named if there's more than one. You'd have to try out different test cases. Too bad if one of the Coen brothers got snubbed every time though, LOL. 

Supplying both plot outline and plot summary would be nice. The summary is usually under the *more* button. I agree that the synopsis is far too much. 

I probably don't have time to try out the script just yet, but keep up the good work! Have you looked at the [g-scripts page]("http://g-scripts.sourceforge.net/") for Nautilus?

I decided that the rename function should just rename the movie to the official movie title. If it were to rename it to "Title(Director,Year)", the script would be unable to locate the movie if it were to be run a second time. You can change this feature by modifying line number 255. Whatever it returns becomes the name of the file.

I quickly added an option to display the full movie summary. That way, it isn't displayed every time the script is run. In a later version, I will make it get displayed in a neater fashion.

In order to make it easier to read the output of the script, I made the headings bold. This may or may not work depending on what shell you are using. If you know a bit about escape sequences in bash, you can modify $startFormat and $endFormat to change how they look. I left an example of how to make the headings underlined instead of bold in the comments near the top.

I have been to g-scripts before. Don't worry, I will get this turned into a working nautilus script sooner or later.

Please run the script when you get a chance. I really would like some input.

[http://paste.ubuntu-nl.org/59215/](http://paste.ubuntu-nl.org/59215/)

---

### Post by nhandler on 2008-03-14
graabein, I would really appreciate any feedback on the script.

---

### Post by graabein on 2008-03-17
Hello! I've been busy the last week as I mentioned but now I'm on holiday and I'll try it out tonight or tomorrow.

UPDATE: OK I tried it now and it looks great! Here's an output (I created an empty text file named *capote.avi*):

> $ perl ./imdb.pl 
**FILE**: Capote.avi
1. Capote (2005)  

# Of Correct Title: 1
URL: [http://www.imdb.com/title/tt0379725](http://www.imdb.com/title/tt0379725)

**TITLE**: Capote
**YEAR**: 2005
**USER RATING**: 7.7/10
**DIRECTOR(S)**: Bennett Miller
**WRITER(S)**: Dan Futterman (screenplay)Gerald Clarke (book)
**RELEASE DATE**: 3 February 2006 (USA) 
**GENRE**: Biography / Crime / Drama
**TAGLINE**: Biography / Crime / Drama
**PLOT OUTLINE**: Truman Capote (Hoffman), during his research for his book In Cold Blood, an account of the murder of a Kansas family, the writer develops a close relationship with Perry Smith, one of the killers.
**RUNTIME**: 114 min  / Canada:110 min (Toronto International Film Festival)
**COUNTRY**: Canada / USA
**LANGUAGE**: English
**COLOR**: Color 
**ASPECT RATIO**: 2.35 : 1
**SOUND MIX**: Dolby Digital 
**CERTIFICATION**: Hungary:16  / Germany:12  / Brazil:14  / Finland:K-15  / Switzerland:14 (canton of Geneva) / Switzerland:14 (canton of Vaud) / Hong Kong:IIB  / Canada:PG (Ontario) / Singapore:NC-16  / USA:R (certificate #41953) / UK:15  / South Korea:15  / Netherlands:16  / Canada:13+ (Quebec) / Ireland:15A  / Iceland:16  / Canada:14A (British Columbia) / Australia:M  / Argentina:13  / France:U  / Norway:15  / Malaysia:U  / Sweden:11 
Display Full Movie Summary (Y,N)? Y
**MOVIE SUMMARY**:
In 1959, Truman Capote, a popular writer for The New Yorker, learns about the horrific and senseless murder of a family of four in Holcomb, Kansas. Inspired by the story material, Capote and his partner, Harper Lee, travel to the town to research for an article. However, as Capote digs deeper into the story, he is inspired to expand the project into what would be his greatest work, In Cold Blood. To that end, he arranges extensive interviews with the prisoners, especially with Perry Smith, a quiet and articulate man with a troubled history. As he works on his book, Capote feels some compassion for Perry which in part prompts him to help the prisoners to some degree. However, that feeling deeply conflicts with his need for closure for his book which only an execution can provide. That conflict and the mixed motives for both interviewer and subject make for a troubling experience that would produce an literary account that would redefine modern non-fiction.
 Written by
 Kenneth Chisholm (kchishol@rogers.com)
  
On the night of 14 November 1959, in Holcomb, Kansas, a farmhouse is broken into by the criminals Perry Smith and Dick Hickock that expect to get US$ 10,000.00. With the policy of "no witness", the murderers kill the entire family. The homosexual writer Truman Capote travels to the small town with his friend Nelle Harper Lee and decide to use the topic to write a book. When the killers are arrested, he becomes friend of Perry for his own interest and then he falls in love for him, and gets a new lawyer for them, postponing their execution until 14 April 1965.
 Written by
 Claudio Carvalho, Rio de Janeiro, Brazil



I'll take a closer look at it and do more runs later on.

---

### Post by IsawSp4rks on 2008-03-17
Awesome idea graabien and great work Cheater!  Kudos to you both.

---

### Post by graabein on 2008-03-19
Hi Cheater, I take it you're pretty good with regular expressions and string parsing? Cause I think the search function needs a bit of work. 

I tried the following test cases:
[LIST]
[*]Capote.(2005).BlahBlah.avi
[*]Capote.(2005).DVD.avi
[*]Capote.(2005).avi
[/LIST]

and none of them yielded any result. 

Maybe remove substrings like (nnnn) and [nnnn] etc and characters following the year part? Then use the year when filtering more than one search hit? Just an idea.

---

### Post by nhandler on 2008-03-19
> **graabein said:**
> Hi Cheater, I take it you're pretty good with regular expressions and string parsing? Cause I think the search function needs a bit of work. 

I tried the following test cases:
[LIST]
[*]Capote.(2005).BlahBlah.avi
[*]Capote.(2005).DVD.avi
[*]Capote.(2005).avi
[/LIST]

and none of them yielded any result. 

Maybe remove substrings like (nnnn) and [nnnn] etc and characters following the year part? Then use the year when filtering more than one search hit? Just an idea.

Ok, I made the script look for a () or [] pair. It then removes the parentheses or brackets, anything in between them, and anything after them. It will now work for all of the test cases you posted.

I also added a quick check before it renames the file. Before, if you had a file named Capote.avi, it would get overwritten if you tried running the script on any of the test cases. Now, the script checks to make sure it isn't overwriting any files before it renames the movie.

[http://paste.ubuntu-nl.org/60213/](http://paste.ubuntu-nl.org/60213/)

---

### Post by graabein on 2008-03-20
Good stuff. I'm running some more tests. Two things stand out though. 

Renaming the file(s) should not be automatic. There should be a question like with the full summary display, or maybe both these things should be default off, and enabled through switches when you run the script?

Like **--full-summary** and **--rename-files**?


I tried with the file *hitman.avi* and according to [IMDb]("http://www.imdb.com/title/tt0465494/") this movie don't have a tagline but the script shows the same as the previous category (genre). So remember to reset the string variables.


And I still feel the rename function would be better if it included director or at least release year. There are so many movies with similar names it's impossible to keep track of every one with just the title...

---

### Post by graabein on 2008-03-20
More test data. 

```
$ perl ./imdb.pl 
FILE: The.Water.Horse-Legend.Of.The.Deep.avi
1. The Water Horse: Legend of the Deep (2007)  Titles (Partial Matches) (Displaying 1 Result) 1.
2. Starz Special: The Water Horse: Legend of the Deep (2007) (TV)  

# Of Correct Title: 
```

Some line breaks in there would be sweet and the **1.** at the end of the line before option 2 is pretty confusing. Can you get rid of these?

You should also add a choice to cancel the script if no matches fit. Maybe put it up as option 0 or something, I don't know what's "best".

Good work btw!

---

### Post by graabein on 2008-03-20
Roman numbers seem to mess up either IMDb's search engine or could it be something in the string parsing?

```
$ perl ./imdb.pl 
FILE: Saw IV.avi

No Matches!
```

Renamed to *Saw 4.avi*

```
$ perl ./imdb.pl 
FILE: Saw 4.avi
1. Saw IV (2007) 
2. Saw (2004) 
3. Saw II (2005) 
4. Saw III (2006) 
5. The Texas Chain Saw Massacre (1974)  

# Of Correct Title: 
Argument "" isn't numeric in numeric lt (<) at ./imdb.pl line 90, <STDIN> line 1.
# Must Be >= 1
# Of Correct Title: 
```

And instead of choosing a line number I hit enter. 

Maybe change it to something like this?
**# Of Correct Title (0 = Cancel): **

---

### Post by nhandler on 2008-03-20
Thanks a lot for all of the feedback. I really appreciate it. In this new update, I added a few command line arguments that you can pass to the script.

--summary (-s)      This causes the full summary to be displayed without prompting
--rename (-r)         This causes all files to be renamed without prompting. It will NOT overwrite files.
--force (-f)             This enables the rewrite function of the script to overwrite existing files.

I also added some checks to the script. Now, it will tell you if it is unable to retrieve certain information about the movie. This should fix the hitman tagline problem.

I personally like my movies to just be called MoveTitle.extension. To make it name the movies in the format MovieTitle(Year).extension, uncomment line 402 (remove the #), and comment out line 403 (Place a # at the beginning of the line).

The issue with the waterhorse has been fixed.

Now, when the script is prompting you to select the appropriate title, you can hit ENTER without typing anything to select the first result (this is the same as typing 1). You can also enter 0 to skip to the next file.

The one issue that I have not addressed is the Saw IV one. This issue is caused not by the roman numerals, but because a search for "Saw IV" takes you directly to the Saw IV page on IMDB. It doesn't display the search results like other movie titles. This problem will take a little extra time to fix.

[http://paste.ubuntu-nl.org/60368/](http://paste.ubuntu-nl.org/60368/)

---

### Post by hlverstoep on 2008-03-23
A few days ago I stumbled on (almost) the same problem. I solved it with a script too: [http://paste.ubuntu-nl.org/60747/]("http://paste.ubuntu-nl.org/60747/"). Maybe you can find some new ideas in it...

It does pretty much the same, but there are a few differences. My movie directory layout is: "movies/TITLE (YEAR)/file.ext". When you place the script in ~/.gnome2/nautilus-scripts/ and make it executable you can do these things:
[LIST=1]
[*]Run the script by right-clicking in a directory: when the directory contains torrent files, search for the movies. Otherwise search for the directory name.
[*]Run the script by right-clicking on a file: when the file is a torrent file, search for the movie. Otherwise search for the parent directory name.
[*]Run the script by right-clicking on a directory: same as 1.
[*]It also possible to select multiple folders/files and then run the script by right-clicking on the selection.
[*]All searches with IMDb are opened in the default browser.
[/LIST]

---

### Post by graabein on 2008-04-22
**aeiah** also has a script for this. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?p=4621556"). 

Looks like he's using Google's I'm feeling lucky search with the movie name and open Firefox with the url.

---

### Post by nhandler on 2008-04-22
It seems a lot of people are interested in having the script open up the default internet browser to the IMDB page for the movie. As a result, I have added that feature. After you select the correct title for the movie, you will be asked if the script should launch the default browser and open the IMDB page for the movie. You can also pass the script the *--browser* or *-b* arguments to automatically launch the browser without asking the user.

I also added support for passing the script an individual file instead of a directory. The only limitation is that the rename function is currently not working, so it has been disabled. You can still use the rename function when you run the script on a directory, just not when you run it on an individual file.

As always, post any feedback in this thread.

[http://paste.ubuntu-nl.org/64048/](http://paste.ubuntu-nl.org/64048/)

---

### Post by cprofitt on 2008-06-22
> **kool_kat_os said:**
> either im retarded or you avatar looks like Borat (no offense intended:-) )

I am not going to call you retarded, but you are definitely young... that is Tom Selleck from his Magnum PI days. If you were over the age of ten during the 1980s or 1990s you should have known who this guy was... most women were gaga about him... I doubt that Borat has solicited the same reaction.

---

### Post by nhandler on 2008-10-11
Sorry to bump this old thread, but I recently got a request for this script. Since all of the links in this thread are invalid, there is currently no way to access it. In order to make sure that people have access to the script, I am going to add it to this post in <code> tags.

Enjoy!

```
#!/usr/bin/perl 
#Author: Nathan Handler <nhandler@ubuntu.com>
#File Name: imdb.pl
#Description: Retrieves Infromation about all Movies in a Specified Directory from IMDB.com
#Date: April 22, 2008
#Version 0.2.7
#Usage: perl ./imdb.pl /PATH/TO/MOVIES
#(If No Path is Given, The Script Assumes The Current (.) Directory)
use LWP::Simple;

$movieDir=shift || ".";
$summary=0;
$rename=0;
$force=0;
$browser=0;

#Bold
$startFormat="\033[1m";
$endFormat="\033[0m";

#Underline
#$startFormat="\033[4m";
#$endFormat="\033[0m";

foreach $argnum (0 .. $#ARGV) {
	chomp $ARGV[$argnum];
	if($ARGV[$argnum]=~m/^\-\-summary$/i) {
		$summary=1;
	}
	elsif($ARGV[$argnum]=~m/^\-s$/i) {
		$summary=1;
	}
	elsif($ARGV[$argnum]=~m/^\-\-rename$/i) {
		$rename=1;
	}
	elsif($ARGV[$argnum]=~m/^\-r$/i) {
		$rename=1;
	}
	elsif($ARGV[$argnum]=~m/^\-\-force$/i) {
		$force=1;
	}
	elsif($ARGV[$argnum]=~m/^\-f$/i) {
		$force=1;
	}
	elsif($ARGV[$argnum]=~m/^\-\-browser$/i) {
		$browser=1;
	}
	elsif($ARGV[$argnum]=~m/^\-b$/i) {
		$browser=1;
	}
}
if (-d $movieDir) {
	opendir(DIR,"$movieDir") or die "Can Not Open Movie Directory ($movieDir): $!";
	@files=readdir(DIR);
	closedir(DIR);
	foreach $file (@files) {
		if($file=~m/^.*\.(mp4|avi|mpg|3gp|flv|mov|wmv)$/i) {	#This is the list of movie file extensions
			$origFile=$file;
			chomp $origFile;
			$origFile=~m/^.*\.(.*)$/;
			$extension=$1;
			chomp $extension;
			$ctr=0;
			$file=~s/\.(mp4|avi|mpg|3gp|flv|mov|wmv)$//i;	#This list should match the one above
			$file=~s/\(.*\).*$//ig;
			$file=~s/\[.*\].*$//ig;
			print "$startFormat" . "FILE" . "$endFormat" . ": $origFile\n";
			$content=get("http://www.imdb.com/find?q=$file");
			die "Couln't Get $origFile" unless defined $content;
			$content=~s/^.*\<b\>Popular Titles\<\/b\>//is;
			$content=~s/\n.*$//s;
			$content=~s/\<img src.*?\>//ig;
			$content=~s/\<table.*?\>//ig;
			$content=~s/\<\/table.*?\>//ig;
			$content=~s/\<tr.*?\>//ig;
			$content=~s/\<\/tr.*?\>//ig;
			$content=~s/\<td.*?\>//ig;
			$content=~s/\<\/td.*?\>//ig;
			$content=~s/\&nbsp\;//ig;
			$content=~s/\<br\>//ig;
			$content=~s/\<em\>//ig;
			$content=~s/\<\/em\>//ig;
			$content=~s/\<small\>//ig;
			$content=~s/\<\/small\>//ig;
			$content=~s/\<b\>//ig;
			$content=~s/\<\/b\>//ig;
	                $content=~s/\<p\>//ig;
	                $content=~s/\<\/p\>//ig;
			$content=~s/Titles \(Partial Matches\).*$//si;
			$content=~s/Titles \(Exact Matches\).*$//si;
			$content=~s/Titles \(Approx Matches\).*$//si;
			$content=~s/Characters \(Exact Matches\).*$//si;
			$content=~s/Characters \(Approx Matches\).*$//si;
			$content=~s/Names \(Approx Matches\).*$//si;
			@lines=split(/\<a href\=/,$content);
			foreach $line (@lines) {
				$line=~s/\".*?\" onClick.*?\>//;
				$line=~s/^\<\/a\>.*$//;
				$line=~s/\<\/a\>//;
				$line=~s/\&\#160.*$//;
				$line=~s/^\s.*$//;
				$line=~s/\"\/title\///;
				$line=~s/\/\"\>/\:/;
				$line=~s/\&\#\d+\;//;		
				if($line!~/^$/) {
					($code,$title)=split(/\:/,$line,2);
					$codes[$ctr]=$code;
					chomp $line;
					print $ctr+1 . ". " . $title . "\n";
					$ctr++;
				}
			}
			$ctr--;	
			print "\n";
			if($ctr<0) {
				print "No Matches!\n";
			}
			else {
				$num=-1;			
				getNum: while ($num<0 || $num>$ctr+1) {
					print "# Of Correct Title (0=Cancel): ";
					$num=<STDIN>;
					chomp $num;
					if($num=~m/^$/) {
						last getNum;
					}
					if($num<0) {
						print "# Must Be >= 0\n";
					}
					if($num>$ctr+1) {
						print "# Must Be <= $ctr\n";
					}
				}
				if($num=~m/^$/) {
					$num=1;
				}
				if($num==0) {
					next;
				}
				$num--;
				$id=$codes[$num];
				$url="http://www.imdb.com/title/$id";
				print "URL: $url\n\n";
				if($browser==0) {
					do {
						print "Open IMDB In Internet Browser (Y,N)? ";
						$choice=<STDIN>;
						chomp $choice;
						if(($choice!~/^y$/i) && ($choice!~/^n$/i)) {
							print "You Must Enter Either \"Y\" or \"N\"\n";
						}
					} while (($choice!~/^y$/i) && ($choice!~/^n$/i));
					if($choice=~/^y$/i) {
						`gnome-www-browser $url`;
					}
				}
				elsif($browser==1) {
					`gnome-www-browser $url`;
				}
				$name=&parseMovie($url);
				if($summary==0) {
					do {
						print "Display Full Movie Summary (Y,N)? ";
						$choice=<STDIN>;
						chomp $choice;
						if(($choice!~/^y$/i) && ($choice!~/^n$/i)) {
							print "You Must Enter Either \"Y\" or \"N\"\n";
						}
					} while (($choice!~/^y$/i) && ($choice!~/^n$/i));
					if($choice=~/^y$/i) {
						&plotSummary($url);
					}
				}
				elsif($summary==1) {
					&plotSummary($url);
				}
				if($rename==1) {
					if($force==0) {
						if (-e "$movieDir/$name.$extension") {
							print "Can Not Rename File. $movieDir/$name.$extension already exists!\n";
						}
						else {
							rename("$movieDir/$origFile", "$movieDir/$name.$extension");
						}
					}
					elsif($force==1) {
						rename("$movieDir/$origFile", "$movieDir/$name.$extension");
					}
				}
				elsif($rename==0) {
					do {
						print "Rename File (Y,N)? ";
						$choice=<STDIN>;
						chomp $choice;
						if(($choice!~/^y$/i) && ($choice!~/^n$/i)) {
							print "You Must Enter Either \"Y\" or \"N\"\n";
						}
					} while (($choice!~/^y$/i) && ($choice!~/^n$/i));
					if($choice=~/^y$/i) {
						if($force==0) {
							if (-e "$movieDir/$name.$extension") {
								print "Can Not Rename File. $movieDir/$name.$extension already exists!\n";
							}
							else {
								rename("$movieDir/$origFile", "$movieDir/$name.$extension");
							}
						}
						else {
							rename("$movieDir/$origFile", "$movieDir/$name.$extension");
						}
					}
				}
				print "\n";
			}
		}
	}
}
else {
	if(! -e $movieDir) {
		die("Can Not Open Movie: $movieDir\n");
	}
	$file=$movieDir;
	$file=~s/^.*\///g;
	$origFile=$file;
	chomp $origFile;
	$origFile=~m/^.*\.(.*)$/;
	$extension=$1;
	chomp $extension;
	$ctr=0;
	$file=~s/\.(mp4|avi|mpg|3gp|flv|mov|wmv)$//i;	#This list should match the one above
	$file=~s/\(.*\).*$//ig;
	$file=~s/\[.*\].*$//ig;
	print "$startFormat" . "FILE" . "$endFormat" . ": $origFile\n";
	$content=get("http://www.imdb.com/find?q=$file");
	die "Couln't Get $origFile" unless defined $content;
	$content=~s/^.*\<b\>Popular Titles\<\/b\>//is;
	$content=~s/\n.*$//s;
	$content=~s/\<img src.*?\>//ig;
	$content=~s/\<table.*?\>//ig;
	$content=~s/\<\/table.*?\>//ig;
	$content=~s/\<tr.*?\>//ig;
	$content=~s/\<\/tr.*?\>//ig;
	$content=~s/\<td.*?\>//ig;
	$content=~s/\<\/td.*?\>//ig;
	$content=~s/\&nbsp\;//ig;
	$content=~s/\<br\>//ig;
	$content=~s/\<em\>//ig;
	$content=~s/\<\/em\>//ig;
	$content=~s/\<small\>//ig;
	$content=~s/\<\/small\>//ig;
	$content=~s/\<b\>//ig;
	$content=~s/\<\/b\>//ig;
        $content=~s/\<p\>//ig;
        $content=~s/\<\/p\>//ig;
	$content=~s/Titles \(Partial Matches\).*$//si;
	$content=~s/Titles \(Exact Matches\).*$//si;
	$content=~s/Titles \(Approx Matches\).*$//si;
	$content=~s/Characters \(Exact Matches\).*$//si;
	$content=~s/Characters \(Approx Matches\).*$//si;
	$content=~s/Names \(Approx Matches\).*$//si;
	@lines=split(/\<a href\=/,$content);
	foreach $line (@lines) {
		$line=~s/\".*?\" onClick.*?\>//;
		$line=~s/^\<\/a\>.*$//;
		$line=~s/\<\/a\>//;
		$line=~s/\&\#160.*$//;
		$line=~s/^\s.*$//;
		$line=~s/\"\/title\///;
		$line=~s/\/\"\>/\:/;
		$line=~s/\&\#\d+\;//;		
		if($line!~/^$/) {
			($code,$title)=split(/\:/,$line,2);
			$codes[$ctr]=$code;
			chomp $line;
			print $ctr+1 . ". " . $title . "\n";
			$ctr++;
		}
	}
	$ctr--;	
	print "\n";
	if($ctr<0) {
		print "No Matches!\n";
	}
	else {
		$num=-1;			
		getNum: while ($num<0 || $num>$ctr+1) {
			print "# Of Correct Title (0=Cancel): ";
			$num=<STDIN>;
			chomp $num;
			if($num=~m/^$/) {
				last getNum;
			}
			if($num<0) {
				print "# Must Be >= 0\n";
			}
			if($num>$ctr+1) {
				print "# Must Be <= $ctr\n";
			}
		}
		if($num=~m/^$/) {
			$num=1;
		}
		if($num==0) {
			die;
		}
		$num--;
		$id=$codes[$num];
		$url="http://www.imdb.com/title/$id";
		print "URL: $url\n\n";
		if($browser==0) {
			do {
				print "Open IMDB In Internet Browser (Y,N)? ";
				$choice=<STDIN>;
				chomp $choice;
				if(($choice!~/^y$/i) && ($choice!~/^n$/i)) {
					print "You Must Enter Either \"Y\" or \"N\"\n";
				}
			} while (($choice!~/^y$/i) && ($choice!~/^n$/i));
			if($choice=~/^y$/i) {
				`gnome-www-browser $url`;
			}
		}
		elsif($browser==1) {
			`gnome-www-browser $url`;
		}
		$name=&parseMovie($url);
		if($summary==0) {
			do {
				print "Display Full Movie Summary (Y,N)? ";
				$choice=<STDIN>;
				chomp $choice;
				if(($choice!~/^y$/i) && ($choice!~/^n$/i)) {
					print "You Must Enter Either \"Y\" or \"N\"\n";
				}
			} while (($choice!~/^y$/i) && ($choice!~/^n$/i));
			if($choice=~/^y$/i) {
				&plotSummary($url);
			}
		}
		elsif($summary==1) {
			&plotSummary($url);
		}
#		if($rename==1) {
#			if($force==0) {
#				if (-e "$movieDir/$name.$extension") {
#					print "Can Not Rename File. $movieDir/$name.$extension already exists!\n";
#				}
#				else {
#					rename("$movieDir/$origFile", "$movieDir/$name.$extension");
#				}
#			}
#			elsif($force==1) {
#				rename("$movieDir/$origFile", "$movieDir/$name.$extension");
#			}
#		}
#		elsif($rename==0) {
#			do {
#				print "Rename File (Y,N)? ";
#				$choice=<STDIN>;
#				chomp $choice;
#				if(($choice!~/^y$/i) && ($choice!~/^n$/i)) {
#					print "You Must Enter Either \"Y\" or \"N\"\n";
#				}
#			} while (($choice!~/^y$/i) && ($choice!~/^n$/i));
#			if($choice=~/^y$/i) {
#				if($force==0) {
#					if (-e "$movieDir/$name.$extension") {
#						print "Can Not Rename File. $movieDir/$name.$extension already exists!\n";
#					}
#					else {
#						rename("$movieDir/$origFile", "$movieDir/$name.$extension");
#					}
#				}
#				else {
#					rename("$movieDir/$origFile", "$movieDir/$name.$extension");
#				}
#			}
#		}
		print "\n";
	}
}
sub parseMovie {
	$movieURL=shift;
	$page=get("$url");
	die "Couln't Get $movieURL" unless defined $page;
	$page=~s/^.*\<div id\=\"tn15title\"\>//is;
	$page=~m/\<h1\>(.*?) \<span\>/;
	$title=$1;
	chomp $title;
	$page=~m/\<a href\=.*?\>(.*?)\<\/a\>\)/;
	$year=$1;
	chomp $year;
	if($page!~m/^.*?\<b\>User Rating\:\<\/b\>/is) {
		$userRating="Can Not Retrieve User Rating!";
	}
	else {
		$page=~s/^.*?\<b\>User Rating\:\<\/b\>//is;
		$page=~m/\<b\>(.*?)\<\/b\>/;
		$userRating=$1;
		chomp $userRating;
	}
	if($page!~m/^.*?\<h5\>(Director|Directors)\:\<\/h5\>/is) {
		$directors="Can Not Retrieve Director(s)";
	}
	else {
		$page=~s/^.*?\<h5\>(Director|Directors)\:\<\/h5\>//is;
		$page=~m/^(.*?)\<\/div\>/si;
		$directors=$1;
		$directors=~s/^.*?\<\/h5\>//is;
		$directors=~s/^\n//s;
		$directors=~s/\<a.*?\>//gis;
		$directors=~s/\<\/a\>//gis;
		$directors=~s/\<br\/\>$//gi;
		$directors=~s/\<br\/\>/ \/ /gis;
		$directors=~s/\&\#.*?\;/\/ /gis;
		chomp $directors;
	}
	if($page!~m/^.*?\<h5\>(Writer|Writers)/is) {
		$writers="Can Not Retrieve Writer(s)";
	}
	else {
		$page=~s/^.*?\<h5\>(Writer|Writers)//is;
		$page=~m/^(.*?)\<\/div\>/is;
		$writers=$1;
		$writers=~s/^.*?\<\/h5\>//is;
		$writers=~s/^\n//s;
		$writers=~s/\<a.*?\>//gis;
		$writers=~s/\<\/a\>//gis;
		$writers=~s/\<br\/\>//gis;
		$writers=~s/\&\#.*?\;/\/ /gis;
		chomp $writers;
	}
	if($page!~m/^.*?\<h5\>Release Date/is) {
		$releaseDate="Can Not Retrieve Release Date!";
	}
	else {
		$page=~s/^.*?\<h5\>Release Date//is;
		$page=~m/^(.*?)\<a/is;
		$releaseDate=$1;
		$releaseDate=~s/\<\/h5\>//gsi;
		$releaseDate=~s/\n//gsi;
		$releaseDate=~s/\://si;
		$releaseDate=~s/^\s//s;
		chomp $releaseDate;
	}
	if($page!~m/^.*?\<h5\>Genre:/is) {
		$genre="Can Not Retrieve Genre!";
	}
	else {
		$page=~s/^.*?\<h5\>Genre://is;
		$page=~m/^\<\/h5\>(.*?)\<\/div\>/is;
		$genre=$1;
		$genre=~s/\<a.*?\>//gis;
		$genre=~s/\<\/a\>//gis;
		$genre=~s/\smore$//i;
		$genre=~s/^\n//s;
		chomp $genre;
	}
	if($page!~m/^.*?\<h5\>Tagline\:/is) {
		$tagline="Can Not Retrieve Tagline!";
	}
	else {
		$page=~s/^.*?\<h5\>Tagline\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$tagline=$1;
		$tagline=~s/^\n//s;
		$tagline=~s/\<a.*?\>//gis;
		$tagline=~s/\<\/a\>//gis;
		$tagline=~s/\smore$//i;
		chomp $tagline;
	}
	if($page!~m/^.*?\<h5\>Plot Outline\:/is) {
		$plotOutline="Can Not Retrieve Plot Outline!";
	}
	else {
		$page=~s/^.*?\<h5\>Plot Outline\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$plotOutline=$1;
		$plotOutline=~s/^\s+\n//s;
		$plotOutline=~s/\<a.*?\>//gis;
		$plotOutline=~s/\<\/a\>//gis;
		$plotOutline=~s/\smore$//i;
		chomp $plotOutline;
	}
	if($page!~m/^.*?\<h5\>Runtime\:/is) {
		$runtime="Can Not Retrieve Runtime!";
	}
	else {
		$page=~s/^.*?\<h5\>Runtime\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$runtime=$1;
		$runtime=~s/^\n//s;
		chomp $runtime;
	}
	if($page!~m/^.*?\<h5\>Country\:/is) {
		$country="Can Not Retrieve Country!";
	}
	else {
		$page=~s/^.*?\<h5\>Country\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$country=$1;
		$country=~s/^\n//s;
		$country=~s/\<a.*?\>//gis;
		$country=~s/\<\/a\>//gis;
		chomp $country;
	}
	if($page!~m/^.*?\<h5\>Language\:/is) {
		$language="Can Not Retrieve Language!";
	}
	else {
		$page=~s/^.*?\<h5\>Language\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$language=$1;
		$language=~s/^\n//s;
		$language=~s/\<a.*?\>//gis;
		$language=~s/\<\/a\>//gis;
		chomp $language;
	}
	if($page!~m/^.*?\<h5\>Color\:/is) {
		$color="Can Not Retrieve Color!";
	}
	else {
		$page=~s/^.*?\<h5\>Color\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$color=$1;
		$color=~s/^\n//s;
		$color=~s/\<a.*?\>//gis;
		$color=~s/\<\/a\>//gis;
		$color=~s/\<i\>//gis;
		$color=~s/\<\/i\>//gis;
		chomp $color;
	}
	if($page!~m/^.*?\<h5\>Aspect Ratio\:/is) {
		$aspectRatio="Can Not Retrieve Aspect Ratio!";
	}
	else {
		$page=~s/^.*?\<h5\>Aspect Ratio\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$aspectRatio=$1;
		$aspectRatio=~s/^\n//s;
		$aspectRatio=~s/\<a.*?\>//gis;
		$aspectRatio=~s/\<\/a\>//gis;
		$aspectRatio=~s/\smore$//i;
		chomp $aspectRatio;
	}
	if($page!~m/^.*?\<h5\>Sound Mix\:/is) {
		$soundMix="Can Not Retrieve Sound Mix!";
	}
	else {
		$page=~s/^.*?\<h5\>Sound Mix\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$soundMix=$1;
		$soundMix=~s/^\n//s;
		$soundMix=~s/\<a.*?\>//gis;
		$soundMix=~s/\<\/a\>//gis;
		$soundMix=~s/\<i\>//gis;
		$soundMix=~s/\<\/i\>//gis;
		chomp $soundMix;
	}
	if($page!~m/^.*?\<h5\>Certification\:/is) {
		$certification="Can Not Retrieve Certification!";
	}
	else {
		$page=~s/^.*?\<h5\>Certification\://is;
		$page=~m/\<\/h5\>(.*?)\<\/div\>/is;
		$certification=$1;
		$certification=~s/^\n//s;
		$certification=~s/\<a.*?\>//gis;
		$certification=~s/\<\/a\>//gis;
		$certification=~s/\<i\>//gis;
		$certification=~s/\<\/i\>//gis;
		chomp $certification;
	}
	print "$startFormat" . "TITLE" . "$endFormat" . ": $title\n";
	print "$startFormat" . "YEAR" . "$endFormat" . ": $year\n";
	print "$startFormat" . "USER RATING" . "$endFormat" . ": $userRating\n";
	print "$startFormat" . "DIRECTOR(S)" . "$endFormat" . ": $directors\n";
	print "$startFormat" . "WRITER(S)" . "$endFormat" . ": $writers\n";
	print "$startFormat" . "RELEASE DATE" . "$endFormat" . ": $releaseDate\n";
	print "$startFormat" . "GENRE" . "$endFormat" . ": $genre\n";
	print "$startFormat" . "TAGLINE" . "$endFormat" . ": $tagline\n";
	print "$startFormat" . "PLOT OUTLINE" . "$endFormat" . ": $plotOutline\n";
	print "$startFormat" . "RUNTIME" . "$endFormat" . ": $runtime\n";
	print "$startFormat" . "COUNTRY" . "$endFormat" . ": $country\n";
	print "$startFormat" . "LANGUAGE" . "$endFormat" . ": $language\n";
	print "$startFormat" . "COLOR" . "$endFormat" . ": $color\n";
	print "$startFormat" . "ASPECT RATIO" . "$endFormat" . ": $aspectRatio\n";
	print "$startFormat" . "SOUND MIX" . "$endFormat" . ": $soundMix\n";
	print "$startFormat" . "CERTIFICATION" . "$endFormat" . ": $certification\n";
	#return "title($year)";
	return "$title";
}
sub plotSummary {
	$movieURL=shift;
	$page=get("$url/plotsummary");
	die "Couln't Get $movieURL" unless defined $page;
	if($page!~m/^.*?<p class\=\"plotpar\"\>/is) {
		$page="Can Not Retrieve Summary!";
	}
	else {
		$page=~s/^.*?<p class\=\"plotpar\"\>//is;
		$page=~s/\<div class\=\"info\"\>.*$//is;
		$page=~s/\<a.*?\>//gis;
		$page=~s/\<\/a\>//gis;
		$page=~s/\<i\>//gis;
		$page=~s/\<\/i\>//gis;
		$page=~s/\<p.*?\>//gis;
		$page=~s/\<\/p\>//gis;
		$page=~s/\<hr\/\>//gis;
		$page=~s/\n+/\n/gis;
		$page=~s/^\n//is;
	}
	print "$startFormat" . "MOVIE SUMMARY:\n" . "$endFormat";
	print "$page\n";
}
```

---

