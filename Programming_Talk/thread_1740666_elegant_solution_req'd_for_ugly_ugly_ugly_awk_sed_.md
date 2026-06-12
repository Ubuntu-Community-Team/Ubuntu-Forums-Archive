---
title: "elegant solution req'd for ugly ugly ugly awk sed sed hack"
date: 2011-04-27
forum: Programming Talk
---

### Post by thaitang on 2011-04-27
I am using an ugly solution for a common task I have and I would love to find a more elegant solution without having to learn the nuts and bolts of awk. I am ok using sed and use it almost daily, but for some tasks I can not find a good solutions like this:
```
awk 'NF{$0=++a+371 " :" $0};{print}' 1.html>2.html
```this awk command numbers every line in file 1.html that is not blank and dumps the result into file 2.html.
then using sed:
```
sed -i '/^$/N;s/^\n\([1-9][0-9]\{0,4\}\) :\(.*\)$/<p><font size="-1"><a href="#l\1Top" name"l\1" style="text-decoration:none">\1<\/a><\/font><br>\n\2/g' 2.html
```this puppy merges any blank lines with the next line in the file (2.html) and then grabs the line number of the line that follows the blank line and inserts it onto the blank line and formats it with an (html) anchor tag and deletes the line number and colon inserted with the awk command.
using sed again:
```
sed -i 's/^[1-9][0-9]\{0,4\} ://g' 2.html
```and this little bad boy cleans up the mess of line numbers I created with awk now that all the line number anchors for the web page have been created.

I know I could join the two sed commands into a single command, and probably even pipe the sed or awk commands, but there really has to be a better way.

I know sed can count and insert line numbers with the '=' command, but I do not know of any way to insert a number for sed to use to start numbering lines with like I was able to do with the awk command (it numbers the first line in the file as number 372 and increments from there. I need this b/c I often split up large pages of hundreds of lines into multiple pages but want to maintain the line numbers and not start with line number 1 on each successive page.

I hope that makes sense. And I am absolutely sure awk and perl can do what I need; I would be happy as punch if sed could do what I needed, but I do not think it does. Unfortunately I do not have time to sit and work my way thru awk, to beccome somewhat proficient, so if anyone might be able to just whip me up a oneliner to take care of this that would rawk the house!

cheers,
tt

---

### Post by roccivic on 2011-04-27
Don't know perl or awk. But how about a PHP solution? Not a one-liner...

First:
```
sudo apt-get install php-cli
```

Then save this as "foo.php":
[PHP]<?php

// if true will insert a link ONCE where there are multiple consecutive newline
// if false, will insert links only where there is exactly one empty line.
$flag = true;

// initial line number
$ln = 372;

// file names
$infile  = "1.html";
$outfile = "2.html";

// read file
$in = explode("\n", file_get_contents($infile));

//output buffer
$out = array();

// process each line
for ($i=0; $i<count($in); $i++) {
	$line     = trim($in[$i]);
	$prevline = isset($in[$i-1]) ? trim($in[$i-1]) : 'undefined';
	$nextline = isset($in[$i+1]) ? trim($in[$i+1]) : 'undefined';

	if ($flag) {
		if ($in[$i] == '' && $nextline != '') {
			$out[] = "<p><font size='-1'><a href='#l{$ln}Top' name='l$ln' style='text-decoration:none'>$ln</a></font></p><br>{$in[$i]}";
		} else {
			$out[] = $in[$i];
		}
	} else {
		if ($in[$i] == '' && $nextline != '' && $prevline != '') {
			$out[] = "<p><font size='-1'><a href='#l{$ln}Top' name='l$ln' style='text-decoration:none'>$ln</a></font></p><br>{$in[$i]}";
		} else {
			$out[] = $in[$i];
		}
	}

	if (!empty($line)) {
		$ln++;
	}
}

// write output to file
file_put_contents($outfile, implode("\n", $out));

?>[/PHP]

and finally run it with:
```
cd /path/to/script
php foo.php
```

The output is slightly different from that of your scripts, but I think it's more accurate.

Hope this helps,
Rouslan

---

### Post by krazyd on 2011-04-27
This should get you started (I don't quite understand the output format you require):

```
awk 'BEGIN{i=371} {if($0!~/^$/) i++; print "<a href=\"#"i"\">"i"</a>",$0}' page1.html page2.html ...
```
Note that you can begin numbering at any value and accept any number of input files (output is concatenated). Also, the spaces inside the single quotes are purely for readability and can be removed without affecting the function.

Post back with your solution once you figure it out :)

---

### Post by Desidero on 2011-04-27
Is this what you're looking for?

Output of test file:
```

test@ubuntu:~/Desktop$ cat test_anchor 
Title 1
Subtitle 1
Subtitle 2
Subtitle 3

Title 2
Subtitle 1


Subtitle 2
Subtitle 3
Subtitle 4


Title 3


```Output of awk script:
```

test@ubuntu:~/Desktop$ awk 'BEGIN{i=370}NF{i++;print "<p><font  size=\"-1\"><a href=\"#l" i "Top\" name\"l" i "\"  style=\"text-decoration:none\">" i  "<\/a><\/font><br>"}' test_anchor 2>/dev/null
<p><font size="-1"><a href="#l371Top" name"l371"  style="text-decoration:none">371</a></font><br>
<p><font size="-1"><a href="#l372Top" name"l372"  style="text-decoration:none">372</a></font><br>
<p><font size="-1"><a href="#l373Top" name"l373"  style="text-decoration:none">373</a></font><br>
<p><font size="-1"><a href="#l374Top" name"l374"  style="text-decoration:none">374</a></font><br>
<p><font size="-1"><a href="#l375Top" name"l375"  style="text-decoration:none">375</a></font><br>
<p><font size="-1"><a href="#l376Top" name"l376"  style="text-decoration:none">376</a></font><br>
<p><font size="-1"><a href="#l377Top" name"l377"  style="text-decoration:none">377</a></font><br>
<p><font size="-1"><a href="#l378Top" name"l378"  style="text-decoration:none">378</a></font><br>
<p><font size="-1"><a href="#l379Top" name"l379"  style="text-decoration:none">379</a></font><br>
<p><font size="-1"><a href="#l380Top" name"l380"  style="text-decoration:none">380</a></font><br>

```Note: this is starting the line number count at 371 since you seemed to want to do that in yours for whatever reason.

*edit*
I didn't notice the \n\2 at the end of your sed statement... here's the new output:
```

test@ubuntu:~/Desktop$ awk 'BEGIN{i=370}NF{i++;print "<p><font size=\"-1\"><a href=\"#l" i "Top\" name\"l" i "\" style=\"text-decoration:none\">" i "<\/a><\/font><br>\n" $0}' test_anchor 2>/dev/null
<p><font size="-1"><a href="#l371Top" name"l371" style="text-decoration:none">371</a></font><br>
Title 1
<p><font size="-1"><a href="#l372Top" name"l372" style="text-decoration:none">372</a></font><br>
Subtitle 1
<p><font size="-1"><a href="#l373Top" name"l373" style="text-decoration:none">373</a></font><br>
Subtitle 2
<p><font size="-1"><a href="#l374Top" name"l374" style="text-decoration:none">374</a></font><br>
Subtitle 3
<p><font size="-1"><a href="#l375Top" name"l375" style="text-decoration:none">375</a></font><br>
Title 2
<p><font size="-1"><a href="#l376Top" name"l376" style="text-decoration:none">376</a></font><br>
Subtitle 1
<p><font size="-1"><a href="#l377Top" name"l377" style="text-decoration:none">377</a></font><br>
Subtitle 2
<p><font size="-1"><a href="#l378Top" name"l378" style="text-decoration:none">378</a></font><br>
Subtitle 3
<p><font size="-1"><a href="#l379Top" name"l379" style="text-decoration:none">379</a></font><br>
Subtitle 4
<p><font size="-1"><a href="#l380Top" name"l380" style="text-decoration:none">380</a></font><br>
Title 3
```

---

