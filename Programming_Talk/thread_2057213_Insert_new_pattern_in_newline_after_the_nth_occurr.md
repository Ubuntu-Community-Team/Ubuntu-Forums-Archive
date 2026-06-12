---
title: "Insert new pattern in newline after the nth occurrence of a line pattern - Bash in Ub"
date: 2012-09-13
forum: Programming Talk
---

### Post by Phil3759 on 2012-09-13
Hi,

I am getting crazy after days on looking at it:
Bash in Ubuntu 12.04.1

I want to do this:
pattern="system /path1/file1 file1"
new_pattern="    data /path2/file2 file2"
file to edit: data.db

 - I need to search in the file data.db for the **nth** occurrence of pattern
 - pattern must match a complete line
 - insert **after** pattern a **new line** with new_pattern

Sed in my installed Ubuntu does not seem to accept /c or /a commands, only -i !!

So, I tried this:
```

sed "s%system /path1/file1 file1%&\n    data /path2/file2 file2%" -i data.db

```

Which works except:
 1- all occurrences of pattern will be replaced in data.db, not only the nth one
 2- pattern will be matched even if it is not ending with a new line

So, tried to add \n at end of pattern to fix issue 2:
```

sed "s%system /path1/file1 file1\n%&\n    data /path2/file2 file2%" -i data.db

```

Result is pattern will not be replaced at all

and to fix issue 1, I tried the following with and without the -i:
```

sed "0,%system /path1/file1 file1%s%system /path1/file1 file1%&\n    data /path2/file2 file2%" [-i] data.db

```

No output error, but pattern is not matched

Any help please even if it is with another command
Difficulty seems to be caused by the / and spaces in my patterns!

---

### Post by steeldriver on 2012-09-13
I think your main problem is that the sed 's/pattern/replacement/n' is meant to replace the nth occurrence within a single line

You might want to try 'awk' instead, something like

```
awk 'BEGIN {n=0;OFS="\n"}; /system \/path1\/file1 file1$/ {n=n+1;}; {if (n==7) print "data /path2/file2 file2", "new pattern"; else print $0;}' data.db
```(I'm not good with awk so don't treat that as gospel)

---

### Post by Phil3759 on 2012-09-13
Thank you for the trial,

I was finally advised with awk in another forum

```

awk 'which!=n&&$0~"^[ \t]*"patt"[ \t]*$"{which++;if(which==n)$0=$0 RS repl}1' patt="$pattern" repl="$new_pattern" n=$n data.db
```

This is one of the most complex commands I feel

---

### Post by Vaphell on 2012-09-13
naah, in general it's very similar to steeldriver's idea. Looks more convoluted that it really is because the author apparently had something against readability ;-)

if which (occurence counter) !=n and record (line) matches '(optional whitespace)patt(optional whitespace)':
- add 1 to which
- if which==n:  record='recordRSrepl' (RS being \n by default)

---

### Post by steeldriver on 2012-09-13
actually for the record I realized I bracketed the expression incorrectly - the regex match should apply to the WHOLE expression, more like

```
awk 'BEGIN {n=0;OFS="\n"}; /system \/path1\/file1 file1$/ **[COLOR=Red]{[/COLOR]**n=n+1; if (n==7) print "data /path2/file2 file2", "new pattern"; else print; next**[COLOR=Red]}[/COLOR]** {print}' data.db
```otherwise it continues to print the replacement text until the (n+1)th occurrence of the match

---

### Post by Phil3759 on 2012-09-13
Thank you both for the explanations

---

### Post by steeldriver on 2012-09-13
OK for the terminal sed-heads:

```
sed -e :a -e '$!{N;ba};s#system /path1/file1 file1\n#data /path2/file2 file2\nnew pattern\n#4' data.db
```replaces / appends to the 4th occurrence using the 's/pattern/replacement/n' syntax as per the OP

If doing it interactively it could be made more efficient by simply branching to quit after a successful match (so that only the lines up to and including the match are buffered instead of the whole file)

```
sed -i -e :a -e '$!{N;s#system /path1/file1 file1\n#data /path2/file2 file2\nnew pattern\n#4;t;ba};q' data.db
```

:popcorn:

---

### Post by Some Penguin on 2012-09-15
For a non-one-liner (shudder...), something like

```

#!/bin/perl -w
use strict;
use Symbol;

(scalar(@ARGV)== 3) || die "Usage:  $0 <N> <literal1> <literal2>\n; input is STDIN, output is STDOUT.\n";

my $N    = shift @ARGV;
my $literal1 = shift @ARGV;
my $literal2 = shift @ARGV;

my $seen = 0;
my $line = undef;
my $keep_reading = 0;

# Streaming input so we can handle e.g. a 20GB file easily.
while ($line = <STDIN>) {
    # Note that the above preserves the trailing newline.
    #
    # ^, $ = whole line match
    # \s* : be tolerant of leading whitespace
    # \Q,\E:  so that we can safely include pattern metachars
    #   in literal.
    # /o : compile once and reuse the compiled state machine
    # Perl does lazy-eval of boolean exp so ++$seen will not
    # increment if match fails
    if (($line =~ /^(\s*)\Q$literal1\E(\s*)$/o) && (++$seen == $N)) {
       # $1 from first capturing group -- leading whitespace so we preserve tabs et al
       # $2 from second capturing group -- for trailing whitespace; it will have the trailing newline, if any
       print $1, $literal2, $2;
       $keep_reading = 1;
       last;
    } else {
       print $line;
    }
}

if ($keep_reading) {
  # Read and write rest of file; no sense parsing for matches
  while ($line = <STDIN>) {
     print $line;
  }
}

exit 0;

```

That's significantly longer than any one-liner, of course, but it also provides a framework for potentially more complex substitutions (like where the substituted expression actually depends upon the line being edited, say; it would be simple to modify the above to handle <any file> instead of a specific 'file1', for instance -- treat literal1 and literal2 as regex strings that you DON'T quote (and thus requiring the caller to explicitly escape characters where appropriate, which is why I didn't write it that way), and use the substitution operator instead of just concatenating the leading whitespace, $literal2, and the trailing whitespace.

It also ignores character set variations, heh.

---

### Post by Phil3759 on 2012-10-09
Big thanks for all your suggestions

---

