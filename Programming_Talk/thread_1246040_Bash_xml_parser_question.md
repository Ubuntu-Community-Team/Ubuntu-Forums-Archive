---
title: "Bash xml parser question"
date: 2009-08-21
forum: Programming Talk
---

### Post by PryGuy on 2009-08-21
Good day, everyone!
I have found a great yet simple [XML parser]("http://nixcraft.com/shell-scripting/11599-parse-xml-file-store-data-array-shell-scripting.html"). Modified it a little, but it still does not work as I want. Here's my script:```
#!/bin/bash
for tag in macAddress hostName userName userType
do
OUT=`grep  $tag in.xml | tr -d '\t' | sed 's/^[ \t]*//;s/^<.*>\([^<].*\)<.*>$/\1/'`

eval ${tag}=`echo -ne \""${OUT}"\"`
done

Macs=( `echo ${macAddress}` )
Hosts=( `echo ${hostName}` )
Users=( `echo ${userName}` )
Types=( `echo ${userType}` )

# Let's find out how it works:
echo ${Users[1]}
echo ${Users[@]}

read

exit 0
```Let's say I have XML file 'in.xml' with entry like this:```
<Users>
  <Host>
    <macAddress>XX:XX:XX:XX:XX:XX</macAddress>
    <hostName>boss</hostName>
    <userName>John Smith</userName>
    <userType>2</userType>
  </Host>
</Users>
```This parser will split 'John Smith' into two different array elements 'cause name has space in it. How do I avoid it and put it into array as one?

Thank you in advance!

---

### Post by geirha on 2009-08-21
If you're using eval, you are most likely approaching the matter in the wrong way.

For your specific example, I'd try something like this. 
```
#! /bin/bash
while IFS='<>' read _ starttag value endtag; do
    case "$starttag" in 
        macAddress) Macs+=("$value") ;;
        hostName)   Hosts+=("$value");;
        userName)   Users+=("$value");;
        userType)   Types+=("$value");;
    esac
done < in.xml

```

However, parsing xml is not something you can do reliably in bash. See [http://mywiki.wooledge.org/BashGuide/Practices/ChooseYourShell?highlight=(xml](http://mywiki.wooledge.org/BashGuide/Practices/ChooseYourShell?highlight=(xml))

---

