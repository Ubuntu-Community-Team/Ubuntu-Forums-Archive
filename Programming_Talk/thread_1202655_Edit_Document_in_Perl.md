---
title: "Edit Document in Perl"
date: 2009-07-02
forum: Programming Talk
---

### Post by Holmes89 on 2009-07-02
I'm kind of new to perl and I need help with a program. I want to change a &nbsp; section on my HTML document to be replaced with one line of code (specifically an image line). I was reading about s/wordtoreplace/replacingword but I'm having problems with it. How do I get this to work? I need replacing word to really be $replacing word. Thanks for the help.

---

### Post by Holmes89 on 2009-07-02
This is what I have
```
#!/usr/bin/perl -w
$picbegin= '<img src="assets/';
$picend= '" width="230" height="175" align="center">';
opendir(DIR, './incoming/thumbnails/');
@files = grep(/\.jpg$/,readdir(DIR));
closedir(DIR);
open(HTML, "<html/test.html");
foreach $file (@files) {
print "$file \n";
$full="$picbegin$file$picend";
s/&nbsp;/$full/g;
print HTML
}
close(HTML);

```

---

### Post by unutbu on 2009-07-02
```
open(HTML, "<html/test.html");
```

It looks like you are opening test.html in read-only mode.

If you want to edit the file, you'll need to open two filehandles:
```

open(HTML, "<html/test.html");
open(HTMLNEW, ">html/testnew.html");
```

Then process each line of HTML:
```

while (<HTML>) {
    ...
    s/&nbsp;/$full/g;
    print HTMLNEW;
    ...
}
close(HTML);
close(HTMLNEW);
```

Then overwrite test.html with testnew.html:
```

rename("html/testnew.html","html/test.html");

```

---

### Post by Holmes89 on 2009-07-06
Is there only a way to replace it only once?

---

### Post by unutbu on 2009-07-06
Can you elaborate on what you are trying to do? I don't really understand the question.

---

### Post by Holmes89 on 2009-07-06
Sorry, I mean that I want to replace only one instance of &nbsp; so that the next file will go in its place. So say I have a table where I have a bunch of cells and I want a different picture in each one. I want to replace one &nbsp; with one file name and so on. Thanks for the help.

---

### Post by unutbu on 2009-07-06
Could you post test.html?

---

### Post by Holmes89 on 2009-07-06
Here is the section where I want the pictures
```
<table width="920" border="0" align="left" cellpadding="0"
cellspacing="0" bgcolor=#FFFFFF>
  <tr><td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center"></td>
 </tr>
 <tr><td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center">&nbsp;</td>
 </tr>
  <tr><td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center">&nbsp;</td>
  <td width="230" height="175" align="center">&nbsp;</td>
 </tr>
</table>

```

I was thinking about using comments <!-- but I can't seem to get it to work either. was trying to name then <!--1-->, <!--2--> and so on but it doesn't seem to work with my counter. Here is the code that I have for that.
```
#!/usr/bin/perl -w
$count=0;
$picbegin= '<img src="assets/';
$picend= '" width="230" height="175" align="center">';
opendir(DIR, './incoming/thumbnails/');
@files = grep(/\.jpg$/,readdir(DIR));
closedir(DIR);
open(HTML, "<html/test.html");
open(HTMLNEW, ">html/testnew.html");

while(<HTML>){
foreach $file (@files) {

$full="$picbegin$file$picend";
$replace='<!--'.$count.'-->';
s/$replace/$full/g;

$count++;
}

print HTMLNEW;
}
close(HTML);
close(HTMLNEW);
rename("html/testnew.html", "html/test.html");

```

---

### Post by unutbu on 2009-07-06
Maybe this will do?
[PHP]#!/usr/bin/perl 
$count=0;
$picbegin= '<img src="assets/';
$picend= '" width="230" height="175" align="center">';
opendir(DIR, './incoming/thumbnails/');
@files = grep(/\.jpg$/i,readdir(DIR));
closedir(DIR);

open(HTML, "<html/test.html");
open(HTMLNEW, ">html/testnew.html");

while(<HTML>){
    if (/&nbsp;/) {
	s/&nbsp;/$files[$count]/;
	$count++;
    }
    print HTMLNEW;   
}
close(HTML);
close(HTMLNEW);
rename("html/testnew.html", "html/test.html"); 
[/PHP]
This piece of code was the problem: 

```

while(<HTML>){
foreach $file (@files) {
```

It tells perl to loop through each of the files in @files for each line of test.html. 

The code above replaces the foreach loop with an if-clause.
Essentially the if-clause says, "If a line of the html file contains '&nbsp;', then replace '&nbsp;' with a filename from @files." Each time such a replacement occurs, $count is increased by one, so the next time '&nbsp;' is found, a different filename gets inserted.

Hope this helps.

---

### Post by Holmes89 on 2009-07-06
Thanks! It works (with a little tweaking) this is the final code:

```
#!/usr/bin/perl -w
$count=0;
$picbegin= '<img src="assets/';
$picend= '" width="230" height="175" align="center">';
opendir(DIR, './incoming/thumbnails/');
@files = grep(/\.jpg$/,readdir(DIR));
closedir(DIR);
[COLOR="Red"]$arraysize=$#files+1;[/COLOR]
open(HTML, "<html/test.html");
open(HTMLNEW, ">html/testnew.html");

while(<HTML>){
    [COLOR="Red"]$file=@files[$count];
    $full="$picbegin$file$picend";[/COLOR]
    if ((/&nbsp;/)&&[COLOR="Red"]($count<$arraysize)[/COLOR]){
    s/&nbsp;/$full/;
    $count++;
    }
    print HTMLNEW;
}


close(HTML);
close(HTMLNEW);
rename("html/testnew.html", "html/test.html");

```

All I changed was the file names which I needed to have the html tags to make it work, then I also added a condition to the if statement which will stop writing when it is out of files by measuring the size of the array. I'm new to perl but your help has really been teaching me. Thanks a bunch.

---

