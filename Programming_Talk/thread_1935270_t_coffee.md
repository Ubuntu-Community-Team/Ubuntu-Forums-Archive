---
title: "t_coffee"
date: 2012-03-03
forum: Programming Talk
---

### Post by eli1 on 2012-03-03
Hi,

I`m trying to do MSA by t_coffee in ubuntu. My multiple sequence file is result.fa that consists of 6 mt sequences. I dont know how to get phylogeny tree by t_coffee. Is there any body who can help me???

---

### Post by 23dornot23d on 2012-03-03
There is a program in the repos

[https://www.google.com/search?q=ClustalX](https://www.google.com/search?q=ClustalX)

[B]sudo apt-get install clustalx 

[IMG]http://img40.imageshack.us/img40/4750/snapshot6dh.jpg[/IMG]
[/B]

---

### Post by eli1 on 2012-03-03
> There is a program in the repos

[https://www.google.com/search?q=ClustalX](https://www.google.com/search?q=ClustalX)


tanX 23dornot23d but this is not T-Coffee...I need to get phylogeny tree through this method. ](*,)

---

### Post by 23dornot23d on 2012-03-04
You did check the wiki out ...... [http://en.wikipedia.org/wiki/T-Coffee](http://en.wikipedia.org/wiki/T-Coffee)

> 
**Comparisons with other alignment software**

 While the default output is a Clustal-like format, it is sufficiently  different from the output of ClustalW/X that many programs supporting  Clustal format cannot read it; [COLOR=Red]**fortunately ClustalX *can* import  T-Coffee output so the simplest fix for this issue is usually to import  T-Coffee's output into ClustalX and then re-export.**[/COLOR] Another possibility  is to request the strict Clustalw output format with the option "-output=clustalw_aln".
 An important specificity of T-Coffee is its ability to combine  different methods and different data types. In its latest version,  T-Coffee can be used to combine protein sequences and structures, RNA  sequences and structures. It can also run and combine the output of the  most common sequence and structure alignment packages. For a complete  list see: [tclinkdb.txt]("http://www.tcoffee.org/Resources/tclinkdb.txt")
 T-Coffee comes along with a sophisticated sequence reformatting  utility named seq_reformat. An extensive documentation is available from  [t_coffee_technical.htm]("http://www.tcoffee.org/Documentation/t_coffee/t_coffee_technical.htm") along with a tutorial [t_coffee_tutorial.htm]("http://www.tcoffee.org/Documentation/t_coffee/t_coffee_tutorial.htm")

Quote from T coffee tutorial .....

> 
**Producing phylogenetic trees**

  Seq_reformat is NOT a phylogeny package, yet over the time it has accumulated a few functions that make it possible to compute simple phylogenetic trees, or similar types of clustering:
  Given a multiple sequence alignment, it is possible to compute either a UPGM or an NJ tree:
    seq_reformat -in <aln> -action +aln2tree -output newick 
  
  Will use an identity matrix to compare your sequences and will output an unrooted NJ tree in newick format. If you want to produce a rooted UPGMA tree:
    seq_reformat -in <aln> -action +aln2tree _TMODE_upgma -output newick 
  
  If your data is not data sequence, but a matrix of 1 and Os (i.e. SAR matrix for instance), you can use a different matrix to compute the pairwise distances:
       seq_reformat -in <aln> -action +aln2tree _MATRIX_sarmat -output newick 
  
  All these parameters can be concatenated:
       seq_reformat -in <aln> -action +aln2tree _TMODE_upgma_MATRIX_sarmat -output newick 
  
  Bootstrap facilities will also be added at some point &#8230; For now we recommend you use Phylip if you need some serious phylogeny&#8230;

[http://code.google.com/p/tcoffee/source/browse/tcoffee/trunk/testsuite/all/server/.testcase?r=1152](http://code.google.com/p/tcoffee/source/browse/tcoffee/trunk/testsuite/all/server/.testcase?r=1152)


[http://spdbv.vital-it.ch/TheMolecularLevel/Matics/improve.html](http://spdbv.vital-it.ch/TheMolecularLevel/Matics/improve.html)

This last link seems to be an online application ..... for it ....

[http://tcoffee.vital-it.ch/cgi-bin/Tcoffee/tcoffee_cgi/index.cgi?stage1=1&daction=TCOFFEE::Regular](http://tcoffee.vital-it.ch/cgi-bin/Tcoffee/tcoffee_cgi/index.cgi?stage1=1&daction=TCOFFEE::Regular)

---

