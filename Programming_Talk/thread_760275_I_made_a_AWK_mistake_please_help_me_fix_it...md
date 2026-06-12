---
title: "I made a AWK mistake please help me fix it.."
date: 2008-04-20
forum: Programming Talk
---

### Post by hopelessone on 2008-04-20
Hi,

I'm a limited self taught person  trying to recreate an old forum and am creating menus for the posts...along the way i had used the LAST USERNAME instead of the FIRST USERNAME...

i have [file A] the menu file which has:

```
<TR>
<TD bgcolor="#F7F7F7">
<IMG SRC="../images/closed.gif" BORDER=0></td>
<TD bgcolor="#F7F7F7"><FONT SIZE="2" FACE="Verdana, Arial">
<A HREF="../Forum6/HTML[COLOR="Red"]/003211.html[/COLOR]">lost worlds </A>
</FONT>
</td>
<td bgcolor="#DEDFDF">
<FONT SIZE="2" FACE="Verdana, Arial">[COLOR="Red"]SlyDog[/COLOR]</font><BR><FONT</FONT>
</td>
<td align=center bgcolor="#F7F7F7">
<FONT SIZE="2" FACE="Verdana, Arial">15</FONT>
</td>
<td NOWRAP bgcolor="#DEDFDF">
<FONT SIZE="2" FACE="Verdana, Arial">04-26-2000 <FONT SIZE="2" FACE="Verdana, Arial" COLOR="#800080">07:22 PM</FONT></FONT>
</td></tr>
```

[COLOR="Red"]SlyDog[/COLOR] is the mistake i made as i would like the FIRST USERNAME...doh!!

[file B] the /003211.htm has the line:

```
<FONT SIZE="2" face="Verdana, Arial"><B>Worlord</B></font><BR><FONT SIZE="1" face="Verdana, Arial">Member</FONT>
</td>
``` there are sometimes many of these but would like just the first occurence of this USERNAME Worlord and insert it in [file A] where SlyDog is..

there's 1300 files to go through [COLOR="Red"]/003211.html[/COLOR]

how can i replace the USERNAMES where file name = 
003211.htm or whatever file it may be?

thanks a lot for reading this...

:)

---

### Post by girishv on 2008-04-20
A very poor and user unfriendly hack to accomplish this :)

---------------------------------------------------------------------------------------
 #!/usr/bin/perl -w

my (@files) = `ls -1 *.html`;
chomp(@files);


foreach $file (@files) {
       print "Working on $file\n";
        open (IN, $file);
        my($i) = 0;
        my ($seen);
        my (@lines);
        while (<IN>) {
                if ($_ =~ SlyDog and $seen != 1) {  # check for the word and only first one
                    $_ =~ s/SlyDog/Worlord/;              # substitute
                    $seen = 1;                                        # now we have seen it
                }
                ($lines[$i++]) = $_; # for writing later
        }
        close(IN);
        print "Finished reading $file\n";

        open (OUT, ">$file") or die "Sorry can not open $file for writing\n";
        print OUT @lines, "\n";
        close(OUT);
}
-----------------------------------------------------------------------------------
Dont forget to try on some sample files and/or take a backup before hand.

Girish

EDIT: Corrected few typos

---

### Post by ghostdog74 on 2008-04-20
if Slydog is constant
```

awk 'FNR==NR && /Member/{
 gsub(/.*<B>|<\/B>.*/,"")
 name=$0
 next
}
/[sS]ly[dD]og/{
  gsub(/[sS]ly[dD]og/,name) 
}1' "fileB" "fileA"

```

---

### Post by ghostdog74 on 2008-04-20
> **girishv said:**
> A very poor and user unfriendly hack to accomplish this :)

---------------------------------------------------------------------------------------
 #!/usr/bin/perl -w

my (@files) = `ls -1 *.html`;
chomp(@files);


use glob, or while ( <*.html> )  {} .

---

### Post by hopelessone on 2008-04-20
thanks...

Slydog is not a constant ...but i know where it would be:

<FONT SIZE="2" FACE="Verdana, Arial">SlyDog</font><BR><FONT</FONT>

would this work?

/<FONT SIZE="2" FACE="Verdana, Arial">*</font><BR><FONT</FONT>/{
user=$4


cheers!!

---

### Post by ghostdog74 on 2008-04-20
> **hopelessone said:**
> thanks...

Slydog is not a constant ...but i know where it would be:

<FONT SIZE="2" FACE="Verdana, Arial">SlyDog</font><BR><FONT</FONT>

would this work?

/<FONT SIZE="2" FACE="Verdana, Arial">*</font><BR><FONT</FONT>/{
user=$4


cheers!!
```

awk 'FNR==NR && /Member/{
 gsub(/.*<B>|<\/B>.*/,"")
 name=$0
 next
}
/<\/font><BR><FONT<\/FONT>/{
  old = $0
  gsub("<[^>]*>", "")
  user=$0
  gsub(user,name,old) 
  print old
  next
}1' "fileB" "fileA"

```

---

### Post by hopelessone on 2008-04-22
can't seem to get things going...have included sample files...

thanks GD74...:KS

I really really do appreciate it!!!

---

### Post by hopelessone on 2008-04-24
where abouts do i change the code to find the USERNAME...as the above code combines the two files together...

thanks

---

### Post by ghostdog74 on 2008-04-24
show what you expect to see, what errors you have if any, provide sample input file, and the code you used.

---

### Post by hopelessone on 2008-04-25
> **ghostdog74 said:**
> show what you expect to see, what errors you have if any, provide sample input file, and the code you used.

OK..have attached files of what the file [menu] should look like...and a copy of the script i am using...the other files are attached to the other post above...Cheers and..

thanks a mill..

---

### Post by ghostdog74 on 2008-04-25
try this
```

awk 'FNR==NR && /Member/{
 gsub(/.*<B>|<\/B><\/font><BR>.*/,"")
 namesfound[++c]=$0
 next
}
/<\/font><BR><FONT<\/FONT>/{  
  old = $0
  gsub("<[^>]*>", "")
  user=$0
  gsub(user,namesfound[++d],old)
  print old
  next
}1' "003245.html" "menu"

```

---

### Post by hopelessone on 2008-04-29
how can i do all the files in the directory instead of "003245.html" ? i tried double quotes i.e. ""*.html"" to no avail...

if i change the scrip file to "003247.html", "003246.html", "003245.html" i get mixed results...

thanks..

---

### Post by ghostdog74 on 2008-04-29
> **hopelessone said:**
> how can i do all the files in the directory instead of "003245.html" ? i tried double quotes i.e. ""*.html"" to no avail...

you can use a for loop to go over the html files
```

for files in *html
do
  # awk ..... $files "menu"
done

```

> 
if i change the scrip file to "003247.html", "003246.html", "003245.html" i get mixed results...

thanks..
if you get mixed results, that means your data structure are not the same. you should review what are the "common" patterns in those files and fine tune your script

---

### Post by hopelessone on 2008-04-29
Ahh OK thanks for loop tip...i see..

having a problem though with 003246.html can't change it...is there a way to not have the .html files combined with the menu files?

have attached a copy of what happens...

thanks

---

### Post by ghostdog74 on 2008-04-29
> **hopelessone said:**
> is there a way to not have the .html files combined with the menu files?

don't understand.

---

### Post by hopelessone on 2008-04-29
sorry i  mustn't have been clear...

i would like the output menu_would_like.txt but get onefile.txt.zip 

have a peek at onefile.txt.zip file then menu_would_like.txt file..

thanks

---

