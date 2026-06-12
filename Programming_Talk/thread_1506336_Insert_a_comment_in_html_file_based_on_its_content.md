---
title: "Insert a comment in html file based on its contents"
date: 2010-06-10
forum: Programming Talk
---

### Post by diaco on 2010-06-10
I have multiple HTML files in a folder. there is a <h2> tag like this: 
```
<h2>some text</h2>
```in each file. 
I want to write a shell script/batch file to add this tag in <head> section of each file: 
```
<!-- TITLE= "same text from h2 tag" -->
```there is a problem: <h2>some text</h2> in some files has 1 or more linebreaks and so I can't capture tag content using a simple grep or...
for example:
<h2>first part of text
second line of text</h2>

The line break shouldn't be shown in <!-- TITLE= "same text from h2 tag" -->. 
The script has to capture tag content & skip line breaks.
Can anybody help me?

---

### Post by DanielWaterworth on 2010-06-10
You can do it in python:
```

import re, sys

if len(sys.argv) != 2:
    print "usage: %s [filename]" % sys.argv[0]
    sys.exit(1)

filename = sys.argv[1]

f = open(filename, "r")
contents = f.read()
f.close()

m = re.search(r"<h2>([^<>]+)</h2>", contents)
if m:
    h2 = m.group(1)
    h2 = re.sub('\n', '', h2)
    contents = re.sub('<head>', '<head>\n<!-- TITLE=\"'+h2+'\" -->', contents)
    f = open(filename, "w")
    f.write(contents)
    f.close()

```It's not tested but it shouldn't need much done to it. If you need any help just post back here with your problems. Obviously backup everything before you use it on indispensable files.

---

### Post by diaco on 2010-06-10
Thank you but it didn't make any change to my html files (and i don't know how to correct python codes!).
Is there any other way? (I rather shell scripting because i can change & correct it & I undrestand the code)
Sorry but sometimes I really miss the power of visual studio.net :(

---

### Post by DanielWaterworth on 2010-06-10
It works for me, this is what I did:

I saved the code above as change.py and made a simple test file, (called file, it didn't contain much just a h2 tag with some text and an empty head below it). In the shell I then typed "python change.py file" and it made the change and saved it.

I prefer python to shell scripting because shell scripting gets very complicated very quickly. Python was originally designed to do work like this anyhow.

---

### Post by DanielWaterworth on 2010-06-10
I don't think it's making a change because it's case sensitive. Are there instances of anything but <h2>, like <H2> or instead of <head>, <HEAD> or even something like <head something=something>?

---

### Post by myrtle1908 on 2010-06-11
Best to use a HTML parser for this task.  However, this nasty Perl script should do what you require

```
use strict;
use warnings;

my $htmlfile = $ARGV[0] || 'h2.html';
my ($buf, $h2, $t, $c);

undef $/;
open IN, $htmlfile or die $!;
$buf = <IN>;
close IN;

if ($buf =~ m!<h2>(.*?)</h2>!gsi) {
  $t = $1;
  $t =~ s#\n# #g;
  $c = qq(<!-- TITLE= "$t" -->);
  $buf =~ s#<head(.*?)>#<head$1>$c#si;
  open OUT, ">$htmlfile" or die $!;
  print OUT $buf;
  close OUT;
  print "Updated $htmlfile\n";
} else {
  print "H2 not found in $htmlfile\n";
}
```

h2.html before
```

<hEaD some="thing" 
another="attrib">
</head>

<h2>Some
heading
and stuff
</h2>
```

h2.html after
```

<head some="thing" 
another="attrib"><!-- TITLE= "Some heading and stuff " -->
</head>

<h2>Some
heading
and stuff
</h2>
```

---

### Post by Milliways on 2010-06-11
> **diaco said:**
> Thank you but it didn't make any change to my html files (and i don't know how to correct python codes!).
Is there any other way? (I rather shell scripting because i can change & correct it & I undrestand the code)
Sorry but sometimes I really miss the power of visual studio.net :(

There are many ways.
I probably would have used sed with a regular expression to make the changes.

I am not sure if this would be easier, but after you debugged it you could include the sed command as 1 or 2 lines in the script.

Unfortunately the documentation for sed 'info sed' is a little intimidating.

---

### Post by diaco on 2010-06-12
> **myrtle1908 said:**
> Best to use a HTML parser for this task.

Is there any suitable HTML parser in linux? I couldn't find a anything more than sed.

---

### Post by diaco on 2010-06-14
Thank you! The problem is solved. This is the simplest solution (for me): 
[http://www.linuxquestions.org/questions/programming-9/insert-a-comment-in-html-file-based-on-its-contents-813325/#post3999066](http://www.linuxquestions.org/questions/programming-9/insert-a-comment-in-html-file-based-on-its-contents-813325/#post3999066)

---

