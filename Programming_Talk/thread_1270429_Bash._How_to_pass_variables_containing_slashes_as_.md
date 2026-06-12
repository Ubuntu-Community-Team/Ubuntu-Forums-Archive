---
title: "Bash. How to pass variables containing slashes as sed command parameters?"
date: 2009-09-19
forum: Programming Talk
---

### Post by r.osmanov on 2009-09-19
Hi all, 

I want replace one string with another in a bunch of files. 
I.e. I want issue a command like 
```
./replace_str.sh '/d/images/t/' '/images/' *.html
```
For that I get a file list for the wildcard;
go through filenames and issue the following:
```
sed -e "s/$in_mask/$out_mask/g" ${files[$i]} > ${files[$i]}.".sed"
```

Could you help me?

---

### Post by r.osmanov on 2009-09-19
Almost forgot, the following is the script I'm testing:
```
#!/bin/bash
# Input params
if [ $# -lt 3 ] ; then 
    echo -e "Error. You should specify at least directory, input and output masks!"
    exit 1
fi 

in_mask=$1
out_mask=$2
dir=$3

# File list
files=(`ls -B ${dir:='./'}`);
echo "Got "${#files
[*]}" files to treat"

# Loop through files
i=0
while (( $i < ${#files
[*]} )) 
do 
    echo "Treating "${files[$i]}" ..."
    sed -e "s/$in_mask/$out_mask/g" ${files[$i]} > ${files[$i]}.".sed"
    (( ++i ))
done

```

When I issue:
```
sudo ~/scripts/bash/replace_in_files.sh '\/\d/58861\/t\/images\/' '' '*.html'
```
it says *"sed: -e expression #1, char 27: unknown option to `s'"*

---

### Post by johnl on 2009-09-19
You can use any character as a separator for send, not just '/' -- ie:

```
sed s/find/replace/g foo.txt
```
and
```
sed s,find,replace,g foo.txt
```
are equivalent.

If you use a different separator character, you won't need to worry about escaping the forward slashes.

Hope this helps.

---

### Post by r.osmanov on 2009-09-19
Yeah, it worked!:)

I didn't know that separator could be any character. I've made 
```
sed -e "s~$in_mask~$out_mask~g" ${files[$i]} > ${files[$i]}".sed"
```

Thanks and regards.

---

