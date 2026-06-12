---
title: "'find' regular expression"
date: 2012-11-08
forum: Programming Talk
---

### Post by dragos2 on 2012-11-08
Dear all,

I have the find below:
```

find . -regextype posix-egrep -iname "*G[0-6]0*[1-4]*REV[1-9]*.pdf" 

```
which returns files of certain revision number.

But I need the latest revision number in every directory and
this regular expression does not work as expected
```

*G[0-6]0*[1-4]*REV(9|8|7|6|5|4|3|2|1)*.pdf

```

The number trick should return the highest number without sort
but it does not work.

What do you think ?

---

### Post by diesch on 2012-11-08
You can't get only the highest number without comparing the numbers, and the regex can't do that as it only tries to match one filename at a time.

---

### Post by Lars Noodén on 2012-11-08
It might help to post a few examples of the file names to be sorted.

It's generally frowned upon to use "ls" in a script, but the following might work:

```

ls -v *.pdf | tail -n 1

```

---

### Post by dragos2 on 2012-11-08
In every directory there should be files like this:
somecharacters-G101-REV2-sometext.pdf
somecharacters-G101-REV4-sometext.pdf

and I need the highest REV4 one from that directory.

Possible with find or grep ?

---

### Post by Vaphell on 2012-11-08
no. Regexes don't compare anything, they find matches. You need some kind of sort to define X>Y relation between returned results.

---

### Post by dragos2 on 2012-11-08
> **Vaphell said:**
> no. Regexes don't compare anything, they find matches. You need some kind of sort to define X>Y relation between returned results.

I know, but I tried the REV(9|8|7|6|5|4|3|2|1).

But I think find operates on individual files and the above regex
can't work.

It seems that I have to use a real language for this.

---

### Post by Vaphell on 2012-11-08
but it didn't make any sense here
it was equivalent of [1-9] either way

```

some-junk: does it match REV[1-9]? NO   
file-REV3: does it match REV[1-9]? YES 
file-REV4: does it match REV[1-9]? YES
file-REV8: does it match REV[1-9]? YES

```
names that got YES will be included in the results. That's all.

> It seems that I have to use a real language for this.

what do you mean by real language? What's wrong with sorting and picking the first/last element? *sort* lets you define arbitrary sorting order.

---

### Post by Lars Noodén on 2012-11-08
> **Vaphell said:**
> *sort* lets you define arbitrary sorting order.

*sort -k* can do a lot, but the manual page is not very clear at all.

---

### Post by drmrgd on 2012-11-08
What about something like this (assuming your name example above is the way you've really named your files):

```
$ ls
somechars-G101-REV1-sometext.pdf  somechars-G101-REV3-sometext.pdf  somechars-G101-REV5-sometext.pdf
somechars-G101-REV2-sometext.pdf  somechars-G101-REV4-sometext.pdf  somechars-G101-REV6-sometext.pdf
$ find . -type f -iname "*REV*" -exec ls {} \; | sort -t "-" -rV -k3
./somechars-G101-REV6-sometext.pdf
./somechars-G101-REV5-sometext.pdf
./somechars-G101-REV4-sometext.pdf
./somechars-G101-REV3-sometext.pdf
./somechars-G101-REV2-sometext.pdf
./somechars-G101-REV1-sometext.pdf
```

---

### Post by dragos2 on 2012-11-08
> **drmrgd said:**
> What about something like this (assuming your name example above is the way you've really named your files):

```
$ ls
somechars-G101-REV1-sometext.pdf  somechars-G101-REV3-sometext.pdf  somechars-G101-REV5-sometext.pdf
somechars-G101-REV2-sometext.pdf  somechars-G101-REV4-sometext.pdf  somechars-G101-REV6-sometext.pdf
$ find . -type f -iname "*REV*" -exec ls {} \; | sort -t "-" -rV -k3
./somechars-G101-REV6-sometext.pdf
./somechars-G101-REV5-sometext.pdf
./somechars-G101-REV4-sometext.pdf
./somechars-G101-REV3-sometext.pdf
./somechars-G101-REV2-sometext.pdf
./somechars-G101-REV1-sometext.pdf
```

Interesting but does not work because there might be dashes before. But I know that its the last dash the one we need.

Can anything be improved upon that ?

File naming syntax:
```

*G[0-6]0*[1-4]*REV[1-9]*.pdf

```

---

### Post by Lars Noodén on 2012-11-08
> **dragos2 said:**
> Interesting but does not work because there might be dashes before. But I know that its the last dash the one we need.

Can anything be improved upon that ?

If the file names will take other forms, it will help to have as much of the full range of variation as possible.  Are there other examples that you can provide?

---

### Post by Vaphell on 2012-11-08
yup, you should give an example as broken as possible. Doing easy stuff is easy, the devil is always in the details and they tend to gather around corner cases and irregularities.

---

### Post by drmrgd on 2012-11-08
I'm not quite sure I'm clear on what you mean by dash comes before.  It seems you're saying you can't use a dash as delimiter in that sense.  So, what if you just sort a grep statement:

```
find new/ -type f -iname "*REV*" -exec ls {} \; | grep -i "REV" | sort -rV 
new/-this-is-a-file-too-string-REV9-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV8-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV7-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV6-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV5-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV4-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV3-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV2-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV1-I-should-do-too.pdf
new/somthingelse-aaa-rev7-something.pdf
new/somthingelse-aaa-rev6-something.pdf
new/somthingelse-aaa-rev5-something.pdf
new/somthingelse-aaa-rev4-something.pdf
new/somthingelse-aaa-rev3-something.pdf
new/somthingelse-aaa-rev2-something.pdf
new/somthingelse-aaa-rev1-something.pdf
new/idunno-abk-REV5-thistext.pdf
new/idunno-abk-REV4-thistext.pdf
new/idunno-abk-REV3-thistext.pdf
new/idunno-abk-REV2-thistext.pdf
new/idunno-abk-REV1-thistext.pdf
new/file1-xxx-rev3-somthing.pdf
new/file1-xxx-rev2-somthing.pdf
new/file1-xxx-rev1-somthing.pdf
```

---

### Post by Lars Noodén on 2012-11-08
> **drmrgd said:**
> 
```

$ find . -type f -iname "*REV*" -exec ls {} \; | sort -t "-" -rV -k3

```

If the REV # goes beyond 9, the sort needs to  be modified.

```

| sort -t "-" -rV -k3.4

```

But that's just having fun with sort until there are more sample data.

---

### Post by drmrgd on 2012-11-08
I think the '-V' option takes care of that case:

```
find . -maxdepth 1 -type f -iname "*REV*" -exec ls {} \; | sort -t "-" -rV -k3./somechars-G101-REV15-sometext.pdf
./somechars-G101-REV14-sometext.pdf
./somechars-G101-REV13-sometext.pdf
./somechars-G101-REV12-sometext.pdf
./somechars-G101-REV11-sometext.pdf
./somechars-G101-REV10-sometext.pdf
./somechars-G101-REV9-sometext.pdf
./somechars-G101-REV8-sometext.pdf
./somechars-G101-REV7-sometext.pdf
./somechars-G101-REV6-sometext.pdf
./somechars-G101-REV5-sometext.pdf
./somechars-G101-REV4-sometext.pdf
./somechars-G101-REV3-sometext.pdf
./somechars-G101-REV2-sometext.pdf
./somechars-G101-REV1-sometext.pdf
```

Good to know you can do that with the -k option for future reference, though.  Didn't know that was possible.

---

### Post by dragos2 on 2012-11-09
> **drmrgd said:**
> I'm not quite sure I'm clear on what you mean by dash comes before.  It seems you're saying you can't use a dash as delimiter in that sense.  So, what if you just sort a grep statement:

```
find new/ -type f -iname "*REV*" -exec ls {} \; | grep -i "REV" | sort -rV 
new/-this-is-a-file-too-string-REV9-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV8-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV7-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV6-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV5-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV4-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV3-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV2-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV1-I-should-do-too.pdf
new/somthingelse-aaa-rev7-something.pdf
new/somthingelse-aaa-rev6-something.pdf
new/somthingelse-aaa-rev5-something.pdf
new/somthingelse-aaa-rev4-something.pdf
new/somthingelse-aaa-rev3-something.pdf
new/somthingelse-aaa-rev2-something.pdf
new/somthingelse-aaa-rev1-something.pdf
new/idunno-abk-REV5-thistext.pdf
new/idunno-abk-REV4-thistext.pdf
new/idunno-abk-REV3-thistext.pdf
new/idunno-abk-REV2-thistext.pdf
new/idunno-abk-REV1-thistext.pdf
new/file1-xxx-rev3-somthing.pdf
new/file1-xxx-rev2-somthing.pdf
new/file1-xxx-rev1-somthing.pdf
```

I get a broken pipe on the ls part.

drmrgd try this: cp new new2 and try your code again.

I need only one file from one directory: the highest REV.

---

### Post by Lars Noodén on 2012-11-09
There might be a way to do this in awk, but after trying for a while I broke down and escalated to perl.  This reads a list of files from stdin and expects the file names to have REV or rev plus some numbers somewhere in the file name.  

```

#!/usr/bin/perl                                                                 

use strict;

my %files = ();

# cycle through files provided on stdin                                         
foreach my $file ( <> ) {
    chomp( $file );
    my @base = ();
    my $revision = 0;

    # cycle through file name components, separated by "-"                      
    foreach my $part ( split( /-/, $file ) ) {

        # grab revision number                                                  
        if ( $part =~ /^rev(\d+)/i) {
            $revision = $1;
            next;
        }
        push( @base, $part);
    }

    my $base = join ('-', @base );

    # keep the file if it is the most recent revision so far                    
    if ( $files{$base}{'rev'} < $revision ) {
        $files{$base}{'rev'} = $revision;
        $files{$base}{'file'} = $file;
    }
}

# print out the latest revisions                                                
foreach my $base ( keys( %files ) ) {
    print qq($files{$base}{'file'}\n);
}

exit (0);

```

It can be invoked like this.

```

find ./new -iname '*rev*' -print | ./latest_revision.pl

```

---

### Post by drmrgd on 2012-11-09
> **dragos2 said:**
> I get a broken pipe on the ls part.

drmrgd try this: cp new new2 and try your code again.

I need only one file from one directory: the highest REV.

Not sure what the broken pipe error is.  If I copy new to new2 as you propose and run the command, I get the same results

```
cp -r new/ new2
$ find new2/ -type f -iname "*REV*" -exec ls {} \; | grep -i "REV" | sort -rV
new/-this-is-a-file-too-string-REV9-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV8-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV7-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV6-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV5-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV4-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV3-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV2-I-should-do-too.pdf
new/-this-is-a-file-too-string-REV1-I-should-do-too.pdf
new/somthingelse-aaa-rev7-something.pdf
new/somthingelse-aaa-rev6-something.pdf
new/somthingelse-aaa-rev5-something.pdf
new/somthingelse-aaa-rev4-something.pdf
new/somthingelse-aaa-rev3-something.pdf
new/somthingelse-aaa-rev2-something.pdf
new/somthingelse-aaa-rev1-something.pdf
new/idunno-abk-REV5-thistext.pdf
new/idunno-abk-REV4-thistext.pdf
new/idunno-abk-REV3-thistext.pdf
new/idunno-abk-REV2-thistext.pdf
new/idunno-abk-REV1-thistext.pdf
new/file1-xxx-rev3-somthing.pdf
new/file1-xxx-rev2-somthing.pdf
new/file1-xxx-rev1-somthing.pdf
```

or:

```
find . -type f -iname "*REV*" -exec ls {} \; | grep -i "REV" | sort -rV
./somechars-G101-REV15-sometext.pdf
./somechars-G101-REV14-sometext.pdf
./somechars-G101-REV13-sometext.pdf
./somechars-G101-REV12-sometext.pdf
./somechars-G101-REV11-sometext.pdf
./somechars-G101-REV10-sometext.pdf
./somechars-G101-REV9-sometext.pdf
./somechars-G101-REV8-sometext.pdf
./somechars-G101-REV7-sometext.pdf
./somechars-G101-REV6-sometext.pdf
./somechars-G101-REV5-sometext.pdf
./somechars-G101-REV4-sometext.pdf
./somechars-G101-REV3-sometext.pdf
./somechars-G101-REV2-sometext.pdf
./somechars-G101-REV1-sometext.pdf
./new/-this-is-a-file-too-string-REV9-I-should-do-too.pdf
./new/-this-is-a-file-too-string-REV8-I-should-do-too.pdf
./new/-this-is-a-file-too-string-REV7-I-should-do-too.pdf
./new/-this-is-a-file-too-string-REV6-I-should-do-too.pdf
./new/-this-is-a-file-too-string-REV5-I-should-do-too.pdf
./new/-this-is-a-file-too-string-REV4-I-should-do-too.pdf
./new/-this-is-a-file-too-string-REV3-I-should-do-too.pdf
./new/-this-is-a-file-too-string-REV2-I-should-do-too.pdf
./new/-this-is-a-file-too-string-REV1-I-should-do-too.pdf
./new/somthingelse-aaa-rev7-something.pdf
./new/somthingelse-aaa-rev6-something.pdf
./new/somthingelse-aaa-rev5-something.pdf
./new/somthingelse-aaa-rev4-something.pdf
./new/somthingelse-aaa-rev3-something.pdf
./new/somthingelse-aaa-rev2-something.pdf
./new/somthingelse-aaa-rev1-something.pdf
./new/idunno-abk-REV5-thistext.pdf
./new/idunno-abk-REV4-thistext.pdf
./new/idunno-abk-REV3-thistext.pdf
./new/idunno-abk-REV2-thistext.pdf
./new/idunno-abk-REV1-thistext.pdf
./new/file1-xxx-rev3-somthing.pdf
./new/file1-xxx-rev2-somthing.pdf
./new/file1-xxx-rev1-somthing.pdf
./new2/-this-is-a-file-too-string-REV9-I-should-do-too.pdf
./new2/-this-is-a-file-too-string-REV8-I-should-do-too.pdf
./new2/-this-is-a-file-too-string-REV7-I-should-do-too.pdf
./new2/-this-is-a-file-too-string-REV6-I-should-do-too.pdf
./new2/-this-is-a-file-too-string-REV5-I-should-do-too.pdf
./new2/-this-is-a-file-too-string-REV4-I-should-do-too.pdf
./new2/-this-is-a-file-too-string-REV3-I-should-do-too.pdf
./new2/-this-is-a-file-too-string-REV2-I-should-do-too.pdf
./new2/-this-is-a-file-too-string-REV1-I-should-do-too.pdf
./new2/somthingelse-aaa-rev7-something.pdf
./new2/somthingelse-aaa-rev6-something.pdf
./new2/somthingelse-aaa-rev5-something.pdf
./new2/somthingelse-aaa-rev4-something.pdf
./new2/somthingelse-aaa-rev3-something.pdf
./new2/somthingelse-aaa-rev2-something.pdf
./new2/somthingelse-aaa-rev1-something.pdf
./new2/idunno-abk-REV5-thistext.pdf
./new2/idunno-abk-REV4-thistext.pdf
./new2/idunno-abk-REV3-thistext.pdf
./new2/idunno-abk-REV2-thistext.pdf
./new2/idunno-abk-REV1-thistext.pdf
./new2/file1-xxx-rev3-somthing.pdf
./new2/file1-xxx-rev2-somthing.pdf
./new2/file1-xxx-rev1-somthing.pdf
```

That being said, I tried Lars' script and it's way nicer and gives much, much better output.  Nice one!  So, that's definitely the better way to go.

```
find ./new* -iname '*rev*' -print | ./latest_revision.pl
./new2/file1-xxx-rev3-somthing.pdf
./new2/-this-is-a-file-too-string-REV9-I-should-do-too.pdf
./new/file1-xxx-rev3-somthing.pdf
./new/-this-is-a-file-too-string-REV9-I-should-do-too.pdf
./new/idunno-abk-REV5-thistext.pdf
./new2/somthingelse-aaa-rev7-something.pdf
./new/somthingelse-aaa-rev7-something.pdf
./new2/idunno-abk-REV5-thistext.pdf
```

---

