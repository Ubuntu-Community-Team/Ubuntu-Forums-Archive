---
title: "SED (regular expression) problem ---"
date: 2010-05-16
forum: Programming Talk
---

### Post by bluesmodular on 2010-05-16
Hello,

I would like to replace Line 187 of my file named run_example.

The original line is below, including the spaces:
```

  celldm(1)   = 6.00, 

```I want it to become something like
```

  celldm(1)   = 6.05,

```or
```

  celldm(1)   = 6.10,

```where the number is stored in a variable called $bulksize . This variable increments properly in my for loop.

I tried doing this:
```

    cat run_example | sed -e "187 s_  [a-z]*(1)   = _& $bulksize,_" > run_example  

```

Didn't work...

Thank you for your help!

---

### Post by iponeverything on 2010-05-16
I can do a simple line replace with awk if it helps..

```
cat run_example|awk 'NR == 187 {print "celldm(1)   = 6.05,"; next} {print $0}'>run_example.new
```

---

### Post by amauk on 2010-05-16
Use sed's in-place flag to edit a file 

```
sed -i "s|\(celldm(1) *= *\)[0-9]\+\.[0-9]\+|\1${bulksize}|" run_example
```

---

### Post by BoneKracker on 2010-05-16
No need to call 'cat'```
sed 's/red/blue/' oldfile >newfile
```or```
sed 's/red/blue/' <oldfile >newfile
```

---

### Post by DaithiF on 2010-05-16
another solution:
```
sed "s/[0-9.]\+,$/$bulksize,/" run_example
```

---

### Post by bluesmodular on 2010-05-16
Thanks all! I found a solution with printf and ed

```

half=....
bulksize=....
for i in */run_example; do
    printf '187s/= [^,]*/= %s/\nwq\n' "$bulksize" | ed -s "$i"
    half=....
    bulksize=....
done 
```

---

### Post by BoneKracker on 2010-05-16
without looking at this in detail, I'll just mention that if you're already working in the shell, it's often worth first trying to apply BASH features such as parameter substitution before defaulting to calling external tools.

Although there are many cased where you need more power, using such features or the shell's built-ins is more efficient than calling externals.

For example, one form of parameter substitution:

${$string/$substring_match/$replacement_substring}

Such might not be applicable here, but it's a useful rule-of-thumb to try the built-in capabilities of whatever you've already got loaded into memory before resorting to external utilities, and also to use what's smaller in preference to what's bigger (e.g. parameter substitution in preference to sed in preference to awk in preference to perl).

---

### Post by bluesmodular on 2010-05-17
Thanks all !!

Using printf and ed, how would I replace a line that contains only a  number, e.g. 6.00, with another number stored in variable $bulksize or  $half ? 

I guess I don't understand all the parts in this [regular expression[IMG]http://images.intellitxt.com/ast/adTypes/2_bing.gif[/IMG]]("http://www.unix.com/#") 
'187s/= [^,]*/= %s/\nwq\n'

I know 187 is the line number, the s after that is substitution, and ^,  matches a comma in the beginning? Or anything that's not a comma? Not  sure what the rest of it means... where can I find a good reference for  this?

---

### Post by sedawk on 2010-05-17
Normally ^ is beginning of the line and $ is the end of a line.

But if the first character in []-brackets is a ^ it means
"not".

---

