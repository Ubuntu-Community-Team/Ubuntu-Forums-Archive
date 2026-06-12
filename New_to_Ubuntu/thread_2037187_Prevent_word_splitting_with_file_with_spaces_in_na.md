---
title: "Prevent word splitting with file with spaces in name"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by kristo5747 on 2012-08-03
Hello, 

I have a script that "validates" a ZIP file that look like this

```
AAA_20120801.zip =>
x~back end~20120801.TXT
y~time in~20120801.TXT
z~heat_chamber~20120801.TXT
AAA_20120801.ctl
```My task is to compare its contents (i.e the  list of files contained inside) with the control file that is provided inside the ZIP file itself.

Since we've started receiving files with spaces in their name, I prevented the OS from word splitting file names when I view the ZIP's contents like so

```
FIRST_Array=(); while read length date time filename; do FIRST_Array+=( "$filename" ); echo -e "$filename"; 
done < <(/usr/bin/unzip -qql AAA_20120801.zip)

```When I try to do the same with the control file, 

```
SECOND_Array=(); while read length date time filename; do SECOND_Array+=( "$filename" ); echo -e "$filename"; done < <(/usr/bin/unzip -c AAA_20120801.zip AAA_20120801.ctl )
```SECOND_Array() correctly outputs the file names in the control files but it also output the file sizes listed in the control file
```

x~back end~20120801.TXT 2KB
y~time in~20120801.TXT 2KB
z~heat_chamber~20120801.TXT 2KB
```and my array comparison (diff -q) fails.

I tried adding this bit of Awk() code to remove the file size field but it brings word splitting back!

```
SECOND_Array=(); while read filename; do SECOND_Array+=( "$filename" ); echo -e "$filename"; done < <(/usr/bin/unzip -p AAA_20120801.zip AAA_20120801.ctl |awk '{print $1}')
```How can I remove the file size info and prevent word splitting? Any ideas?

Thank you.

---

### Post by SeijiSensei on 2012-08-03
If every filename ends with TXT, you could just lop off the sizes with sed:

```
echo 'x~back end~20120801.TXT 2KB' | sed 's/TXT.*$/TXT/g'
```

should return "x~back end~20120801.TXT".  If the extensions differ, you'll need to modify the first regular expression accordingly.  You could try removing the string " .*$" which matches any space followed by text at the end of each line.

You've taken the right approach to avoiding splitting.  You can enclose the string in single or double quotes depending on whether they enclose an environment variable, or escape the spaces with \.

---

### Post by kristo5747 on 2012-08-07
This did the trick:

> while read -r line
do 
file=${line% *}
array+=( "$file" )
printf '%s\n' "$file"
done < <(/usr/bin/unzip -p JABL_XML_20120801_165917.zip JABL_XML_20120801_165917.ctl Thanks for taking the time.

---

