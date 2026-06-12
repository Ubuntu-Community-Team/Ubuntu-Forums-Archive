---
title: "changing word's position in file"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by daniel3ub on 2008-10-24
Hi, people.

I have a large txt file composed of quotes and their authors, but I need to change the position of the author's name.

So, every quote is in this format:
> (tab)Nobody likes me
Author: Tolstoy , Leon (4 spaces)

And I need them to be like this:
> Nobody likes me.
Leon Tolstoy

The various quotes are placed just one after another, with just a simple carriage return between them (ie, no blank line, nothing).
I need to:
. remove the TAB before the quote
. put a period after the quote
. remove the "Author: "
. change the names' position
. remove the 4 spaces from after the name

I apologize if I don't know how to do this, but I've already tryied to learn SED but it's beyond my brain capacity... :(

Thanks a lot!

---

### Post by MusicMastaMike on 2008-10-24
Here's how you can do it in perl (you might have to adapt a little bit if the spacing is off):

```
my $in_file = "test.txt";
my $out_file = "test_out.txt";

my $str;
open (INPUT, $in_file) or die "can't open $in_file: $!";
while (<INPUT>) {
	$str = $str . $_;
}
close (INPUT);

$str =~ s/\t(.+?\s+?)Author:\s(.\w+?)\s,\s(\w+?)\s{4}/$1\n$3 $2/sg;

open (OUTPUT, ">$out_file") or die "can't open $out_file: $!";
print OUTPUT $str;
close (OUTPUT);
```

---

### Post by andrew.46 on 2008-10-25
Hi,

I can't quite get it with a purely sed usage:

```
cat file | sed -e 's/$/\./g' -e 's/^\t//g' \
-e 's/ \{4\}\.$//g' -e 's/Author: //g' \
-e  's/ ,//g'
```

But this does not transpose the final names and the business with the full stops is a bit ugly :-). I would love to see a purely sed version that reverses these names. Anyone?

  Andrew

---

### Post by andrew.46 on 2008-10-26
Hi,

OK so I got a little direction from comp.unix.shell concerning the ttransformation of names and the final purely sed solution is as follows:

```
   cat in_file | \
   sed -e 's/$/\./g' -e 's/^\t//g' \
       -e 's/ \{4\}\.$//g' \
       -e 's/Author: \([a-zA-Z]*\) , \([a-zA-Z]*\)/\2 \1/g' \
       > out_file
```

I love sed when it works so well :-).

  Andrew

---

### Post by nick_h on 2008-10-26
You might find it easier to use awk rather than sed.  Try the following:
```
awk '/^\t/ {sub("\t",""); print $0 "."}
     /Author:/ {print $4 " " $2}' input.txt > output.txt
```

---

