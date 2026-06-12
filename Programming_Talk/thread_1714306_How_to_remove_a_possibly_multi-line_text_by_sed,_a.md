---
title: "How to remove a possibly multi-line text by sed, awk or perl?"
date: 2011-03-25
forum: Programming Talk
---

### Post by mahy on 2011-03-25
Hello people,

I'm struggling with this kind of a task and can't possibly find any help anywhere on the Web: I'd like to remove all text delimited by ####. That text can span multiple lines and delimiters occur multiple times in my file. In short, it has to be:

1.) multi-line regex
2.) lazy regex (otherwise it removes almost the entire file)

(Step two would be to modify the text instead of deleting it, but that's not so important ATM.)

Allowed tools are sed, awk and perl, in this order of succession. If you come up with an even better idea/tool, I won't fuss! Guys, please, help me out if you can, I really can't sort this out. TIA.

---

### Post by slavik on 2011-03-25
sample of text?

delimited by $anything means that $anything is a separator of sorts. having a csv file and removing text delimited by commas, means wiping out the file.

what are you trying to accomplish?

---

### Post by shawnhcorey on 2011-03-25
How big is the file?  If it's small, use Perl to slurp the whole thing and use a multi-line regexp.

```
my $file = 'my_file.txt';
my $lines = '';
{
  local $/;
  open my $in_fh, '<', $file or die "could not open $file: $!\n";
  $lines = <$in_fh>;
  close $fh_in;
}

$lines =~ s{ \#\#\#\# .*? \#\#\#\# }{}gmsx;

```

See:

perldoc perlvar and search for /INPUT_RECORD_SEPARATOR/

---

### Post by gmargo on 2011-03-25
It would help if you would give an example of the input, so we don't have to guess.  Here's what I guessed and how **sed(1)** could work:
```

$ cat foo
line 1
####
line 2
####
line 3
line 4
line 5
####
line 6
line 7
line 8
####
line 9

$ sed '/####/,/####/d' < foo
line 1
line 3
line 4
line 5
line 9

```

---

