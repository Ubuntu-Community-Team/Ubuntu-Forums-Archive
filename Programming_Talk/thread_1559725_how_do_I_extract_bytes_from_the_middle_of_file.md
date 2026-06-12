---
title: "how do I extract bytes from the middle of file"
date: 2010-08-23
forum: Programming Talk
---

### Post by monkeyking on 2010-08-23
How can I using commandline tools extract specific bytes, and byte ranges in the middle of file.

I know I can use 
[PHP]
head -c END_OF_RANGE file.bin |tail -c BYTES_TO_GET
[/PHP]

But for huge files, this takes forever,
I'm looking for something like the fseek.

Thanks in advance

---

### Post by saulgoode on 2010-08-24
[Tcl]("http://www.tcl.tk/man/tcl/tutorial/Tcl0.html") provides a very simple solution:
```
tclsh <<'EOF'
set start_of_range 991000
set bytes_to_get 40
set f [open /home/monkeyking/somefile.txt]
seek $f $start_of_range
set data [read $f $bytes_to_get]
puts $data
close $f
exit
EOF

```

The nice thing about Tcl is that the syntax is quite similar to BASH (commands within square brackets are akin to using backticks in BASH) and man pages are available for all of the commands (Ubuntu may not include them by default, though).

---

### Post by stylishpants on 2010-08-24
Perl provides both buffered and unbuffered versions of this (seek/read vs. sysseek/sysread).

This works fine on an opened file, but it doesn't seem to be able to seek on STDIN directly.

```
$ echo "012345678" > file

# skip past the first 4 bytes(0-4), then print the next 4 bytes (4-7)
$ perl -e 'open(FH, $ARGV[0]) or die($!); seek(FH,4,0) or die ($!); read(FH,$_,4); print'  file
4567 

# Even shorter in ruby...
$ ruby -e 'ARGF.seek(4); print ARGF.read(4)' file
4567


```

---

### Post by Some Penguin on 2010-08-24
> **stylishpants said:**
> Perl provides both buffered and unbuffered versions of this (seek/read vs. sysseek/sysread).

This works fine on an opened file, but it doesn't seem to be able to seek on STDIN directly.


Not surprising.  Seeking on STDIN doesn't make much sense; to do it faster than reading and counting would require time travel and perfect knowledge of when bytes would arrive.

---

### Post by ghostdog74 on 2010-08-24
> **monkeyking said:**
> How can I using commandline tools extract specific bytes, and byte ranges in the middle of file.

I know I can use 
[PHP]
head -c END_OF_RANGE file.bin |tail -c BYTES_TO_GET
[/PHP]

But for huge files, this takes forever,
I'm looking for something like the fseek.

Thanks in advance

first get the byte count
```

wc -c <file

```

next divide by half 
```

bytes=$(wc -c <file)
half=$((bytes/2))

```

then ```
 head -c $half |tail -1
```

---

