---
title: "Best Practice for Iterating Over Two Files at the Same Time?"
date: 2013-07-19
forum: Programming Talk
---

### Post by drmrgd on 2013-07-19
Tonight I was working on a problem where I have two similar files named something like 'file_n_something_x.xls' and 'file_n_something_x.vcf'.  I was trying to extract a subset of the data from each and compare it to find out if it was unique to one file or the other.  Because the data is similar, but different, and I had a few other things that I needed to do, I wrote a quickie Perl script to compare the two.  The issue is, though, that I have around 100 of these to compare side by side, and I don't know the best way to iterate over the pairs of files, passing them into the Perl script.  I ended up loading all of the xls files in to one array and then the vcf file into another:

```
$ declare -a vcf=(*.vcf)
$ declare -a xls=(*.vcf)

```

Then I just iterated over the two arrays, passing them into the script:
```

$ for (( i=0; i<${#xls[@]}; i++ )); do perl vcf_comparison.pl ${xls[i]} ${vcf[i]}; done

```

I figured that was fairly safe as the arrays should have been loaded in asciibetical order and I know all the files are indeed in pairs, and it did seem to work.  But, this doesn't seem like the right way to do this, and I'm wondering what the right way is.  I probably could have read all the files into an array in the Perl script and then more explicitly compared them before processing.  Maybe that's the only way?

What's the better way to do this, or is what I did the right way?

---

### Post by steeldriver on 2013-07-19
Could you not just replace the suffix? something like

```
for f in *.xls; do perl vcf_comparison.pl "$f" "${f%.xls}.vcf"; done
```

---

### Post by drmrgd on 2013-07-20
> **steeldriver said:**
> Could you not just replace the suffix? something like

```
for f in *.xls; do perl vcf_comparison.pl "$f" "${f%.xls}.vcf"; done
```

Brilliant!  I would have never thought of using a substitution like that to solve the problem.  I was stuck on trying to figure out how to iterate through the numbers in the filenames.  This worked perfectly!  Great suggestion, steeldriver!

---

### Post by Vaphell on 2013-07-20
yup, sometimes it's hard to see the forest for the trees ;-)

---

