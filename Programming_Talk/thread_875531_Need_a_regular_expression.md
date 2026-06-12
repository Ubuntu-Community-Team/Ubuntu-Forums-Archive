---
title: "Need a regular expression"
date: 2008-07-30
forum: Programming Talk
---

### Post by bostonaholic on 2008-07-30
I need a regular expression for the following rules:
[I]What I already have is in bold.
I've shortened them to NUM, LIST, RANGE to make it easier to read[/I]
Helpful tool to check your regex: [http://www.regexpal.com/]("http://www.regexpal.com/")

1.  Any number with or without a decimal NUM
**(\d+(\.\d+)?)**
123
123.342

2.  Comma or semicolon lists of numbers LIST
**(NUM((,|;)NUM)*)**
123,234.343;2352,234
123.34,342,3453.435;2342,342.453

3. Colon separated numbers as a range RANGE
**(NUM(\:)NUM+)*)**
123:342.543

4. Combined 2 & 3 to allow lists and ranges in one regular expression.  This is where I need help.
1243,342.342:352,345;345.34
123:345;342,453.43

*THINGS NOT VALID*
a. Cannot begin or end with a symbol *.23 OR 235.*
b. Two ranges in a row 123:231.3:3453

Thanks.

---

### Post by slavik on 2008-07-30
#1 is wrong, you want: ((?:(?:[123456789]\d+)|0)(?:\.\d+)?) (numbers can't start with 0 unless it is 0.something)

#4, why not just do something like NUM([;,:]NUM)+ ???
edit, saw that two ranges in a row are invalid ... hmm ...

edit2: are you looking to validate input? because if so, you can make 2 invalid cases.

---

### Post by CSEatOSU on 2008-07-30
> **slavik said:**
> #1 is wrong, you want: ((?:(?:[123456789]\d+)|0)(?:\.\d+)?) (numbers can't start with 0 unless it is 0.something)

#4, why not just do something like NUM([;,:]NUM)+ ???
edit, saw that two ranges in a row are invalid ... hmm ...

Thanks for the heads up about the leading 0's, although in this case, leading 0's are allowed.

---

### Post by slavik on 2008-07-30
then nvm about that :P, but are you looking to validate input or just parse data?

hmm, you might be able to use NUM(:NUM)?[,;]

---

### Post by CSEatOSU on 2008-07-30
> **slavik said:**
> then nvm about that :P, but are you looking to validate input or just parse data?

I'm in charge of validating the input, someone else will then parse the if-valid expression.

---

### Post by slavik on 2008-07-30
then make the two invalidating expression as if (match) then not valid.

---

### Post by CSEatOSU on 2008-07-30
Sorry, I meant I'm in charge of determining if the input string is valid against the regex.  Someone else will then break apart the string into separate nums, lists, and ranges.

All I'm looking for is a regex for validating the input.

---

### Post by 3370318 on 2008-07-31
I haven't tested it extensively and there's probably a better way of doing it, but this looks like it should work (it's in a Perl flavor):

*****************Edit*****************
Ack, my original pattern neglected single digits.  This ought to fix it.
**************************************

```
/^(\d+(\.\d+)?)+((:\d+(\.\d+)?)?([,;]\d+(\.\d+)?))*(:?\d+(\.\d+)?)?$/
```

Well, since everyone's including a test program, here's mine:
```
#!/usr/bin/perl
while (1) {
    print "Enter a string (q to quit): ";
    $string = <>;
    last if ($string =~ /^q(uit)?/i);
    if ($string =~ /^(\d+(\.\d+)?)+((:\d+(\.\d+)?)?([,;]\d+(\.\d+)?))*(:?\d+(\.\d+)?)?$/) {
        print "valid\n";
    } else {
        print "invalid\n";
    }
}
```

By the way, could somebody who knows Tcl/Tk take a look at my post :)

---

### Post by unutbu on 2008-07-31
Does this satisfy your purpose?
```

^[^\D]?((\d+(\.\d+(?!\d*\.\d*))?[,;]?)+|(\d+(\.\d+(?!\d*\.\d*))?:(?!\d+(\.\d+)?:))+)+[^\D]?$

```
I tested it with this. (I couldn't figure out how to use the link you gave.)

```
#!/usr/bin/env python
import re
good_strs=['123',
           '123.342',
           '123,234.343;2352,234',
           '123.34,342,3453.435;2342,342.453',
           '123:342.543',
           '1243,342.342:352,345;345.34',
           '123:345;342,453.43',
           ]

bad_strs=[
    '.23',
    '235.',
    '123:231.3:3453',
    '123,,231.3',
    '123..3',
    '123;;3',
    '123;.231',
    '123.231.3',
    ]

pat='^[^\D]?((\d+(\.\d+(?!\d*\.\d*))?[,;]?)+|(\d+(\.\d+(?!\d*\.\d*))?:(?!\d+(\.\d+)?:))+)+[^\D]?$'
for astr in good_strs:
    match=re.search(pat,astr)
    if match:
        print "%s matched OK"%astr
    else:
        print "%s missed FAILED"%astr

for astr in bad_strs:
    match=re.search(pat,astr)
    if match:
        print "%s matched FAIL"%astr
    else:
        print "%s missed OK"%astr

```

Output:

```
% test.py
123 matched OK
123.342 matched OK
123,234.343;2352,234 matched OK
123.34,342,3453.435;2342,342.453 matched OK
123:342.543 matched OK
1243,342.342:352,345;345.34 matched OK
123:345;342,453.43 matched OK
.23 missed OK
235. missed OK
123:231.3:3453 missed OK
123,,231.3 missed OK
123..3 missed OK
123;;3 missed OK
123;.231 missed OK
123.231.3 missed OK
```

---

### Post by WW on 2008-07-31
OK, I'll join the party:

numlistcheck.py
```

import re

num = r"(\d+(\.\d+)?)"
item = num+"|"+"("+num+":"+num+")"
pat = "("+item + ")([,;]("+item+r"))*$"

print "pat = %s" % pat

prog = re.compile(pat)

while 1:
    s = raw_input("Enter a list [Hit enter to quit]: ")
    if s == "":
        break
    check = prog.match(s)
    if check is None:
        print "Invalid."
    else:
        print "Match!"

```
Same run:
```

$ python numlistcheck.py 
pat = ((\d+(\.\d+)?)|((\d+(\.\d+)?):(\d+(\.\d+)?)))([,;]((\d+(\.\d+)?)|((\d+(\.\d+)?):(\d+(\.\d+)?))))*$
Enter a list [Hit enter to quit]: 123
Match!
Enter a list [Hit enter to quit]: 123.342
Match!
Enter a list [Hit enter to quit]: 123,234.343;2352,234
Match!
Enter a list [Hit enter to quit]: 123.34,342,3453.435;2342,342.453
Match!
Enter a list [Hit enter to quit]: 123:342.543
Match!
Enter a list [Hit enter to quit]: 1243,342.342:352,345;345.34
Match!
Enter a list [Hit enter to quit]: 123:345;342,453.43
Match!
Enter a list [Hit enter to quit]: .23
Invalid.
Enter a list [Hit enter to quit]: 235.
Invalid.
Enter a list [Hit enter to quit]: 123:231.3:3453
Invalid.
Enter a list [Hit enter to quit]: ,
Invalid.
Enter a list [Hit enter to quit]: :
Invalid.
Enter a list [Hit enter to quit]: 23:
Invalid.
Enter a list [Hit enter to quit]: 
$ 

```

---

### Post by ghostdog74 on 2008-07-31
```

echo "123.432:1234.5,123sdf" | awk 'BEGIN{ FS="[;:,]"}
{
 for(i=1;i<=NF;i++) {
  if ($i+0 == $i ){
   print $i " is a decimal/number"
  }else {
   print $i " is not a good input"
  }
 }
}
'
 

```
output:
```

 # ./test.sh
123.432 is a decimal/number
1234.5 is a decimal/number
123sdf is not a good input


```

---

### Post by CSEatOSU on 2008-07-31
Thanks 3370381, unutbu, and WW.  They all work like a charm, for all that I can see.  QA will try to break it tomorrow so we'll see.

Even though 3370381 is shortest, I think I'm going with WW's solution because it is easier to simplify into componenets. i.e.

^((\d+(\.\d+)?)|((\d+(\.\d+)?):(\d+(\.\d+)?)))([,;]((\d+(\.\d+)?)|((\d+(\.\d+)?):(\d+(\.\d+)?))))*$

^(NUM|(NUM:NUM))([,;](NUM|(NUM:NUM)))*$

^(NUM|RANGE)([,;](NUM|RANGE))*$

---

### Post by ghostdog74 on 2008-07-31
> **CSEatOSU said:**
> 
Even though 3370381 is shortest, I think I'm going with WW's solution because it is easier to simplify into componenets. i.e.

and harder to read and debug. Make sure you document it well.

---

### Post by CSEatOSU on 2008-07-31
> **ghostdog74 said:**
> and harder to read and debug. Make sure you document it well.

Yes, I plan on putting the break-downs into documentation (at least comments in my code).

```
**NUM**    = (\d+(\.\d+)?)
**LIST**   = (NUM([,;]NUM)*)
**RANGE**  = (NUM:NUM)
**REGEX**  = ^((\d+(\.\d+)?)|((\d+(\.\d+)?):(\d+(\.\d+)?)))([,;]((\d+(\.\d+)?)|((\d+(\.\d+)?):(\d+(\.\d+)?))))*$

**REGEX** *breakdown*
^((\d+(\.\d+)?)|((\d+(\.\d+)?):(\d+(\.\d+)?)))([,;]((\d+(\.\d+)?)|((\d+(\.\d+)?):(\d+(\.\d+)?))))*$
^(NUM|(NUM:NUM))([,;](NUM|(NUM:NUM)))*$
^(NUM|RANGE)([,;](NUM|RANGE))*$
```

---

### Post by CSEatOSU on 2008-07-31
> **3370318 said:**
> I haven't tested it extensively and there's probably a better way of doing it, but this looks like it should work (it's in a Perl flavor):

*****************Edit*****************
Ack, my original pattern neglected single digits.  This ought to fix it.
**************************************

```
/^(\d+(\.\d+)?)+((:\d+(\.\d+)?)?([,;]\d+(\.\d+)?))*(:?\d+(\.\d+)?)?$/
```

Well, since everyone's including a test program, here's mine:
```
#!/usr/bin/perl
while (1) {
    print "Enter a string (q to quit): ";
    $string = <>;
    last if ($string =~ /^q(uit)?/i);
    if ($string =~ /^(\d+(\.\d+)?)+((:\d+(\.\d+)?)?([,;]\d+(\.\d+)?))*(:?\d+(\.\d+)?)?$/) {
        print "valid\n";
    } else {
        print "invalid\n";
    }
}
```

By the way, could somebody who knows Tcl/Tk take a look at my post :)

Yours will not work.
*234.2354.3453* tests ok with your regex but should be invalid.

---

