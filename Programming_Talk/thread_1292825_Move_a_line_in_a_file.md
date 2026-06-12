---
title: "Move a line in a file"
date: 2009-10-16
forum: Programming Talk
---

### Post by Gen2ly on 2009-10-16
I'd like to so a simple thing at least it sound like it is but have no idea just how to go about it.  I thought about using sed but from what I know of sed it's a line editor and just doesn't seem right for the task.  First a line would have to be read then deleted then moved, hmm... yeah just thinking that this isn't the best way to go about it.  Or is it?  Off the bat I can't think of any tools that do this.  Currently I got a line that begins with:

```
build...
```

And I'd like to move it earlier in the file that follows the line:

```
source...
```

How would you go about doing this?

---

### Post by benj1 on 2009-10-16
how about this
```

#! /usr/bin/awk -f                                                                                                             
/build/ {build = NR}
/source/ {source = NR}
//{array[NR] = $0}

END{
    for (i=1 ; i<=NR;i++){
        if (i == source){print array[build]}
        if (i == build){continue}
        print array[i]
        }
}

```
you could then pipe it out to a file
ie
awkscript file.txt > outputfile.txt

you may have to modify the regex for /build/ and /source/ to be more specific and eliminate false positives

---

### Post by ghostdog74 on 2009-10-16
the above method leaves a blank line as first line (though a minor issue), and you forgot to include <= in the END block for loop. That will omit out the last line.

another way, probably better with large files as I don't have to store every lines in array and print out at the END block.
```

awk '/build/{
    f=0    
    print $0
    for(i=1;i<=d;i++){ print a[i]  }
    g=0
    delete a # remove array after found
    next
}
/source/{ f=1; g=1 }
f{ a[++d]=$0 }
!g' file

```

---

### Post by benj1 on 2009-10-16
amended.
except the blank line, will have a think

---

### Post by ghostdog74 on 2009-10-16
> **benj1 said:**
> amended.
except the blank line, will have a think

hint: since you build the array using NR, NR doesn't start with 0.

---

### Post by benj1 on 2009-10-17
amended again thanks, again :)

---

### Post by Gen2ly on 2009-10-17
> **benj1 said:**
> how about this
```

#! /usr/bin/awk -f                                                                                                             
/build/ {build = NR}
/source/ {source = NR}
//{array[NR] = $0}

END{
    for (i=1 ; i<=NR;i++){
        if (i == source){print array[build]}
        if (i == build){continue}
        print array[i]
        }
}

```

Hey thanks.  Unfortunately, it didn't work:

```
awk: /home/todd/.bin/bs                                                         
awk:            ^ syntax error
```

I'm new to awk so I don't know how to fix this, but am beginning to realize that I'm going to have to learn this. :)

> **ghostdog74 said:**
> ...as I don't have to store every lines in array and print out at the END block.
```

awk '/build/{
    f=0    
    print $0
    for(i=1;i<=d;i++){ print a[i]  }
    g=0
    delete a # remove array after found
    next
}
/source/{ f=1; g=1 }
f{ a[++d]=$0 }
!g' file

```

This is beyond me to understand but I have seen something like 'for(i=1;i<=d;i++)' in bash scripts before that created lists from discovered contents.  Again, getting to understand that I'll have to learn awk as a couple things I want to do with sed now just aren't possibly.  But this works great, thanks for the help.

---

### Post by A_Fiachra on 2009-10-17
Damn -- I would do it in Perl -- but you guys are handy with awk (a language I've always had a secret envy for).

---

### Post by ghostdog74 on 2009-10-17
> **Gen2ly said:**
> 
This is beyond me to understand but I have seen something like 'for(i=1;i<=d;i++)' in bash scripts before that created lists from discovered contents.  Again, getting to understand that I'll have to learn awk as a couple things I want to do with sed now just aren't possibly.  But this works great, thanks for the help.

```

awk '/build/{
    # if build is found
    f=0    #remove flag
    print $0 # print the current line
    for(i=1;i<=d;i++){ print a[i]  } #print the array of lines after source  and before build
    g=0 #because build already found, set g flag to 0 so the below !g part can print other lines
    delete a # remove array after found 
    next
}
/source/{ f=1; g=1 } #if source found, set flag f and g. 
f{ a[++d]=$0 } # if source is found, store lines after source into array, then continue to search for build
!g'  # print the rest of the lines before source is found and after build is found...
file

```

---

### Post by benj1 on 2009-10-18
> **Gen2ly said:**
> Hey thanks.  Unfortunately, it didn't work:

```
awk: /home/todd/.bin/bs                                                         
awk:            ^ syntax error
```



how did you call it ?, it should be 
```
thisscriptfile.awk foofile.txt
```

not a huge problem ghostdogs script should work fine, and as he points out should be more efficient.

@A_fiachra
you should give it a try, its not especially hard to learn (easier than perl :)) and its amazing at text processing, the only problem is, is that you will be forever looking at shellscripts like:
```
grep foo | sed bar | awk '{print $1}'
```
and thinking it could all have been done, more clearly and concisely in awk.
heres a [link]("http://awk.info/?index") to some useful stuff

---

### Post by geirha on 2009-10-18
I believe this ed should do it. Note that it edits the file in-place.
```
printf "%s\n" "/^build/d" "/^source/x" "w" | ed -s file.txt
```

It sends three commands to ed.
```

/^build/d  - find the first line that mathces "^build" and delete it (The line's content is stored in the cut buffer)

/^source/x - find the first line that matches "^source" and paste the contents of the cut buffer below it.

w          - write the changes

```

---

### Post by Gen2ly on 2009-10-19
> **ghostdog74 said:**
> ```

awk '/build/{
    # if build is found
    f=0    #remove flag
    print $0 # print the current line
    for(i=1;i<=d;i++){ print a[i]  } #print the array of lines after source  and before build...
```

Not sure how the array understands to the source line, but thanks for the explanation.  I'm getting to like how awk works.

> **benj1 said:**
> how did you call it ?, it should be 
```
thisscriptfile.awk foofile.txt
```
...

Yeah, I called this from my script path which is a hidden folder.  I'm thinking your script is interpretting the . as a regexp variable???

> **geirha said:**
> I believe this ed should do it. Note that it edits the file in-place.
```
printf "%s\n" "/^build/d" "/^source/x" "w" | ed -s file.txt
```

It sends three commands to ed...[/code]

Yeah, I originally wrote the thread trying to remember this command.  I had seen 'ed' before but didn't remember it.  +1 for helping me remember this and for ease of use.

I've run into a bit of a problem though.  At times, (I've discovered) the source and build lines expand over more lines.  For example:

```
source=('78905905f5a4ed82160c327f3fd34cba'
        '5277a9164001a4276837b59dade26af2'
        '3f8b60b6fbb993c18442b62ea661aa6b')

build=('a-file-name'
       'another-file-name')
```

I've tried using the ed command and defining a range:

```
printf "%s\n" "/^build/,/)/d" "/^source/,/)/x" "w" | ed -s file.txt
```

with no luck.  Can I do this with 'ed'???  Or anyone know a way to get awk to do it??

---

### Post by ghostdog74 on 2009-10-19
> **Gen2ly said:**
> 
```
source=('78905905f5a4ed82160c327f3fd34cba'
        '5277a9164001a4276837b59dade26af2'
        '3f8b60b6fbb993c18442b62ea661aa6b')

build=('a-file-name'
       'another-file-name')
```
... Or anyone know a way to get awk to do it??
you will need extra check, since your build ends with ), you can check whether it spans another line.
```

/build/ && !/\)$/ {
  # if build found but does not end in )
  s=$0
  getline #get the next line
  s=s$0 # join them
  # if you are sure those statements don't span more than 2 lines
  print s
}
/build/ && /\)$/{
  .......
}

```

---

