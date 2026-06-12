---
title: "How do I print text off a file?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by hardysummer on 2008-08-18
I want to print a section off a text file.  From the line that starts with "# START" to the line that ends with "# END"

Like what the command "cat" does, but instead of the entire text file, I only want a part of it.

---

### Post by Sorivenul on 2008-08-18
Do you want to print it to stdout/terminal/console or to a separate file?  Knowing this would help.

In short, cat FILENAME will display the full contents of a text file on your terminal/console.  For longer files this would be best done throught an extension like "less".

Regualar Expressions may also be of help, but my experience there is fairly limited.

---

### Post by forger on 2008-08-18
This should probably be in programming talk :)

I modified a perl script I'm using to fit your needs:
```
perl -e '
my $file = "yourfilename.txt";
my ($start,$end) = (0,0);
open FILE, $file or die $!;
foreach my $row (<FILE>) {
 if ($row =~ m/^# START/i) { $start = 1; $end = 0; next; } #Reached START section, jump to the next line, start printing
 elsif ($row =~ m/^# END/i) { $end = 1; $start = 0; } #Reached END section
 if (($start == 1) && ($end == 0)) { print "$row"; }
}
'

```

:KS Change **yourfilename.txt** with the file you want
:KS Don't forget the parenthesis and single quote at the end
Note that it can be used for multiple sections of # START / # END ;)

---

### Post by Malta paul on 2008-08-18
Left click on the text you want, which will now be highlighted, Now right click the highlighted area, select copy, now open your word processor and past in.
:)

---

### Post by prshah on 2008-08-18
> **hardysummer said:**
> I want to print a section off a text file.  From the line that starts with "# START" to the line that ends with "# END"
Like what the command "cat" does, but instead of the entire text file, I only want a part of it.

```
cat textfile | grep -i -A 9999 "# START" | grep -i -B 9999 "# END"
```, but this is assuming the total size of the file is less than 10,000 lines.

---

### Post by sisco311 on 2008-08-18
```
awk '/#START/,/#END/' filename
```

---

