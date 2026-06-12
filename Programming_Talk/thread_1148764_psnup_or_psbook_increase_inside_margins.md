---
title: "psnup or psbook increase inside margins?"
date: 2009-05-04
forum: Programming Talk
---

### Post by shane2peru on 2009-05-04
Ok, I have written a fairly in-depth script for printing a pdf file to a book format.  It works great and I'm very pleased with it overall, and use it a lot (I print a lot of books.)  Here is my problem.  When I bind my books the print is a little closer than I would like to the binding.  I print two pages on one page, and need to increase the distance between the two pages, **but not** the outside margin.  Here is what I want

[PHP]
    --------------------------------
    | bla bla bla |  | bla bla bla |
    | bla bla bla |  | bla bla bla |
    | bla bla bla |  | bla bla bla |
    | bla bla bla |  | bla bla bla |
    | bla bla bla |  | bla bla bla |
    | bla bla bla |  | bla bla bla |
    --------------------------------
[/PHP]
to this:
[PHP]
    -----------------------------------
    | bla bla bla |     | bla bla bla |
    | bla bla bla |     | bla bla bla |
    | bla bla bla |     | bla bla bla |
    | bla bla bla |     | bla bla bla |
    | bla bla bla |     | bla bla bla |
    | bla bla bla |     | bla bla bla |
    -----------------------------------
[/PHP]
I exaggerated it to show the idea.  I want to do this with psnup or psbook or something of that nature.  
Any ideas would greatly be appreciated, thanks.

Shane

---

### Post by shane2peru on 2009-05-05
I don't know if it would be of any help, but here is my heavy duty script if you are interested in taking a look at it:

[php]
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
[/php]

Perhaps that will help.  I really need to increase that center margin, any help is appreciated.

Shane

---

### Post by unutbu on 2009-05-05
Try changing
```

 pstops "2:0" $book/book$s.ps > $book/$book-odd$s.ps
 pstops "2:-1" $book/book$s.ps > $book/$book-even$s.ps 
```

to something like
```

 pstops "2:0(1in,0in)" $book/book$s.ps > $book/$book-odd$s.ps
 pstops "2:-1(1in,0in)" $book/book$s.ps > $book/$book-even$s.ps 
```

See [http://dsl.org/cookbook/cookbook_25.html#SEC371](http://dsl.org/cookbook/cookbook_25.html#SEC371)

---

### Post by shane2peru on 2009-05-05
> **unutbu said:**
> Try changing
```

 pstops "2:0" $book/book$s.ps > $book/$book-odd$s.ps
 pstops "2:-1" $book/book$s.ps > $book/$book-even$s.ps 
```

to something like
```

 pstops "2:0(1in,0in)" $book/book$s.ps > $book/$book-odd$s.ps
 pstops "2:-1(1in,0in)" $book/book$s.ps > $book/$book-even$s.ps 
```

See [http://dsl.org/cookbook/cookbook_25.html#SEC371](http://dsl.org/cookbook/cookbook_25.html#SEC371)

Well, that was worth a shot, but that seems to move both pages down on the page and leaves a top border of 1 inch.  if you adjust the second number it runs both pages to the right so that the second page falls off the edge and the right border is 1 inch (or whatever the setting is).  Somehow I think this is going to need to be done with psnup and not use psbook.  I have scoured the web and have been unable to come up with a correct answer.  I can live with what I have, but would really like to tweak it to make it that much better.  Thanks for the input!

Shane

---

### Post by shane2peru on 2009-05-05
OK, I think I have got it!  The key is in psnup.

This code will do the trick:
```

psnup -l -pA4 -2 -m-.5in -b1in file.ps

```
Ok, the **-b1in** puts a 1 inch border around each page (2 pages per sheet) and then the -m is the page margin, so we negate the border by placing a negative margin that goes around the entire sheet with **-m[COLOR="Red"]-[/COLOR].5**.  I still end up loosing space of the top of each sheet, however it increases my center page margin.  Clear as mud?

If someone else finds a better idea, I'm all ears.

Shane

---

### Post by unutbu on 2009-05-05
Sorry about my last suggestion -- I obviously didn't test what I wrote.

The following may work better, but you'll have to experiment a little with it to fit your situation:
```

pstops -d "2:0L@.7(1w,-0.5in)+1L@.7(1w,0.5h)" input.ps output.ps

```
This crazy looking command is sort of like "psnup -2", except that the "(xoffset,yoffset)" syntax gives you a lot of control over the placement of the pages. 

Let's try breaking apart "2:0L@.7(1w,-0.5in)":

"2:0" means print pages congruent modulo 2, starting with page 1.

Now the following transformations are all relative to the lower left-hand corner of the page:

L means rotate the (portrait) page 90 degrees to the left.
@.7 means scale the page by 0.7
(1w,-0.5in) means shift to the right be 1 page width, shift down 0.5 inches.

The transformations always goes in that order: rotate, scale, then shift. 

The "+1L@.7(1w,0.5h)" creates the 2-up effect. 0.5h means shift up half the height of a (A4) page. If you wanted to add extra inner margin, you could change 0.5h to maybe 0.55h. Or convert 0.5h to Postscript points, inches or centimeters.

This command was lifted almost verbatim from the pstops man page.
I added the -0.5in to the yoffset to make a bit of an inner margin. 
I didn't add 0.5in to the yoffset of the second half-page merely because it didn't look right with the ps file I was working with. Your situation may be different.

---

### Post by shane2peru on 2009-05-05
> **unutbu said:**
> Sorry about my last suggestion -- I obviously didn't test what I wrote.
Not a problem, I have a test script that strictly makes a ps file and I can check it out before printing it and see how it looks.  I leave the viewer open and it auto-refreshes when it is overwritten. :D

> **unutbu said:**
> The following may work better, but you'll have to experiment a little with it to fit your situation:
```

pstops -d "2:0L@.7(1w,-0.5in)+1L@.7(1w,0.5h)" input.ps output.ps

```
This crazy looking command is sort of like "psnup -2", except that the "(xoffset,yoffset)" syntax gives you a lot of control over the placement of the pages. 

Let's try breaking apart "2:0L@.7(1w,-0.5in)":

"2:0" means print pages congruent modulo 2, starting with page 1.

Now the following transformations are all relative to the lower left-hand corner of the page:

L means rotate the (portrait) page 90 degrees to the left.
@.7 means scale the page by 0.7
(1w,-0.5in) means shift to the right be 1 page width, shift down 0.5 inches.

The transformations always goes in that order: rotate, scale, then shift. 

The "+1L@.7(1w,0.5h)" creates the 2-up effect. 0.5h means shift up half the height of a (A4) page. If you wanted to add extra inner margin, you could change 0.5h to maybe 0.55h. Or convert 0.5h to Postscript points, inches or centimeters.

This command was lifted almost verbatim from the pstops man page.
I added the -0.5in to the yoffset to make a bit of an inner margin. 
I didn't add 0.5in to the yoffset of the second half-page merely because it didn't look right with the ps file I was working with. Your situation may be different.

Yes, I read that page!  :)  Very informative, nothing like playing with the commands to see what they do.  My venture actually starts as a bunch of tiff files, then I convert them to a pdf.  So I add a padding in this process and modified my printing script to run very nicely with that. My final look is this:
[php]
psnup -l -pA4 -2 -m-.8in -d $book/$book-temp$s.ps > $book/book$s.ps #-m-.5in -b1in
	pstops "2:0(0in,-.355in)" $book/book$s.ps > $book/$book-odd$s.ps #good setting: (0in,-.355in)
	pstops "2:-1(0in,-.355in)" $book/book$s.ps > $book/$book-even$s.ps #good setting: (0in,-.355in)
[/php]

This seems to work like a champ!  We are using [[COLOR="Sienna"]Robinson Curriculum[/COLOR]]("http://www.robinsoncurriculum.com/") (home schooling curriculum for our kids, consequently I print a lot of books, and don't succumb to the need for Windows.)  I have honed the process down to a science, and it seems to be working very well.  Thanks for the help! 

Shane

---

### Post by Arndt on 2009-05-07
Since there have been people knowledgeable about the psnup tool family in this thread, I'll post my otherwise unrelated question here. I already asked the question in another of the forums, but there have been no answers there:

[http://ubuntuforums.org/showthread.php?t=1150602](http://ubuntuforums.org/showthread.php?t=1150602)

Thanks in advance

---

