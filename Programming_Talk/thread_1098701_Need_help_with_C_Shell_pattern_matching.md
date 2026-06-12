---
title: "Need help with C Shell pattern matching"
date: 2009-03-17
forum: Programming Talk
---

### Post by akvino on 2009-03-17
Hello all. I am trying to write a script in C shell, that would check for the current directory and based on which directory it is, allow or dissalow 'rm' command.

My biggest problem so far is checking if the directory "pwd" is resstricted or not. Here is my code where I do pattern matching:


set localdir=`pwd`;
echo "$localdir" ;

if ("$localdir" == '/root') then
echo "this is your root directory";
exit
end if


if ( "$localdir" =~ *[go] )  then
        echo "You are not allowed 1 delete files in $localdir!";
        exit

else if  ( "$localdir" =~ *[qff] )  then
        echo "You are not allowed 2 delete files in $localdir!";
        exit

else if  ( "$localdir" =~ *[fone] )  then
        echo "You are not allowed 3 delete files in $localdir!";
        exit

endif



-----------------------
ANy of the named directories could have different path - for instance:

path1/go
path2/go
path3/go 
etc...

What I have noticed, when I add data directory - it also dissalows root directory so the code:
if  ( "$localdir" =~ *[data] )  then
        echo "You are not allowed 3 delete files in $localdir!";
        exit

endif

IS THE SAME AS:
if  ( "$localdir" =~ *[root] )  then
        echo "You are not allowed 3 delete files in $localdir!";
        exit

endif

---------------------------------------



My question - what is the better way to implement pattern matching into this code? How does C shell interpret these pattern matching conditional statments (does it first convert them to binary?)

---

### Post by lloyd_b on 2009-03-17
You are misunderstanding exactly what the brackets ("[]") do.

The [] tells it "if the string matches *any* of these characters.  So your "*[data]" would translate as "match if string is anything ending in "d", "a", "t", or "a".  So "root" would match, as would "data", "ford", etc.

If you want to see if the end of the string matches "data", then the correct test would be:```
if ( "$localdir" =~ *"data" ) then
```

As a better way to implement these, I'd suggest a "switch" data structure:```
#!/bin/csh

set localdir=`pwd`;
echo "$localdir" ;

switch ("$localdir")
    case "/root"
        echo "This is your root directory"
        exit
        breaksw
    case *"/go"
        echo "You are not allowed 1 delete files in $localdir"
        exit
        breaksw
    case *"/qff"
        echo "You are not allowed 2 delete files in $localdir"
        exit
        breaksw
    case *"/fone"
        echo "You are not allowed 3 delete files in $localdir"
        exit
        breaksw
    case *"/data"
        echo "You are not allowed 4 delete files in $localdir"
        exit
        breaksw
endsw
```

Lloyd B.

---

### Post by akvino on 2009-03-17
> **lloyd_b said:**
> You are misunderstanding exactly what the brackets ("[]") do.

The [] tells it "if the string matches *any* of these characters.  So your "*[data]" would translate as "match if string is anything ending in "d", "a", "t", or "a".  So "root" would match, as would "data", "ford", etc.

If you want to see if the end of the string matches "data", then the correct test would be:```
if ( "$localdir" =~ *"data" ) then
```

As a better way to implement these, I'd suggest a "switch" data structure:```
#!/bin/csh

set localdir=`pwd`;
echo "$localdir" ;

switch ("$localdir")
    case "/root"
        echo "This is your root directory"
        exit
        breaksw
    case *"/go"
        echo "You are not allowed 1 delete files in $localdir"
        exit
        breaksw
    case *"/qff"
        echo "You are not allowed 2 delete files in $localdir"
        exit
        breaksw
    case *"/fone"
        echo "You are not allowed 3 delete files in $localdir"
        exit
        breaksw
    case *"/data"
        echo "You are not allowed 4 delete files in $localdir"
        exit
        breaksw
endsw
```

Lloyd B.

Super - this is exactly what I needed. Thanks a bunch Lloyd.;)

---

