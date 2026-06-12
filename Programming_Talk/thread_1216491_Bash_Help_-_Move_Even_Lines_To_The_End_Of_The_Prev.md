---
title: "Bash Help - Move Even Lines To The End Of The Previous Line"
date: 2009-07-18
forum: Programming Talk
---

### Post by switchrodeo720 on 2009-07-18
I have a list of items, in this case it's artist followed by album name, that I would like to reformat. Here's the sample list:

```
Eminem
- Relapse
Maino
- If Tomorrow Comes...
Ace Hood
- Ruthless
The Alchemist
- Chemical Warfare
Rick Ross
- Deeper Than Rap
Busta Rhymes
- Back On My B.S.
Mos Def
- The Ecstatic
Method Man & Redman
- Blackout! 2
Jadakiss
- The Last Kiss
Lil Wayne
- Tha Carter III
```

I would like to figure out a way of moving the album names up to the previous line like so:

```
Eminem - Relapse
Maino - If Tomorrow Comes...
Ace Hood - Ruthless
The Alchemist - Chemical Warfare
Rick Ross - Deeper Than Rap
Busta Rhymes - Back On My B.S.
Mos Def - The Ecstatic
Method Man & Redman - Blackout! 2
Jadakiss - The Last Kiss
Lil Wayne - Tha Carter III

```

I'm not sure where to start. Is it possible to use sed or something similar?

Thanks in advance.

---

### Post by hetx on 2009-07-18
Smells like a job for Awk... Wish I knew Awk...

If you got the energy for it
[http://www.gnu.org/software/gawk/manual/html_node/index.html](http://www.gnu.org/software/gawk/manual/html_node/index.html)
GNU AWK Guide =)

---

### Post by smartbei on 2009-07-18
Here it is in python:
[php]
#! /usr/bin/python
import sys
import os

if __name__ == "__main__":
    if len(sys.argv) < 2:
        print "Usage: %s <input file>" % (sys.argv[0],)
    else:
        lines = file(sys.argv[1], 'r').read().splitlines()
        if len(lines) % 2 != 0:
            raise ValueError("The file has an odd number of lines")
        lines = [lines[i] + lines[i + 1] for i in xrange(0, len(lines), 2)]
        file(sys.argv[1] + '.out', 'w').write(os.linesep.join(lines))
[/php]
Stick that in a file and chmod +x.

---

### Post by switchrodeo720 on 2009-07-18
smartbei,

That works perfectly. I don't know python. Instead of the output being redirected to file.out, how would I make it go to STDOUT? I want to know because I'm using this in the middle of a bash script that I'm working on.

---

### Post by smartbei on 2009-07-18
You can change this line:
```

file(sys.argv[1] + '.out', 'w').write(os.linesep.join(lines))  

```
To:
```

print os.linesep.join(lines)

```
And that should work :-)
Glad to help.
 

BTW - if this is indeed in the middle of a bash script, then it might be nicer to do it in bash as well, but I don't know bash either.

---

### Post by switchrodeo720 on 2009-07-18
That solution again works as you said.

I agree that writing a solution for this using bash tools would be ideal. I'm fairly new to programming/scripting and have chosen to start out with shell scripting. I've searched for quite a while over the past two days looking for a way to do this using sed and awk, but haven't been able to crack it.

This may be out in left field but, can you embed python language within a bash script? This would solve my problem of having to call this python code from an external location from within the script.

---

### Post by kaibob on 2009-07-18
I agree that awk is probably the best solution, and I'm sure ghostdog74 will have a 1-liner up here in no time. I'm new and came up with the following, but it's a real kludge that creates unnecessary text files. It does work, though, and has that going for it. 

```
grep - -v file > 1 ; grep - file > 2 ; paste -d ' ' 1 2 > newfile
```

---

### Post by stroyan on 2009-07-18
Here is a one-liner using awk and a one-liner using bash.
```

awk '/^-/{print P,$0} /^[^-]/{P=$0}' datafile
while read L; do case "$L" in -*) echo "$P $L" ;; *) P="$L" ;; esac; done < datafile

```

Those both assume your data is in a file named "datafile".
Both of those use a pattern match to find lines that start with "-".
If a line does not start with "-" it is assigned to variable "P".
When a line starts with "-" emit the previous value of "P" and the current line.

If you know that you just want to join odd and even lines you could use one of these-
```

awk '{ALBUM=$0;getline;ARTIST=$0;print ALBUM,ARTIST}' datafile
while read ALBUM && read ARTIST; do echo "$ALBUM $ARTIST"; done < datafile

```

---

### Post by switchrodeo720 on 2009-07-18
To everyone who posted on this thread,

I'd like to say thanks. Even though I ended up choosing the solution presented by stroyan, I learned several ways of accomplishing my task. You'll see which option I went with below. I decided to share the finished code for everyone as well.

This script parses the top 10 rap albums from Billboard.com. I'm just new to programming as a hobby, and bash is my first language. I know this type of project is better handled by perl, but I wanted to see if it could be done in bash.

```

curl -s --user-agent "Mozilla/4.0" --anyauth "http://www.billboard.com/bbcom/charts/chart_display.jsp?g=Albums&f=Top+Rap+Albums" | \
sed "s/[\<]/\n\</g" | \
grep -E "green2|cbbTable_link" | \
sed "s/\<a.*green2//g" | \
sed "s/[\"]//g" | \
sed "s/\<a.*_link\>/ - /g" | \
sed "s/[\<\>]//g" | \
sed "s/\&amp\;/\&/g" | \
sed 1,2d | \
while read L; do case "$L" in -*) echo "$P $L" ;; *) P="$L" ;; esac; done
```

I wanted to create this list for use with conky on my desktop. It's now opening my imagination to other uses in conjunction with applications like flexget.

Let me know if anyone else finds this useful or if anyone has any feedback.

Oh yeah...how do I mark this thread solved?

---

### Post by SecretCode on 2009-07-18
You need a Perl solution too. :)

Do you always have "- " at the beginning of the album name lines? If so, this looks like a simple regular expression job. 
```
perl -e '$a = join "", <>; $a =~ s/\n- / - /g; print $a;' < musiclist
```
or as a program file
```
#!/usr/bin/perl

$a = join "", <>;
$a =~ s/\n- / - /g;
print $a;
```

---

### Post by kaibob on 2009-07-18
stroyan,

Good post. I was impressed by the second bash solution--it's surprising how simple things can be when you know what you're doing. 

kaibob

---

### Post by ghostdog74 on 2009-07-18
just awk

```

 # awk 'ORS=(/^-/)?"\n":" "' file
Eminem - Relapse
Maino - If Tomorrow Comes...
Ace Hood - Ruthless
The Alchemist - Chemical Warfare
Rick Ross - Deeper Than Rap
Busta Rhymes - Back On My B.S.
Mos Def - The Ecstatic
Method Man & Redman - Blackout! 2
Jadakiss - The Last Kiss
Lil Wayne - Tha Carter III

```

---

