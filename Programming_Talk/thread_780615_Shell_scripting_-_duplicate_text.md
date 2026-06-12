---
title: "Shell scripting - duplicate text"
date: 2008-05-03
forum: Programming Talk
---

### Post by omrsafetyo on 2008-05-03
I'm trying to find a simple way to move all of my music into subdirectories.
**Step 1 - make the directories.**
I did this with the following 1 liner:
```

ls -ld * | grep -v drwx | awk '{print $8, $9, $10, $11}' | grep '-' | cut -d'-' -f1 | uniq -i > make_dirs.sh

```
I then used some simple search routines in vi to have this listing create the directories:
```

%s/^/mkdir "/g
%s/$/"/g

```
That way, for every band there is an entry:
```
mkdir "Band Name"
```

**Step 2 - move files into directories.**
This is where I run into trouble.  I am trying to do something similar.  I have again output the same bandnames to a file, and am trying to find a way to double the text on each line:

Band Name ->  Band Name Band Name

The final goal is:

```
mv "Band Name"* "Band Name"/.
```
Effectively moving all files into the folders.

I thought I would start in vi with the following search/replace:

%s/$/"* "/g

Giving me:
Band Name"* "

I then thought I might be able to use cut to duplicate:

cat make_dirs.sh | cut -d"\"" -f1,2,3,1

printing the 
1. Band Name
2. "*
3. "
1. Band Name

But unfortunately, it doesn't repeat printing the first field.

Any ideas?

---

### Post by unutbu on 2008-05-03
```
ls -ld * | grep -v drwx | awk '{print $8, $9, $10, $11}' | grep '-' | cut -d'-' -f1 | uniq -i | sed 's/.*/mv \"&\"* \"&\"\/./'
```

---

### Post by omrsafetyo on 2008-05-03
Whoa - now that right there is some sed action.

Thanks!

NOTE:

Once outputting this to a file, I had to remove some spacing issues:

%s/\ \"\/\./"\/\./g

Spaces after the filename of the directory prevented it from moving.

This also caused some files to get renamed funny... but other than that worked like a charm.

---

### Post by ghostdog74 on 2008-05-03
you can do that all in awk
```

find /fullpath -maxdepth 1 -type f  -printf "%f\n"| awk 'BEGIN{
 q="\047"
 FS="-"
}
/-/{
  unique[$1] 
  files[$0]=$1
}
END {
  #make directories
  for ( dir in unique) {
    cmd = "mkdir -p "q dir q
    # system(cmd) #uncomment to use
  }
  for( f in files ){
   print "moving files in  "f" to "files[f]
   cmd = "mv "q f q"* "q files[f] q
   # system(cmd) # uncomment to use  
  }  
}' 

```

---

### Post by ghostdog74 on 2008-05-03
> **omrsafetyo said:**
> 
```

ls -ld * | grep -v drwx | awk '{print $8, $9, $10, $11}' | grep '-' | cut -d'-' -f1 | uniq -i > make_dirs.sh

```


by using awk with specified columns to get the file names, you are prone to to getting date fields as well as file names with spaces. Your result will have errors. Use find instead of ls -l.

---

