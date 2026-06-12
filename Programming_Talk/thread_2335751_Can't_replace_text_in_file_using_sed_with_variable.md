---
title: "Can't replace text in file using sed with variable containing slashes and new lines"
date: 2016-08-31
forum: Programming Talk
---

### Post by ericson-paul on 2016-08-31
This problem is fairly common and there are numerous solutions all over the place--none of them work.

I try   

sed -i "s~blah~$var~g file"  

 and get: 

"sed -e expression #1, char 70: unterminated `s' command".

 I have confirmed that the culprit is a slash in $var. Variants of this solution to this are all over the place and none of them work. Was sed recently updated? I'm on v4.2.2 on Ubuntu 14.04.4 LTS.

$var contains:

"arn:aws:ec2:region:account-id:subnet/subnet-id",
"arn:aws:ec2:region:account-id:subnet/subnet-id",
"arn:aws:ec2:region:account-id:subnet/subnet-id"

There are "\n"s at the end of the first two lines.

I'm wondering if the \n is messing with sed.

Any thoughts?

I'm not married to sed. I need to replace a string like "SUBNET" in a file with the 3 lines in $var.

Thanks for your time.

---

### Post by steeldriver on 2016-08-31
Hello and welcome to the forums

Do you actually need to *substitute *the string (anywhere in a line, possibly multiple times) or do you want to replace whole lines containing the SUBNET marker by the contents of $var?

If the latter, there are more robust ways of doing that e.g. given
```

$ cat somefile
stuff
more stuff
SUBNET
even more stuff

```

then
```

$ sed '/SUBNET/{
r /dev/stdin
d
}' somefile <<< "$var"
stuff
more stuff
"arn:aws:ec2:region:account-id:subnet/subnet-id",
"arn:aws:ec2:region:account-id:subnet/subnet-id",
"arn:aws:ec2:region:account-id:subnet/subnet-id"
even more stuff

```

---

### Post by Habitual on 2016-09-01
> **ericson-paul said:**
> ```
sed -i "s~blah~$var~g file**[COLOR=#ff0000]"[/COLOR]**
```
Try 
```
sed -i "s~blah~\$var~g**[COLOR=#ff0000]"[/COLOR]** file
```

---

