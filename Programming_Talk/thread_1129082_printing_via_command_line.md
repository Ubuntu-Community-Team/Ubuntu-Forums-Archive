---
title: "printing via command line?"
date: 2009-04-18
forum: Programming Talk
---

### Post by shane2peru on 2009-04-18
Ok, I have been getting into this command line stuff for a while, and it is unbelievable powerful and fast.  So I have a lot of pdf files that I want to print, however they need to be booklet style.  I can send it out to ps via acroread in the format I want if need be, but in an effort to speed up my printing process I want to print it via command line, and script it out.  I'm printing on a non-duplex printer and want to print lets say about 20 pages at a time for simplicity sake.  Here is what I have come up with,
```

lp -dhp-laserjet -P4 -q90 -t"test run" -Himmediate -o media=a4 filename

``` I understand all of the above, and could easily manipulate the page numbers and script that.  However the job goes to que and sets there and doesn't print.  Ideally I would like to print odd pages then even pages at 20 pages at a time.  Print odd, then wait while I re-insert pages print even pages in reverse order, then start the process all over again for the next 20 pages till it hits the end of the file.  If I can put print directly from the pdf file it would save me a step of opening the pdf in acroread and sending it to a ps file as booklet format, but either way it would be a faster process than manually opening it in acroread and printing 20 pages, then fliping printing another the same 20 etc until the end of the book which has 300+ pages.  Any help would be greatly appreciated.  Thanks!!!

Shane

---

### Post by unutbu on 2009-04-18
There is a utililty called pdftops (in the poppler-utils package) which can do the conversion:
```

pdftops test.pdf test.ps
```

There is a utility called psselect (in the psutils package) which can split a ps file into its odd-pages and even-pages halves.
```

psselect -o test.ps test_odd.ps
psselect -e test.ps test_even.ps

```
psselect can also pick-off certain pages within a postscript file.
```

psselect -p1-20 test_odd.ps test_odd_1_20.ps
```

Using this command repeatedly, you can prepare 20-page chunks of odd and even pages that you can send to the printer individually, flipping the pages as needed to create the duplex effect. 

Below is a script which automates the process.
If you'd like to try it, first install these packages:
[PHP]
sudo apt-get install poppler-utils psutils[/PHP]

Here is the script:
[PHP]
#!/usr/bin/env python

from subprocess import Popen,PIPE,STDOUT
import optparse
import os
import re

__usage__='''
lp_duplex.py -f test.pdf -n 20 -c "lpr -o number-up=2 -o sides=two-sided-short-edge -o media=A4"
'''
usage = 'usage: %prog [options]'
parser = optparse.OptionParser(usage=usage)
parser.add_option('-f', '--file', dest='file', 
                  default='',
                  help='pdf file', 
                  metavar='FILE')
parser.add_option('-c', '--command', dest='command', 
                  default='lpr',
                  help='the command used to print, e.g. "lpr"', 
                  metavar='COMMAND')
parser.add_option('-n', '--num', dest='num', 
                  default=20,
                  type='int',
                  help='number of pages to do at a time', 
                  metavar='INTEGER')

(opt, args) = parser.parse_args()
if not opt.file:
    parser.print_help()
    exit(1)

ps_file=opt.file

pat='Wrote (\d+) pages'

basename,ext=os.path.splitext(ps_file)
ps_odd_file=basename+'_odd'+'.ps'
cmd='psselect -o %s %s'%(ps_file,ps_odd_file)
print(cmd)
proc=Popen(cmd, shell=True, stdout=PIPE, stderr=PIPE)
output=proc.communicate()[1]
match=re.search(pat,output)
num_odd_pages=int(match.group(1))

ps_even_file=basename+'_even'+'.ps'
cmd='psselect -e %s %s'%(ps_file,ps_even_file)
print(cmd)
proc=Popen(cmd, shell=True, stdout=PIPE, 
           stderr=PIPE)
output=proc.communicate()[1]
match=re.search(pat,output)
num_even_pages=int(match.group(1))

begin=1
end=opt.num

partials=[]
while num_odd_pages>0:
    ps_even_partial=basename+'_even_%s_%s'%(begin,end)+'.ps'
    cmd='psselect -p%s-%s %s %s'%(begin,end,ps_even_file,ps_even_partial)
    print(cmd)
    proc=Popen(cmd, shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    partials.append(ps_even_partial)

    ps_odd_partial=basename+'_odd_%s_%s'%(begin,end)+'.ps'
    cmd='psselect -r -p%s-%s %s %s'%(begin,end,ps_odd_file,ps_odd_partial)
    print(cmd)
    proc=Popen(cmd, shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    partials.append(ps_odd_partial)

    begin+=opt.num
    end+=opt.num
    num_odd_pages-=opt.num

for filename in partials:
    cmd='%s %s'%(opt.command,filename)
    print(cmd)
    proc=Popen(cmd, shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    raw_input('Flip pages and press Enter to continue')
[/PHP]

Save this as ~/bin/lp_duplex.py

Make it executable:
```

chmod 755 ~/bin/lp_duplex.py
```

Run it like this:
```

lp_duplex.py -f test.ps -n 20 -c "lp -dHP-Laserjet-1022n"
```

The program tells you the commands it is running. Here is what the output would look like:

```

psselect -o test.ps test_odd.ps
psselect -e test.ps test_even.ps
psselect -p1-20 test_even.ps test_even_1_20.ps
psselect -r -p1-20 test_odd.ps test_odd_1_20.ps
psselect -p21-40 test_even.ps test_even_21_40.ps
psselect -r -p21-40 test_odd.ps test_odd_21_40.ps
psselect -p41-60 test_even.ps test_even_41_60.ps
psselect -r -p41-60 test_odd.ps test_odd_41_60.ps
psselect -p61-80 test_even.ps test_even_61_80.ps
psselect -r -p61-80 test_odd.ps test_odd_61_80.ps
lp -dHP-Laserjet-1022n test_even_1_20.ps
Flip pages and press Enter to continue
lp -dHP-Laserjet-1022n test_odd_1_20.ps
Flip pages and press Enter to continue
lp -dHP-Laserjet-1022n test_even_21_40.ps
Flip pages and press Enter to continue
lp -dHP-Laserjet-1022n test_odd_21_40.ps
Flip pages and press Enter to continue
lp -dHP-Laserjet-1022n test_even_41_60.ps
Flip pages and press Enter to continue
lp -dHP-Laserjet-1022n test_odd_41_60.ps
Flip pages and press Enter to continue
lp -dHP-Laserjet-1022n test_even_61_80.ps
Flip pages and press Enter to continue
lp -dHP-Laserjet-1022n test_odd_61_80.ps
Flip pages and press Enter to continue

```

---

### Post by shane2peru on 2009-04-18
> **unutbu said:**
> There is a utililty called pdftops (in the poppler-utils package) which can do the conversion:
```

pdftops test.pdf test.ps
```

There is a utility called psselect (in the psutils package) which can split a ps file into its odd-pages and even-pages halves.
```

psselect -o test.ps test_odd.ps
psselect -e test.ps test_even.ps

```
psselect can also pick-off certain pages within a postscript file.
```

psselect -p1-20 test_odd.ps test_odd_1_20.ps
```

Using this command repeatedly, you can prepare 20-page chunks of odd and even pages that you can send to the printer individually, flipping the pages as needed to create the duplex effect. 

Below is a script which automates the process.
If you'd like to try it, first install these packages:
[PHP]
sudo apt-get install poppler-utils psutils[/PHP]

Here is the script:
[PHP]
#!/usr/bin/env python

from subprocess import Popen,PIPE,STDOUT
import optparse
import os
import re

usage = 'usage: %prog [options]'
parser = optparse.OptionParser(usage=usage)
parser.add_option('-f', '--file', dest='file', 
                  default='',
                  help='pdf file', 
                  metavar='FILE')
parser.add_option('-n', '--num', dest='num', 
                  default=20,
                  type='int',
                  help='number of pages to do at a time', 
                  metavar='INTEGER')

(opt, args) = parser.parse_args()

pdf_file=opt.file
basename,ext=os.path.splitext(pdf_file)
ps_file=basename+'.ps'

cmd='pdftops %s %s'%(pdf_file,ps_file)
print(cmd)
proc=Popen(cmd, shell=True, stdout=PIPE, )
proc.communicate()[0]

pat='Wrote (\d+) pages'

ps_odd_file=basename+'_odd'+'.ps'
cmd='psselect -o %s %s'%(ps_file,ps_odd_file)
print(cmd)
proc=Popen(cmd, shell=True, 
           stdout=PIPE, 
           stderr=PIPE
           )
output=proc.communicate()[1]
match=re.search(pat,output)
num_odd_pages=int(match.group(1))

ps_even_file=basename+'_even'+'.ps'
cmd='psselect -e %s %s'%(ps_file,ps_even_file)
print(cmd)
proc=Popen(cmd, shell=True, stdout=PIPE, 
           stderr=PIPE)
output=proc.communicate()[1]
match=re.search(pat,output)
num_even_pages=int(match.group(1))

begin=1
end=opt.num

partials=[]
while num_odd_pages>0:
    ps_odd_partial=basename+'_odd_%s_%s'%(begin,end)+'.ps'
    cmd='psselect -p%s-%s %s %s'%(begin,end,ps_odd_file,ps_odd_partial)
    print(cmd)
    proc=Popen(cmd, 
               shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    partials.append(ps_odd_partial)

    ps_even_partial=basename+'_even_%s_%s'%(begin,end)+'.ps'
    cmd='psselect -p%s-%s %s %s'%(begin,end,ps_even_file,ps_even_partial)
    print(cmd)
    proc=Popen(cmd, 
               shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    partials.append(ps_even_partial)

    begin+=opt.num
    end+=opt.num
    num_odd_pages-=opt.num

os.unlink(ps_odd_file)
os.unlink(ps_even_file)
for filename in partials:
#     cmd='lpr %s'%filename
    cmd='lp -dhp-laserjet -q90 -Himmediate -o media=a4 %s'%filename
    print(cmd)
    proc=Popen(cmd, 
               shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    raw_input('Flip pages and press Enter to continue')

# Clean up temporary files
for filename in partials:
    os.unlink(filename)
os.unlink(ps_file)[/PHP]

Save this as ~/bin/lp_pdf_duplex.py

Make it executable:
```

chmod 755 ~/bin/lp_pdf_duplex.py
```

Run it like this:
```

lp_pdf_duplex.py -f test.pdf -n 20
```

The program tells you the commands it is running. Here is what the output would look like:

```
pdftops test.pdf test.ps
psselect -o test.ps test_odd.ps
psselect -e test.ps test_even.ps
psselect -p1-20 test_odd.ps test_odd_1_20.ps
psselect -p1-20 test_even.ps test_even_1_20.ps
psselect -p21-40 test_odd.ps test_odd_21_40.ps
psselect -p21-40 test_even.ps test_even_21_40.ps
psselect -p41-60 test_odd.ps test_odd_41_60.ps
psselect -p41-60 test_even.ps test_even_41_60.ps
psselect -p61-80 test_odd.ps test_odd_61_80.ps
psselect -p61-80 test_even.ps test_even_61_80.ps
lp -dhp-laserjet -q90 -Himmediate -o media=a4 test_odd_1_20.ps
Flip pages and press Enter to continue
lp -dhp-laserjet -q90 -Himmediate -o media=a4 test_even_1_20.ps
Flip pages and press Enter to continue
lp -dhp-laserjet -q90 -Himmediate -o media=a4 test_odd_21_40.ps
Flip pages and press Enter to continue
lp -dhp-laserjet -q90 -Himmediate -o media=a4 test_even_21_40.ps
Flip pages and press Enter to continue
lp -dhp-laserjet -q90 -Himmediate -o media=a4 test_odd_41_60.ps
Flip pages and press Enter to continue
lp -dhp-laserjet -q90 -Himmediate -o media=a4 test_even_41_60.ps
Flip pages and press Enter to continue
lp -dhp-laserjet -q90 -Himmediate -o media=a4 test_odd_61_80.ps
Flip pages and press Enter to continue
lp -dhp-laserjet -q90 -Himmediate -o media=a4 test_even_61_80.ps
Flip pages and press Enter to continue
```
WOW!  :shock:  That is an awesome script (python coding).  Ok, I don't understand all of that since I don't know python.  I do bashscripting, and some of it does make sense.  After running it, it seems to not quite work right.  It printed, however all the pages were blank.  :D   After looking at the ps files that were made they aren't quite right either, they came out with super small page printed on it.  If that can be revised to take my current ps file (which I printed out of Adobe to ps) it has two pages per page for booklet printing style, and print that with this script I would be just as happy!  It would need to print even pages and odd pages just as the current script does.  Thanks!!

Shane

---

### Post by unutbu on 2009-04-18
Yes, I think taking pdftops out of the script is a good idea.

I've edited my first post.

---

### Post by shane2peru on 2009-04-18
> **unutbu said:**
> Yes, I think taking pdftops out of the script is a good idea.

I've edited my first post.
Ok, after picking through the coding I'm deciphering some of this stuff.  We are almost there, however after flipping the pages we need to run this line:
```

psselect -q -r|lp -dHP-Laserjet-1022n -q90 -Himmediate -o A4

```
  The psselect -q -r will reverse the page order feeding them through backwards to keep me from having to sort through all the pages, and change their order.
  I keep playing with the -o media=a4 because it isn't printing the right page size.  We use a4 here.  The printer is set at a4, and on the lp line I have tried several ways to get it to a4, and it doesn't seem to print correctly.  Any help anyone could offer to that end would be appreciated as well!  Thanks unutbu for this script!!!

Shane

---

### Post by unutbu on 2009-04-19
Ack! I forgot about the need to reverse some of the pages.
I've edited the script once more.

I've changed the script so all the partial files will remain (instead of being removed at the end). This way, if there is a paper jam or other mishap, you can reprint the necessary partial files more easily.

To make the script more generally useful, I've made the print command an option. The new way to run script is like this:
```

lp_duplex.py -f file.ps -n 20 -c "lp -dHP-Laserjet-1022n"
```

Are you using a CUPS ppd file to configure your printer?
If so, look in /etc/cups/ppd/. This file might contain a line like

```
*DefaultPageSize: Letter
```

This is probably not the proper way to do it, but if you edit this line, perhaps it will make the printer print in A4 format by default.

---

### Post by shane2peru on 2009-04-19
> **unutbu said:**
> Ack! I forgot about the need to reverse some of the pages.
I've edited the script once more.

I've changed the script so all the partial files will remain (instead of being removed at the end). This way, if there is a paper jam or other mishap, you can reprint the necessary partial files more easily.

To make the script more generally useful, I've made the print command an option. The new way to run script is like this:
```

lp_duplex.py -f file.ps -n 20 -c "lp -dHP-Laserjet-1022n"
```

Are you using a CUPS ppd file to configure your printer?
If so, look in /etc/cups/ppd/. This file might contain a line like

```
*DefaultPageSize: Letter
```

This is probably not the proper way to do it, but if you edit this line, perhaps it will make the printer print in A4 format by default.


Script works like a charm!!!  I need to work on getting the printout fixed, there is something not quite right with the pages.  It leaves a large border on one side a small border on the other side.  I thought it may have been the page size, but I'm not sure.  I checked the ppd file and the default is already set to A4 (I usually set that up graphically because that is the paper we use here.)  I like that it doesn't clean up the directory I can do that afterwards, and like you said in case of paper jams, or toner runs out etc.  I will continue to google the web and find the right options for the print command.  With the ps files hanging in the directory I can pick any of them and give it a whirl to see how it works. Thanks for the great script!!!  Makes me want to learn a little python.

Shane

---

### Post by shane2peru on 2009-04-23
Ok, I got this thing fixed!!!  This is great!  I need a little python help though.  I went back to the old script and figured out how to pdftops correctly and set it up to print booklet style on the command line, and have it print out correctly!!!  Don't even need to open Adobe Reader!  However I need you to help fix the page selection thing so that it reverses the second set of pages, here is the modified script.  
[php]
#!/usr/bin/env python

from subprocess import Popen,PIPE,STDOUT
import optparse
import os
import re

usage = 'usage: %prog [options]'
parser = optparse.OptionParser(usage=usage)
parser.add_option('-f', '--file', dest='file', 
                  default='',
                  help='pdf file', 
                  metavar='FILE')
parser.add_option('-n', '--num', dest='num', 
                  default=20,
                  type='int',
                  help='number of pages to do at a time', 
                  metavar='INTEGER')

(opt, args) = parser.parse_args()

pdf_file=opt.file
basename,ext=os.path.splitext(pdf_file)
ps_file=basename+'.ps'

cmd='pdftops -nocrop -paper A4 -expand %s %s'%(pdf_file,ps_file)
print(cmd)
proc=Popen(cmd, shell=True, stdout=PIPE, )
proc.communicate()[0]

pat='Wrote (\d+) pages'

ps_odd_file=basename+'_odd'+'.ps'
cmd='psselect -o %s %s'%(ps_file,ps_odd_file)
print(cmd)
proc=Popen(cmd, shell=True, 
           stdout=PIPE, 
           stderr=PIPE
           )
output=proc.communicate()[1]
match=re.search(pat,output)
num_odd_pages=int(match.group(1))

ps_even_file=basename+'_even'+'.ps'
cmd='psselect -e %s %s'%(ps_file,ps_even_file)
print(cmd)
proc=Popen(cmd, shell=True, stdout=PIPE, 
           stderr=PIPE)
output=proc.communicate()[1]
match=re.search(pat,output)
num_even_pages=int(match.group(1))

begin=1
end=opt.num

partials=[]
while num_odd_pages>0:
    ps_odd_partial=basename+'_odd_%s_%s'%(begin,end)+'.ps'
    cmd='psselect -p%s-%s %s %s'%(begin,end,ps_odd_file,ps_odd_partial)
    print(cmd)
    proc=Popen(cmd, 
               shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    partials.append(ps_odd_partial)

    ps_even_partial=basename+'_even_%s_%s'%(begin,end)+'.ps'
    cmd='psselect -p%s-%s %s %s'%(begin,end,ps_even_file,ps_even_partial)
    print(cmd)
    proc=Popen(cmd, 
               shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    partials.append(ps_even_partial)

    begin+=opt.num
    end+=opt.num
    num_odd_pages-=opt.num

os.unlink(ps_odd_file)
os.unlink(ps_even_file)
for filename in partials:
#     cmd='lpr %s'%filename
    cmd='lpr -o number-up=2 -o sides=two-sided-short-edge -o media=A4 %s'%filename
    print(cmd)
    proc=Popen(cmd, 
               shell=True, stdout=PIPE, stderr=PIPE)
    proc.communicate()
    raw_input('Flip pages and press Enter to continue')

# Clean up temporary files
for filename in partials:
    os.unlink(filename)
os.unlink(ps_file)  
[/php]

lpr doesn't need the printer specified so long it is the default printer (mine is).  Also I do like the printer option on the command line to.  I appreciate your help with this!

Shane

PS - this is the page that was of great help:  [http://www.dice.inf.ed.ac.uk/units/user_support/docs/cups-printing.html](http://www.dice.inf.ed.ac.uk/units/user_support/docs/cups-printing.html) for future reference.

---

### Post by unutbu on 2009-04-23
shane2peru, I'm happy you've found the right pdftops and lpr commands!

I will be happy to edit the script for you if that is truly what you want, but first consider this:

There is a unix principle (that I am prone to violating), which says small tools are often more useful than one big tool because small tools may be used in a variety of ways, while the big tool is only good for one thing.

In deference to this principle, I don't think it is a good idea to reintroduce pdftops to the python script. Instead, how about make a bash script:

```
#!/bin/sh
pdftops -nocrop -paper A4 -expand "$1".pdf "$1".ps
lp_duplex.py -f "$1".ps -n 20 -c "lpr -o number-up=2 -o sides=two-sided-short-edge -o media=A4"
```

Which you could call something like ~/bin/lp_pdf_duplex.sh
and which you could run on filename.pdf with a command like
```

lp_pdf_duplex.sh filename

```

---

### Post by shane2peru on 2009-04-23
> **unutbu said:**
> shane2peru, I'm happy you've found the right pdftops and lpr commands!

I will be happy to edit the script for you if that is truly what you want, but first consider this:

There is a unix principle (that I am prone to violating), which says small tools are often more useful than one big tool because small tools may be used in a variety of ways, while the big tool is only good for one thing.

In deference to this principle, I don't think it is a good idea to reintroduce pdftops to the python script. Instead, how about make a bash script:

```
#!/bin/sh
pdftops -nocrop -paper A4 -expand "$1".pdf "$1".ps
lp_duplex.py -f "$1".ps -n 20 -c "lpr -o number-up=2 -o sides=two-sided-short-edge -o media=A4"
```

Which you could call something like ~/bin/lp_pdf_duplex.sh
and which you could run on filename.pdf with a command like
```

lp_pdf_duplex.sh filename

```
Sounds like a plan!  I have a much better understanding of bash scripts anyways and I can edit them to meet the need.  I can set that up and then have it call the python script as you stated.  Thanks for the thought, and thanks for the help in whipping up the python script!

Shane

---

### Post by shane2peru on 2009-04-23
Ok if I haven't used up my favors yet, I would like to switch the even and odd page printing.  Even pages first, then odd pages in reverse order.  I was going to try and cut and past and switch the two sections, but something tells me that won't make the odd pages print in the reverse order then.  Man I wish I knew enough python to decipher this stuff.   Thanks for the help!

Shane

---

### Post by unutbu on 2009-04-23
No problem; the script on the first page has been so changed.

(Actually, your intuition was correct. All you need to do is swap the two sections and move the -r flag. The commands```


    partials.append(ps_even_partial)
...
    partials.append(ps_even_partial)

``` load the filenames into a list called partials. Their order in the list controls the order that they are printed.
)

---

### Post by Jiraiya_sama on 2009-04-23
Every time I read this topic title I think of cout and printf.

---

### Post by shane2peru on 2009-04-23
I found a few crash courses on python, looks learnable.  I will have to look into it.  It seems like bash scripts on steroids. :D  Python is heavily used on the Gnome desktop if I'm not mistaken.  Thanks for whetting the appetite. :)

Shane

---

### Post by shane2peru on 2009-04-23
> **Jiraiya_sama said:**
> Every time I read this topic title I think of cout and printf.

What are they?

Shane

---

### Post by unutbu on 2009-04-23
Glad to hear you are interested in Python. I think you will like it. Its a nifty language, simple and powerful.

There are others here who know much more about Python and programming than I do, but if I can be of any assistance, feel free to drop me a line.

---

### Post by Miljet on 2009-04-23
I, too am just beginning to learn Python. I have looked at a lot of different beginner tutorials, but the best one that I have found so far is:

[http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)

As an added bonus he compares Python script to VBscript and JavaScript for comparison.

---

### Post by shane2peru on 2009-04-30
Don't hate me, because I do appreciate the work you put into the script, but I needed something I could edit and work on.  I came up with this bash script:

[PHP]
#!/bin/bash
##Setting up all the variables that will be used.
#This script depends on psutils Make sure it is installed before running.
read -p "What book do you want to convert and print (you don't need the pdf extension)?     " book
read -p "Page numbers to print? (Multiples of 8 are best)   " p
read -p "What printer default press enter, for PDF type PDF:   "  printer
rm -f *.ps
s=1
f=1
l=$p
mkdir $book
## Declaring the functions to be used.
function pagerun {
	psnup -l -pA4 -2 $book/$book-temp$s.ps > $book/book$s.ps
	pstops "2:0" $book/book$s.ps > $book/$book-odd$s.ps
	pstops "2:-1" $book/book$s.ps > $book/$book-even$s.ps
	read -p "Ready to send to printer?" enter 
	lpr -P $printer -o media=A4 $book/$book-odd$s.ps
	#lpr -o media=A4 $book/odd$s.ps
	echo "Printing $book/$book-odd$s pages with - lpr -o media=A4 $book/$book-odd$s.ps"
	read -p "Re-insert pages and press enter" enter 
	lpr -P $printer -o media=A4 $book/$book-even$s.ps
	#lpr -o media=A4 $book/$book-even$s.ps
	echo "Printing $book/$book-even$s pages with - lpr -o media=A4 $book/$book-even$s.ps"
	echo .
	echo .
	read -p "To print next set press enter" enter
	echo .
	echo .
	s=$((s+1))
}

function cleanup {
	read -p "Did all the sets print correctly?  y/n   " ans
	if [ "$ans" = "y" ] ; then rm -rfv $book
	else
	exit
	fi
	exit
}

function selectpage {
	psselect -p$((l+1))-$((l+$p)) $book/$book.ps | psbook > $book/$book-temp$s.ps
	l=$((l+$p))
echo $l
}

function repeat {
	if [ $pcount -lt $l ] ; then echo "we are at page $l" 
	cleanup 
	else
	echo "we are at page $l"
	selectpage
	pagerun
	fi
}

## Checking page numbering to see if this script can handle the book.
total=$(grep -c %%Page: $book.pdf)

pdftops -nocrop -paper A4 -expand $book.pdf $book/$book.ps
pcount=$(grep -c %%Page: $book/$book.ps)
echo "$book has $pcount pages"

##  Sending the book to the printer!
psselect -p$f-$l $book/$book.ps | psbook > $book/$book-temp$s.ps 
pagerun

###  Right here is where I should be able to loop this and avoid the repetition.
echo "starting the loop section"

while [ $pcount -gt $l ]
	do
		repeat
	if [ $pcount -lt $l ]
	then cleanup
	fi
done

exit
[/PHP]

You did teach me a bit though.  Python is still on my plate to learn, but I needed something I could fix and edit for the time being.  Thanks for the help and input with this.  Also, I learned the value of having a bin folder in my home directory, something I have never done before.  

Shane

---

### Post by unutbu on 2009-04-30
Hey, good for you! Whatever works is a win in my book.

---

### Post by shane2peru on 2009-04-30
> **unutbu said:**
> Hey, good for you! Whatever works is a win in my book.

It turned out that psbook was what I needed to use to setup the pages correctly, so now it converts any pdf to a booklet format.  I used a lot of the things that you originally setup, pages, printer, file, so it works like a charm.  I'm running books on a regular basis with it.  Thanks again for the help.

Shane

---

