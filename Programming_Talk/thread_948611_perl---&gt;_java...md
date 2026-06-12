---
title: "perl---&gt; java.."
date: 2008-10-15
forum: Programming Talk
---

### Post by wzwz123456 on 2008-10-15
can any one convert the below perl code to java...

open(AGE, $readf) || die "$readf.\n";

while (my $line = <AGE>)
{
  chomp($line);
  my @array = split(/\s+/, $line);
  my $index = $array[Pindex];
  my $value = $array[Kindex];
}

---

### Post by geirha on 2008-10-15
I can give you some tips. Use the [Scanner](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html) class to read lines using the nextLine() method.

[String](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html)s have some split methods that can split on regexes.

---

