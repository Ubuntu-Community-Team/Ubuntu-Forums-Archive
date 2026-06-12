---
title: "Perl Substrings"
date: 2008-03-09
forum: Programming Talk
---

### Post by vicpascow on 2008-03-09
I have a set of sentences:

The code for this is UPN:9021
UPN:4321 is in this sentence
The code UPN:3490 and No:2938 are for something else

etc.

I want to search out the substring that contains
\UPN:/d{4}\
for each line and print the following:

UPN:
UPN:9021
UPN:4321
UPN:3490,UPN:2938

what I have done so far is

foreach $readout (@receipt) {
   if ($line =~ \UPN:/d{4}\) {
      print $1;
   }
}


which is not working out (and is not preserving the sentence breaks.

any suggestions?

---

### Post by ghostdog74 on 2008-03-09
only if you have no language constraints
```

awk '
{
  for(i=1;i<=NF;i++){
   if ( $i ~ /UPN|No/ ) {
        sub("No","UPN",$i)
        a[$i]
   }
  }
}
END{
 for(i in a ) print a[i],i
}
' file

```
output:
```

# ./test.sh
 UPN:3490
 UPN:9021
 UPN:4321
 UPN:2938


```

---

### Post by slavik on 2008-03-09
you are not extracting anything ... put \d{4} in parenthesis :)

also, if you want to match UPN: or No: then you want something like
```
$string = "The code for this is UPN:9021
UPN:4321 is in this sentence
The code UPN:3490 and No:2938 are for something else";

@match = $string =~ m/(?:upn|no):(\d{4})/igs;

print $_."\n" foreach(@match);

```

---

### Post by vicpascow on 2008-03-09
Thanks for the quick replies.

I think I mis-wrote:

the "No:" should be "UPN:"




So...
```

@match = $string =~ m/(upn):(\d{4})/igs;

print $_."\n" foreach(@match);


```


would this work?

---

### Post by vicpascow on 2008-03-09
got it:

@match = $string =~ m/(upn:\d{7})/igs;

---

### Post by slavik on 2008-03-09
you can also do:
(upn:\d+)\D

:) (\D is non-digit character)

---

