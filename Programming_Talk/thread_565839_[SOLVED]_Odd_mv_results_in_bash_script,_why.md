---
title: "[SOLVED] Odd mv results in bash script, why ?"
date: 2007-10-02
forum: Programming Talk
---

### Post by arsenic23 on 2007-10-02
Ok I was trying to write a script to rename a set of files and since Ubuntu's rename command wasn't going to cut it this time I was using a for loop in bash.  

I had the script set up where I thought it should be correct, but I was getting "*mv: invalid option -- \*" errors.

So I changed the script to echo the mv command to see if I'd messed up part of my sed.  For some reason, though, the echo'd mv commands where valid and worked when I copy and pasted them into the terminal.

Here's what I was doing:

**[COLOR="DarkRed"]Directory:[/COLOR]**
> [Ureshii] Dennou Coil - 01 v2 [1280x720-H264-AAC] [EE5C7065].mkv
[Ureshii] Dennou Coil - 02 [1280x720-H264-AAC] [260D682D].mkv
[Ureshii] Dennou Coil - 03 [1280x720-H264-AAC] [3F761B9E].mkv
[Ureshii] Dennou Coil - 04 [1280x720-H264-AAC] [37B60EA0].mkv
[Ureshii] Dennou Coil - 05 [1280x720-H264-AAC] [C8D044EA].mkv
[Ureshii] Dennou Coil - 06 [1280x720-H264-AAC] [0D3FAA94]v2.mkv
[Ureshii] Dennou Coil - 07 [1280x720-H264-AAC] [DDA0D73F].mkv

**[COLOR="#8b0000"]Code that was erroring:[/COLOR]**
```
for a in *.mkv; do 
mv `echo $a | sed -e 's/\ /\\\ /g' -e 's/\[/\\\[/g' -e 's/\]/\\\]/g'` `echo $a | sed -e 's/\(\[[^]]*\]\)\([^[\.]*\)/\2\1/' -e 's/^\ //' -e 's/\]\ \[/\]\[/' -e 's/\ /\\\ /g' -e 's/\[/\\\[/g' -e 's/\]/\\\]/g'`; 
done
```

[COLOR="#8b0000"]**Code that outputs the working commands:**[/COLOR]
```
for a in *.mkv; do 
echo "mv `echo $a | sed -e 's/\ /\\\ /g' -e 's/\[/\\\[/g' -e 's/\]/\\\]/g'` `echo $a | sed -e 's/\(\[[^]]*\]\)\([^[\.]*\)/\2\1/' -e 's/^\ //' -e 's/\]\ \[/\]\[/' -e 's/\ /\\\ /g' -e 's/\[/\\\[/g' -e 's/\]/\\\]/g'`"; 
done
```

**[COLOR="#8b0000"]The working commands:[/COLOR]**
> mv \[Ureshii\]\ Dennou\ Coil\ -\ 01\ v2\ \[1280x720-H264-AAC\]\ \[EE5C7065\].mkv Dennou\ Coil\ -\ 01\ v2\ \[Ureshii\]\[1280x720-H264-AAC\]\[EE5C7065\].mkv
mv \[Ureshii\]\ Dennou\ Coil\ -\ 02\ \[1280x720-H264-AAC\]\ \[260D682D\].mkv Dennou\ Coil\ -\ 02\ \[Ureshii\]\[1280x720-H264-AAC\]\[260D682D\].mkv
mv \[Ureshii\]\ Dennou\ Coil\ -\ 03\ \[1280x720-H264-AAC\]\ \[3F761B9E\].mkv Dennou\ Coil\ -\ 03\ \[Ureshii\]\[1280x720-H264-AAC\]\[3F761B9E\].mkv
mv \[Ureshii\]\ Dennou\ Coil\ -\ 04\ \[1280x720-H264-AAC\]\ \[37B60EA0\].mkv Dennou\ Coil\ -\ 04\ \[Ureshii\]\[1280x720-H264-AAC\]\[37B60EA0\].mkv
mv \[Ureshii\]\ Dennou\ Coil\ -\ 05\ \[1280x720-H264-AAC\]\ \[C8D044EA\].mkv Dennou\ Coil\ -\ 05\ \[Ureshii\]\[1280x720-H264-AAC\]\[C8D044EA\].mkv
mv \[Ureshii\]\ Dennou\ Coil\ -\ 06\ \[1280x720-H264-AAC\]\ \[0D3FAA94\]v2.mkv Dennou\ Coil\ -\ 06\ \[Ureshii\]\[1280x720-H264-AAC\]\[0D3FAA94\]v2.mkv
mv \[Ureshii\]\ Dennou\ Coil\ -\ 07\ \[1280x720-H264-AAC\]\ \[DDA0D73F\].mkv Dennou\ Coil\ -\ 07\ \[Ureshii\]\[1280x720-H264-AAC\]\[DDA0D73F\].mkv


[COLOR="#8b0000"]**The resulting directory:**[/COLOR]
> Dennou Coil - 01 v2 [Ureshii][1280x720-H264-AAC][EE5C7065].mkv
Dennou Coil - 02 [Ureshii][1280x720-H264-AAC][260D682D].mkv
Dennou Coil - 03 [Ureshii][1280x720-H264-AAC][3F761B9E].mkv
Dennou Coil - 04 [Ureshii][1280x720-H264-AAC][37B60EA0].mkv
Dennou Coil - 05 [Ureshii][1280x720-H264-AAC][C8D044EA].mkv
Dennou Coil - 06 [Ureshii][1280x720-H264-AAC][0D3FAA94]v2.mkv
Dennou Coil - 07 [Ureshii][1280x720-H264-AAC][DDA0D73F].mkv


If anyone could explain these results to me it would really help with my bash education.

---

### Post by Arndt on 2007-10-03
> **arsenic23 said:**
> Ok I was trying to write a script to rename a set of files and since Ubuntu's rename command wasn't going to cut it this time I was using a for loop in bash.  

I had the script set up where I thought it should be correct, but I was getting "*mv: invalid option -- \*" errors.

So I changed the script to echo the mv command to see if I'd messed up part of my sed.  For some reason, though, the echo'd mv commands where valid and worked when I copy and pasted them into the terminal.

Here's what I was doing:

**[COLOR="DarkRed"]Directory:[/COLOR]**


**[COLOR="#8b0000"]Code that was erroring:[/COLOR]**
```
for a in *.mkv; do 
mv `echo $a | sed -e 's/\ /\\\ /g' -e 's/\[/\\\[/g' -e 's/\]/\\\]/g'` `echo $a | sed -e 's/\(\[[^]]*\]\)\([^[\.]*\)/\2\1/' -e 's/^\ //' -e 's/\]\ \[/\]\[/' -e 's/\ /\\\ /g' -e 's/\[/\\\[/g' -e 's/\]/\\\]/g'`; 
done
```

[COLOR="#8b0000"]**Code that outputs the working commands:**[/COLOR]
```
for a in *.mkv; do 
echo "mv `echo $a | sed -e 's/\ /\\\ /g' -e 's/\[/\\\[/g' -e 's/\]/\\\]/g'` `echo $a | sed -e 's/\(\[[^]]*\]\)\([^[\.]*\)/\2\1/' -e 's/^\ //' -e 's/\]\ \[/\]\[/' -e 's/\ /\\\ /g' -e 's/\[/\\\[/g' -e 's/\]/\\\]/g'`"; 
done
```

**[COLOR="#8b0000"]The working commands:[/COLOR]**


[COLOR="#8b0000"]**The resulting directory:**[/COLOR]


If anyone could explain these results to me it would really help with my bash education.

I think what's happening is that your sed commands produce a command line suitable for giving to the shell (which you confirmed by running them), but when giving the arguments directly to 'mv', the quoting character \ should not be there, and is taken by 'mv' to be part of the argument. So it sees ... -\ and thinks it's an option named \ and reports it, because there is no such option.

Either use the command 'eval' to run your command, or modify the command to not contain those quoting characters.

---

### Post by stylishpants on 2007-10-03
What's the problem with 'rename'?

You don't say exactly what you want, but you could produce the same output filenames with a shorter and slightly more readable 'rename' command:

```

rename 's/^([^ ]+) (\w+ \w+ - \d+( \w+)?) ([^ ]+) /$2 $1$4/' *.mkv

```

---

### Post by bulldog060 on 2007-10-03
i wrote a perl script a while back to do the same basic thing and keep my expressions clean and in order ... sorry it is not one of the one-liners people are throwing out above but if it is common for you to do bigger moves with alot of expressions this might be something you could get some use out of.
(it was tweaked slightly and tested with the initial examples)

```


#!/usr/bin/perl

my $dir = '/tmp/mkv';

my %replace_me = (
        # order => [ replace_what, replace_with ]
        '1' => ['\s+|\[|\]'    , '_'],    # space,[,] replaced with _
        '2' => ['_+'           , '_'],    # one or more _ replace with _
        '3' => ['_-_'          , '-'],    # _-_ replace with -
        '4' => ['^_'           , ''],     # leading _ removed
        '5' => ['_\.mkv'       , '.mkv'], # _.mkv replace with .mkv
    );

opendir(DIR,"$dir");
while ( my $orig_file = readdir(DIR) ) {
    # if the file does not end with .mkv skip it
    next if ( $orig_file !~ /\.mkv$/ );

    my $new_file = $orig_file;
    foreach my $seq ( sort keys %replace_me ) {
        $new_file =~ s/$replace_me{$seq}[0]/$replace_me{$seq}[1]/g;
    }

    print "Moving $orig_file\nTo     $new_file\n";

    # Correct way
    link("$dir/$orig_file","$dir/$new_file");
    unlink("$dir/$orig_file");
    
    # Or you could shell out

    # `mv "$dir/$orig_file" "$dir/$new_file"`;

}
closedir(DIR);


```

~ron

---

### Post by arsenic23 on 2007-10-03
> **stylishpants said:**
> What's the problem with 'rename'?

You don't say exactly what you want, but you could produce the same output filenames with a shorter and slightly more readable 'rename' command:

```

rename 's/^([^ ]+) (\w+ \w+ - \d+( \w+)?) ([^ ]+) /$2 $1$4/' *.mkv

```

Thanks for the pointer, but I don't undersand the regex in your rename command.  Mostly, I've never seen '\w' and '\d'.  I also don't understand why it doesn't do similar when ran as a sed command.  For instance:

```
i="[Ureshii] Dennou Coil - 01 v2 [1280x720-H264-AAC] [EE5C7065].mkv"; 
echo $i | sed 's/^([^ ]+) (\w+ \w+ - \d+( \w+)?) ([^ ]+) /$2 $1$4/'
```

does nothing.  Is there a difference between the way sed's 's/' and rename's 's/' work that I'm not familiar with?  Normally when rename fails to do what I expect it too I just attempt to make it work with a for loop and sed.

Thanks again, everyone.  As always you've all been a big help.

---

### Post by stylishpants on 2007-10-03
You're right, there is a difference between the regexps in sed and the ones in rename.

"rename" is just a short perl script.  The s/// command you provide it is just eval'd by perl directly.

Perl uses perl-compatible regular expressions, while sed uses POSIX regular expressions.  There are numerous small differences, but for the purposes of this particular regexp, the only important one is that perl-compatible regexps support \d and \w, while POSIX-compatible regexps do not.

\d just means any digit. 
\w means any alphanumeric character, or _.

For a reference to perl-compatible regexps, see 'man perlre'.

---

### Post by arsenic23 on 2007-10-04
That was very helpfull - thank you.

---

