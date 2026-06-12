---
title: "Parse websearch with Perl (RegEx?)"
date: 2008-07-18
forum: Programming Talk
---

### Post by hansoffate on 2008-07-18
I am trying to query the yeastGFP DB at UCSF to get which regions GFP will effect.  I have a list of about 250 different IDs that can just be inserted in the URL to get the different results.  I have done this before (with help here) on the NCBI database and on the yeastgenome database with RegEx to strip out what I needed to get.  However, now when I read the page source, I don't think there is a way to write a RegEx because there is no unique tag identifier.

[http://yeastgfp.ucsf.edu/getOrf.php?orf=YPL231W](http://yeastgfp.ucsf.edu/getOrf.php?orf=YPL231W)
[http://yeastgfp.ucsf.edu/getOrf.php?orf=YLL009C](http://yeastgfp.ucsf.edu/getOrf.php?orf=YLL009C)

The data that I want to use is always in the first form table of the page source.  Basically, I want to get if it says Nucleus, Cytoplasm, Mitochondrion, etc.  Depending on which ORF I put in the URL, changes what which regions illuminate.  Here is an example of where there are two regions that illuminate; the nucleus and cytoplasm.    

```
<form action="" target="" name="f5153">
<table width="542" border="0" cellpadding="0" cellspacing="0" bgcolor="#CCCCCC">
<tr>
<td width="330" rowspan="2" colspan="2"><table width="330" border="0" cellpadding="0"><tr><td width=90 colspan=2><b class="searchDisp">COX17</b></td><td  width=80 align=middle><b><a href="http://db.yeastgenome.org/cgi-bin/SGD/locus.pl?locus=YLL009C" target="_blank">YLL009C</a></b></td><td width=80 align=middle>&nbsp</td><td width=80 align=middle><b>comments</b></td></tr><tr><td colspan="4"><a href="javascript: openAbundance();"> molecules/cell:</a> not visualized</td><td align=center><a href="javascript:openComment(5153);">add</a></td></tr><tr><td>loc</td><td colspan="3"><input type="text" name="n5153" value="none"></td><td align=center>&nbsp;</td></tr></table></td><td rowspan="4" width="2">&nbsp;</td><td width="60" height="40" valign="top"><a href="javascript:void(0);" onclick="return false;" onmouseover="popupOpen('initial localizations scored in first pass','INIT');" onmouseout="popupClose();"><img name="INIT" src="orfIcons/initial.jpg" width="60" height="40" alt="" border="0"></a></td>

<td width=40 height=40><a href="javascript: changeAll('document.clip5153','/images/clipsNew/6557_clipPlus0.png','f5153','n5153','cytoplasm','locLink5153','displayLocImage.php?loc=6557');" target="_top"  onMouseOver="popupOpen('cytoplasm','cytoplasm');" onMouseOut="popupClose();">
<img src="orfIcons/locIcon[FONT="Arial Black"]Cytoplasm[/FONT].jpg" alt="" name="o5153I0" width="40" height="40" border="0" onload=""></a></td>
<td width=40 height=40><a href="javascript: changeAll('document.clip5153','/images/clipsNew/6558_clipPlus0.png','f5153','n5153','nucleus','locLink5153','displayLocImage.php?loc=6558');" target="_top"  onMouseOver="popupOpen('nucleus','nucleus');" onMouseOut="popupClose();">
<img src="orfIcons/locIcon[FONT="Arial Black"]Nucleus[/FONT].jpg" alt="" name="o5153I1" width="40" height="40" border="0" onload=""></a></td>
<td width=40 height=40><img src="orfIcons/white.jpg" alt="" name="o5153I2" width="40" height="40" border="0" onload=""></td>
<td width=40 height=40><img src="orfIcons/white.jpg" alt="" name="o5153I3" width="40" height="40" border="0" onload=""></td>
<td width=40 height=40><img src="orfIcons/white.jpg" alt="" name="o5153I4" width="40" height="40" border="0" onload=""></td>
<td width=40 height=40><img src="orfIcons/white.jpg" alt="" name="o5153I5" width="40" height="40" border="0" onload=""></td>
</tr>
```

Here is my attempt of a perl script to do this.  I either need a  RegEx or use a module that can easily get the information I want.  Maybe I can't even do this in Perl?  

Thanks for the help,
Hans

```
#!/usr/bin/perl
#use strict;
use warnings;
use LWP::Simple


open IDS, "<ids.txt";
@orfs = <IDS>;
close(IDS);


open (MYFILE, '>data.csv');
print MYFILE "ORF,GFP_Region\n";


foreach $orf (@orfs) 
	{
	chomp($orf);
    $html = 
get("http://yeastgfp.ucsf.edu/getOrf.php?orf=$orf");
    unless (length($html)) {
	warn "Unable to load page for '$orf'\n";
	next;
    }


    @found = ();
    {
##RegEx Here?
    ($gfp) = $html =~ /.*?<img src="orfIcons\/locIcon"(.*?)\.jpg/gsi;
    push(@found, $gfp);
    }
      print MYFILE "$orf,@found\n";
}

```

---

### Post by unutbu on 2008-07-18
```
#!/usr/bin/perl
use strict;
use warnings;
use LWP::Simple;

open IDS, "<ids.txt";
my @orfs = <IDS>;
close(IDS);

open (MYFILE, '>data.csv');
print MYFILE "ORF,GFP_Region\n";

foreach my $orf (@orfs) {
    chomp($orf);
    my $html = get("http://yeastgfp.ucsf.edu/getOrf.php?orf=$orf");
    unless (length($html)) {
	warn "Unable to load page for '$orf'\n";
	next;
    }

    my %found;
    my @lines=split(/<img src="/,$html);
    foreach my $line (@lines) {
	my ($gfp) = ($line =~ /^orfIcons\/locIcon([^.]+)\.jpg/gsi);
	$found{$gfp}=1 if ($gfp);
    }
    print MYFILE "$orf, ".join(', ',keys %found)."\n" if (scalar (keys %found));
}
```

Output:
```

ORF,GFP_Region
YPL231W, Cytoplasm
YLL009C, Nucleus, Cytoplasm
```

---

### Post by ghostdog74 on 2008-07-18
you are going to hit a block in time to come when you change your requirements. Its advisable to use a dedicated HTML parser.

---

### Post by hansoffate on 2008-07-19
@unutbu  I tried out the script but it doesn't finish running.  
```
perl projectV3.pl 
Can't locate object method "found" via package "Nucleus" (perhaps you forgot to load "Nucleus"?) at projectV3.pl line 25.
```

@ghostdog74 Thanks for the help in other posts of mine.  What would you recommend me using then?

---

### Post by unutbu on 2008-07-19
Strange -- I can't reproduce that error message. The script works for me (even with the semicolon missing. See below)

I did notice I forgot a semicolon however:
```

use LWP::Simple
```

should be

```
use LWP::Simple;
```

Cut and paste my slightly edited post #2 into a new file and try again?

---

### Post by ghostdog74 on 2008-07-19
> **hansoffate said:**
> @ghostdog74 Thanks for the help in other posts of mine.  What would you recommend me using then?

HTML::Parser

---

### Post by hansoffate on 2008-07-21
Thanks for the help unutbu. I thought I tried fixing the semi colon and it still had a problem.  Anyways, I used your edited script and it worked great.  

If you have time, I have a couple of quick questions about the script.  First, you split(/<img src="/,$html); so that there is a new line after that statement so the RegEx can search for "orfIcons/locIcon" at the beginning of the line, correct?

```
	$found{$gfp}=1 if ($gfp);
    }
    print MYFILE "$orf, ".join(', ',keys %found)."\n" if (scalar (keys %found));

```

I don't understand why you used the keys/how that code works in the second line. How did the keys get setup?  The first line?

Thanks for the help,
Hans

---

### Post by unutbu on 2008-07-21
> 
First, you split(/<img src="/,$html); so that there is a new line after that statement so the RegEx can search for "orfIcons/locIcon" at the beginning of the line, correct?

Yep. That's what I did. This would break if [http://yeastgfp.ucsf.edu/getOrf.php](http://yeastgfp.ucsf.edu/getOrf.php) decided to write html which broke <img src= on to two lines for example:

```
<img
src="

```
Hence the need for something like HTML::Parser to really do the job right. (Just a little warning).

> 
```
	$found{$gfp}=1 if ($gfp);
    }
    print MYFILE "$orf, ".join(', ',keys %found)."\n" if (scalar (keys %found));
```

I don't understand why you used the keys

In your original code you used an array, @found, to collect $gfp's, whereas I used a hash, %found. I don't know anything about $gfps. In particular, I didn't know if the same $gfp might show up twice in the same document. If it did, @found would have the same $gfp listed twice. Since you only want gfp's listed once (I assumed), I changed found to a hash.
(A hash is like a telephone book, each name(or key) in the telephone book only gets listed once. Similarly, if %found is a hash, and $gfp is the key, the $gpf key will only get listed once in the hash no matter how many times $found{$gfp} is assigned a value.)

> How did the keys get setup? The first line?
Indeed, "$found{$gfp}=1 if ($gfp);" is the line which sets up the hash. Whenever a $gfp is found, "if ($gfp)" is true and "$found{$gfp}=1" gets executed. The %found hash gets a key/value pair. $gfp is the key, 1 is the value, though any value would have worked.

> ... how that code works in the second line. 
Read "print MYFILE "$orf, ".join(', ',keys %found)."\n" if (scalar (keys %found));" from the right to the left:

(keys %found) returns a list of the keys -- that's a list of gfp's.

(scalar (keys %found)) returns the number of elements in the list. Really, this was not necessary, "if (keys %found)" would have worked too.

"if (scalar (keys %found))" will be true if the list (keys %found) has any keys (i.e. any gpf's), and it will be false if there are no keys. So the print statement only gets executed if gfps had been found.

join(', ',keys %found) creates a string. The elements of the list (keys %found) are joined by commas, or more precisely, a comma followed by a space: ', '. If there is only one gfp in the list, then no comma gets written, but if there are two or more, they get joined with ', ' in between.

```
"$orf, "                   is a string 
join(', ',keys %found)     is a string 
"\n"                       is a string
```

These strings are concatenated with the period (.) to form one big string.

Hope that helps.

---

### Post by hansoffate on 2008-07-21
Lots of thanks Unutbu for explaining everything in such great detail.  Also, thank you for explaining how HTML::Parser would have been better.  I didn't need the explanation for the join in the second line, just the section that dealt with the keys, but thanks.  I understand everything completely now.

---

