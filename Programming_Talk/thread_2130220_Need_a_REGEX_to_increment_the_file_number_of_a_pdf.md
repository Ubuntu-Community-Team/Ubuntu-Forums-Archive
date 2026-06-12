---
title: "Need a REGEX to increment the file number of a pdf file"
date: 2013-03-28
forum: Programming Talk
---

### Post by Marcus Aurelius on 2013-03-28
Hello,

I have a few thousand .pdf files in various folders each have a naming scheme like this:

006_-_Titled_Document_#34_-_September-25-2011-side-1.pdf

In each folder, the number system starts at 001 (as you see on the far  left of the file name), and then ends at 999 (maximum .pdf files).

Somewhere in the collection of files say .pdf # 286, I have 286 twice (duplicate).  Which screws up my numbering system.

I need a REGEX that I can enter into the shell when I'm in the .pdf  directory, and start from say the duplicate # 286 and increment that 2nd  duplicate # 286 & all the numbers after that by +1.  So that they  are all renamed appropriately.  

This way I don't have to go in there and rename each .pdf file manually one by one.

Unfortunately, I am not very good with REGEX and haven't had much need for it in the past until now.

Would anyone know the best way to automate this .pdf renumbering task?  I  would appreciate any constructive thoughts on how to accomplish this.

Thank you.

---

### Post by trent.josephsen on 2013-03-28
You'll need more than a regex to solve this problem... here, have some Perl.

I'd do something like this:

```
$ cat >fixnames.pl <<"EOF"
#!/usr/bin/perl -n

($old, $num) = /(?:.*\/)((\d{3})[^\/]*\.pdf)$/;
next unless $old;
$new = $old;
$new =~ s/$num/sprintf "%03d", $num+1/e;
if ($old > 286) {
    print "rename '$old', '$new'\n";
}
EOF
$ chmod +x fixnames.pl
$ find . -name '*.pdf' | ./fixnames.pl
```
Change the 'find' command if necessary to get all the files you want without any false positives. Run it as-is first, and when you're sure it does what you want, edit fixnames.pl and change the "print" line to just
```

    rename $old, $new;

```

It won't rename the extra #286, though, you'll have to fix that by hand. It's a feature, really. :)

---

### Post by ofnuts on 2013-03-28
No need for a regex to do this... The real question is whether you want to renumber everything (filling any gaps), or whether the sequence should be altered only when finding a duplicate. Renumbering everything bluntly is likely going to be a bit easier:
```

#! /bin/bash

count=0;
for file in *
do 
    count=$(( $count + 1 ))
    count0="000$count"
    renumbered="${count0: -3}_${file#???_}"
    [[ "$file" != "$renumbered" ]] && [COLOR=#ff0000]echo[/COLOR] mv -v "$file" "$renumbered"
done

```

This code won't behave correctly is some non-numbered files starts with three characters and an underscore. Remove the red "echo" when you are confident it fits your needs.

---

### Post by schragge on 2013-03-28
Well, I guess something like what **trent.josephsen** suggested can also be done with [rename]("http://manpages.ubuntu.com/manpages/precise/en/man1/prename.1.html") command alone as it is actually a perl script:
```

[COLOR=green]$[/COLOR] ls
[COLOR=#008000]001_Document0.pdf  004_Document3.pdf  006_Document6.pdf  009_Document9.pdf
002_Document1.pdf  004_Document4.pdf  007_Document7.pdf  010_Document10.pdf
003_Document2.pdf  005_Document5.pdf  008_Document8.pdf
$[/COLOR] rename -v[COLOR=#ff0000]n[/COLOR] 's/^\d{3}/sprintf("%03d",$&+1)/e if substr($_,0,3)>4' *
[COLOR=#008000]005_Document5.pdf renamed as 006_Document5.pdf
006_Document6.pdf renamed as 007_Document6.pdf
007_Document7.pdf renamed as 008_Document7.pdf
008_Document8.pdf renamed as 009_Document8.pdf
009_Document9.pdf renamed as 010_Document9.pdf
010_Document10.pdf renamed as 011_Document10.pdf[/COLOR]

```

---

### Post by trent.josephsen on 2013-03-28
Ah, I realize now that I misunderstood the problem... I was thinking you had many files with sequential names spread throughout a directory hierarchy, instead of a set of sequential names all in one folder. So I wrote a script that would handle whole paths when all that was really necessary was something much simpler, like what schragge did.

---

### Post by papibe on 2013-03-28
Hi Marcus Aurelius.

I had a similar challenge some time ago. What I did was create a script that reports the integrity of the directories, so that I could design a better solution.

This would be that reporting script adapted to your case:
```
#!/bin/bash

# Base directory containing other directories with pdfs.
PROJECT_DIR="/path/to/project/"

# Cycle through all subdirectories
while IFS= read -d '' dir; do
    echo "$dir"

    all_ok=false

    # cycle through all prefixes: 001...999
    for index in $(seq -f "%03.0f" 1 999); do

        # Get all files that start with prefix "$index".
        unset list i
        while IFS= read -d '' file; do
            list[i++]="$file"
        done< <(find "$dir" -maxdepth 1 -type f -name "${index}*" -print0)

        count=${#list[@]}
        all_ok=false

        # Missing file.
        if [ $count -eq 0 ]; then
            echo "    missing file: $index"

        # Perfect case: 1 file per index.
        elif [ $count -eq 1 ]; then
            #echo "    index $index OK: ${list[0]}"
            all_ok=true

        # Duplicate case.
        elif [ $count -gt 0 ]; then
            echo "    $index prefix: $count duplicate files:"
            for f in "${list[@]}"; do
                echo "      $f"
            done
        fi
    done

    # Summary message in case no errors.
    if $all_ok; then
        echo "    All OK."
    fi

done< <(find "$PROJECT_DIR" -mindepth 1 -type d -print0)

```

---

### Post by Marcus Aurelius on 2013-03-28
> **schragge said:**
> Well, I guess something like what **trent.josephsen** suggested can also be done with [rename]("http://manpages.ubuntu.com/manpages/precise/en/man1/prename.1.html") command alone as it is actually a perl script:
```

[COLOR=green]$[/COLOR] ls
[COLOR=#008000]001_Document0.pdf  004_Document3.pdf  006_Document6.pdf  009_Document9.pdf
002_Document1.pdf  004_Document4.pdf  007_Document7.pdf  010_Document10.pdf
003_Document2.pdf  005_Document5.pdf  008_Document8.pdf
$[/COLOR] rename -v[COLOR=#ff0000]n[/COLOR] 's/^\d{3}/sprintf("%03d",$&+1)/e if substr($_,0,3)>4' *
[COLOR=#008000]005_Document5.pdf renamed as 006_Document5.pdf
006_Document6.pdf renamed as 007_Document6.pdf
007_Document7.pdf renamed as 008_Document7.pdf
008_Document8.pdf renamed as 009_Document8.pdf
009_Document9.pdf renamed as 010_Document9.pdf
010_Document10.pdf renamed as 011_Document10.pdf[/COLOR]

```



OK,  thank you to all for all the input.
I tried so far:
#1: I set up some test files in a new directory, heres the original ls: #015-023 and #017 are the duplicates (see no # 018).

$ ls
015_-_Test_File_#34_-_September-28-2011-side-1.pdf  020_-_Test_File_#34_-_September-30-2011.pdf
016_-_Test_File_#34_-_September-28-2011-side-2.pdf  021_-_Test_File_#34_-_October-1-2011.pdf
017_-_Test_File_#34_-_September-28-2011-side-3.pdf  022_-_Test_File_#34_-_October-1-2011-side-2.pdf
017_-_Test_File_#34_-_September-29-2011.pdf         023_-_Test_File_#34_-_October-1-2011-side-3.pdf
019_-_Test_File_#34_-_September-29-2011-side-1.pdf


If I run the following using # 019, I get an illegal octal digit error:

$ rename -vn 's/^\d{3}/sprintf("%03d",$&+1)/e if substr($_,0,3)>019' *
Illegal octal digit '9' at (eval 1) line 1, at end of line


AGAIN:
If instead of # 019 like above, I choose #017, this is the output.  However, if I look at line 016 it renames to 017.  Shouldn't the numbers higher than 017 be the only ones that changed?

$ rename -vn 's/^\d{3}/sprintf("%03d",$&+1)/e if substr($_,0,3)>017' *
016_-_Test_File_#34_-_September-28-2011-side-2.pdf renamed as 017_-_Test_File_#34_-_September-28-2011-side-2.pdf
017_-_Test_File_#34_-_September-28-2011-side-3.pdf renamed as 018_-_Test_File_#34_-_September-28-2011-side-3.pdf
017_-_Test_File_#34_-_September-29-2011.pdf renamed as 018_-_Test_File_#34_-_September-29-2011.pdf
019_-_Test_File_#34_-_September-29-2011-side-1.pdf renamed as 020_-_Test_File_#34_-_September-29-2011-side-1.pdf
020_-_Test_File_#34_-_September-30-2011.pdf renamed as 021_-_Test_File_#34_-_September-30-2011.pdf
021_-_Test_File_#34_-_October-1-2011.pdf renamed as 022_-_Test_File_#34_-_October-1-2011.pdf
022_-_Test_File_#34_-_October-1-2011-side-2.pdf renamed as 023_-_Test_File_#34_-_October-1-2011-side-2.pdf
023_-_Test_File_#34_-_October-1-2011-side-3.pdf renamed as 024_-_Test_File_#34_-_October-1-2011-side-3.pdf


I appreciate all the info so far.

---

### Post by ofnuts on 2013-03-29
Don't use '019' but '19'. When you write '019' it is assumesd to be a number in octal notation (in which '9' isn't a valid digit)....

May I point out that the code by my esteemed co-posters requires you to first spot any duplicates, while my suggestion can be applied blindly?

---

### Post by schragge on 2013-03-29
+1 to **ofnuts** on both accounts. Applying his solution to the test case from my previous post:
```

[COLOR=green]$[/COLOR] c=0;for f in *;{ printf -vn "%03d${f#???}" $((++c));[[ $f != $n ]]&&echo "$f -> $n";}
[COLOR=green]004_Document4.pdf -> 005_Document4.pdf
005_Document5.pdf -> 006_Document5.pdf
006_Document6.pdf -> 007_Document6.pdf
007_Document7.pdf -> 008_Document7.pdf
008_Document8.pdf -> 009_Document8.pdf
009_Document9.pdf -> 010_Document9.pdf
010_Document10.pdf -> 011_Document10.pdf[/COLOR]

```

---

### Post by steeldriver on 2013-03-29
^^^ that's almost exactly what I came up with as well, but since the OP mentioned regexs I wondered if it would be worth adding a regex check on the 3 digit prefix, something like

```
i=0; for file in *.pdf; do [COLOR=#0000ff]if [[ "$file" =~ ^[0-9]{3}.* ]]; then[/COLOR] printf -v newfile "%03d%s" $((i++)) "${file:3}"; echo mv "$file" "$newfile"; fi; done
```

---

### Post by Marcus Aurelius on 2013-03-29
> **ofnuts said:**
> Don't use '019' but '19'. When you write '019' it is assumesd to be a number in octal notation (in which '9' isn't a valid digit)....

May I point out that the code by my esteemed co-posters requires you to first spot any duplicates, while my suggestion can be applied blindly?



OK, thank you, that worked.  I also see the wisdom of using your program as it reorders from start to finish, thanks for pointing that out.  I'm very new to any programming so I started with the easiest to read.  I have a question about reading your code:

count=$(( $count + 1 ))
I understand increments and saves count...then:

count0="000$count"
What's here, count0 is assigned 0001?

renumbered="${count0: -3}_${file#???_}"
THEN, get a little mixed up.  Takes file number whatever say 256_ (puts in $)....then count0 (or 0001): -3 ...this lost me
so what is ${count0: -3} saying exactly?

[[ "$file" != "$renumbered" ]] && [COLOR=#ff0000]echo[/COLOR] mv -v "$file" "$renumbered"
I think I understand this: (& finally pop out the echo when test succeeds)

OK, other than my lack of coding knowledge I think you found the best solution to my issue.  
Thanks again.

---

### Post by schragge on 2013-03-29
*$count0* just pads *$count* on the left with *000*, then *${count0: -3}* takes only the three rightmost characters of it. That gives

[TABLE="width: 380, align: center, class: grid"]
[TR][TD]**$count**[/TD][TD]**$count0**[/TD][TD]**${count0: -3}**[/TD][/TR]
[TR][TD]1[/TD][TD]0001[/TD][TD]001[/TD][/TR]
[TR][TD]23[/TD][TD]00023[/TD][TD]023[/TD][/TR]
[TR][TD]456[/TD][TD]000456[/TD][TD]456[/TD][/TR]
[/TABLE]

---

### Post by Marcus Aurelius on 2013-03-29
Thank you very much, and I completely understand now.

---

### Post by Vaphell on 2013-03-30
about that zero forcing octal system where 9 is illegal: you can easily circumvent that issue and force decimal system

```
$ x=019
$ printf "%03d\n" $(( x+5 ))  # pad with 0s to 3digits
bash: 019: value too great for base (error token is "019")
$ printf "%03d\n" $(( **10#**$x+5 ))
024
```

---

### Post by Marcus Aurelius on 2013-04-03
.........Since the upgrade of the forum there's still a problem with the option  to mark the threads as solved in the Thread Tools combo. The workaround  is to edit the thread Title and inserting [SOLVED] at the beginning of  it............

I've been trying to close this thread.  I do not have the ability to do this in thread tools or in go advanced.

---

