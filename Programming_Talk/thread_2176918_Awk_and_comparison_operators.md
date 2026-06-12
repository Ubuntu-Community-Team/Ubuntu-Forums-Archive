---
title: "Awk and comparison operators"
date: 2013-09-26
forum: Programming Talk
---

### Post by vasa1 on 2013-09-26
I'm trying to understand how comparison operators for **awk** work. I made a file, **awkcomp.txt**:
```
01:dnsmasq:x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
02:ntp:x:105:109::/home/ntp:/bin/false
03:whoopsie:x:106:110::/nonexistent:/bin/false
04:lightdm:x:107:115:Light Display Manager:/var/lib/lightdm:/bin/false
05:longword:x:1000:1000:longword,,,:/home/longword:/bin/bash
06:alongword:x:1000:1000:longword,,,:/home/longword:/bin/bash
07:longworda:x:1000:1000:longword,,,:/home/longword:/bin/bash
08:longwo:x:1000:1000:longword,,,:/home/longword:/bin/bash
09:ngword:x:1000:1000:longword,,,:/home/longword:/bin/bash
10:avahi:x:108:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
```
Then, I ran the following commands:
[LIST=1]
[*]
[*][FONT=Courier New]awk -F: '$2 == "longword" { print }' awkcomp.txt[/FONT] prints only line 5 because in that line $1 is exactly equal to "longword".
[*][FONT=Courier New]awk -F: '$2 ~ "longword" { print }' awkcomp.txt[/FONT] seems less stringent and prints lines 5, 6, and 7 because they all contain "longword" in $1.
[*][FONT=Courier New]awk -F: '$2 != "longword" { print }' awkcomp.txt[/FONT] prints all lines except line 5.
[*][FONT=Courier New]awk -F: '$2 < "longword" { print }' awkcomp.txt[/FONT] prints lines 1, 4, 6, 8, and 10.
[*][FONT=Courier New]awk -F: '$2 > "longword" { print }' awkcomp.txt[/FONT] prints lines 2, 3, 7, and 9.
[/LIST]
While commands 1, 2, and 3 give understandable results, I don't understand what "**<**" in command 4 and "**>**" in command 5 do other than not printing any common lines between them. I couldn't make out any pattern as to the lines printed with these two commands.

---

### Post by Vaphell on 2013-09-26
alphanumeric order (think dictionary)

```
$ echo $'a\naa\nac\nb\ncc'
a
aa
ac
b
cc
$ echo $'a\naa\nac\nb\ncc' | awk '$1<"ab" { print $1 " < ab"; }; $1>"ab" { print $1 " > ab"; }'
a < ab
aa < ab
ac > ab
b > ab
cc > ab
```

---

### Post by vasa1 on 2013-09-26
> **Vaphell said:**
> alphanumeric order (think dictionary)
...
Thanks! It didn't seem clear at first but after reading your post, I sorted awkcomp.txt to get:
```
06:alongword:x:1000:1000:longword,,,:/home/longword:/bin/bash
10:avahi:x:108:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
01:dnsmasq:x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
04:lightdm:x:107:115:Light Display Manager:/var/lib/lightdm:/bin/false
08:longwo:x:1000:1000:longword,,,:/home/longword:/bin/bash
05:longword:x:1000:1000:longword,,,:/home/longword:/bin/bash
07:longworda:x:1000:1000:longword,,,:/home/longword:/bin/bash
09:ngword:x:1000:1000:longword,,,:/home/longword:/bin/bash
02:ntp:x:105:109::/home/ntp:/bin/false
03:whoopsie:x:106:110::/nonexistent:/bin/false
```

and those above "longword" were in the "**<**" group and those below "longword" were in the "**>**" group.

Marked as [Solved]

---

### Post by vasa1 on 2013-09-27
I also changed Vaphell's command:
```
echo $'a\naa\nac\nb\ncc' | awk '$1<"ab" { print $1 " < ab"; }; $1>"ab" { print $1 " > ab"; }'
```to
```
awk -F: '$2<"longword" { print $2 " < longword"; }; $2>"longword" { print $2 " > longword"; }' awkcomp.txt
```and got
```
dnsmasq < longword
ntp > longword
whoopsie > longword
lightdm < longword
alongword < longword
longworda > longword
longwo < longword
ngword > longword
avahi < longword

```

---

### Post by vasa1 on 2013-09-27
> **Vaphell said:**
> ...
```
...
$ echo $'a\naa\nac\nb\ncc' | awk '$1<"ab" { print $1 " < ab"; }; $1>"ab" { print $1 " > ab"; }'
a < ab
aa < ab
ac > ab
b > ab
cc > ab
```

I have a follow-up question ... What is the use of "**;**" in the code? I get the same result after removing all the instances of "**;**":```
[04:52 PM] ~ $ echo $'a\naa\nac\nb\ncc' | awk '$1<"ab" { print $1 " < ab" } $1>"ab" { print $1 " > ab" }'
a < ab
aa < ab
ac > ab
b > ab
cc > ab
[04:53 PM] ~ $ 

``` 

Similarly, ```
awk -F: '$2<"longword" { print $2 " < longword"; }; $2>"longword" { print $2 " > longword"; }' awkcomp.txt
```and```
awk -F: '$2<"longword" { print $2 " < longword" } $2>"longword" { print $2 " > longword" }' awkcomp.txt
```both give:```
dnsmasq < longword
ntp > longword
whoopsie > longword
lightdm < longword
alongword < longword
longworda > longword
longwo < longword
ngword > longword
avahi < longword

```

---

### Post by Vaphell on 2013-09-27
they are not necessary but i like using them in oneliners so i don't have to think much where one thing ends and another starts.

---

### Post by vasa1 on 2013-09-27
> **Vaphell said:**
> they are not necessary but i like using them in oneliners so i don't have to think much where one thing ends and another starts.
Okay and thanks!

---

