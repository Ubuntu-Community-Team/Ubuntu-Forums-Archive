---
title: "Simple Program Needs Help"
date: 2009-04-29
forum: Programming Talk
---

### Post by akxiii on 2009-04-29
I've done a little bit of programming, but not in Ubuntu before. I'm new to Ubuntu and wasn't sure what program to use. Any pertinent suggestions would be great, and if anyone wants to build this very simple program for me you would have my undying gratitude. [-o<

I'll explain what I am trying to do and then how I planned on doing it. I have a large image that I am going to slice apart. I intend to use the code to output html code for a grid of images that are 2wide and 3tall (referred to as a page from now on). I would like each page to be referred to by its top left image, and each image in a column-row type format. I also have two control buttons at the bottom that would move the grid up or down. The example below starts on column 01, and row 02 to help illustrate how the up and down buttons would link and reposition the page.

Example of one "page" of output data:
```
name	01-02
01-02,02-02
01-03,02-03
01-04,02-04
up 	01-01
down 	01-03

```

Example of one "page" in HTML code:
[PHP]<a name="01-02"></a>
<img class="block" src="images/01-02.jpeg">
<img class="block" src="images/02-02.jpeg">
<img class="block" src="images/01-03.jpeg">
<img class="block" src="images/02-03.jpeg">
<img class="block" src="images/01-04.jpeg">
<img class="block" src="images/02-04.jpeg">
<a href="#01-01"><img class="control" src="images/up.jpeg"></a>
<a href="#01-03"><img class="control" src="images/down.jpeg"></a>[/PHP]

I was thinking the code could ask the user how many columns and how many rows, then as it runs in a loop outputs the data with repetitive html code wrapped around it. (I put in two digit fields because I can't imagine ever having more than 99 sliced columns or rows).

When writing this code I would like it if the up and down buttons had no link if they are at the coordinates given by the user. For example at x-1 the "up" button would be left empty. I think this could be accomplished with an if/else clause to see if it meets the top value, or the user submitted values x-yFinal.

If anyone takes this upon themselves, I would appreciate it if the code could be output such that a full row would be written before a full column would be written (I think this can be accomplished by running the if loop for the row first).

The separator between the columns and rows can be anything, I just picked a dash for this example. If it messes with the code please let me know, or change it.

Thank you in advance for any help!
AK

***************************************************************
For the future...
I was thinking about adding some kind of "zoom" functionality to each image. I was thinking about accomplishing this by breaking each image apart into it's own set of 6 images, and creating a link on each image that could correspond to the set below it. Perhaps I am being a bit naive, but it seems like adding another level to the coding say zoomLevel-column-row could make this possible. I'd love any insight!

---

### Post by MeLight on 2009-04-30
What language are we talking about? 
Do you have problem with the logics only, or you have "technical" difficulties also? 
Can we see something you've tried already?

---

### Post by akxiii on 2009-04-30
[SIZE="3"]Perhaps I wasn't clear, I didn't know what program to use in Ubuntu to program this code (or compile it? basically get it done and usable). I was hoping for advice that would make this easier. I haven't done any of the coding yet but I can picture what it should look like in my head.

I don't think the code is particularly difficult, I think it is just a couple of loops. I am certain that I don't have the formatting correct, but here is what core of the code should convey

Thank you for any and all help,
AK[/SIZE]

*Note: I used curly brackets to enclose text that printed, I don't know what the standard is, but doing this made enclosing the code in php brackets go all wonky. So I've enclosed them in code brackets.*

```
//Call out variables
numbers: col, row, rcount, ccount, ctemp, up, dwn
ccount=01
rcount=01

//Ask for number of columns
print: {Enter the number of columns (greater than 2) as two digits?}
input: col

//Ask for number of rows
print: {Enter the number of rows (greater than 3) as two digits?}
input: row


//Row Loop
for rcount = 01 to (row-2)

	//Column Loop, I want all of the columns done before it goes to the next row
	for ccount = 01 to (col-1)
		print: {<a name="} ccount {-} rcount {"></a>}
		print: {<img class="block" src="images/} ccount {-} rcount {.jpeg">}
		print: {<img class="block" src="images/} ccount+1 {-} rcount {.jpeg">}
		print: {<img class="block" src="images/} ccount {-} rcount+1 {.jpeg">}
		print: {<img class="block" src="images/} ccount+1 {-} rcount+1 {.jpeg">}
		print: {<img class="block" src="images/} ccount {-} rcount+2 {.jpeg">}
		print: {<img class="block" src="images/} ccount+1 {-} rcount+2 {.jpeg">}
		
		if rcount = 01
			//up button link dies if we are on the top row
			dwn = rcount+1
			print {<img class="control" src="images/up.jpeg">}
			print {<a href="#} ccount {-} dwn+1 {"><img class="control" src="images/down.jpeg"></a>}
		else if rcount = row-2
			//dwn button link dies if we are on the bottom row
			up = rcount-1
			print {<a href="#} ccount {-} up-1 {"><img class="control" src="images/up.jpeg"></a>}
			print {<img class="control" src="images/down.jpeg">}
		else
			//both buttons are alive
			up = rcount+1
			dwn = rcount-1
			print {<a href="#} ccount {-} up {"><img class="control" src="images/up.jpeg"></a>}
			print {<a href="#} ccount {-} dwn {"><img class="control" src="images/down.jpeg"></a>}
```

---

### Post by MeLight on 2009-04-30
If I got you right,
shouldn't you break up the big picture to smaller parts prior to showing it? If so you can name them accordingly, put the names in to a 2d array and afterwards you can show any part of the big image (who's smallest piece is a single cell of the array) by two for loops one inside the other when they actually start to count from the upper left corner cell of the part you're showing.

If you already have the naming right and you know the order of the images you should only do the 2d array part. That'd be my tactics anyways.

---

### Post by akxiii on 2009-04-30
> **MeLight said:**
> If I got you right,
shouldn't you break up the big picture to smaller parts prior to showing it? If so you can name them accordingly, put the names in to a 2d array and afterwards you can show any part of the big image (who's smallest piece is a single cell of the array) by two for loops one inside the other when they actually start to count from the upper left corner cell of the part you're showing.

If you already have the naming right and you know the order of the images you should only do the 2d array part. That'd be my tactics anyways.

I'm not sure I get what you are saying, or perhaps you don't get what I'm saying :)

I have a few sets of large images. I plan on using photoshop's slice tool to break them apart into grids of images so I can name them anything, I thought the easiest naming convention would be their location in an xy coordinate type way (so yes, the picture is already going to be broken apart, I just want to display a 2x3 "page" of it at a time). What is going to change between the base images is the scale, some will be 8x9 or 4x11 or 7x25, whatever.

Did that help to clarify? I thought naming the pictures would be the easy part, and with a piece of code like above I thought I could generate the html so that a webpage could display it easily.

---

### Post by MeLight on 2009-04-30
Ok, so as far as the code "cares" you have the images already. I think naming according to index (opposed to xy coords) is a cleaner solution, but that's up to you.

Lets assume your naming convention is xindex_yindex.jpg. What you need is a 2D array that holds all the images names in the correct order, ie if you have a 2x3 image, the array would look like this:

[0][0] "0_0.jpg" [0][1] "0_1.jpg"
[1][0] "1_0.jpg" [1][1] "1_1.jpg"
[2][0] "2_0.jpg" [2][1] "2_1.jpg"

*Note: if you look at the array as matrix you'll see that it is transformed (the coords of x and y are switched), and thus you must switch places in the loop for x and y.*

Now, if you want to display the part starting from 0_1.jpg and who's size is 2x2 cells you'll do this:

```

xStart = 0;
yStart = 1;
for(y = yStart; y < 2; y++) {//note that y is the outer loop
    for(x = xStart; x < 2; x++) {
        printLineForOnePic(imagesArray[x][y]);
    }
    breakLineHere();//Start a new row, as you jump to the next y
}

```

Let me know if that's what you meant

---

### Post by akxiii on 2009-04-30
> **MeLight said:**
> I think naming according to index (opposed to xy coords) is a cleaner solution, but that's up to you.
I'm not sure what you mean by "index"


> **MeLight said:**
> What you need is a 2D array that holds all the images names in the correct order
I also don't understand why I need an array, I just need the program to shoot out the the order of images in each "page," and then print out html code around it. I plan on taking the html code and dropping it into a word file and having it run a very simple webpage.
So I don't need the code to actually display pictures, I just need it to spit out html. I thought using a program would be the quickest way to repeat this process, as it is a little too complicated for excel.

When I chop up the large image I plan on labeling each of the image-blocks by their corresponding column and row.

I am looking for advice on which program and language to write this in, on Ubuntu. If you could explain what doesn't work with my concept of loops I'd appreciate it.

---

### Post by MeLight on 2009-04-30
By index I meant row and column, where x is column and y is row.

You need an array in order to easily manipulate the file names. If you know **exactly** how each of your files is going to be named - 01_21.jpg would be completely different from 1_21.jpg, - you can manage somehow without arrays, otherwise use arrays. php arrays can solve this problem easily.

Your loops concept is same as mine, only you're using 6 lines of code to cover all the row/col options which is bad - you can misspell something, or just might need to scale up the program, so you'll have to add even more lines.

here's the code I came up with:
[PHP]
<?php
$dh = opendir(".");

$xStart = 0;
$yStart = 1;
$xSize = 2;
$ySize = 2;

$pics = array();

//This part arranges everything in the array
while(($file = readdir($dh)) !== FALSE) {		//we check all the files in the folder, and write down only the ones we need
	if($file == "." || $file == "..") continue;
	
	//get the extension
	$break = explode(".", $file);
	$ext = $break[count($break) - 1];
	if($ext != "jpg" && $ext != "jpeg") continue;
	
	//if extension is ok we'll get here
	$break = explode("_", substr($file, 0, strlen($file) - (strlen($ext) + 1)));
	$pics[(int)$break[0]][(int)$break[1]] = $file;		//putting the file name in the right index
}

//This part will spit out the HTML
for($i = $yStart; $i < $yStart + $ySize; $i++) {
	for($j = $xStart; $j < $xStart + $xSize; $j++) {
		echo $pics[$j][$i]." ";		//put your html here
	}
	echo "\n";
}
?>
[/PHP]

---

### Post by akxiii on 2009-04-30
1. I don't quite understand what xSize represents, is that the total number of columns? 

2. Just to clarify, with this code I should still name the files based on their xColumn_yRow? or are you saying  that I can just name them in 1 through whatever, and because the code knows how many rows and cols there are, and can thus break them apart appropriately?

3. So all of the code above "//This part will spit out the HTML" is for checking that I have named the files correctly?

4. What program do I use to run this code? Ubuntu preferably, but I have windows as well.

5. Can you give me an example of how to incorporate (echo?) the the HTML code to have it print text onto the screen?

---

### Post by MeLight on 2009-04-30
xSize and ySize are the number of corresponding cells you want to print. If you have a 32x44 parts image, and you want to show a 3x4 part which starts at 16_18 you'll set xStart to 16, yStart to 18, xSize to 3, and ySize to 4.

Yes you should still name it as xCol_yRow.jpg

All the code above the "HTML spitting code" is for going through the folder of images (the script should be inside that folder) and putting all relevant files (*.jpeg or *.jpg) in to the array, indexing the array by the xCol_yRow convention so it can later be used when printing out the relevant parts.

This script is PHP, thus you're going to need PHP installed on your Ubuntu machine (can be installed on Windows also) to run it.

To spit out html and the files name:

[PHP]echo "<image src=\"".$pics[$j][$i]."\">";[/PHP]

---

### Post by akxiii on 2009-04-30
> **MeLight said:**
> xSize and ySize are the number of corresponding cells you want to print. If you have a 32x44 parts image, and you want to show a 3x4 part which starts at 16_18 you'll set xStart to 16, yStart to 18, xSize to 3, and ySize to 4.


I think we hit another miscommunication. I always want it to start of 0_0.jpg, but the html needs to be spit out in 2 column by 3 row chunks. So the overall image may be 3c by 3r, in which case there would be two "pages" of HTML. One 2x3 page starting at 0_0 and one starting at 1_0.

Similarly there could an overall image that is 2c by 4r, in which case there would still only be two "pages" of html. One starting at 0_0 and one at 0_1.

I hope this helps with things

---

### Post by MeLight on 2009-04-30
Ok, that's why I proposed a general case solution. 

Two options:
A. You add a piece of code which will count the pages/num of images already printed, **inside** the loops. When the right number is printed (you can check this using the modulo '%' operator) you should print end of page or something similar. I that case you don't need to change the start x and y.

B. You can wrap both loops with another loop which will go through **pages**, and update the xStart and yStart accordingly on each page (on each page you'd want to start from a different y i assume)

---

### Post by akxiii on 2009-04-30
To make things a little less complicated, lets assume that we don't need the array because I'm really great at entering in names for pictures. Would the following code work?
Any advice on PHP programs for Ubuntu or windows that you like?

I haven't programmed with PHP before so bear with me if I make dumb mistakes:

I wasn't sure if the following characters needed a forward slash before them to appear as text: #, <, >, /

Also, am I allowed to do math on the variables like I did, without altering what the variable equals? 
Like I want [$ccount+1] to register as 2 (if we assume $ccount=1, but I don't want to reassign $ccount to equal 2 at the end of the operation.

Gravy?

[PHP]
<?PHP
//User enters data for total number of rows
$row=;
$col=;

$rowLimit=$row-2;
$colLimit=$col-1;

// Row Loop
for($rcount = 1; $rcount==$rowLimit; $rcount++) {
	
	// Column Loop
	for($ccount = 1; $ccount==$colLimit; $ccount++) {
		echo "<a name=\"".[$ccount]."_".[$rcount]."\"></a>";
		echo "<img class=\"block\" src=\"".[$ccount]."_".[$rcount].".jpeg\">";
		echo "<img class=\"block\" src=\"".[$ccount+1]."_".[$rcount].".jpeg\">";
		echo "<img class=\"block\" src=\"".[$ccount]."_".[$rcount+1].".jpeg\">";
		echo "<img class=\"block\" src=\"".[$ccount+1]."_".[$rcount+1].".jpeg\">";
		echo "<img class=\"block\" src=\"".[$ccount]."_".[$rcount+2].".jpeg\">";
		echo "<img class=\"block\" src=\"".[$ccount+1]."_".[$rcount+2].".jpeg\">";
		if ($rcount == 1){
			//up button link dies if we are on the top row
			$dwn = $rcount + 1;
			echo "<img class=\"control\" src=\"images/up.jpeg\">";
			echo "<a href=\"\#" .$ccount. "_" .$dwn. "\"><img class=\"control\" src=\"images/down.jpeg\">";
		} elseif ($rcount == $rowlimit)
			//dwn button link dies if we are on the bottom row
			$up = $rcount - 1;
			echo "<a href=\"\#" .$ccount. "_" .$up. "\"><img class=\"control\" src=\"images/up.jpeg\">";
			echo "<img class=\"control\" src=\"images/down.jpeg\">";
		} else {
			$up = $rcount - 1;
			$dwn = $rcount + 1;
			echo "<a href=\"\#" .$ccount. "_" .$dwn. "\"><img class=\"control\" src=\"images/down.jpeg\">";
			echo "<a href=\"\#" .$ccount. "_" .$up. "\"><img class=\"control\" src=\"images/up.jpeg\">";
		}
	}
	echo "\n";		//I wasn't sure what this did, but you had it in yours
}

?>[/PHP]

---

### Post by MeLight on 2009-05-01
Even if it doesn't work as expected it will give you a good starting point, from which you can see what needs to be fixed. Oh, and you don't need to escape # with a slash.

[PHP]echo "\n"; //this will print and end-of-line char[/PHP]

So, the next thing you should do is install php (and php-cli if you're on Linux), give your program a shot and let us know how it goes :D

---

