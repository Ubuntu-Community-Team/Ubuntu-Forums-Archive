---
title: "[SOLVED] Perl CGI Help"
date: 2007-10-10
forum: Programming Talk
---

### Post by Dylock on 2007-10-10
Alright got some questions with perl CGI

```
#!/usr/bin/perl --

use CGI qw/:standard/;

my $CGI=new CGI;

my $mode=param('mode');

print header,	start_html('Testing upload');
			
if($mode eq 'Submit')
{	
	my $file=$CGI->upload('file');
	my $line=readline($file);
	print "<center><b>";
	print $line;
	print "</b></center>";
	print "<br>";	
}

$action='testreadlineapp.pl';
print "<center>";
print "<table style=\"background-color:#ebebec; margin:0px; padding:0px;\">";
print "<tr><td style=\"margin-top:10px; border: 1px solid #aaaaaa; margin-bottom: 10px;\">";
print "<form method=post enctype=\"multipart/form-data\" action=\"$action\">";
print "<input type=\"file\" name=\"file\" value=\"\" size=\"50\" maxlength=\"50\">";
print "<input type=\"submit\" value=\"Submit\" name=\"mode\">";
print "</form>";
print "</td></tr>";
print "</table>";
print "</center>";
```

that is the script I'm using, my objective is to take a textfile and read in lines from it for parsing. But something strange seems to happen. It seems extra whitespace is dropped when it reads in the line.

Here is the line of the file I'm reading in
```
111111111111111111111   1111 #3333    N 9999904444444       1
```

Here is the result
```
111111111111111111111 1111 #3333 N 7046004444444 1
```

I need to maintain the whitespace in this file.

Any suggestions?

---

### Post by Dylock on 2007-10-10
I figured it out. 
HTML doesnt keep the space that are in a string when a print is issued. 
Bleh stupid mistake. Oh well.

---

