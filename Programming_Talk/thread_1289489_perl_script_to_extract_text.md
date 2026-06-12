---
title: "perl script to extract text"
date: 2009-10-12
forum: Programming Talk
---

### Post by hanlin on 2009-10-12
I have a large comma separated file that I want to process. Each line looks like:
bla,bla,bla,x,x,x,bla,bla

I want to save each section as a separate variable. So var1=bla,bla,bla, var2=x,x,x and var3=bla,bla. 

How do I write a script to tell var1 to be set to the text up to the nth comma? And how do you set var2 to be the text from comma n to comma m?

---

### Post by TCSnyder on 2009-10-12
is there any difference between the text blah and the text x. if not, is it in some kind of order on the lines?

---

### Post by hanlin on 2009-10-12
The blas are different and the xs are different. But it's always in the same order, and the number of commas before you get to the xs are the same. Also, the number of commas in the xs section is the same.

---

### Post by tino27 on 2009-10-12
Split into tokens by commas:

```

@toks = split(/,/,$line);
while (defined($tok = shift(@toks))) {
      (grab value from $tok)
}

```

Then I'd compare the token to the last one to see if it's the same, and add on if it is.

---

### Post by ibuclaw on 2009-10-12
Look up array indexes, that should answer your question.

ie:
```

my $foo = "bla,bla,bla,x,x,x,bla,bla";
# split
my @foo = split(',', $foo);
# join
my $var1 = join(',', @foo[0..2]);
my $var2 = join(',', @foo[3..5]);
my $var3 = join(',', @foo[6..7]);

```

---

### Post by hanlin on 2009-10-12
Thank you all. I think that the array indecies will work perfectly for what I need.

---

