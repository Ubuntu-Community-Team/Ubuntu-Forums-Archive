---
title: "perl error......"
date: 2009-07-22
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-22
when i try matching uppercase or lower case scalar variable, its not recognising, is regular expression wrong in if statement??

```
#!/usr/bin/perl
%words= qw(
                abc cool
                gabreilla fool
                sony pool
                brooke bool
          );
print "whats your partner??\n";
$n=<STDIN>;
chomp($n);
if($n = ~/^abhilash\b/i)
{
        print "hi $n, you can enjoy night !!!!!\n";
}
else
{
        $sw=$words{$n};
        print "hi $n, tell proper codeword\n";
        $code=<STDIN>;
        chomp($code);
        while($code ne $sw)
        {
                print "hey your code is not matching, try once again!!!\n";
                $code=<STDIN>;
                chomp($code);
        }
print "howdy $n!!!, welcome to party\n";
}

```

abhilash@abhilash:~$ perl pgm7.pl
whats your partner??
abhilash
hi 4294967295, you can enjoy night !!!!!
abhilash@abhilash:~$ 
abhilash@abhilash:~$ perl pgm7.pl
whats your partner??
sony
hi 4294967295, you can enjoy night !!!!!


its not checking for other inputs also, i even tried substituting eq instead of =, but din't work.....

---

### Post by unutbu on 2009-07-22
```
if($n = ~/^abhilash\b/i)

```
This tells Perl to set $n equal to ~/^abhilash\b/i.
Apparently Perl evaluates ~/^abhilash\b/i and returns 4294967295 in a scalar context. 

If you remove the space between "=" and "~" then you get the match operator =~ which matches $n against the regexp ^abhilash\b:

```
if($n =~/^abhilash\b/i)

```

---

### Post by abhilashm86 on 2009-07-22
> **unutbu said:**
> ```
if($n = ~/^abhilash\b/i)

```
This tells Perl to set $n equal to ~/^abhilash\b/i.
Apparently Perl evaluates ~/^abhilash\b/i and returns 4294967295 in a scalar context. 

If you remove the space out between "=" and "~" then you get the match operator =~ which matches $n against the regexp ^abhilash\b:

```
if($n =~/^abhilash\b/i)

```

yes i totally missed it, now i understood, thanks a lot.

---

