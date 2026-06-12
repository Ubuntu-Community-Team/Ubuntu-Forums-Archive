---
title: "Using Braces (or REGEX??) with Wget URL to ensure most fresh download pulled."
date: 2015-03-31
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2015-03-31
Thanks for reading. 

Question. I use Open Office.org. Course I want to keep it updated to latest greatest. (fyi-yes, I know I can update inside the app--but I'm trying to use this to learn "Braces" and "Regex" for wget pulls)--Any other URL example could do. 
You know, "Mentor" help :-) ****
____________________________________________

Thus Example Wget Pull from SourceForge

[wget http://sourceforge.net/projects/openofficeorg.mirror/files/4.1.0/binaries/en-US/Apache_OpenOffice_4.1.0_Linux_x86_install-deb_en-US.tar.gz]("http://wget http://sourceforge.net/projects/openofficeorg.mirror/files/4.1.0/binaries/en-US/Apache_OpenOffice_4.1.0_Linux_x86_install-deb_en-US.tar.gz")

Thus, thought process is. To even get this "Right" I have to account for teh 4.1.0/binaries (precending binaries)--and (presumably)--have that match 4.1.0 after the Office_4.1.0


Or if this is an easier example (don't have to work with both sets of numbers). 
[wget http://download.code42.com/installs/linux/install/CrashPlan/CrashPlan_3.6.3_Linux.tgz]("http://download.code42.com/installs/linux/install/CrashPlan/CrashPlan_3.6.3_Linux.tgz")

FYI, I DO KNOW there is an update on the server that is 3.7.0 (thus working with known data easier for showig examples???) 





Thus FAR, I've tried the following (and of course failed). ----FYI--I searched the web, tried to hack other exmaples people were asking for (most of which help with pics)

```

for i in {1..9}; do wget http://sourceforge.net/projects/openofficeorg.mirror/files/$i.$i.$i/binaries/en-US/Apache_OpenOffice_$i.$i.$i_Linux_x86_install-deb_en-US.tar.gz; done

--2015-03-29 19:15:33--  http://sourceforge.net/projects/openofficeorg.mirror/files/2.2.2/binaries/en-US/Apache_OpenOffice_2.2.-deb_en-US.tar.gz
Resolving sourceforge.net (sourceforge.net)... 216.34.181.60
Connecting to sourceforge.net (sourceforge.net)|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2015-03-29 19:15:34 ERROR 404: Not Found.

```

I see the flaw in that logic (now)--but what I was assuming was that as soon as it found a "hit", it would then look for the next place holder. AKA---It found "4"---would place holder that, iterate through 1-9 next place holder 
(help me here, that would have needed an "array" correct?) 



```

Was hopeful here, NO GO
wget http://sourceforge.net/projects/openofficeorg.mirror/files/{version,new}/binaries/en-US/Apache_OpenOffice_package{00..99}.deb_en-US.tar.gz

The Example I found, was  using "version,old" just assumed version new would work. 

```




Advice?













_________________________________

***(aka "Mentor Help" --great Doc with Steve Jobs. To which I agree. He said he thought  that Computer (specifically talking topic programming)---but should be  taught as a Liberal Art---akin to become a Lawyer. Law school teaches  one "how to think". 
Thus (I agree)--he said  most of life the  difference between good and "the best" is minimal--(uses Cab ride in  NYC--aka "The Best" will get you there what, 20, 30% faster. 
BUT, IN PROGRAMMING---the difference in good and "Best" is 100x maybe 500x better. (I agree) SORRY---I digress.

---

### Post by bardo2 on 2015-04-01
Hi,

not sure if i get your question right. So let me take it to pieces... ;-)

I understand - you want to find an expression to make downloads automatically without knowing the correct version number in advance.
Are you aware, that there is a problem attached with that approach?
What, if there are several valid version numbers for download available? Would you want all of them fetched, or only the first? according to which algorithm?
Next, the syntax for version numbers is very different in different places (sometimes delimited with "." (point), sometime with "-" (dash), sometimes date-encoded, and many more.
That is why i myself refuse to even design a one-size-fits-all solution, as there will be limits to such an approach - inevitable.
But...

You seamingly wanted to iterate through a space ({n}.{m].{l}) of 1-digit decimal numbers. That can be done, of course. But...
apart from the possible complexity, there is a very bad behavior exhibited by that algorithm: you would need to test the internet repeatedly for possibly downloadable packages, knowing the command will be rejected most of the time because of an invalid package version number, but creating quite some traffic, and most well configured webservers would block you even before you got to the correct number. So this would count on dumb webserver operators in order for it to work.

Now, let me tell you, how i personally approach such a job (for real). I try to behave like an ordinary user searching for the package, a.k.a. requesting websites that point to the download and identifying the link there, then downloading from that link. (Even that doesnt always work, as there could be a captcha involved, but it does most of the time.)

Basically, i suggest 3 steps: wget a webpage containing the link, search for the href tag and extract the link, download from that value.
wget -> awk -> wget

If you want to stick with your approach, i recommend to look into the command "parallel", which can do the iterating for you with a very easy syntax. I am using it quite often, as it is more powerful than "xargs", but sure less efficient than a bit of code (say in python). The last option for me would be to generate commands automatically and to hand-pick from those what i actually need.

Does that help?

---

### Post by Lars Noodén on 2015-04-01
> **bardo2 said:**
> 
Basically, i suggest 3 steps: wget a webpage containing the link, search for the href tag and extract the link, download from that value.
wget -> awk -> wget

I'd recommend that, too, or even sed.  Or since HTML is not to be relied upon, I would also consider using Perl to grab the first A in the first TH in the first TBODY using a proper HTML parser.

---

### Post by bardo2 on 2015-04-01
Just to give a primitive example, that DOES NOT involve software downloads:
```
wget -q -O - http://www.einsundsein.org/texte.php | awk '/meditation/ { sub ("^.*medi", "http://www.einsundsein.org/medi"); sub ("pdf.*$", "pdf"); print $0; }' | xargs -l wget -N 

```

---

### Post by Lars Noodén on 2015-04-02
Depending on how much the spacing and line breaks of the HTML page change, you might need the flexibility of an HTML parser.  

```

wget -q -O -  http://sourceforge.net/projects/openofficeorg.mirror/files/ | ./AOO.pl

```

Where the file AOO.pl consists of something like the following:

```

#!/usr/bin/perl                                                                 

use strict;
use warnings;
use HTML::TokeParser;

# http://sourceforge.net/projects/openofficeorg.mirror/files/                   

my $base = qq(http://sourceforge.net);

my $p = HTML::TokeParser->new(*STDIN) or
    die "Can't open: $!";

$p->get_tag("tbody");           # get first table body                               
$p->get_tag("th");              # get first table header after that                       
my $token = $p->get_tag("a");   # get first anchor after that                   

my $url = $token->[1]{href} || "-";     # extract href attribute from anchor    

my ( $version ) = ( $url =~ /\/([\.\d]+)\/$/ ); # extract version number        

print $base,$url,qq(binaries/en-US/Apache_OpenOffice_),$version,qq(_Linux_x86_install-deb_en-US.tar.gz/download\n);

print $base,$url,qq(binaries/en-US/Apache_OpenOffice_),$version,qq(_Linux_x86_install-deb_en-US.tar.gz.asc/download\n);

exit ( 0 );

```

That needs the HTML parser in package libhtml-parser-perl from the repository and will output two URLs which can then be used by your shell script.

---

