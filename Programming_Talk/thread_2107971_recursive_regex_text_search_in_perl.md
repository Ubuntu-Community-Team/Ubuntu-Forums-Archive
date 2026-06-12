---
title: "recursive regex text search in perl"
date: 2013-01-23
forum: Programming Talk
---

### Post by Keiran230 on 2013-01-23
I'm looking for pointers from anyone who's been using perl for a while on how to do a recursive text search through a massive directory using perl and when searching for a regex, not a simple string (since grep -lR can just do that). Ideally it should be perl, since once it's effective enough at locating the files I'm looking for, I'll add functions which make it do something to the results. Which functions would you use for this?

Before I decided to try perl , I had a oneliner which I use for searching through (website) files, written in bash and awk. The first search is basically just a grep -lR which searches for a regex of things I'm looking for. The second search is basically a grep -R on it and shows the contents of the file too. The problem is, every time I add another set line to the giantic regex, awk becomes an order of magnitude slower at processing it. Perl is powerful when it comes to this kind of task when done correctly, but I work in awk/bash/java and the like, and have barely begun learning perl.

For the curious:
```
BAK=$IFS; IFS=$(echo -en "\n\b"); for i in `find . -type f -regex "**regex for file types I want to search**"`; do echo "$i :: `awk '**ten page regex goes here for what I'm looking for**' "$i" | head -1`"; done | awk -F '::' '$2 !~ /^ *$/ {print $1}'; for i in `find . -type f -name "**second set of file types I want to search**"`; do echo "$i :: `awk '**another gigantic regex of what I want to look for**`"; done | awk -F '::' '$2 !~ /^ *$/ {print $0}';  IFS=$BAK
```

---

### Post by Vaphell on 2013-01-23
don't expect miracles, complicated regexes are rather heavy
>  searching for a regex, not a simple string (since grep -lR can just do that)
what? grep does regexes just fine, you can even pick your favorite flavor

```

$ grep --help

  -E, --extended-regexp     PATTERN is an extended regular expression (ERE)
  -F, --fixed-strings       PATTERN is a set of newline-separated fixed strings
  -G, --basic-regexp        PATTERN is a basic regular expression (BRE)
  -P, --perl-regexp         PATTERN is a Perl regular expression
```

care to give more details? that bash is so ugly it's hard to describe ;-) oneliners are overrated, especially when they do anything remotely complicated

ten page regex? cheesus o.O :-)
compilation of regexes is rather complicated and your code has to do it for each file, which equals a lot of wasted time. Figure out a way to run a single command for all files at once, so once compiled regexes stay in memory and can be reused.

i'd try something like this
```
files=()
while read -rd $'\0' f
do
  files+=( "$f" )
done < <( find . -type f -iregex '<regex>' -print0 )

grep -P -f file_with_perl_regexes.txt "${files[@]}"

```

---

### Post by Keiran230 on 2013-03-21
Actually, that works, and I'm saving that example for later.

I'd have to benchmark grep -E against perl to know which is really faster between the two, but after finding out how awesome nawk is vs the default gawk found in most distributions, this isn't really necessary if you can modify the system.

Since it's in bash though, the only thing I have to worry about are bash's little quirks like the IFS variable and such. I can handle it.

---

