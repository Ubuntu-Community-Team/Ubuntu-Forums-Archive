---
title: "perl +file permissions formatting script"
date: 2008-10-26
forum: Programming Talk
---

### Post by ian dobson on 2008-10-26
Hi All,

Anyone got a perl script that converts from the numeric file permissions (0755,0666) to the ascii (rw-rw-rw) format.

I know I could use stat::lsmode module but I'd like to avoid having too many dependancies.

Regards
Ian Dobson

---

### Post by ZuLuuuuuu on 2008-10-26
Actually, you can do it. I don't know much about it but roughly: In 0755 (or whatever) every digit has a meaning:

0 => this is the leftmost digit and I guess it defines the type of the file (regular file, directory etc...)
7 => read, write, execute permissions
5 => read, execute permissions
5 => read, execute permissions

How do we know which number belongs to which permissions? Every permission has its own weight:

read => 4 (binary 100)
write => 2 (binary (010)
execute => 1 (binary (001)

So **for read, write and execute: 4+2+1 = 7**
**For read and execute 4+1 = 5**

```
1) So you should first seperate the digits,
2) Test the first digit and specify the type of the file
3) Then for each digit (from leftmost to rightmost):
    If it is > 4 then it has read permission so append "r" to the string
        Subtract 4 from that digit
    Else it does not have read permission so append "-" to the string

    If it is still > 2 then it has write permission so append "w" to the string
        Subtract 2 from that digit
    Else it does not have write permission so append "-" to the string

    If it is still > 1 then it has execute permission so append "x" to the string
    Else it does not have execute permission so append "-" to the string
```

That's it :) Maybe the testing part can be done with a masking technique, more efficiently.

I'm not sure about that first digit, you can omit it if it doesn't matter what type the file is.

---

### Post by ghostdog74 on 2008-10-26
you can use associative arrays (or hashes in Perl)
```

#!/bin/bash
    ls -l  | awk '
    BEGIN{
        perm["rwx"]=7
        perm["rw-"]=6
        perm["r--"]=4
        perm["-wx"]=3
        perm["--x"]=1
        perm["r-x"]=5
        pern["-w-"]=2
    }
    {
        uperm = substr($1,2,3)
        gperm = substr($1,5,3)
        operm = substr($1,8,3) 
        printf "%s has permission: %s%s%s\n", $9,perm[uperm],perm[gperm],perm[operm]
    }
    '


```

---

### Post by ian dobson on 2008-10-26
Hi ghostdog74,

Thanks for the idea, here's the perl code I've created based on your awl code

```

sub GetPermissions{
 my ($in) =@_; 
 my @perm = ("---","--x","-w-","-wx","r--","r-x","rw-","rwx") ;
 my $uperm = substr($in,1,1);
 my $gperm = substr($in,2,1);
 my $operm = substr($in,3,1);
 my $Text="$perm[$uperm] $perm[$gperm] $perm[$operm]";
 return $Text;
}

```

Regards
Ian Dobson

---

