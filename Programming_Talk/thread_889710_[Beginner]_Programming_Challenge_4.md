---
title: "[Beginner] Programming Challenge: 4"
date: 2008-08-14
forum: Programming Talk
---

### Post by LaRoza on 2008-08-14
The last challenge was rather simple. All the languages used had all the functions built into the language.

Here is the last challenge: [http://ubuntuforums.org/showthread.php?t=884394](http://ubuntuforums.org/showthread.php?t=884394)

For this one, I ask that non beginners (that means you **[color=red]slavik[/color]**) do not post anything except possible advice. DO NOT POST SOLUTIONS IF YOU ARE NOT A BEGINNER!


[size=+1]The Challenge:[/size]
Now that we dealt with user IO and file IO, lets do a little networking. Most languages do not have this built in, but some have standard library functions for it.

The challenge will be simple, but will require the use of either another library or exploring the standard libraries. As many of you are using Python it seems, I will tell you that Python has standard libraries to do everything here, so explore the documentation page (you'll find that programmers spend a lot of time reviewing API's and documentation, so might as well practice now)

You will have to do the following:

[list]
[*] Write a program that will read a webpage and puts its text into a file named "index.xhtml"
[*] The test site will be: [http://laroza.freehostia.com/home/index.php](http://laroza.freehostia.com/home/index.php)
[*] That is the bare minimum requirements, but I would ask you try to make it work for any site.
[/list]

You do NOT have to:

[list]
[*] Have it do anything but download the single file of a web page, so ignore any external scripts or css.
[*] Have it to any rendering, just write it to a file (for opening with a browser, most likely)
[/list]

For extra credit:

[list]
[*] Have either prompt or use a command line argument to do do this with any webpage
[*] Have it name the output file after the title of the document (hint: text in the elements <title></title>, you can use xml or html parsers for this, or you can use regular expressions)
[/list]

The test page is valid XHTML 1.1 (and is valid XML). All conditions and extra credit can be done with standard Python. If you use another language or non standard libs, let me know exactly how to get your entry working.



[size=+1]Rules:[/size]
Do not copy code, but you can obviously read it :-)

Try not to comment on other submissions. It will be hard to judge changing entries. If you edit your code, post the new version and make it clear there is a new code.

[size=+1]How it will be judged[/size]
[list]
[*] It has to do what it is specified.
[/list]

As before, try to follow the following (although I think it won't come down to judging on this, as the challenge will be tricky for beginners):
[list]
[*] Clean code. Readable code is a must for being a programmer who wishes to possibly interact with others. Some languages can be more readable than others, so it will be judged on the effort of writing clean code, not which language is easier to read by design.
[*] Logical code. Be a programmer, not a code monkey :-)
[*] Commented code. If something is possibly unclear (like an obscure use of math), let the readers know. Do not over comment, and let the code speak for itself whenever you can. Have logical variable names and function names. (Excessive commenting is a minus factor)
[*] Working code. It has to work as it is posted. The codw will be read on the forum, so remember to use this guide to paste code if you don't know how: [http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)
[/list]

---

### Post by slavik on 2008-08-14
:( :cry:

I would've done it in C and Perl, too ...

---

### Post by TreeFinger on 2008-08-14
The website isn't a valid url. not sure if you meant for this or not.

Did you mean this? [http://laroza.freehostia.com/home/index.php](http://laroza.freehostia.com/home/index.php)

---

### Post by Titan8990 on 2008-08-14
Ehh, I was running through some example code on a tutorial and couldn't figure out why it was not working. Turns out that link you gave is dead.

---

### Post by M_the_C on 2008-08-14
When you say:
> ...puts its text into a file named "index.xhtml"Do you mean the source text, or just the words we see in a browser?  Like this:
> LaRoza
Computer Programming

   1. Home
   2. How to Start
   3. Forums
   4. Contact
   5. Applications

Learning to Program

See the Language Selector for a test to see what languages you might be interested in learning.

    * Learn to Program - My Wiki
    * Programming in Ubuntu
    * Learn to Program Forum

Valid XHTML 1.1 Also, thanks for keeping this going. :)

EDIT:  Should page come out without any of the colours or have I done something wrong?

---

### Post by nvteighen on 2008-08-14
Do I qualify as a beginner? :)

---

### Post by Kadrus on 2008-08-14
You should know for yourself ^

---

### Post by LaRoza on 2008-08-14
> **slavik said:**
> :( :cry:

I would've done it in C and Perl, too ...

Well, you can do a fancy one at the end, but for now, I'd like beginners to figure it out on their own. It isn't fair to them to post first (like you did last time. If your answer had been readable, I'd have moved it)

> **Titan8990 said:**
> Ehh, I was running through some example code on a tutorial and couldn't figure out why it was not working. Turns out that link you gave is dead.

Fixed it. Sorry about that.

> **M_the_C said:**
> When you say:
Do you mean the source text, or just the words we see in a browser?  Like this:
Also, thanks for keeping this going. :)


The source of the file. You don't have to deal with markup (unless you do the title thing).

Go to the site, and view the source.

---

### Post by Titan8990 on 2008-08-14
Here is my first draft. I will come up with another that will include the "extra credit".

[php]#!/usr/bin/env python

import urllib2

xhtml_file = open("index.xhtml", "w")

web = urllib2.urlopen('http://laroza.freehostia.com/home/index.php')

xhtml_file.write(web.read())

xhtml_file.close()[/php]


What is considered a "non-standard" library? Is it anything you have to import or libraries that are not included in the standard python package?

---

### Post by LaRoza on 2008-08-14
> **Titan8990 said:**
> 
What is considered a "non-standard" library? Is it anything you have to import or libraries that are not included in the standard python package?

Not part of the standard language. That is a standard library for Python.

---

### Post by dje on 2008-08-14
my first attempt, html parsing coming soon... i hope :D **( see post 18 )**
```
#!/usr/bin/env python

# import modules
import urllib2
import sys

class web_get:
	def __init__(self):
                # get desired web page
		print "Welcome - web page downloader\n"
		get_page = raw_input('Please enter web page to download: ')
                # test if web page given
		while get_page == "":
			print "You must enter a web page to continue"
			get_page = raw_input('Please enter web page to get: ')
		print "Please wait..."
                # open the web page
		try:
			web_page = urllib2.urlopen(get_page)
		except:
			print "\n--> An error ocurred, please try again (include the http://)"
			sys.exit(1)
                # write web page to file
		for line in web_page:
			open('web_page.xhtml', 'a').write(line)
		open('web_page.xhtml').close()
		print "Done"
                sys.exit(0)
if __name__ == '__main__':
	try:
		web_get()
	except KeyboardInterrupt:
		print "\n\nExiting..."
		sys.exit(0)

```

dje

---

### Post by jimi_hendrix on 2008-08-14
i would like to thank you for coming up with an abosultly burtal task that i am definetly going to try...any hints on what i could type into google to get help (like a name for what were doing)?

---

### Post by greps5 on 2008-08-14
I started learning Python yesterday, and I created this in Windows in Notepad++, so I'm not sure if anything needs to added for Linux/Ubuntu compatability as I've only been running my programs through the Windows console.  Anyway, here's my attempt:

[PHP]
# Beginner Challenge 4 in Python
# by greps5 8/14/08

import urllib2

a, b = 0, 0 # a = file-in fail/success flag, b = file-out flag

# # # Read in webpage source # # #
try:
	wbpg = raw_input("\nEnter the url of the desired webpage: ")
	print "\nLoading webpage source from %s ...\n" % wbpg
	webpage = urllib2.urlopen(wbpg)
	source = webpage.read()
	webpage.close()
	a = 1
except ValueError:
	print "Sorry, %s is not a valid url" % wbpg
except IOError:
	print "Error, unable to obtain source from %s" % wbpg
# # # End read-in # # #

# # # Write source to file index.xhtml # # #
if a == 1:	
	print "Saving webpage source to index.xhtml...\n"
	try:
		sourceOut = open('index.xhtml', 'w')
		sourceOut.write(source)
		sourceOut.close()
		b = 1
	except IOError:
		print "Error, unable to save source\n"
# # # End file-writing  # # #

if a == 1 and b ==1:
	print "Source was successfully processed!\n"
[/PHP]

I'll try to update it later to include the webpage <title>.  I also think I'll give it a try in Java when I get a chance.

---

### Post by LaRoza on 2008-08-14
> **jimi_hendrix said:**
> i would like to thank you for coming up with an abosultly burtal task that i am definetly going to try...any hints on what i could type into google to get help (like a name for what were doing)?

For C#, the class you can use are: HTTPWebRequest and HTTPWebResponse (they are .NET, so you'll have to look around if they aren't part of the ECMA standard (which mono follows))

Basically, you are downloading a web page, or doing http with a language.

---

### Post by jimi_hendrix on 2008-08-14
LaRoza you have to be inside my computer to know i was going to do C#

---

### Post by LaRoza on 2008-08-14
> **jimi_hendrix said:**
> laroza you have to be inside my computer to know i was going to do c#

&#2346;&#2381;&#2352;&#2340;&#2367;&#2352;&#2379;&#2343; &#2357;&#2381;&#2351;&#2352;&#2381;&#2341; &#2361;&#2376;

---

### Post by bobbocanfly on 2008-08-14
Quick attempt in Python. I have spent far too long attempting to learn Perl this week, which is obvious because of the mess of line 19.

```
import urllib2
import sys

#Try to get the address from args, else get it from a prompt
try:
    address = sys.argv[1]
except IndexError:
    address = str(raw_input("Address: "))

#Attempt to connect to the website
try:
    xhtml = urllib2.urlopen(address)
except urllib2.HTTPError:
    print "Could not connect to %s and pull down data" % address
    sys.exit(1)
    
#Read data from site and get title
data = xhtml.read()
title = data.split("<title>")[1].split("</title>")[0] #Crufty hack to get title

if len(title) < 1:
    print "Couldnt get page title, using address instead"
    title = address #If somehow we didnt get the title, write the the address

#Write data into the local file
open(title + ".xhtml", 'w').write(data)
print "%s -> %s.xhtml" % (address, title)
```

---

### Post by dje on 2008-08-14
here's my latest:
```
#!/usr/bin/env python

import urllib2
import sys
import os

class web_get:
	def __init__(self):
		print "Welcome - web page downloader\n"
		# get desired web page
		get_page = raw_input('Please enter web page to download: ')
		# test if web page given
		while get_page == "":
			print "You must enter a web page to continue"
			get_page = raw_input('Please enter web page to get: ')
		print "Please wait..."
		# open web page
		try:
			web_page = urllib2.urlopen(get_page)
		except:
			print "\n--> An error ocurred, please try again (include the http://)"
			sys.exit(1)
		# write web page to file
		for line in web_page:
			title_line = '<title>' in line
			if title_line == True:
				title = line[7:-9]
			open('web_page.xhtml', 'a').write(line)
		open('web_page.xhtml').close()
		os.rename('web_page.xhtml', title + '.xhtml')
		print "Done"
		sys.exit(0)
if __name__ == '__main__':
	try:
		web_get()
	except KeyboardInterrupt:
		print "\n\nExiting..."
		sys.exit(0)

```

---

### Post by cardboardtoast on 2008-08-14
My try:

Python
[PHP]
#!/usr/bin/env python
#challenge 4
import urllib2
t = 0
while t == 0:
    address = raw_input("Enter a web address: ")
    try:
        page = urllib2.urlopen(address)
        t = 1
        print "Please wait..."
        break
    except:
        print "couldn't find address, check for mistakes"
        t = 0
pageread = page.read()
#get the title
try:
    title = pageread.split("<title>")[1]
    title = title.split("</title>")[0]
except:
    title = "webpage"
#name the new file
out = open(str(title) + ".xhtml", "w")
out.write(pageread)
out.close()

test = raw_input("Done!")
[/PHP]
popcorn :popcorn:

---

### Post by jimi_hendrix on 2008-08-14
> **LaRoza said:**
> &#2346;&#2381;&#2352;&#2340;&#2367;&#2352;&#2379;&#2343; &#2357;&#2381;&#2351;&#2352;&#2381;&#2341; &#2361;&#2376;

can u translate that? and i expected something in borg not arabic

---

### Post by Kadrus on 2008-08-14
That's not arabic ^

---

### Post by M_the_C on 2008-08-14
My entry:
```
#!/usr/bin/env python

import urllib
import re

t = re.compile('<title>(.*)</title>')
url = raw_input('What page do you wish to copy?\n')
index = urllib.urlopen(str(url)).read()
title = t.search(index).group(1)
f = open(str(title), 'w')
f.write(index)
f.close()
print 'Saved as %s .xhtml' % (title)
```

---

### Post by jimi_hendrix on 2008-08-14
> **Kadrus said:**
> That's not arabic ^

ur right...missed that...Chinese?

---

### Post by Kadrus on 2008-08-14
Not really,Hindi if I am not mistaken.I know arabic so I would have known..
[http://en.wikipedia.org/wiki/Hindi](http://en.wikipedia.org/wiki/Hindi)

---

### Post by jimi_hendrix on 2008-08-14
ur right thanks

---

### Post by jimi_hendrix on 2008-08-14
> **LaRoza said:**
> 
You will have to do the following:

[list]
[*] Write a program that will read a webpage and puts its text into a file named "index.xhtml"
[*] The test site will be: [http://laroza.freehostia.com/home/index.php](http://laroza.freehostia.com/home/index.php)
[*] That is the bare minimum requirements, but I would ask you try to make it work for any site.
[/list]

You do NOT have to:

[list]
[*] Have it do anything but download the single file of a web page, so ignore any external scripts or css.
[*] Have it to any rendering, just write it to a file (for opening with a browser, most likely)
[/list]

For extra credit:

[list]
[*] Have either prompt or use a command line argument to do do this with any webpage
[*] Have it name the output file after the title of the document (hint: text in the elements <title></title>, you can use xml or html parsers for this, or you can use regular expressions)
[/list]

The test page is valid XHTML 1.1 (and is valid XML). All conditions and extra credit can be done with standard Python. If you use another language or non standard libs, let me know exactly how to get your entry working.



[size=+1]Rules:[/size]
Do not copy code, but you can obviously read it :-)

Try not to comment on other submissions. It will be hard to judge changing entries. If you edit your code, post the new version and make it clear there is a new code.

ok a few questions
[list]
[*] 1. can you explain the render thing better...i don't get that but i found a good example on the web that taught me how to do this challenge but has poor documentation and mentions something about renders in the comments
[*] 2. is it just me or are the forum tags the same has html/xhtml tags but with [] brackets instead of <> ones
[/list]

---

### Post by Titan8990 on 2008-08-14
> 2. is it just me or are the forum tags the same has html/xhtml tags but with [] brackets instead of <> ones

This is more or less true but HTML has **a lot** more tags than BBC (forum) code has.

---

### Post by badperson on 2008-08-14
always wanted to do this in perl, 
here's mine:

```
## Ubuntu Challenge #4, written by Badperson 8/14/08 
## this script will default to look for http://laroza.freehostia.com/home/index.php, 
## but will accept an arugument for a url
use LWP::Simple;
use strict;
use warnings;


my $url;


if (@ARGV == 1 ){
$url = $ARGV[0];
} else {
$url = "http://laroza.freehostia.com/home/index.php";

}

my $content = get($url) or die "can't read $url $!\n";

open(OUT, ">index.xhtml");
print OUT '<!-- Ubuntu Challenge #4, written by Badperson 8/14/08 -->';
print OUT '<!-- searching for url: $url -->';
print $content;
print OUT $content;

print "\n\nScript done. \n";
```

---

### Post by jimi_hendrix on 2008-08-14
also does the program have to load it or just save it to a xhtml file

---

### Post by OutOfReach on 2008-08-14
OK, I thought this was the perfect opportunity to practice the PyQt that I was learning, so I created both a CLI version and a GUI version, for the GUI version you need to have Qt4 and PyQt4 both installed.

The CLI version:
[PHP]import urllib2

class WebsiteCopier(object):
    
    def SaveWebsite(self):
        try:
            websiteChoice = raw_input("What website would you like to copy?: ")
            website = urllib2.urlopen(str(websiteChoice)).read()
            fileTitle = website.split("<title>")[1].split("</title>")[0] + ".xhtml"
            websiteFile = open(fileTitle, "w")
            websiteFile.writelines(website)
            print "Successfully completed copying website to " + fileTitle + "!"
        except:
            print "Error in downloading or writing website to file."
        finally:
            websiteFile.close()

if __name__ == "__main__":
    WebsiteCopier = WebsiteCopier()
    WebsiteCopier.SaveWebsite()[/PHP]

The GUI Version:
[PHP]import sys
import urllib2
from PyQt4.QtCore import *
from PyQt4.QtGui import *

class WebsiteForm(QDialog):
    
    def __init__(self, parent=None):
        super(WebsiteForm,self).__init__(parent)
        
        self.WebsiteLine = QLineEdit("Type a website URL here.")
        self.WebsiteLine.selectAll()
        
        self.browser = QTextBrowser()
        
        grid = QGridLayout()
        grid.addWidget(self.WebsiteLine, 0, 0)
        grid.addWidget(self.browser, 1, 0)
        self.setLayout(grid)
        self.setWindowTitle("Website Copier")
        
        self.connect(self.WebsiteLine, SIGNAL("returnPressed()"), self.updateUi)
        
    def updateUi(self):
        try:
            text = self.WebsiteLine.text()
            website = urllib2.urlopen(str(text)).read()
            fileTitle = website.split("<title>")[1].split("</title>")[0] + ".xhtml"
            websiteFile = open(fileTitle, "w")
            websiteFile.writelines(website)
            self.browser.append("<b>Successfully finished saving website to %s!</b>" % fileTitle)
        except:
            self.browser.append("<font color=red>%s is an invalid website URL!</font>" % text)
        finally:
            websiteFile.close()
            
app = QApplication(sys.argv)
form = WebsiteForm()
form.show()
app.exec_()
[/PHP]

Suggesstions, etc... are welcomed :D

Cheers :popcorn:

---

### Post by -grubby on 2008-08-14
This is what I have.. for now...

```
[color=#408080]*#!/usr/bin/python*[/color]

[color=#008000]**from**[/color] [color=#0000FF]**__future__**[/color] [color=#008000]**import**[/color] with_statement
[color=#008000]**import**[/color] [color=#0000FF]**urllib2**[/color]

URL [color=#666666]=[/color] [color=#008000]raw_input[/color]([color=#BA2121]"What web page would you like to access?[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color])    
FILE [color=#666666]=[/color] [color=#008000]raw_input[/color]([color=#BA2121]"What file would you like to save this page to?[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color])

[color=#008000]**def**[/color] [color=#0000FF]main[/color]() : 
    [color=#008000]**try**[/color] :
        readurl [color=#666666]=[/color] urllib2[color=#666666].[/color]urlopen(URL)[color=#666666].[/color]read()
        
        [color=#008000]**try**[/color] : 
            [color=#008000]**with**[/color] [color=#008000]open[/color](FILE, [color=#BA2121]"w"[/color]) [color=#008000]**as**[/color] output : 
                output[color=#666666].[/color]write(readurl)
                
            [color=#008000]**print**[/color] [color=#BA2121]"The page '[/color][color=#BB6688]**%s**[/color][color=#BA2121]' was saved successfully to [/color][color=#BB6688]**%s**[/color][color=#BA2121]!"[/color] [color=#666666]%[/color] (URL, FILE)

        [color=#008000]**except**[/color]([color=#D2413A]**IOError**[/color]) : 
            [color=#008000]**print**[/color] [color=#BA2121]"[/color][color=#BB6688]**%s**[/color][color=#BA2121] is not a valid filename"[/color] [color=#666666]%[/color] FILE
                    
    [color=#008000]**except**[/color](urllib2[color=#666666].[/color]URLError) : 
        [color=#008000]**print**[/color] [color=#BA2121]"'[/color][color=#BB6688]**%s**[/color][color=#BA2121]' is not a valid URL. Please check your spelling"[/color] [color=#666666]%[/color] URL
    [color=#008000]**except**[/color]([color=#D2413A]**ValueError**[/color]) :
        [color=#008000]**print**[/color] [color=#BA2121]"'[/color][color=#BB6688]**%s**[/color][color=#BA2121]' is not a valid http URL."[/color] [color=#666666]%[/color] URL
                
[color=#008000]**if**[/color] __name__ [color=#666666]==[/color] [color=#BA2121]"__main__"[/color] : main()

```

---

### Post by Darkhack on 2008-08-14
Here is my entry.  I did it in my favorite programming language, C, and I used libcurl which is an amazing networking library that made this challenge so much easier.

_Required packages_

build-essential
libcurl3
libcurl3-gnutls
libcurl4-gnutls-dev

```

**main.c**

#include <stdlib.h>
#include <stdio.h>
#include <getopt.h>
#include <curl/curl.h>

void print_help()
{
	printf("usage: ./main.bin -g http://...\n");
}

void get_page(char *url)
{
	CURL *curl = curl_easy_init();
	FILE *fp = fopen("index.xhtml", "w");
	double fsize;
	
	curl_easy_setopt(curl, CURLOPT_URL, url);
	curl_easy_setopt(curl, CURLOPT_WRITEDATA, fp);
	curl_easy_perform(curl);
	
	curl_easy_getinfo(curl, CURLINFO_SIZE_DOWNLOAD, &fsize);
	curl_easy_perform(curl);
	
	printf("size: %d bytes\n", (int)fsize);

	curl_easy_cleanup(curl);
	fclose(fp);
}

int main(int argc, char *argv[])
{
	int next_option;
	const char *short_options = "hg:";
	const struct option long_options[] =
	{
		{ "help",  0, NULL, 'h' },
		{ "get",   1, NULL, 'g' },
		{ NULL,	   0, NULL,  0  }
	};
	
	do
	{
		next_option = getopt_long(argc, argv, short_options,
					  long_options, NULL);
		switch(next_option)
		{
			case 'h': print_help();	break;
			case 'g': get_page(optarg);	break;
			case '?': perror("Invalid argument\n"); break;
			case  -1: break;
			default: abort();
		}
	} while (next_option != -1);
	
	return 0;
}

```

```

gcc `pkg-config --cflags --libs libcurl` main.c -o main.bin

```

```

./main.bin --get http://laroza.freehostia.com/home/index.php

```

---

### Post by jacensolo on 2008-08-14
[php]#!/usr/bin/env python

import urllib
import re

titlepat = re.compile('<title>(.*)</title>')

page = urllib.urlopen(raw_input(" Enter the page you would like to save. \n"))
for line in page:
    title = titlepat.search(line)
    if title:
        title = title.group(1)
        break

file = open(str(title), 'w')
for line in page:
    file.write(line)
file.close()
[/php]

I wanted to use HTMLParser but I don't understand it. I looked online for tutorials or examples, but I can't find much. Can anyone help?

---

### Post by jimi_hendrix on 2008-08-14
question: whats an html parser?

---

### Post by Kadrus on 2008-08-14
Heres an [image ]("http://upload.wikimedia.org/wikipedia/en/a/a9/Parser_Flow.gif")that might help

---

### Post by jimi_hendrix on 2008-08-14
nope it didnt

---

### Post by Kadrus on 2008-08-14
Here's a breif explination.
An HTML "parser" parses the source code of an HTML code to create an internal representation.
Read this [article]("http://en.wikipedia.org/wiki/Parsing") for more information.

---

### Post by jimi_hendrix on 2008-08-14
ok question 2...is there some specific directory we are saving this to?

---

### Post by Kadrus on 2008-08-14
I don't think so,the home directory or /tmp would be best.

---

### Post by jimi_hendrix on 2008-08-14
can u give me the stream to home...im currently not on a ubuntu computer :(

---

### Post by Kadrus on 2008-08-14
the home directroy is usually: /home/username where of course username is replaced with your username when you installed your system.
the tmp directory: /tmp
you can get your home directory but outputting this into terminal: pwd

---

### Post by OutOfReach on 2008-08-14
or you can use ~/
which also stands for the home directory.

---

### Post by jimi_hendrix on 2008-08-14
so would this would in theory save it to the home folder (just look at the part StreamWriter("") part)

[PHP]
StreamWriter sw = new StreamWriter("~/");
sw.Write("some text here" + .txt);
sw.Close();
[/PHP]

---

### Post by shae on 2008-08-14
I am working on it accepting input from any website and am wondering with what extension should we save the file?

---

### Post by jimi_hendrix on 2008-08-14
here is my C# entry...ill edit it if i find its not compilable in ubuntu (i dont have linux access tonight)  

[PHP]
//needed for program
using System;
using System.Collections.Generic;
using System.Text;
using System.IO;//for saving the file
using System.Net;//for getting the source code

namespace Website_Download
{
    class Program
    {
        static void Main(string[] args)
        {   
                Console.WriteLine("enter the url of the webpage you would like to save without the http:// \n ex. google would be google.com");//instructions
                string url = "http://" + Console.ReadLine();//simplifies input for user
                url.Trim();//clears whitespace
                try//try is used if there is a possibillity of an error.  If there is then the code picks up at the catch part
                {
                    //prints data
                    string source = downloadWebsite(url);//gets source code
                    Console.WriteLine(source);//prints source code
                    Console.WriteLine();//white space for neat reading
                    Console.WriteLine();
                    Console.WriteLine();
                    Console.WriteLine();
                    Console.WriteLine();
                    Console.WriteLine();
                    Console.WriteLine("the webpage title is: " + GetTitle(source));//prints webpage title
                    Console.WriteLine("do you want to save this source code? type yes to save or anything else to exit");//asks for save

                    if (Console.ReadLine() == "yes")
                    {
                        Save(source);//saves data


                    }
                }
                catch//error handling
                {
                    Console.WriteLine("error...either you entered the url incorrectly or there was an error in saving the file");
                }
                Console.WriteLine("Press enter to continue...");
                Console.ReadLine();
        }

        private static void Save(string Source)//the save method
        {
            //saves data to the title .xhmtl
            StreamWriter sw = new StreamWriter("~/" + GetTitle() + ".xhtml");//creates a streamwriter to write to the file
            sw.Write(Source);//writes to the file
            Console.WriteLine("saved to: ~/" + GetTitle() + ".xhtml");
            sw.Close();//closes the stream to prevent data leak
        }

        
        public static string downloadWebsite(string Url)
        {
            
            HttpWebRequest webRequestObject = (HttpWebRequest)HttpWebRequest.Create(Url);//connects to website

            WebResponse response = WebRequestObject.GetResponse();//requests a response

            Stream webStream = Response.GetResponseStream();//opens a stream to the site

            StreamReader reader = new StreamReader(WebStream);//creates a reader to read the stram

            string pageContent = Reader.ReadToEnd();

            //closes objects to prevent data leak
            reader.Close();
            webStream.Close();
            response.Close();

            return pageContent;
        }

        public static string GetTitle(string Source)
        {   
            //these find the start and end of the title
            int titleStart = Source.IndexOf("<title>") + 7;//the IndexOf method find the array number of the char that begins the quote.  We add 7 because we want to start at the end of <title> and its 7 digits long
            int titleEnd = Source.IndexOf("</title>");//finds the end of the title
            string title = Source.Substring(titleStart, titleEnd - titleStart);//
            title.Trim();//trips whitespace in title
            return title;
        }
    }
}
[/PHP]

---

### Post by OutOfReach on 2008-08-14
> **shae said:**
> I am working on it accepting input from any website and am wondering with what extension should we save the file?

.xhtml

---

### Post by jimi_hendrix on 2008-08-14
> **shae said:**
> I am working on it accepting input from any website and am wondering with what extension should we save the file?

.xhtml i believe we had to save it as right

---

### Post by shae on 2008-08-14
> **jimi_hendrix said:**
> .xhtml i believe we had to save it as right

But if you input a site that does not use xhtml (such as one that uses non-valid html), then the resulting file will not be usable I believe.

---

### Post by cardboardtoast on 2008-08-15
> But if you input a site that does not use xhtml (such as one that uses non-valid html), then the resulting file will not be usable I believe.
I believe he/she said that his/her site(the test site) is valid xhtml

---

### Post by Mr_Chapendi on 2008-08-15
It seems to work OK.  Written with liberal help from various Rdoc's.

```
#!/usr/bin/env ruby
require 'uri'
require 'net/http'

include Net

# Magic method for handling redirects.
def fetch(uri, interval = 5)
  raise ArgumentError, 'Too many redirects!' if interval <= 0

  response = HTTP.get_response(URI.parse(uri))

  case response
  when HTTPSuccess         then response
  when HTTPRedirection     then fetch(response['location'], interval - 1)
  else
    response.error!
  end
end

# Open 'er up.
response = fetch(ARGV[0])

# Yes, Ruby, this variable exists.  I promise.  See?
outtitle = nil

# Use regexes to find the <title>...</title> part of the webpage, cut it out,
# append .xhtml to it and use it to save the file name.  (Break out when found.)
response.body.each do |line|
  if line =~ /<title>/
    puts outtitle = "#{line.gsub(/(.*<title>|<\/title>.*)/, '').chomp}.xhtml"
    breaknow = true 
  end
  break if breaknow
end

# Get rid of any leading whitespace (because it's really irritating.)
outtitle.gsub!(/^\s/, '')

# Make/override the file and write it all out.
# By the way, when reading some XHTML files this outputs the XHTML code
# entities for some characters.  Is there a way to get Ruby to convert these
# to regular text so you don't end up with files like Bobês Blog.xhtml?
output = File.new(outtitle, 'w+')
output.puts(response.body)
output.close
```

First Ruby entry!  w00t!

---

### Post by slavik on 2008-08-15
> **cardboardtoast said:**
> I believe she said that **her** site(the test site) is valid xhtml

Do you know something we don't??? :)

BTW, is use of urllib/lwp and such allowed, LaRoza? Seems like a cop out to me. :P (Use the socket, Luke).

---

### Post by shae on 2008-08-15
> **cardboardtoast said:**
> I believe she said that her site(the test site) is valid xhtml

I am already able to get the test site, I am working on the extra credit which stipulates you can do that to any site.  I am asking how he wants us to handle any site that is not xhtml.

---

### Post by yabbadabbadont on 2008-08-15
Solution in white on white text since I doubt that I count as a beginner.  ;)  I had to remove the code tags to get the text to be white.  So the formatting has been lost.  It'll still work though.
[COLOR="White"]#!/usr/bin/env bash

echo -n "Enter website address: "

read website

echo "Retrieving '${website}' ..."

curl "${website}" > index.xhtml 2>/dev/null
rc=$?

if [ $rc -ne 0 ]
then
        echo "Uh oh.  Curl returned error number $rc"
        exit $rc
else
        echo "Page retrieved successfully."
fi

pagename=$(grep "<title>.*</title>" index.xhtml | sed 's/^.*<title>//' | sed 's/<\/title>.*//')

mv index.xhtml "${pagename}".xhtml

echo "Page saved as '${pagename}.xhtml'"
[/COLOR]

---

### Post by mcsimon on 2008-08-15
my entry in java :)

```
import java.net.*;
import java.io.*;
/**
 * Read a webpage and write to index.xhtml
 * 
 * @author Simon McMahon
 */
public class URLReader
{

    public static void writeURL(String site) throws IOException
    {
        String inputLine;
        URL siteToRead = new URL(site);
        
        PrintWriter myOut = new PrintWriter(new FileOutputStream("index.xhtml"));    
        BufferedReader in = new BufferedReader(new InputStreamReader(siteToRead.openStream()));
        
        while ((inputLine = in.readLine()) != null) {
            myOut.println(inputLine);
        
        }
        myOut.close();
        in.close(); 
                
    }
    
    public static void main(String[] args) {
        try{
            writeURL(args[0]);
        } catch(Exception e) {
            System.err.println(e);
        }
    }
}

```

---

### Post by LaRoza on 2008-08-15
> **jimi_hendrix said:**
> can u translate that? and i expected something in borg not arabic

It is written in Devanagari, which is just an abugida (type of alphabet). The first part is "LaRoza" transliterated (Devanagari is used to write many languages) and the second part (after the |) is "Resistance is futile" in Hindi.

> **jimi_hendrix said:**
> ur right...missed that...Chinese?

You much to learn young grasshopper...

> **jimi_hendrix said:**
> ok a few questions
[list]
[*] 1. can you explain the render thing better...i don't get that but i found a good example on the web that taught me how to do this challenge but has poor documentation and mentions something about renders in the comments
[*] 2. is it just me or are the forum tags the same has html/xhtml tags but with [] brackets instead of <> ones
[/list]

You don't have to render it. The forum tags don't matter, they are just used by the internal PHP to do the formatting.

> **jimi_hendrix said:**
> also does the program have to load it or just save it to a xhtml file

Just save it.

> **jimi_hendrix said:**
> question: whats an html parser?

A parser for HTML (a program that reads and interprets HTML)

> **jimi_hendrix said:**
> ok question 2...is there some specific directory we are saving this to?

The same directory the program is in, so it doesn't matter.

> **shae said:**
> I am working on it accepting input from any website and am wondering with what extension should we save the file?

A workable one ;) The safest would be .htm

> **shae said:**
> But if you input a site that does not use xhtml (such as one that uses non-valid html), then the resulting file will not be usable I believe.

That is part of the challenge, .htm would be the safest extension.

> **slavik said:**
> Do you know something we don't??? :)

BTW, is use of urllib/lwp and such allowed, LaRoza? Seems like a cop out to me. :P (Use the socket, Luke).

Everything that you need to know is in the first post.

slavik, you find it a cop out to use the best tool (in Python standard libs) to do this job? Perhaps you need to go back to Programming 101 where they explain programs make things easier for people ;)

> **shae said:**
> I am already able to get the test site, I am working on the extra credit which stipulates you can do that to any site.  I am asking how he wants us to handle any site that is not xhtml.

You parse the doctype, or just assume it is .htm

---

### Post by Reiger on 2008-08-15
For obtaining the correct file extension you would parse the following (in order of importance)

[list]
[*] MIME type as specified in the http-equiv
[*] DOCTYPE
[*] Supplied file extension in the URL
[/list]

---

### Post by jimi_hendrix on 2008-08-15
> **cardboardtoast said:**
> I believe she said that her site(the test site) is valid xhtml

also the xhtml doesnt have to be useable just getable...and now i believe xhtml is alsway valid thats why they made it to replace html

---

### Post by Def13b on 2008-08-15
Well it took me about 20mins to get this working using simple string methods but thought I'd give it a go using Parsing, I've not really done much of anything with classes so figured it would be the better path to take.

Having said that, I pretty quickly came across a problem where I simply couldn't get my __init__ method to work no matter what I did, came across something on the net that said to put anything you need to initialize into the reset method and while it worked I still can't figure out why. Anyway, here it is. 

Takes the URL as a command line argument, 

[PHP]#!/usr/bin/env python

import urllib, sys, os
from sgmllib import SGMLParser

class WebPages(SGMLParser):
    def reset(self):
        SGMLParser.reset(self)
        self.ext = '.htm'
        
    def handle_decl(self, text):
        self.ext = '.' + text.lower().split()[4]
        
    def start_title(self, text):
        pass
        
    def end_title(self):
        self.title = self.info.lstrip()
        
    def handle_data(self, data):
        self.info = data

try:
    source = urllib.urlopen(sys.argv[1]).read()
except IOError:
    print '\nThe specified URL could not be opened.'
    print 'Ensure the full address is used. eg http://www.google.com\n'
    sys.exit()

parser = WebPages()
parser.feed(source)
parser.close()

open(parser.title + parser.ext, 'w').write(source)
print '\nOutput saved as %s/%s%s\n' % (os.getcwdu(), parser.title, parser.ext)[/PHP]

---

### Post by jimi_hendrix on 2008-08-15
anyone know a version of

[PHP]using System.Net;[/PHP]

that is platform independent/usable on linux?

---

### Post by LaRoza on 2008-08-15
> **jimi_hendrix said:**
> anyone know a version of

[PHP]using System.Net;[/PHP]

that is platform independent/usable on linux?

I think that can be used on mono.

You can always get mono for Windows and try it.

(I compiled a C# programming with that in it, and it worked)

---

### Post by jimi_hendrix on 2008-08-15
im on my linux computer now...wont compile i get the following

```
[Task:File=/home/vincent/Documents/Programs/UserInput.cs, Line=11, Column=1, Type=Error, Priority=Normal, Description=The type or namespace name `System.Net' could not be found. Are you missing a using directive or an assembly reference?(CS0246)]

[Task:File=/home/vincent/Documents/Programs/UserInput.cs, Line=11, Column=14, Type=Error, Priority=Normal, Description=The type or namespace name `Net' does not exist in the namespace `System'. Are you missing an assembly reference?(CS0234)]

```

---

### Post by cardboardtoast on 2008-08-15
> **slavik said:**
> Do you know something we don't??? :)


Umm...I'm a spy?:rolleyes: Nope, just was tired and in a rush...fixed
> **slavik said:**
> 
BTW, is use of urllib/lwp and such allowed, LaRoza? Seems like a cop out to me. :P (Use the socket, Luke).
Some of us didn't even know what urllib was before we did this(or that it was a "cop-out"), and stop making me look bad!!!!!:cry:
I doubt i will be able to, but I'll try a lib-less one...

popcorn:popcorn:

---

### Post by LaRoza on 2008-08-15
> **jimi_hendrix said:**
> im on my linux computer now...wont compile i get the following


I just installed "mono-gmcs" and compiled it with no trouble.

> **cardboardtoast said:**
> 
Some of us didn't even know what urllib was before we did this(or that it was a "cop-out"), and stop making me look bad!!!!!:cry:
I doubt i will be able to, but I'll try a lib-less one...


No, that was the point of the challenge, to use libraries you probably didn't use before. Sure, it is easy once you know how to do it, but some people seem to forget that not everyone has experience from the start.

That was also the point of having the statement about only beginners do it.

---

### Post by jimi_hendrix on 2008-08-15
did u compile my program or just something that was like

[PHP]
using System;
using System.Collections.Generic;
using System.Text;
using System.IO;
using System.Net;//for getting the source code
[/PHP]

if you compiled mine did it work???

---

### Post by LaRoza on 2008-08-15
> **jimi_hendrix said:**
> did u compile my program or just something that was like

[PHP]
using System;
using System.Collections.Generic;
using System.Text;
using System.IO;
using System.Net;//for getting the source code
[/PHP]

if you compiled mine did it work???

I don't know a lot about C#. This was the error I got from yours:

```

~/p$gmcs p.cs
p.cs(49,55): error CS1501: No overload for method `GetTitle' takes `0' arguments
p.cs(51,48): error CS1501: No overload for method `GetTitle' takes `0' arguments
p.cs(61,36): error CS0103: The name `WebRequestObject' does not exist in the current context
p.cs(63,32): error CS0103: The name `Response' does not exist in the current context
p.cs(65,52): error CS0103: The name `WebStream' does not exist in the current context
p.cs(67,34): error CS0103: The name `Reader' does not exist in the current context
Compilation failed: 6 error(s), 0 warnings
~/p$

```

This works:
[php]
using System;
using System.IO;
using System.Net;
using System.Text;


/// <summary>
/// Fetches a Web Page
/// </summary>
class WebFetch
{
	static void Main(string[] args)
	{
		// used to build entire input
		StringBuilder sb  = new StringBuilder();

		// used on each read operation
		byte[]        buf = new byte[8192];

		// prepare the web page we will be asking for
		HttpWebRequest  request  = (HttpWebRequest)
			WebRequest.Create("http://www.mayosoftware.com");

		// execute the request
		HttpWebResponse response = (HttpWebResponse)
			request.GetResponse();

		// we will read data via the response stream
		Stream resStream = response.GetResponseStream();

		string tempString = null;
		int    count      = 0;

		do
		{
			// fill the buffer with data
			count = resStream.Read(buf, 0, buf.Length);

			// make sure we read some data
			if (count != 0)
			{
				// translate from bytes to ASCII text
				tempString = Encoding.ASCII.GetString(buf, 0, count);

				// continue building the string
				sb.Append(tempString);
			}
		}
		while (count > 0); // any more data to read?

		// print out page source
		Console.WriteLine(sb.ToString());
	}
}[/php]

---

### Post by jimi_hendrix on 2008-08-15
didnt compile for me...same errors in mono

---

### Post by jimi_hendrix on 2008-08-15
this should compile...i was getting sleepy when i did this and changed my naming convention (bad idea)

thanks for being patient

[PHP]// UserInput.cs created with MonoDevelop
// User: vincent at 7:40 AM*8/15/2008
//
// To change standard headers go to Edit->Preferences->Coding->Standard Headers
//
using System;
//needed for program
using System.Collections.Generic;
using System.Text;
using System.IO;//for saving the file
using System.Net;//for getting the source code

namespace Website_Download
{
    class Program
    {
        static void Main(string[] args)
        {   
                Console.WriteLine("enter the url of the webpage you would like to save without the http:// \n ex. google would be google.com");//instructions
                string url = "http://" + Console.ReadLine();//simplifies input for user
                url.Trim();//clears whitespace
                try//try is used if there is a possibillity of an error.  If there is then the code picks up at the catch part
                {
                    //prints data
                    string source = downloadWebsite(url);//gets source code
                    Console.WriteLine(source);//prints source code
                    Console.WriteLine();//white space for neat reading
                    Console.WriteLine();
                    Console.WriteLine();
                    Console.WriteLine();
                    Console.WriteLine();
                    Console.WriteLine();
                    Console.WriteLine("the webpage title is: " + GetTitle(source));//prints webpage title
                    Console.WriteLine("do you want to save this source code? type yes to save or anything else to exit");//asks for save

                    if (Console.ReadLine() == "yes")
                    {
                        Save(source);//saves data


                    }
                }
                catch//error handling
                {
                    Console.WriteLine("error...either you entered the url incorrectly or there was an error in saving the file");
                }
                Console.WriteLine("Press enter to continue...");
                Console.ReadLine();
        }

        private static void Save(string Source)//the save method
        {
            //saves data to the title .xhmtl
            StreamWriter sw = new StreamWriter("~/" + GetTitle(source) + ".xhtml");//creates a streamwriter to write to the file
            sw.Write(Source);//writes to the file
            Console.WriteLine("saved to: ~/" + GetTitle(source) + ".xhtml");
            sw.Close();//closes the stream to prevent data leak
        }

        
        public static string downloadWebsite(string Url)
        {
            
            HttpWebRequest webRequestObject = (HttpWebRequest)HttpWebRequest.Create(Url);//connects to website

            WebResponse response = webRequestObject.GetResponse();//requests a response

            Stream webStream = response.GetResponseStream();//opens a stream to the site

            StreamReader reader = new StreamReader(webStream);//creates a reader to read the stram

            string pageContent = reader.ReadToEnd();

            //closes objects to prevent data leak
            reader.Close();
            webStream.Close();
            response.Close();

            return pageContent;
        }

        public static string GetTitle(string Source)
        {   
            //these find the start and end of the title
            int titleStart = Source.IndexOf("<title>") + 7;//the IndexOf method find the array number of the char that begins the quote.  We add 7 because we want to start at the end of <title> and its 7 digits long
            int titleEnd = Source.IndexOf("</title>");//finds the end of the title
            string title = Source.Substring(titleStart, titleEnd - titleStart);//
            title.Trim();//trips whitespace in title
            return title;
        }
    }
}  [/PHP]

i hope it compiles (it should) but if it doesn't work on ubuntu i know it worked on the windows comp i did it on and i taught me how to do it (also told me how to deny a website even if the person is using one of the millions of proxy sites out there) and thats what these are all about

i might have used a few too many comments but thats so people who dont know alot of C# (since very few people on this forum seem to know it) know how it works

---

### Post by arsenic23 on 2008-08-15
Oh man, I didn't notice this was up again.
Anyway, I've been working on a script for spidering images off of websites, so I borrowed almost all of the code from that for this one.

This will work if you enter the site like this:
[COLOR="DarkRed"]./programname.py [http://laroza.freehostia.com/home/index.php](http://laroza.freehostia.com/home/index.php)[/COLOR]

or if you just use the prompt that comes up when the program isn't run with a site after itself.



```
#!/usr/bin/env python
# Simple html downloader
# Based off my pydump script

import urllib2
import sys

def Cprint(string,color='reset',p=False): 
	""" A simple colorizing function for pydump.  
	Takes string and color, then uses p to set if there will be a linebreak after the string is printed """
	if color=='red':	color='\033[0;31m'
	elif color=='pink':	color='\033[1;31m'
	elif color=='blue':	color='\033[1;34m'
	elif color=='reset':	color='\033[0;39m'
	
	sys.stdout.write(color + string + '\033[0;39m')
	if p:	sys.stdout.write('\n')

def mainaction(site):
	try:
		webfile=urllib2.urlopen(site)
		val=webfile.read()
		
		## The only new code ~~
		## Will overwrite files if they have the same name as the incoming page
		filename=site.split('/')[-1]
		if filename.endswith('html') or filename.endswith('.htm')\
		or filename.endswith('.xml'): None
		elif filename.endswith('.php'): filename=filename.split('.php')[0]+'.xhtml'
		else:
			filename+='.htm'

		localfile=open(filename,'w')	
		localfile.write(val)
		## The only new code ~~		

		localfile.close
		webfile.close
	except urllib2.HTTPError:
		Cprint("ERROR: The page you attempted to use does not appear to exist.",'red',p=True)
		Cprint("Make sure you've typed the full address, including 'http://'",'red',p=True)
	except ValueError:
		Cprint("ERROR: "+ site +" is not a valid website.",'red',p=True)
		Cprint("Make sure you've typed the full address, including 'http://'",'red',p=True)
	except:	Cprint("ERROR: -unknown-",'red',p=True)


def prompt():
	try: 
		mainaction(sys.argv[1])
	except IndexError:
		while 1:
			Cprint('-HTMLdownload-','blue') # changed prompt
			promptinput=raw_input("[url or 'exit']>>>> ")
			if promptinput.lower() == "exit":
				break
			else:
				try:	mainaction(promptinput)
				except:	Cprint("  --input error--",'red',p=True)
	
	
if __name__ == '__main__':
	try: prompt()
	except KeyboardInterrupt: print 'Goodbye... \n\n'
	except EOFError: print '\n'
```

---

### Post by TreeFinger on 2008-08-15
I'm confused by the following:
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
            "http://www.w3.org/TR/html4/strict.dtd">

```

not showing up in my output file. Anyone care to explain?

---

### Post by Reiger on 2008-08-15
You probably use a library for processing XML, one that unfortunately strips parser instructions (and a DTD-declaration *is* a parser instruction). Funny thing is that some libraries even add XML-declarations. (<?xml version=...?>) ! 

Hint: download the file as just that: a file; and build your own parser (which can be one (!) regular expression in PHP). Use regular expressions for the parser.

---

### Post by slavik on 2008-08-15
Using a socket and writing a request by hand is much more fun. :) This way, YOU are the one doing the requesting and such, not some magic library. :) What about writing my own http library? :P

---

### Post by Reiger on 2008-08-15
Yeah but the alternative takes just 2 lines of PHP code; which is nice in the vein of the challenge (which isn't "implement your own functions calling the built-in-your-OS functions doing TCP-Reno" ;))

---

### Post by slavik on 2008-08-15
shell: 1 line. :)

---

### Post by Reiger on 2008-08-15
Yeah to accomplish the same objective as that of the challenge - it would take just one call to wget. Still, that's not the challenge either. ;)
EDIT: Oh and it'd have arbitrary URL's too.

---

### Post by LaRoza on 2008-08-15
> **slavik said:**
> Using a socket and writing a request by hand is much more fun. :) This way, YOU are the one doing the requesting and such, not some magic library. :) What about writing my own http library? :P

You can do that. This challenge is about using existing libraries, but having the non beginners write things from the ground (on whatever level the ground is) up would be interesting.

> **slavik said:**
> shell: 1 line. :)

Which is why it is no longer in this thread ;)

---

### Post by schauerlich on 2008-08-15
> **LaRoza said:**
> Which is why it is no longer in this thread ;)

Well, wget was my first thought when I opened this thread, but I also saw the other thread in OMGPP and I don't want to copy.

---

### Post by shae on 2008-08-15
> **Reiger said:**
> For obtaining the correct file extension you would parse the following (in order of importance)

[list]
[*] MIME type as specified in the http-equiv
[*] DOCTYPE
[*] Supplied file extension in the URL
[/list]

I cannot seem to find any useful information about the MIME type as specified in http-equiv, could you perhaps give me a good starting place.

I am already checking DOCTYPE.

I do not know how useful this would be because often pages might be given the extension .php, etc.

---

### Post by Reiger on 2008-08-15
Never heard of:
```

<meta http-equiv="content-type" content="[omit: MIME type should be inserted here]" />

```

The stuff between square brackets typically reads 'text/html' but for XHTML it *should* be 'application/xhtml+xml'.

To be *really* sure you can check with whatever the interface to HTTP & TCP connections is in your language what MIME type the HTTP header specifies. Note that there is a siginificant difference for this challenge between the few possible MIME types:
[list]
[*]text/html corresponds to a DOCTYPE of HTML which means the browser should work in Quirksmode to accomodate many of the shorthands, and inconsistencies in HTML;
[*]application/xhmtl+xml corresponds to XHTML which requires the browser to be as standards-compliant as possible.
[/list]

---

### Post by jimi_hendrix on 2008-08-15
when does this close for grading?

---

### Post by shae on 2008-08-15
> **Reiger said:**
> Never heard of:
```

<meta http-equiv="content-type" content="[omit: MIME type should be inserted here]" />

```

The stuff between square brackets typically reads 'text/html' but for XHTML it *should* be 'application/xhtml+xml'.

To be *really* sure you can check with whatever the interface to HTTP & TCP connections is in your language what MIME type the HTTP header specifies. Note that there is a siginificant difference for this challenge between the few possible MIME types:
[list]
[*]text/html corresponds to a DOCTYPE of HTML which means the browser should work in Quirksmode to accomodate many of the shorthands, and inconsistencies in HTML;
[*]application/xhmtl+xml corresponds to XHTML which requires the browser to be as standards-compliant as possible.
[/list]

Actually I had not heard of that.  I really do not do (x)html any more.

Furthermore, the HTTP header would not work as a great way to differentiate between them because even for LaRosa's site it returns "text/html".

---

### Post by LaRoza on 2008-08-15
> **jimi_hendrix said:**
> when does this close for grading?

Not sure.

> **shae said:**
> Actually I had not heard of that.  I really do not do (x)html any more.

Furthermore, the HTTP header would not work as a great way to differentiate between them because even for LaRosa's site it returns "text/html".

The HTTP header for my site used to be the appropriate one, but I changed it to avoid issues with legacy browsers because old browsers will parse it as HTML, whereas new ones will see what it is and handle it appropriately.

---

### Post by yabbadabbadont on 2008-08-15
> **EDavidBurg said:**
> Well, wget was my first thought when I opened this thread, but I also saw the other thread in OMGPP and I don't want to copy.

I too first thought of using wget.  In the end, I used curl, grep, and sed in a nice little bash script.

---

### Post by shae on 2008-08-15
The first draft of my entry in C++ (3rd program in C++)

It does the following:
Takes any URL as an argument
It accepts non-standard ports if part of the URL
Names the result title.extension (supports xhtml,html, fallback htm)
If the page lacks a title, it is named index.extension.

[PHP]#include <iostream>
#include <fstream>
#include <string>
#include <cstring>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>

using namespace std;

int get_port(string url)
{
    if(url.find(":") == string::npos)
        return 80;

    return atoi(url.substr(url.find(":") + 1).c_str());
}

string get_page(string url)
{
    if(url.find("http://") != string::npos)
        url.erase(0, 7);

    int sockfd = socket(PF_INET, SOCK_STREAM, 0);

    struct hostent *h = gethostbyname(url.find(":")!=string::npos?url.substr(0, url.find(':')).c_str():url.substr(0, url.find('/')).c_str());
    if(!h)
    {
        cout << "Please make sure you entered the URL correctly and try again." << endl;
        exit(1);
    }

    struct sockaddr_in dest_addr;
    dest_addr.sin_family = AF_INET;
    dest_addr.sin_port = htons(get_port(url));
    dest_addr.sin_addr.s_addr = inet_addr(inet_ntoa(*((struct in_addr *)h->h_addr)));
    memset(dest_addr.sin_zero, '\0', sizeof dest_addr.sin_zero);

    connect(sockfd, (struct sockaddr *)&dest_addr, sizeof dest_addr);

    string get_request = "GET " + url.substr(url.find('/')) + " http/1.2\nHost: " + url.substr(0, url.find('/')) + "\n\n";
    send(sockfd, get_request.c_str(), get_request.length(), 0);

    string response;
    int size = -1;
    while(size != 0)
    {
        char buffer[100];
        size = recv(sockfd, buffer, 100, 0);

        response.append(buffer, size);

        if (size == -1)
            break;
    }

    close(sockfd);

    response.erase(0,response.find("<")); //Removes the HTTP header from the response
    return response;
}

string substr_between(string s, int index_beg, int index_end)
{
    return s.substr(index_beg, index_end - index_beg);
}

string get_filename(string page)
{
    string title = page.substr(page.find("<title>") + 7, page.find("</title>") - (page.find("<title>") + 7));
    if (title.size() == 0)
        title = "index";

    if(page.find("<meta http-equiv=\"content-type\"") != string::npos)
    {
        string http_equiv = substr_between(page, page.find("content=\"", page.find("<meta http-equiv=\"content-type\"")) + 9, page.find("\"", page.find("content=\"", page.find("<meta http-equiv=\"content-type\"")) + 9));

        if(http_equiv.find("xhtml") != string::npos)
            return title + ".xhtml";
    }

    if(page.find("<!DOCTYPE") != string::npos)
    {
        string doctype = page.substr(page.find("<!DOCTYPE"), page.find(">", page.find("<!DOCTYPE")) - page.find("!DOCTYPE") + 2);

        if(doctype.find("XHTML") != string::npos || doctype.find("xhtml") != string::npos)
            return title + ".xhtml";

        return title + ".html";
    }

    return title + ".htm";
}

void write_file(string page)
{
    ofstream output(get_filename(page).c_str());
    output << page;
    output.close();
}

int main(int argc, char *argv[])
{
    if (!argv[1])
    {
        cout << "Please pass the address of the page you want to fetch as an argument." << endl << "Examples: http://www.example.com/index.html, test.example.com/example.php, etc.";
        return 1;
    }

    write_file(get_page(argv[1]));
    return 0;
}[/PHP]

---

### Post by jimi_hendrix on 2008-08-15
well i would like to thank this thread for rekindling my intrest in my get rich quick web scheme...html imo is the funnest language to write

---

### Post by Sinkingships7 on 2008-08-15
Python

Just meeting the bare requirements here.
[PHP]
import urllib

file = open("index.xhtml", "w")
site = urllib.urlopen("http://laroza.freehostia.com/home/index.php")

file.write(site.read())
[/PHP]

That's my first Python program. After doing a lot of research, I've certainly learned something: Neither C nor C++ are good networking languages.

I will attempt to add the extra credit with I find the time. I'm also struggling to do this in Java, but I think I'm almost there.

---

### Post by Darkhack on 2008-08-15
> **Sinkingships7 said:**
> After doing a lot of research, I've certainly learned something: Neither C nor C++ are good networking languages.

That's true if you're only using the standard library, but nobody expects that these days.  [Curl]("http://curl.haxx.se/") is absolutely amazing and can do almost anything.

---

### Post by lisati on 2008-08-15
My thought on first reading the challenge was something along the lines of "eeek..... back when I first learnt programming, networking wasn't taught to beginners"...... At present, the nearest thing I've ever done to programming for something that happens over a network is an error handler for a file transfer program (written by other people) that got called up for the equivalent of "file not found": about all it did was make a note in the list of queued files that the offending file was "on hold".

Good efforts, everyone!

---

### Post by Geekkit on 2008-08-15
Very interesting coding challenge (and great idea). I'm excited to see the results myself (sorry, don't have time to contribute). My prediction for performance (based on all examples being run on the same machine with the same OS) is (in order of speed, with first number being fastest):

1.) C
2.) Straight ASM, that is, not just ASM inline in C (these days I think you'll be extremely hard pressed to outsmart the average C compiler but I could be wrong) :)
3.) Java
4.) C++ (yes, you read these two in the right order) :)
5.) PHP
6.) Python
... All the rest

A further (and even more interesting) test would be to pit C compilers against each other (e.g., Intel's Borland's, GNU's), as well as Java runtimes (Sun's IBM's, GNU's).

Ninja edit: Are compile-time/runtime performance enhancement options allowed or disallowed? Some may say they are like allowing Olympic athletes to take performance enhancers, whereas some may say that this is just part of the advantage of that particular language/platform.

---

### Post by jimi_hendrix on 2008-08-15
> **Geekkit said:**
> My prediction for performance (based on all examples being run on the same machine with the same OS) is (in order of speed, with first number being fastest):

1.) C
2.) Straight ASM, that is, not just ASM inline in C (these days I think you'll be extremely hard pressed to outsmart the average C compiler but I could be wrong) :)
3.) Java
4.) C++ (yes, you read these two in the right order) :)
5.) PHP
6.) Python
... All the rest

wait is this challenge based on speed or just preformence?

---

### Post by Geekkit on 2008-08-15
> **jimi_hendrix said:**
> wait is this challenge based on speed or just preformence?

Sorry, I meant speed ... I interchanged the two words ... I meant to say speed. I don't think it was based on performance.

---

### Post by jimi_hendrix on 2008-08-15
i used preformence the wrong way...since its interchangable with speed...i thought we just had to do it as clearly and cleanly as possible...if it is based on speed then whats faster...methods and functions or loops?

---

### Post by Ed J on 2008-08-15
No glolbal warming vars, I'm into OOP, passing args, works on many valid pages.  I tried facebook, unbuntuforums.org, yahoo and LaRoza's page successfully. For some reason doesn't work on msn.com, go figure.  HTMLParser was a battle.  Look below to see how I own that lib now.

```

#!/usr/bin/env python

from HTMLParser import HTMLParser
import urllib2

class MyHTMLParser(HTMLParser):
 
    datatag = ''  #The data in between tags.
    starttag = '' #The tag name.

    def handle_starttag(self, tag, attrs):
        self.starttag = str(tag)
                
    def handle_data(self, tag):
        tag = str(tag.rstrip())   
        if self.starttag == 'title' and len(tag) > 0:
            for character in tag:
                if not character.isalnum(): #remove special chars
                     tag = tag.replace(character, '') 
            self.datatag = tag                

class PageProcessor():

    outputfilename = 'index.xhtml'
    rawdata = []   #holds the page xhtml while looking 4 title

    def process(self, myurl):
        hp = MyHTMLParser()
    
        for line in urllib2.urlopen("http://" + myurl):
            hp.feed(line)
            if len(hp.datatag) > 0:
                self.outputfilename = hp.datatag + '.xhtml'
            self.rawdata.append(line)              

        outputfile = open(self.outputfilename, 'w')
        for item in self.rawdata:
            outputfile.write(item)                  
        outputfile.close()

pp = PageProcessor()
pp.process(raw_input("Enter web site, http://"))


```

---

### Post by OutOfReach on 2008-08-15
OK I updated the script a bit, you can now save as .xhtml, .html, or .htm. Again you need PyQt4 and Qt4 for the GUI version, the command line version doesn't take any arguments, it just prompts you for the website.

PyQt4 version:
[PHP]import sys
import urllib2
from PyQt4.QtCore import *
from PyQt4.QtGui import *

class WebsiteForm(QDialog):

    def __init__(self, parent=None):
        super(WebsiteForm,self).__init__(parent)

        #Create our widgets.
        self.WebsiteLine = QLineEdit("Type a website URL here.")
        self.WebsiteLine.selectAll()

        self.browser = QTextBrowser()

        self.typeLabel = QLabel("Save as:")

        self.typeComboBox = QComboBox()
        self.WebsiteLabel = QLabel("Website URL:")
        self.typeComboBox.addItem(".xhtml")
        self.typeComboBox.addItem(".html")
        self.typeComboBox.addItem(".htm")
        self.newLineCheck = QCheckBox()

        self.okButton = QPushButton("Ok")

        #Setup the layout and add the widgets to it.
        layout = QVBoxLayout()
        layout.addWidget(self.WebsiteLabel)
        layout.addWidget(self.WebsiteLine)
        layout.addWidget(self.typeLabel)
        layout.addWidget(self.typeComboBox)
        layout.addWidget(self.browser)
        layout.addWidget(self.okButton)
        self.setLayout(layout)
        self.setWindowTitle("Website Copier")

        self.connect(self.okButton, SIGNAL("clicked()"), self.updateUi)

    def updateUi(self):
        """ The 'brains' of the program """
        try:
            text = self.WebsiteLine.text()
            if not str(text).startswith("http://"):
                text = "http://" + text
            website = urllib2.urlopen(str(text)).read()
            self.browser.append("Reading URL...")
            fileType = self.typeComboBox.currentText()
            fileTitle = website.split("<title>")[1].split("</title>")[0] + fileType
            websiteFile = open(fileTitle, "w")
            self.browser.append("Opening %s..." % fileTitle)
            websiteFile.writelines(website)
            websiteFile.close()
            self.browser.append("<b>Successfully finished saving website to %s!</b>" % fileTitle)
        except:
            self.browser.append("<font color=red>%s is an invalid website URL!</font>" % text)

app = QApplication(sys.argv)
form = WebsiteForm()
form.show()
app.exec_()[/PHP]


The CLI version:
[PHP]import urllib2

class WebsiteCopier(object):

    def SaveWebsite(self):
        try:
            websiteChoice = raw_input("What website would you like to copy?: ")
            fileType = raw_input("Would you like to save it as .xhtml or .html or .htm?: ")
            if not fileType in (".xhtml", ".html", ".htm"):
                raise ValueError, "the specified file type is not valid."
                exit(1)
            if not websiteChoice.startswith("http://"):
                websiteChoice = "http://" + websiteChoice
            website = urllib2.urlopen(str(websiteChoice)).read()
            print "Opening URL..."
            fileTitle = website.split("<title>")[1].split("</title>")[0] + fileType
            websiteFile = open(fileTitle, "w")
            print "Opening %s..." % fileTitle
            websiteFile.writelines(website)
            websiteFile.close()
            print "Successfully completed copying website to " + fileTitle + "!"
        except Exception, e:
            print "Error in downloading or writing website to file: \t%s" % e
if __name__ == "__main__":
    WebsiteCopier = WebsiteCopier()
    WebsiteCopier.SaveWebsite()

[/PHP]

---

### Post by conehead77 on 2008-08-16
Haskell (only basic reqirements)
```

import Network.URI (parseURI)
import Network.HTTP.Simple (httpGet)
   
main = do
  Just content <- httpGet uri
  writeFile "index.xhtml" content
  where Just uri = parseURI "http://laroza.freehostia.com/home/index.php"

```

Edit: Another version using curl bindings:
```

import qualified Data.ByteString.Char8 as B (unpack)
import Network.Curl.Download (openURI)

main = do
  uri <- openURI "http://laroza.freehostia.com/home/index.php"
  writeFile "index.xhtml" $ either show B.unpack uri

```

If you dont know about cabal install (unfortunately not packaged in Hardy) it will probably take some time to install the libraries. If someone really wants to know i can post a little howto.

---

### Post by Sinkingships7 on 2008-08-16
> **Darkhack said:**
> That's true if you're only using the standard library, but nobody expects that these days.  [Curl]("http://curl.haxx.se/") is absolutely amazing and can do almost anything.

When I was attempting this in C++ (before I tried Python), I looked into Curl. But I cannot, for the life of me, figure out how to use it. Any guidance here?

---

### Post by shae on 2008-08-16
> **Sinkingships7 said:**
> When I was attempting this in C++ (before I tried Python), I looked into Curl. But I cannot, for the life of me, figure out how to use it. Any guidance here?

When I first started out on mine, I tried to figure out libcurl, but for the life of me I did not get it.  I ended up just figuring out sockets.

It was not too bad with this guide: [http://www.beej.us/guide/bgnet/output/html/multipage/index.html](http://www.beej.us/guide/bgnet/output/html/multipage/index.html)

---

### Post by Darkhack on 2008-08-16
> **Sinkingships7 said:**
> When I was attempting this in C++ (before I tried Python), I looked into Curl. But I cannot, for the life of me, figure out how to use it. Any guidance here?

Curl works in a sort of odd way and I was a little stumped at first too, but I think I actually like it.  It works by writing code as if was being used like a command line program.  You pass all your arguments, telling curl what you want to do, via curl_easy_setopt(), before it actually does anything.  The actual process of running the command isn't done until you call curl_easy_perform().

First, make sure libcurl4-gnutls-dev is installed and you have #include <curl/curl.h> in your program.

Now we need a handler, much like a FILE handler when working with file streams.  This is the same kind of thing but we're using a network stream with curl's interface.

```

CURL *curl = curl_easy_init();
...
curl_easy_cleanup(curl);

```

Above I created the stream with a pointer called curl and at the end I cleaned it up (acts like free() or fclose() function).  You do not need to create a new instance of curl for each and every connection.  Use the same instance and just clean up when you're done with all networking.  Here is how I did the challenge.

```

char *url = "http://...";
FILE *fp = fopen("index.xhtml", "w");

CURL *curl = curl_easy_init();
curl_easy_setopt(curl, CURLOPT_URL, url);
curl_easy_setopt(curl, CURLOPT_WRITEDATA, fp);
curl_easy_perform(curl);
curl_easy_cleanup(curl);

```

curl_easy_setopt() works like this...

```

curl_easy_setopt(1, 2, 3);
1 = the instance of curl
2 = the variable to change
3 = the value of that variable

```

There are lots of different variables I can set in curl.  CURLOPT_URL for example tells curl to download the URL via http.  CURLOPT_WRITEDATA takes a FILE pointer for an argument and writes what ever data has been received to the file.  curl_easy_perform() actually carries out the action.

See Also:
[http://curl.haxx.se/libcurl/c/libcurl-tutorial.html](http://curl.haxx.se/libcurl/c/libcurl-tutorial.html)
[http://curl.haxx.se/libcurl/c/curl_easy_setopt.html](http://curl.haxx.se/libcurl/c/curl_easy_setopt.html)

---

### Post by Sinkingships7 on 2008-08-16
[QUOTE=shae]When I first started out on mine, I tried to figure out libcurl, but for the life of me I did not get it.  I ended up just figuring out sockets.

It was not too bad with this guide: [http://www.beej.us/guide/bgnet/output/html/multipage/index.html](http://www.beej.us/guide/bgnet/output/html/multipage/index.html)[/QUOTE]

I'm reading through the tutorial and taking notes/reference as I go along. I love his writing style; it lightens up the situation with humor. :)

@Darkhack: Thanks for the explanation!

I've decided to take on both. Though I think the socket tutorial has a greater hold on my interest. Thank you both! I'm going to attempt this program again using one or both of those methods.

---

### Post by myrtle1908 on 2008-08-16
```

#!/usr/bin/perl

use strict;
use warnings;
use LWP::Simple;
use Getopt::Std;

my %options;
my ($url, $content, $title);

&getopts("u:", \%options);
&usage if !$options{u};

$url = $options{u};
if ($url !~ /^http:\/\//i) {
	$url = 'http://' . $url;
}

$content = get($url);
if ($content) {
	$title = ($content =~ /<title>(.*?)<\/title>/gi) ? $1 : "index";
	$title .= ".xhtml";
	open F, ">$title" || die "Cannot write: $!\n";
	print F $content;
	close F;
} else {
	die "Could not open resource: $url\n";
}

print "Resource saved as: $title\n";

sub usage() {
	print "Usage: $0 -u url\n";
	exit;
}

```

---

### Post by Titan8990 on 2008-08-16
Alright, here is my updated code. It complies with one of the two extra credits. If I have time before the thread is closed I will make another attempt at part 2 of the extra credit.

[php]#!/usr/bin/env python

import urllib2
import sys

xhtml_file = open("index.xhtml", "w")

the_page = raw_input("Please enter a URL to download: ")

try: 
	web = urllib2.urlopen(the_page)

except:
	print "\n\nThe URL you have entered is not valid.\n\n Don't forget the http:// prefix on your URL."
	raw_input("\nPress the enter key to exit.")
	sys.exit()


xhtml_file.write(web.read())

xhtml_file.close()

raw_input("\n\nIt's done, please press the enter key to exit")[/PHP]

---

### Post by true_friend on 2008-08-17
C# and the simplest way to download a file. Here what I did.
```
using System;
using System.Net;
namespace WebPage
{
	class WebPage
	{
		static void Main(string[] args)
		{
			string path = @"http://laroza.freehostia.com/home/index.php";
			Console.WriteLine("Enter the file name to save data");
			string localpath = Console.ReadLine();
//c# class simplest class to deal with web
			WebClient wc = new WebClient();
//it will download the file to local path
			wc.DownloadFile(path, localpath);
			Console.WriteLine("Thank You. Press Any Key to Exit");
			Console.ReadKey();
		}
	}

}
```
Regards

---

### Post by jimi_hendrix on 2008-08-17
well that beats my C# app with simplicity...question: what does the @sign before the first string definition mean...i never learned that

EDIT: also what does the WebClient class do?

---

### Post by true_friend on 2008-08-18
@ sign ignores all the unescaped characters in a string. Like to write '\' in a string it is escaped '\\' but by adding @ sign the engine ignores such things. It is specially useful while constructing regex and such http and ftp addresses. 
WebClient is the simplest class to download a file. I haven't used it extensively, because i m a beginner and still learner of c# (which is my first ever programming lang aswell). You can find details on [msdn]("http://msdn.microsoft.com/en-us/library/system.net.webclient(VS.80).aspx") and [mono docs]("http://www.go-mono.com/docs/")
Regards

---

### Post by Titan8990 on 2008-08-18
Would someone mind posting a python example using regular expression? The python reference manual was not helpful to me. Their examples uses re.compile yet anytime I try to use one of the re. modules it tells me that "re" is not defined.

[php]jordan@bourne:~$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import urllib2
>>> xhtml_file = open("index.xhtml", "w")
>>> web = urllib2.urlopen('http://laroza.freehostia.com/home/index.php')
>>> re.compile("<title>").match(web, 1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 're' is not defined
>>> web.compile("<title>").match(web, 1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: addinfourl instance has no attribute 'compile'
>>> web("<title>").match(web, 1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: addinfourl instance has no __call__ method
>>> web = re.match(str)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 're' is not defined
>>> web = re.compile(str)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 're' is not defined[/php]


Can anyone point be in the right direction?

---

### Post by LaRoza on 2008-08-18
> **Titan8990 said:**
> Would someone mind posting a python example using regular expression? The python reference manual was not helpful to me. Their examples uses re.compile yet anytime I try to use one of the re. modules it tells me that "re" is not defined.

Can anyone point be in the right direction?

Run this first ;)

```

import re

```

---

### Post by Wybiral on 2008-08-18
> **slavik said:**
> BTW, is use of urllib/lwp and such allowed, LaRoza? Seems like a cop out to me. :P (Use the socket, Luke).

Not everyone likes to do things the hard way :)

---

### Post by LaRoza on 2008-08-18
> **Wybiral said:**
> Not everyone likes to do things the hard way :)

You should have seen his solution...

---

### Post by Titan8990 on 2008-08-18
Thank you, LaRoza. I want to make sure I understand something else correctly. In order to use the search() or match() functions I must first convert the web page in to a string?

I have used regular expression a little bit in school with grep and would like to make it work here.

---

### Post by LaRoza on 2008-08-18
> **Titan8990 said:**
> Thank you, LaRoza. I want to make sure I understand something else correctly. In order to use the search() or match() functions I must first convert the web page in to a string?

I have used regular expression a little bit in school with grep and would like to make it work here.

I don't know. I never use RE's in Python.

You shouldn't use them for structured markup especially. I could put a "<!--<title>Alternative Title</title>-->" in there and your entry would be wrong.

---

### Post by Titan8990 on 2008-08-18
It also looks like converting the variable that contains the web page data into a string is not trivial either:

[php]Python 2.5.1 (r251:54863, Jul 31 2008, 23:17:40) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import urllib2
>>> import re
>>> web = urllib2.urlopen('http://laroza.freehostia.com/home/index.php')
>>> print web
<addinfourl at 3081093036L whose fp = <socket._fileobject object at 0xb7dc2304>>
>>> web = str(web)
>>> print web
<addinfourl at 3081093036L whose fp = <socket._fileobject object at 0xb7dc2304>>
>>> test = str(web)
>>> print test
<addinfourl at 3081093036L whose fp = <socket._fileobject object at 0xb7dc2304>>[/php]

I guess I will have to look in to another method of doing a grep type search of a variable containing web page code...

---

### Post by M_the_C on 2008-08-18
> **Titan8990 said:**
> It also looks like converting the variable that contains the web page data into a string is not trivial either:

[php]Python 2.5.1 (r251:54863, Jul 31 2008, 23:17:40) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import urllib2
>>> import re
>>> web = urllib2.urlopen('http://laroza.freehostia.com/home/index.php')
>>> print web
<addinfourl at 3081093036L whose fp = <socket._fileobject object at 0xb7dc2304>>
>>> web = str(web)
>>> print web
<addinfourl at 3081093036L whose fp = <socket._fileobject object at 0xb7dc2304>>
>>> test = str(web)
>>> print test
<addinfourl at 3081093036L whose fp = <socket._fileobject object at 0xb7dc2304>>[/php]

I guess I will have to look in to another method of doing a grep type search of a variable containing web page code...I think I see your problem.  urllib.urlopen returns the location, you need to end it with .read() .  To use your example:
```
web = urllib2.urlopen('http://laroza.freehostia.com/home/index.php').read()
```This way, instead of storing the location it stores what is there.

---

### Post by jimi_hendrix on 2008-08-18
when are we judging this...im curious to see the winners

---

### Post by LaRoza on 2008-08-18
> **jimi_hendrix said:**
> when are we judging this...im curious to see the winners

I am not going to judge anymore (no polls)

Hopefully, the challenges will be good learning experiences with feedback.

I will make a new challenge soon with this new scheme explictly described in the first post.

---

### Post by Titan8990 on 2008-08-18
Even though I am typically a very competitive person I do not view these challenges as a competition. They are good learning experiences and nothing more.

---

### Post by jimi_hendrix on 2008-08-18
winner was the wrong word...i should have said if mine can compile :) and when the next one comes out

---

### Post by LaRoza on 2008-08-18
> **jimi_hendrix said:**
> winner was the wrong word...i should have said if mine can compile :) and when the next one comes out
I tried this: [http://ubuntuforums.org/showpost.php?p=5594160&postcount=67](http://ubuntuforums.org/showpost.php?p=5594160&postcount=67)

Because I felt sympathetic, I fixed two bugs in it, and it couldn't save (I was running it not in my home).

Please look it over and fix the variable names (remember, they are case sensitive!) and have it save where ever it is being run.

---

### Post by jimi_hendrix on 2008-08-18
ya i know what happend...it was late and my OCD to make my naming convention perfect and i kinda fell asleep halfway through me changing the capitalization

any clue why it wont compile on my ubuntu computer...says something along the lines of System.Net doesnt exist

---

### Post by true_friend on 2008-08-19
> **jimi_hendrix said:**
> ya i know what happend...it was late and my OCD to make my naming convention perfect and i kinda fell asleep halfway through me changing the capitalization

any clue why it wont compile on my ubuntu computer...says something along the lines of System.Net doesnt exist
"System.Net" is a standard class library shipped with c# (both ms .net and mono).
Perhaps the compiler u are using is old. Looks it is mcs try to use gmcs (mono 2). Otherwise the problem is of mono installation, as far as I think, because there is nothing "advanced" in this code that mono hasn't implemented.
Regards

---

### Post by Titan8990 on 2008-08-20
Ignore this post. I descided it was best to create a different thread geared towards my question (which is somewhat unrelated to the challenge).

---

### Post by dwhitney67 on 2008-08-20
It doesn't get any easier than this...
[PHP]#include <cstdlib>
int main()
{
  system( "wget http://laroza.freehostia.com/home/index.php >& /dev/null; mv index.php index.xhtml" );
  return 0;
}[/PHP]

---

### Post by jimi_hendrix on 2008-08-20
> **true_friend said:**
> "System.Net" is a standard class library shipped with c# (both ms .net and mono).
Perhaps the compiler u are using is old. Looks it is mcs try to use gmcs (mono 2). Otherwise the problem is of mono installation, as far as I think, because there is nothing "advanced" in this code that mono hasn't implemented.
Regards

i followed what was in the sticky for getting a compiler

---

### Post by Sinkingships7 on 2008-08-24
Is there going to be a 5th challenge?

---

### Post by nvteighen on 2008-08-24
I might have an idea for a fifth... It would be to solve a real daily life problem I have and combine some of the knowledge stated here...

---

### Post by Sinkingships7 on 2008-08-24
> **nvteighen said:**
> I might have an idea for a fifth... It would be to solve a real daily life problem I have and combine some of the knowledge stated here...

PM the idea to LaRoza?

---

### Post by LaRoza on 2008-08-24
> **nvteighen said:**
> I might have an idea for a fifth... It would be to solve a real daily life problem I have and combine some of the knowledge stated here...

PM's and suggestion welcome on the subject!

I am still thinking of what 5 should be...

---

### Post by jimi_hendrix on 2008-08-24
> **nvteighen said:**
> I might have an idea for a fifth... It would be to solve a real daily life problem I have and combine some of the knowledge stated here...

also you could probably post the idea yourself...theres no rule saying laroza has to  post it

---

### Post by DaymItzJack on 2008-08-24
> **jimi_hendrix said:**
> also you could probably post the idea yourself...theres no rule saying laroza has to  post it

It's more uniform and official if only one person does it.

---

### Post by Sinkingships7 on 2008-08-24
> **daymitzjack said:**
> it's more uniform and official if only one person does it.

+1

---

### Post by nvteighen on 2008-08-25
Ok, I'll PM LaRoza.

Also, I think the idea should be reviewed first in order to see if it's appropiate or not.

---

### Post by generalguy on 2008-08-25
[PHP]
wget -O index.xhtml http://laroza.freehostia.com/home/index.php
[/PHP]

:D

---

### Post by JupiterV2 on 2008-10-03
It works, it does what is asked of it. It doesn't handle poor user input all that well though.

[PHP]#!/bin/sh

target_site="http://laroza.freehostia.com/home/index.php"
temp_file=/tmp/www.$$

trap 'rm -f $temp_file' EXIT

if [ "$1" != "" ]; then 
    target_site=$1
fi

echo "Attempting to acquire file: $target_site"
wget -q $target_site -O $temp_file

if [ $? ]; then
    echo "Failed to aquire file: $target_site"
    exit 1
fi

title="$(grep '<title>' $temp_file | sed 's/<\.title>//' | sed 's/<\/title>//')"

file_ext=${target_site##*.}
cp -f $temp_file "$title.$file_ext"

exit 0[/PHP]

---

### Post by RobOrr on 2009-06-03
Here's my code. Larger than it strictly needs to be, but mostly due to my exception handling and user interface. 
[php]#!/usr/bin/python
#Filename: challenge4.py
#Author: Robert Orr

import sys
import urllib2

print '\nWelcome to the WebPage Download Program.\nIf you wish to exit, \
please type exit at the prompt.'
print '--------------------------------------------------------'
url = raw_input('Please enter the URL you wish to download source code from:\n')

if url == 'exit':
    print 'Thankyou for using this program.'
    sys.exit()

#open the url file if it is a valid url
try:    
    webpage = urllib2.urlopen(url)
except urllib2.URLError:
    print 'Please enter a working URL next time.'
    sys.exit()
except ValueError:
    print 'Incorrect format. Please enter a URL next time.'
    sys.exit()

#create the local file and transfer the data over.
localpage = file('index.xhtml', 'w')
transferdata = webpage.read()
localpage.write(transferdata)

webpage.close()
localpage.close()

print '\nThankyou for using this program.'
print '%s is now stored in index.xhtml.' % url
[/php]

---

### Post by texaswriter on 2010-08-21
Most basic, in C#, requires a valid html address including http:// ... 

This does virtually no validation, but it works if valid html addresses are entered, 100%. This I compile in Monodevelop, I don't think anything special is required to compile. 

[PHP]using System;
using System.Net;

class MainClass
{
    public static void Main (string[] args)
    {
        WebClient client = new WebClient();
        int i = 0;
        string filebase = "wgetted - ";
        string filename;
        
        foreach(string arg in args)
        {
            Console.WriteLine("{0}", arg);
            client.DownloadFile(arg, filebase+i.ToString());
            i++;
        }
        
    }
}
 [/PHP]

---

### Post by xSaintFunkyx on 2011-05-11
Way too late. Just wanted the comments if anyone had any...

```

import java.net.*;
import java.io.*;
import javax.swing.*;

public class URLWriter {
    public static void main(String[] args) throws Exception {
           
        String inputUrl = JOptionPane.showInputDialog("Please enter the url you wish to read: ");
        URL url = new URL(inputUrl);
        URLConnection uC = url.openConnection();
        BufferedReader in = new BufferedReader(
                                new InputStreamReader(
                                uC.getInputStream()));
        String inputLine;

        PrintWriter outFile = new PrintWriter("HTMLFILE.txt");    
          
        System.out.println("Writing to file...");
        while ((inputLine = in.readLine()) != null) 
        {
            outFile.println(inputLine);
        }
        System.out.println("\nDone.");
        in.close();
        outFile.close();
    }
}

```Vers. 1.1

```

import java.net.*;
import java.io.*;
import javax.swing.*;

public class URLWriter {
    public static void main(String[] args) throws Exception {
           
          boolean valid = false;          
          while (!(valid))
          {      
              try
              {    
                   String inputUrl = JOptionPane.showInputDialog("Please enter the url you wish to read: ");
                   URL url = new URL(inputUrl);
                   URLConnection yc = url.openConnection();
                   valid = true; // if connection is succesful    
                   BufferedReader in = new BufferedReader(
                                        new InputStreamReader(
                                        yc.getInputStream()));        
                   String inputLine;
                   PrintWriter outFile = new PrintWriter("HTMLFILE.txt");    
                  
                   System.out.println("Writing to file...");
                   while ((inputLine = in.readLine()) != null) 
                   {
                       outFile.println(inputLine);
                   }
                   System.out.println("\nDone.");
                   in.close();
                   outFile.close();            
                  
              }
              catch(MalformedURLException e)
              {
                  JOptionPane.showMessageDialog(null, "Please enter a valid url in the format - http://theurladdresshere/");

              }
          }
          
     }
}

```

---

### Post by CuracaoThe on 2011-07-10
Written in Ruby:

[PHP]
require 'open-uri'

module PageScrape

  def self.start_scraping(url="http://www.tomayko.com/")
    # Either open an url from command line argument 
    # or, if no argument provided, open a default url.
    page = open(ARGV[0] || url)

    # Default filename.
    filename = "index"

    # Parse webpage to find a title. If no title
    # provided, then use default filename.
    page.readlines.each do |line|
      filename = $1 if line.match(/<title>(.*)<\/title>/)
    end

    page.rewind
    File.open("#{filename}.xhtml", "w+") do |f|
      f.puts page.readlines.join
    end
  end
  
end

PageScrape.start_scraping
[/PHP]

---

### Post by CoyleTrydan on 2013-01-03
I know I'm a little late to the party here, but I'm working on learning Python, and hope to be able to contribute some in the future. This seems like a great way to start towards that goal. Sorry if I'm necro-ing something that I'm not supposed to. :) I'm not sure if I should do these all sequentially, or jump up to some of the later challenges.

Here is my Challenge 4. I like to separate things out into functions, but I'm not sure if doing so like I have is good form. I'd love feedback on that. I also tried to get exception handling in there, and it seems to work, but it just doesn't feel quite right...

Thanks for any feedback! Not sure if anyone will even see this... :)

[php]
from __future__ import print_function
import urllib2

def getWeb(url):
    try:    
        site = urllib2.urlopen(url)
        source = site.read()
        return(source)
    except urllib2.URLError:
        print("The page was unable to be accessed.")
        
def writeFile(source):
    try:    
        file = open("index.xhtml", "w")
        file.write(source)
        file.close()
    except IOError:
        print("The file was not able to be saved.")

def selectSite():
        url = raw_input("Please enter a URL:")
        return(url)
        
def main():
    url = selectSite()
    
    while True:    
        try:    
            source = getWeb(url)
            writeFile(source)
            print("The page was successfully saved.")
            break
        except ValueError:
            print("That is not a valid URL.")
            url = selectSite()

main()
[/php]

---

### Post by r-senior on 2013-01-03
> **CoyleTrydan said:**
> I like to separate things out into functions, but I'm not sure if doing so like I have is good form. I'd love feedback on that. I also tried to get exception handling in there, and it seems to work, but it just doesn't feel quite right...
I found both your programs easy to read and understand largely because of the way you have separated them into individual functions that each have a clear purpose. You could work on the names (functions and variables) a little bit to make the code that calls them read even more clearly but the structure is good IMO.

You might want to look more closely at your error handling of the file in this submission, in particular whether you need a finally block and whether your error message is accurate. Or consider the 'with' statement.

In your [other submission]("http://ubuntuforums.org/showthread.php?p=12436560#post12436560"), I found your checkGuess function and while loop a bit cumbersome. Also, checking for an out of range input would be better handled with simple loops and conditionals rather than assert and exceptions IMO.

Icing on the cake would be some docstrings and perhaps choose to follow the PEP8 Python style guide more rigorously. Tools like pylint are very useful for advising you about code quality in that respect.

---

### Post by shadyWilliams on 2013-03-05
Hi all,

First things first, first post here on Ubuntu forums!

Second, I know I am way too late to enter the contest, but I am using these beginner exercises to learn C#. Here is what I came up with:


C# (C-Sharp)
```
using System;using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Net;


namespace ProgramChallenge4
{
    class ProgramChallenge4
    {
        static void Main(string[] args)
        {
            bool keepRunning = true;
            string url = "";
            while (keepRunning)
            {
                url = SelectSite();
                UpdateURL(ref url);
                try
                {
                    DownloadSite(ref url);
                    keepRunning = false;
                }
                catch (Exception)
                {
                    Console.WriteLine("You've entered an invalid URL =/");
                }
            }
            Console.WriteLine(url + " downloaded and saved!");
            Console.ReadLine();
        }


        public static string SelectSite()
        {
            Console.WriteLine("Please enter a valid URL: ");
            string url = Console.ReadLine();
            return url;
        }


        public static string UpdateURL(ref string url)
        {
            url = url.Trim();
            if (url.IndexOf("http://", 0) != 0)
                url = "http://" + url;
            return url;
        }


        public static string DownloadSite(ref string url)
        {
                WebClient wc = new WebClient();
                wc.DownloadFile(url, @"C:\Users\Will\Desktop\Programming Material\Challenges\Program Challenge 4\index.html");
                return url;
        }


    }
}



```

---

