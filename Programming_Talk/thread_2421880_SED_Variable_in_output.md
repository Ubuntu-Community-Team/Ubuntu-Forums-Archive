---
title: "SED Variable in output"
date: 2019-06-28
forum: Programming Talk
---

### Post by ylafont on 2019-06-28
I think i have looked everywhere for a solution to this without success.

```
#!/bin/sh
shopt -s nullglob
FILES=/mnt/c/temp/3/000*.txt


Result=results.txt
touch $Result


for f in $FILES




do
    filename=${f##*/}
    echo "Processing $f" >> $Result
    sed -rn \
        -e '/^Name:/{
            s/Local:.*//
            s/Book.*//
            s/Name: //
            s//\1/
            h
            #p
            }'\
        -e '/.*NORTHSTAR CONTRACTING.*/{
            s/(.*)/\1/
            G
            s/(.*)\n(.*)/$f\t\2\t\1/
            p
        }' $f
done

```
I am trying to include the file name along with the SED output  in  the line   s/(.*)\n(.*)/$f\t\2\t\1/ -   I have tried single/double quotes, double quotes surrounded by single quotes and all other variations.  is this not possible


s/(.*)\n(.*)/'"$f'"\t\2\t\1/
s/(.*)\n(.*)/"'$f"'\t\2\t\1/


Any assistance is greatly appreciated. thank you in advance.

---

### Post by ylafont on 2019-06-28
Figured this out shortly after posting.

It look like one cannot use the variable that is used in the for loop.  I needed to declare a new one.


```
#!/bin/sh
shopt -s nullglob
FILES=/mnt/c/temp/3/000*.txt


Result=results6.txt
touch $Result


for f in $FILES




do
    fPath=${f%/*}                                 #File Path 
    fName=${f##*/}                                #File Namew with Extension
    fExt=${fName##*.}                            #File Extension Only
    fNameNoExt=${fName%.*}                        #File Name without Extension
    
    #echo "Processing $f" >> $Result
    sed -rn \
        -e '/^Name:/{
            s/Local:.*//
            s/Book.*//
            s/Name: //
            s//\1/
            h
            #p
            }'\
        -e '/.*NORTHSTAR.*/{
            s/(.*)/\1/
            G
            s/(.*)\n(.*)/'$fNameNoExt'\t\2\t\1/
            p
        }' $f >> $Result
done
```

---

### Post by dmnur on 2019-06-28
> It look like one cannot use the variable that is used in the for loop. I needed to declare a new one.

You can, and you already did that here:
```
echo "Processing $f" >> $Result
```

I guess you just got the quotes wrong previous times. Let me give you some examples.

Let's say we have a file named **example.txt** with the following contents:
```
foo bar
```

Suppose we want to do the following substitution: take **foo** and **bar**, swap them, and add the name of a file before them:
```
example.txt bar foo
```

Your first try might be:
```

$ echo $f
example.txt
$ sed -r 's/(foo) (bar)/$f \2 \1/' $f
$f bar foo

```

This didn't work because **$f** in the expression is within the single quotes, and thus is printed as is.

To print the contents of the **$f** variable, you have to get it out of quotes:
```

$ sed -r 's/(foo) (bar)/'$f' \2 \1/' $f
example.txt bar foo

```

A closer look:
```

's/(foo) (bar)/'$f' \2 \1/'

Quoted: 's/(foo) (bar)/'
Unquoted: $f
Quoted: ' \2 \1/'

```

But that's not all. If a filename contains whitespace, the above will fail. You need to quote **$f** too, but using double quotes:
```

$ f='another example.txt'
$ sed -r 's/(foo) (bar)/'$f' \2 \1/' "$f"  # fails
sed: -e expression #1, char 21: unterminated `s' command
$ sed -r 's/(foo) (bar)/'"$f"' \2 \1/' "$f"
another example.txt bar foo

```

Again, closely:
```

's/(foo) (bar)/'"$f"' \2 \1/'

Single-quoted: 's/(foo) (bar)/'
Double-quoted: "$f"
Single-quoted: ' \2 \1/'

```

But wait a minute! If **$f** contains forward slashes or backslashes, that will fail too:
```

$ f='example/another example.txt'
$ sed -r 's/(foo) (bar)/'"$f"' \2 \1/' "$f"
sed: -e expression #1, char 23: unknown option to `s'

# may cause unexpected results
$ f='another example \1.txt'
$ sed -r 's/(foo) (bar)/'"$f"' \2 \1/' "$f"
another example foo.txt bar foo

```

To make it robust, you need to sanitize the contents of the variable:
```

$ f='example/another example \1.txt'
$ sanitized=$(printf %s "$f" | sed 's@\\@\\\\@g; s@/@\\/@g')
$ echo "$sanitized"
example\/another example \\1.txt
$ sed -r 's/(foo) (bar)/'"$sanitized"' \2 \1/' "$f"
example/another example \1.txt bar foo

```

And now that's it. I guess these are all the issues you might encounter. :)

---

