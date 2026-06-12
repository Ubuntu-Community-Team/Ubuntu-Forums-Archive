---
title: "bash to perl translation please"
date: 2007-03-12
forum: Programming Talk
---

### Post by newbie22 on 2007-03-12
```
if [ -f 001.foo ]; then
for abc in `ls ???.foo`
do xyz=`echo $abc | sed 's/^0//g'`
mv $abc $xyz
done
fi
```
Would someone please translate the above bash code into perl?

---

### Post by colo on 2007-03-12
Can't help you with perl, but maybe a more coarse and error-prone version for bash will help you out, too.
```

[ -f 001.foo] && for file in 0??.foo; do mv "$file" "${file:1}"; done

```
Should have the exact same effect as your script.

---

### Post by Mr. C. on 2007-03-12
```
#!/usr/bin/perl

if ( -f "001.foo" ) {

    foreach (glob "???.foo") {
        $old = $_;
        (my $new = $old) =~ s/^0+//;

        print "renamed $old -> $new\n";
        rename ($old, $new);
    }
}

```

This only works correctly on files as you've specified.  It will fail on things like abc.foo, since they are non-numeric and your program ignored that problem.

MrC

---

