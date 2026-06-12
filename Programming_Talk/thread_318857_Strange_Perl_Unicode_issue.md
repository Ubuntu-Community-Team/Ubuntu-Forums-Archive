---
title: "Strange Perl Unicode issue"
date: 2006-12-14
forum: Programming Talk
---

### Post by Third Thoughts on 2006-12-14
I'm having a bizarre and annoying perl issue. I'm working on a script to automate the process of putting a magazine online. The magazine is put together with Adobe Incopy, so all of the articles are stored in .incx files. I'm writing a perl script that will scrape the article content out of the .incx files and then insert the article text into an html template.

The problem I've having is in trying to make the article text html friendly. The text from the .incx has some Unicode in it, specifically <U+2029>, the paragraph separator. I know the seperator is in there, because I can see it when I open the text with less. I want to replace it with the <p> tag. However, my script refuses to match the character. I've tried  two methods:
```
  if (/\x{2029}/) {print "HEY!!!"} /
``` or
```
use charnames ':full' ;
if (/\N{PARAGRAPH SEPARATOR}/) {print "HEY!!!"} 
```
But neither worked. 
Here's the bizarre thing though. This piece of code does work
```
use charnames ':full';
$test = "\N{PARAGRAPH SEPARATOR} I'm a paragraph separator.\n";
print $test ;

$_=$test ;
if (/\N{PARAGRAPH SEPARATOR}/) {print "HEY!!!"}
```
In other words, if I add the paragraph separator to a string myself, my script can recognize it, but when I bring in the text that already has the separator in it, my script can't recognize it. If you want to see the code fully in action, I've put the two relevant sub routines below. The first one is where I open the file and get the text, the second is where I try to make the replacement. 

```

#Gets passed the file path of the incx file and stores it in $content_file.
#Then opens the file and scrapes out the text I care about.
sub scrape_content_from_incx_file {
	local $content_file=$_[0];
		
	open(CONTENT, $content_file);
		@content=<CONTENT> ;
	
	local @article_content ;	
	local $i = 0 ;
	
        #Here we walk through each line and see if it has the string "<pcnt>c_."
        #As far as I can tell this string always preceeds the actual text of the article. 
        #Then we delete every line that doesn't contain "<pcnt>_c". 
        #I don't quite understand why this works. 
        #It seems that a number of the article lines should be deleted along with the extra lines,
        #but for some reason they aren't. I'm looking into this, 
        #but for now I'm sticking with what works. 
        #After we delete all the extra lines, we get rid of the all "<pcnt>_c"'s. 
	
        foreach $line (@content){
				
		$_=$line ;
		if (!/<pcnt>c_/) {
			$article_content[$i]="" ;
			}
		else {
			$_=$line ;
			s/<pcnt>c_//g ;
			s/<pcnt>//g ;
			s/<\/pcnt>//g ;
			#if (/[^.]\n/ &! /BY/)  {
			#	s/\n//g ;
			#}			

			$article_content[$i]=$_ ;	
			}
		#print $article_content[$i];
		$i++;		
		}
	
	@formatted_content = &make_content_html_friendly(@article_content) ;

	return @formatted_content;
	}	

#Replace troublesome characters with their nice counterparts to make valid html
sub make_content_html_friendly {
	local @content = @_;
	local @formatted_content ;
	local $i = 0 ;	
	
	

	#Parse for unfriendly characters, make replacments
	foreach $line (@content) {
		$_= $line ;
		s/\"/&quot\;/g ;
		if (/&/ &! /&amp\;/) {s/\&/&amp\;/g ;}
		s/\n//g ;		

               #Here's the part thats been plaguing me,
               #I've added the print HEY part to see if its at least matching things and it isn't.
               if (/\N{PARAGRAPH SEPARATOR}/) {print "HEY!!!"} 		
		s/\N{PARAGRAPH SEPARATOR}/<p>/g ;
		s/\t//g ;	
		$formatted_content[$i] = $_ ;
		$i++ ;
		}
	
	print @formatted_content ;
	return @formatted_content;
	}

```

---

### Post by slavik on 2006-12-15
try this:
```
if (/\x{2029}/g) {print "HEY!!!"} /
```

g switch means to match it globally. :)

You might want to store the entire thing in a single variable with:
```
$text = join '', <$filehandle>;
```

---

### Post by godwinoganiru on 2006-12-15
I am new to PERL and I don't know how to testrun my programs. I tried using FIREFOX Web browser but it will open the "open with" dialogue. Please can you help?

---

### Post by Third Thoughts on 2006-12-15
> **slavik said:**
> try this:
```
if (/\x{2029}/g) {print "HEY!!!"} /
```

g switch means to match it globally. :)

You might want to store the entire thing in a single variable with:
```
$text = join '', <$filehandle>;
```

Thanks slavik, but I figured it out. Turns out it wasn't a regex problem, I just had to let perl know what kind of string it was dealing with. I did this by inserting this command just after my foreach statement 
```

foreach $line (@content) {
		$line = pack "U0C*", unpack "C*", $line;	
```

> **godwinoganiru said:**
> I am new to PERL and I don't know how to testrun my programs. I tried using FIREFOX Web browser but it will open the "open with" dialogue. Please can you help?

Before I answer your question, I'd like to point out that you probably should have started a new thread. Generally if you have a new question you should start a new thread for it instead of posting on an unrelated one. You're question is more likely to get answered. Don't worry about it this time, just future reference. Now the answer.
You need to open up a terminal. Go Applications --> Accessories --> Terminal If you're not familiar with how to use the terminal go here [http://ubuntuforums.org/showthread.php?t=45651](http://ubuntuforums.org/showthread.php?t=45651)

Once you're at the terminal go to the directory where you've saved your script. Then type ```
perl your_script_name
```. It should run, with any output going to the terminal.

~Andrew S.

---

### Post by newsman on 2006-12-15
> 
I am new to PERL and I don't know how to testrun my programs. I tried using FIREFOX Web browser but it will open the "open with" dialogue. Please can you help?


if your running a script .... from an introductory book you probably need to call the perl interpreter to execute the script file...i have done this in windows...for a cgi script you need to put the file in a server in its designated cgi directory and then call the file (in this case, the server will handle the request and produce the output) if the server is not configured for cgi or the perl file is not placed in the cgi directory, the web browser will just open it as text file (and that may cause the browser to treat it as file that either you are trying to download or should open with another program.. thus the "open with" dialogue"

and yeah it should reall be in a new thread... and also i recommend you use a book for introduction to cgi as well... (i think your trying to use perl for cgi right.. thats why your using firefox????.....anyhoo perl can be used for many things espacially in linux besides cgi work in web server)

i recomend dietel's "perl how to program"... (did it three years ago)

---

