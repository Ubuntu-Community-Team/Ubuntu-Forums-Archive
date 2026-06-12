---
title: "perl oneliner to extract first letters of regex search"
date: 2011-09-23
forum: Programming Talk
---

### Post by thaitang on 2011-09-23
can someone help me with a perl oneliner to parse regex search patterns by allowing me to extract/isolate the first letter of each word in the search pattern matched and then joining all of the first letters of each word together into a single string.

for example, in sed I might use something like:
```
sed -ri 's/<p><\/p><center><b>([A-Za-z])([A-Za-z@:,]{0,20})[ ]{0,1}([A-Za-z]{0,1})[ ]{0,1}([A-Za-z@:,]{0,20})[ ]{0,1}([A-Za-z]{0,1})[ ]{0,1}([A-Za-z@:,]{0,20})[ ]{0,1}([A-Za-z]{0,1})(.*)<\/b><\/center>/<p><font size="-1"><a href="#\1\3\5\7Toc" name="\1\3\5\7Txt" style="text-decoration:none">\1 \2 \3 \4 \5 \6 \7 \8<\/a><\/font><br>/' 1.html
```which I realize needs some nurturing to work as I want, but really I want to start mopving toward doing this kind of stuff using perl. So the before might look like:
[HTML] <p></p><center><b>Part I: Introduction to <i>Beyond Good and Evil</i></b></center>[/HTML]and the desired after like:
[HTML]<p><a href="#PIItBGaEToc" name="PIItBGaETxt" style="text-decoration:none">Part I: Introduction to <i>Beyond Good and Evil</a></font><br>[/HTML]I know the html could use some tweaking as well, but one thing at a time. :) If anyone can help with a perl oneliner example of how to do the above I would really appreciate it.

cheers, tt

---

### Post by dethorpe on 2011-09-26
If your going to be parsing and manipulation HTML like this i'd recomend using an HTML parsing module from CPAN rather than trying to do it using regexs.
 
e.g. [http://search.cpan.org/~gaas/HTML-Parser/](http://search.cpan.org/~gaas/HTML-Parser/)[]("http://search.cpan.org/~gaas/HTML-Parser/") or [http://search.cpan.org/dist/HTML-Parser/lib/HTML/PullParser.pm](http://search.cpan.org/dist/HTML-Parser/lib/HTML/PullParser.pm) depending on how you want to do it.

---

### Post by myrtle1908 on 2011-09-26
Does it have to be a one liner?  I would first strip the HTML then use a regex with word boundary

```
use strict;
use warnings;

my $s = '<p></p><center><b>Part I: Introduction to <i>Beyond Good and Evil</i></b></center>';
$s =~ s/<.*?>//g;
my @m = ($s =~ m/\b(\w)/g);
print "@m";
```

Yields

```
P I I t B G a E
```

---

### Post by stylishpants on 2011-09-26
Here is one way to do it.

Since you're interested in learning how to build one-liners, I'm showing all the steps I did to construct this.  
You don't need to run the earlier steps, the last one does everything.

```
# File of test data:
bob@cob:/tmp$ cat file.html 
 <p></p><center><b>Part I: Introduction to <i>Beyond Good and Evil</i></b></center>
 <p></p><center><b>Part II: The <i>Wrath</i> of <i>Khan</i></b></center>
 <p></p><center><b>Part III: Return Of The <i>Jedi</i> </b></center>

# Extract title from surrounding text.
# Take everything between the <b> tags, but not the tags themselves.
bob@cob:/tmp$ cat file.html | perl -nle '/<b>(.*)<\/b>/; print $1' 
Part I: Introduction to <i>Beyond Good and Evil</i>
Part II: The <i>Wrath</i> of <i>Khan</i>
Part III: Return Of The <i>Jedi</i> 

# strip out all tags within the title
bob@cob:/tmp$ cat file.html | perl -nle '/<b>(.*)<\/b>/; print $1' | perl -pe 's/<.*?>//g'
Part I: Introduction to Beyond Good and Evil
Part II: The Wrath of Khan
Part III: Return Of The Jedi 

# use match operator to match the first char in every sequence of consecutive non-whitespace chars
# returns list context, which gets printed as a group of letters
# "-l" flag adds a newline after each print, but has other side effects so beware if you keep that
bob@cob:/tmp$ cat file.html | pcregrep -o '<b>.*</b>' | perl -nle 's/<.*?>//g; print m/(\S)\S*/g '
PIItBGaE
PITWoK
PIROTJ

# Save the abbreviation and the original string (including its inner tags) into variables
bob@cob:/tmp$ cat file.html | perl -nle '/<b>(.*)<\/b>/; print $1' | perl -ne 'chop; $s=$_; s/<.*?>//g; $a=join("",m/(\S)\S*/g); printf(qq[%s: %s\n],$a,$s)'
PIItBGaE: Part I: Introduction to <i>Beyond Good and Evil</i>
PITWoK: Part II: The <i>Wrath</i> of <i>Khan</i>
PIROTJ: Part III: Return Of The <i>Jedi</i> 

# Use the (broken) HTML you supplied in the original post as a template and substitute in the variables
bob@cob:/tmp$ cat file.html | perl -nle '/<b>(.*)<\/b>/; print $1' | perl -ne 'chop; $s=$_; s/<.*?>//g; $t=join("",m/(\S)\S*/g); printf(qq[<p><a href="#%s" name="%s" style="text-decoration:none">%s</a></font><br>\n],$t,$t,$s) '
<p><a href="#PIItBGaE" name="PIItBGaE" style="text-decoration:none">Part I: Introduction to <i>Beyond Good and Evil</i></a></font><br>
<p><a href="#PITWoK" name="PITWoK" style="text-decoration:none">Part II: The <i>Wrath</i> of <i>Khan</i></a></font><br>
<p><a href="#PIROTJ" name="PIROTJ" style="text-decoration:none">Part III: Return Of The <i>Jedi</i> </a></font><br>


# Merge all of that into one single perl instance for brevity.
# (readability / maintainability is another story.  I would not want to maintain code like this.)
bob@cob:/tmp$ perl -ne '/<b>(.*)<\/b>/; $s=$1; s/<.*?>//g; $t=join("",m/(\S)\S*/g); printf(qq[<p><a href="#%s" name="%s" style="text-decoration:none">%s</a></font><br>\n],$t,$t,$s) ' file.html
<p><a href="#PIItBGaE" name="PIItBGaE" style="text-decoration:none">Part I: Introduction to <i>Beyond Good and Evil</i></a></font><br>
<p><a href="#PITWoK" name="PITWoK" style="text-decoration:none">Part II: The <i>Wrath</i> of <i>Khan</i></a></font><br>
<p><a href="#PIROTJ" name="PIROTJ" style="text-decoration:none">Part III: Return Of The <i>Jedi</i> </a></font><br>

```

---

