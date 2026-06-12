---
title: "XML::Simple doesn't use utf8?"
date: 2008-02-09
forum: Programming Talk
---

### Post by chemical on 2008-02-09
Hi all,
I'm trying to create an xml with a perl script using XML::Simple.

There are some titles in that I want to put into the xml that are in Japanese, but looks like that when I use XMLout() to write my data to the file some information gets lost/corrupted and opening the resulting xml the titles in japanese are completely garbled.

I later noticed that this doesn't happen only with foreign chars but also with special ones, like the little TM or mainly anything that isn't plain ascii.

I tried to use 'use utf8;' on top of the script or adding a xml declaration to the file saying to use utf8 encoding, but without luck...

I tried to output my Japanese titles to a plain text file and everything works fine, so it seems it's a XMLout() issue.
Everything should be working fine, but just isn't... any help will be appreciated!

Thanks!

---

### Post by Shin_Gouki2501 on 2008-02-09
set encoding?!
dunno in perl how to set that...
googel say:
[http://uucode.com/xml/perl/index.html](http://uucode.com/xml/perl/index.html)
?!

---

### Post by chemical on 2008-02-10
The fact is that I shouldn't set the encoding at all, Ubuntu uses UTF-8 as default and so does XML::Simple...

I used a 'file' command on the resulting xml file and looks like it is in utf8 encoding after all... but the chars don't get displayed well...

---

### Post by popch on 2008-02-10
Where do the texts (titles) come from which your script writes into the xml document? 

How are those sources encoded, and how does your script know how they are encoded?

---

### Post by Shin_Gouki2501 on 2008-02-10
"default" setting.. if u create "text" files u HAVE to set encoding (imo)

---

### Post by chemical on 2008-02-11
> **popch said:**
> Where do the texts (titles) come from which your script writes into the xml document? 

How are those sources encoded, and how does your script know how they are encoded?

The text comes from a binary file and is converted into a string that I can visualize correctly and print to every file I like a part from the xml in question.

> "default" setting.. if u create "text" files u HAVE to set encoding (imo)

I never set the encoding before, they always defaulted to utf8 (that is default system encoding). 
Moreover the only way to set an encoding with XML::Simple is to include 'encoding=utf8' in the xml description, but that 1. doesn't work, 2. to do it you simply have to pass a string to XMLout() that just paste it on top of your xml file.

---

### Post by siouzi on 2008-02-13
> **chemical said:**
> The text comes from a binary file and is converted into a string that I can visualize correctly and print to every file I like a part from the xml in question.

AFAIK XML::Simple doesn't care what encoding the internal perl strings are and does not handle any character encoding. So I suspect the problem is converting the text from the binary file. Example EUC-JP data to UTF-8 XML:

```

#!/usr/bin/perl -w
use strict;
use Encode;
use XML::Simple;

# the data structure to be converted into XML
my $data =&#65371; text => undef };

# read the text data
my $eucjp_string = read_data_from_somewhere();

# decode from the original charset
$data = decode( 'euc-jp', $eucjp_string );

# convert to xml
my $xml = XMLout( $data );

# write xml to utf8 file
open my $fh, '>:utf8', 'out.xml' or die $!;
print $fh $xml;
close $fh;

```

---

