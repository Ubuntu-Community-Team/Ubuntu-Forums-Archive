---
title: "Perl: package err msg from my perl pgm ?"
date: 2006-08-26
forum: Programming Talk
---

### Post by Browser_ice on 2006-08-26
I am working on my first Perl program. When I run it, I get a weird package error message pointing at code lines that only do string manipulations. :confused: ](*,)  

Can anyone tell me why ?

**Program :**
...
#open output file
open(OUTFILE,">CleanPlanOutput.pl.tmp") or die "Cannot open CleanPlanOutput output!";
...
		$OutputRec="$fl[0],$fl[1],$fl[2],$fl[3] $fl[4],$fl[5] $fl[6],$fl[7] $fl[8]";
...
			$OutputRec="$fl[0],$fl[1],$fl[2] $fl[3],$fl[4] $fl[5],$fl[6] $fl[7],$fl[8] $fl[9]";
...
			$OutputRec="";
...
	print OUTFILE $OutputRec;
...
#close output
close OUTFILE;


**Error message**

>~/MyProjects/Perl$ perl CleanPlanOutput.pl
Global symbol "$OutputRec" requires explicit package name at CleanPlanOutput.pl line 47.
Global symbol "$OutputRec" requires explicit package name at CleanPlanOutput.pl line 52.
Global symbol "$OutputRec" requires explicit package name at CleanPlanOutput.pl line 56.
Global symbol "$OutputRec" requires explicit package name at CleanPlanOutput.pl line 60.
Execution of CleanPlanOutput.pl aborted due to compilation errors.

---

### Post by Woei on 2006-08-26
> **Browser_ice said:**
> I am working on my first Perl program. When I run it, I get a weird package error message pointing at code lines that only do string manipulations. :confused: ](*,)  

Can anyone tell me why ?

**Program :**
...
#open output file
open(OUTFILE,">CleanPlanOutput.pl.tmp") or die "Cannot open CleanPlanOutput output!";
...
		$OutputRec="$fl[0],$fl[1],$fl[2],$fl[3] $fl[4],$fl[5] $fl[6],$fl[7] $fl[8]";
...
			$OutputRec="$fl[0],$fl[1],$fl[2] $fl[3],$fl[4] $fl[5],$fl[6] $fl[7],$fl[8] $fl[9]";
...
			$OutputRec="";
...
	print OUTFILE $OutputRec;
...
#close output
close OUTFILE;


**Error message**

>~/MyProjects/Perl$ perl CleanPlanOutput.pl
Global symbol "$OutputRec" requires explicit package name at CleanPlanOutput.pl line 47.
Global symbol "$OutputRec" requires explicit package name at CleanPlanOutput.pl line 52.
Global symbol "$OutputRec" requires explicit package name at CleanPlanOutput.pl line 56.
Global symbol "$OutputRec" requires explicit package name at CleanPlanOutput.pl line 60.
Execution of CleanPlanOutput.pl aborted due to compilation errors.


Do you have the *use strict;* pragma in effect in the codeblock where you're using $OutputRec ? use strict; forces you to declare all your variables with 'my', so they're in the smallest lexical scope possible, which is generally a *good thing*. Always use 'use strict;' and add '-w' at the end of the perl interpreter.

---

