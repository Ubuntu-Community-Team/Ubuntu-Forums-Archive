---
title: "treatment of text either by AWK or SHELL script"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by xptional on 2012-11-05
Hello, 

I need to treat a text file. called xxx.bib. It contains about 3000 lines, mainly with " % " sign, .. title=  and url=  etc. The count of title rows is 229 and same for url. 
```

%
@INPROCEEDINGS{LiuH2006,
author={Liu, H. and Wan, P. and Jia, X. and Liu, X. and Yao, F.},
booktitle={INFOCOM 2006. 25th IEEE International Conference on Computer Communications. Proceedings}, 
title={Efficient Flooding Scheme Based on 1-Hop Information in Mobile Ad Hoc Networks},
year={2006},
month={april },
volume={},
number={},
pages={1 -12},
keywords={},
doi={10.1109/INFOCOM.2006.17},
url={http://ieeexplore.ieee.org/xpl/articleDetails.jsp?tp=&arnumber=4146670},
ISSN={0743-166X},}
%
@INPROCEEDINGS{ZhaoJ2006,
author={Zhao, J. and Cao, G.},
booktitle={INFOCOM 2006. 25th IEEE International Conference on Computer Communications. Proceedings}, 
title={VADD: Vehicle-Assisted Data Delivery in Vehicular Ad Hoc Networks},
year={2006},
month={april },
volume={},
number={},
pages={1 -12},
keywords={},
doi={10.1109/INFOCOM.2006.298},
url={http://ieeexplore.ieee.org/xpl/articleDetails.jsp?tp=&arnumber=4146951},
ISSN={0743-166X},}
%

```

What I want, I want to copy the url e.g. " [http://ieeexplore.ieee.org/xpl/articleDetails.jsp?tp=&arnumber=4146951](http://ieeexplore.ieee.org/xpl/articleDetails.jsp?tp=&arnumber=4146951) " and want to embed it with the title row as like, " \href{http://ieeexplore.ieee.org/xpl/articleDetails.jsp?tp=&arnumber=4146951}, 
The title row eventually should look like this, I don't want to remove url= line. 
```
title={\href{http://ieeexplore.ieee.org/xpl/articleDetails.jsp?tp=&arnumber=4146951}{VADD: Vehicle-Assisted Data Delivery in Vehicular Ad Hoc Networks}}
```

Attention, in each bibtex reference file, specific url is for the specific corresponding title. 

Could anyone please help me out about coding or any help to create AWK or SHELL script etc. 
I will be very much thankful to you for your cooperation.

---

### Post by Lars Noodén on 2012-11-05
If you work with perl scripting instead of the shell, you have the advantage of two CPAN modules, [Text::BibTeX](http://search.cpan.org/~gward/Text-BibTeX-0.34/BibTeX.pm) and [BibTeX::****Parser](http://search.cpan.org/~gerhard/BibTeX-Parser-0.64/lib/BibTeX/Parser.pm).  So that work has already been done for you.  Text::BibTeX is available in the repository as libtext-bibtex-perl.

---

### Post by Lars Noodén on 2012-11-05
This changes the title, there is probably an OO way, but it does produce the output you wanted.

```

#!/usr/bin/perl                                                                 

use strict;
use warnings;
use Text::BibTeX;

my $bibfile = new Text::BibTeX::File 'xxx.bib';
my $newfile = new Text::BibTeX::File '>zzz.bib';

while (my $entry = new Text::BibTeX::Entry $bibfile) {

    my ($author, $title, $url) = $entry->get ('author', 'title', 'url');
    print qq($author\n\t$title\n\t$url\n\n);

    $title = qq({\\href{$url}{$title}});
    $entry->set ('title', $title);
    $entry->write ($newfile);

}

```

---

### Post by xptional on 2012-11-06
Thanks you so much Lars :), 

It is really helpful, and thats I was searching. 

Here I came to install Text::BibTeX, but there is some error, I don"t know , how to solve it, 

Everthing goes fine like below, make and make test commands, but not make install, 
```
khan@khan:~/textBibTex/Text-BibTeX-0.34$ ls
BibTeX     BibTeX.c  BibTeX.pm  blib     btformat       btparse       btsort          btxs_support.h  CHANGES   Makefile     MANIFEST    README  typemap
BibTeX.bs  BibTeX.o  BibTeX.xs  btcheck  btool_faq.pod  btparse-0.33  btxs_support.c  btxs_support.o  examples  Makefile.PL  pm_to_blib  t
khan@khan:~/textBibTex/Text-BibTeX-0.34$ make
khan@khan:~/textBibTex/Text-BibTeX-0.34$ make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/bib.t ......... ok     
t/macro.t ....... ok     
t/modify.t ...... ok     
t/nameformat.t .. ok   
t/namelist.t .... ok     
t/names.t ....... ok     
t/output.t ...... ok     
t/parse.t ....... ok     
t/parse_f.t ..... ok     
t/parse_s.t ..... ok     
t/purify.t ...... ok     
All tests successful.
Files=11, Tests=337,  0 wallclock secs ( 0.09 usr  0.03 sys +  0.34 cusr  0.07 csys =  0.53 CPU)
Result: PASS
```
make install command shows the below error, 
```
khan@khan:~/textBibTex/Text-BibTeX-0.34$ make install
Files found in blib/arch: installing files in blib/lib into architecture dependent library tree
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
ERROR: Can't create '/usr/local/lib/perl/5.10.1/Text'
mkdir /usr/local/lib/perl: Permission denied at /usr/share/perl/5.10/ExtUtils/Install.pm line 483

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 at -e line 1
make: *** [pure_site_install] Error 13
```

Then I tried to create manually the desired directories , (/usr/local/lib/perl/5.10.1/Text) by going into root. 

when i repeat the procedure to install,  make install, There is change in error but it exists
```
khan@khan:~/textBibTex/Text-BibTeX-0.34$ make install
Files found in blib/arch: installing files in blib/lib into architecture dependent library tree
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
ERROR: Can't create '/usr/local/lib/perl/5.10.1/Text'
Do not have write permissions on '/usr/local/lib/perl/5.10.1/Text'
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 at -e line 1
make: *** [pure_site_install] Error 13

```

I thank in advance for any help please :)

---

### Post by SeijiSensei on 2012-11-06
Use "sudo make install" instead.  The installer is trying to write to directories that are owned by the root user.

---

### Post by xptional on 2012-11-06
Thank you so much, 
it works with 
```
sudo make install
```

Just a little point did not get , :D

---

### Post by xptional on 2012-11-06
Thanks you so much, 
The code you have provided, it works well. 

Its so interesting to work on .bib files. I thank you again to introduce it to me. :)

cheers !

---

### Post by Lars Noodén on 2012-11-06
Glad it worked.  The easy way on Ubuntu to grab Text::BibTeX, or any other CPAN module, is to use the package in the repository.  That will also make it easy to update, if the need ever arises.  

You can find them using Synaptic or apt-cache.  In this case the package you are looking for is [libtext-bibtex-perl](apt:libtext-bibtex-perl)  There is just about anything imaginable there.  

Have fun.

---

### Post by xptional on 2012-11-07
Thanks you so much again for your help .

---

