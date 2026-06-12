---
title: "filter lines in a file by keywords in another file"
date: 2009-08-26
forum: Programming Talk
---

### Post by steve_c on 2009-08-26
Ok for some reason my brain is not functioning today and I could use some help on what I think should be a really easy task.

I have two files, FILTER and DATA. I want to go through DATA, and if any of the words in FILTER are in there, I want that line of DATA to be put in a new file OUTPUT.

I'm trying to teach myself python right now so that would be ideal. However I'm willing to do this in perl, bash, or php as well.

Doing it in python, right now I have:
```
#!/usr/bin/python

filterfile = 'FILTER'
filter = open(filterfile, 'r').readlines()

infile = 'DATA'
input = open(infile, 'r').readlines()

outfile = 'OUTPUT'
output = open(outfile, 'w')

for item in filter:
    for line in input:
        if line.find(item):
            output.write(line)
```
That seems to be giving me an OUTPUT file with every line of the DATA file in it times the number of items in FILTER. So obviously I'm way the heck off.

I'd *prefer* not to read the entire DATA file into dictionary because some of the DATA files I will be using this for are several gigabytes large and may not fit into RAM. However I'll make do with whatever help I can get.

Thank you very much for any help.

---

### Post by unutbu on 2009-08-26
Reverse the order in which you execute the loops, and use a
"break" command so you do not write the same line twice.
```

for line in input:
    for item in filter:
        item=item.strip()
        if item in line:
            output.write(line)
            break


```

---

### Post by steve_c on 2009-08-26
I feel like this would be super-easy to do in bash also, as essentially I just want to
```
grep "item" DATA >> OUTPUT
```
but I want to do that for each "item" in FILTER. I actually did try writing that script, but for some reason OUTPUT only contains the matches for the last item in FILTER.
```
FILTER="$1"
INPUT="$2"
OUTPUT="$3"

processLine(){
    line="$@"
    grep $line $INPUT >> $OUTPUT
}

x=`wc -l $FILTER | awk '{print $1}'`
echo "Number of lines in filter: $x \n"

ORIGIFS=$IFS
IFS=$(echo -en "\n\b")

exec 3<&0
exec 0<$FILTER
while read line
do
    # use $line variable to process line in processLine() function
    processLine $line
done
exec 0<&3

IFS=$ORIGIFS

y=`wc -l $OUTPUT | awk '{print $1}'`
echo "Number of genes found: $y \n"

exit 0

```

---

### Post by steve_c on 2009-08-26
> **unutbu said:**
> Reverse the order in which you execute the loops, and use a
"break" command so you do not write the same line twice.
```

for line in input:
    for item in filter:
        item=item.strip()
        if item in line:
            output.write(line)
            break


```
Weird... This is working better, but I'm still getting some false positives. I'm guessing .find() is getting an item in the filter that must be a substring of a line in the data.

---

### Post by steve_c on 2009-08-26
Awesome. Think I got what I was looking for:
```
for line in input:
    linelist = line.split()
    for item in filter:
        item = item.strip()
        if item in linelist:
            output.write(line)
            break
```

Thank you very much for the help unutbu!

If anyone feels like fixing the bash attempt I wouldn't mind knowing what I did wrong there either.

---

