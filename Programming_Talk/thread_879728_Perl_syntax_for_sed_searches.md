---
title: "Perl syntax for sed searches"
date: 2008-08-04
forum: Programming Talk
---

### Post by masinick on 2008-08-04
I am aware that Perl has a lot of features that originally came from sed and awk. I have a pattern that I am using like this:

sed -n '/|Y|/p'

I want to do the same thing in Perl and be able to either save that value in some kind of variable or array or potentially write it out to a file.

For the simple case, writing out to a file, I think the syntax is very close to the sed syntax. I would like to get a few recommendations, first, on a few alternative ways to write a similar expression in Perl, then how to do I/O properly.

My second question is that I have two files, both with pipe separated data. In the first file, I want to do a large data reduction first, taking the pattern above, and retaining only records containing |Y|. In the second file, I have a field containing an employee number with an A as the first digit. The other larger file contains this same data, but with a lower case a.

The complete exercise, then, is to first reduce the first file to records containing Y in the field, surrounded by the pipe symbol. Next, I compare the records that match in the second file to the employee ID field, after making sure it is lower cased in both files.  Then I need to print matching records, possibly printing the first, third, and fourth fields within the matching records.

Can anyone give me a few key technology snippets on this so I don't keep struggling with it, and I will then apply that technology to my modest sized application, which I am writing in Perl - for speed and portability. I have used Perl before, but I have never become an expert, and it has been years since I used it last. I am confusing myself with pieces of different syntax and making a lot of silly mistakes, therefore I would appreciate some sound advice to set me back on course. I am reading up using a few classics - the Perl Cookbook and Programming Perl, but both are large books and daunting to get through. Until I can digest them, I'd appreciate some pointers to accelerate my learning, and more importantly, get a script in at least a minimally usable form ASAP. Therefore, I appreciate specific tips. I'll get better at it once I have digested the classic resources and actually done more coding to regain the experience.

---

### Post by masinick on 2008-08-04
I implemented this first part and got the first file reduced to records containing |Y| using the following code:

```

while (<MINPUT>) {
   if ( /\|Y\|/ ) {
      print MOUTPUT;
      my $line = <SINPUT>;
   }
}


```

Now if I can take that data and compare the second field (pipe separated) in this file and the fourth field in the second file, then output to a third file the records found in both files, including the first, second, and fourth fields from that second file this tool will be complete.

Any suggestions on that part?

---

### Post by masinick on 2008-08-04
It is the nested reading of the two files and the comparison of the second and fourth fields where I am looking for appropriate techniques.  If anyone has expertise in this I would sure appreciate it.  Thanks!

---

### Post by ghostdog74 on 2008-08-04
open the second file, assign variable to each line, split on pipes, check array item against file one

---

### Post by masinick on 2008-08-05
> **ghostdog74 said:**
> open the second file, assign variable to each line, split on pipes, check array item against file one

Thanks!  I did indeed use a split on pipes and got a solution working!  Appreciate the help!

---

