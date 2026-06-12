---
title: "Perl: Why (print) ?"
date: 2016-04-19
forum: Programming Talk
---

### Post by donsy on 2016-04-19
According to *Programming Perl*, the -p switch wraps the following code around your script:
```
LINE:
while(<>) {
    ... # script goes here
}
continue {
    (print) || die "-p destination: $!\n";
}

```Why the parentheses around the print statement? I thought the print statement always executed in list context anyway.

---

### Post by QDR06VV9 on 2016-04-19
Print is not actually a real function (it is a language construct) so you are not required to use parentheses with its argument list.
> In fact, using parentheses can cause confusion with the syntax of a function and SHOULD be omited.

Most would expect the following behavior:
<?php
    if (print("foo") && print("bar")) {
        // "foo" and "bar" had been printed
    }
?>

But since the parenthesis around the argument are not required, they are interpretet as part of the argument.
This means that the argument of the first print is

    ("foo") && print("bar")

and the argument of the second print is just

    ("bar")

For the expected behavior of the first example, you need to write: 
<?php
    if ((print "foo") && (print "bar")) {
        // "foo" and "bar" had been printed
More Info here: [http://php.net/manual/en/function.print.php](http://php.net/manual/en/function.print.php)

---

