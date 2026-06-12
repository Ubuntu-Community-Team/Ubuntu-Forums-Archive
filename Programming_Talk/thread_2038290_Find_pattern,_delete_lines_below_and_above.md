---
title: "Find pattern, delete lines below and above"
date: 2012-08-06
forum: Programming Talk
---

### Post by Srdjan01 on 2012-08-06
Hi,

I am totally new with scripting and could really use help from someone more experienced. I have to create a bash script that would look in particular folder, identify files that contain "P_SGSN_SESSION_MANAGEMENT" in filename. For every one of those files it should find pattern "PAPU_INDEX 36" and delete that pattern (which is in one line) and delete 42 lines above and 144 lines below. Here is part of one file:

      MNC 3
      SUCC_DEACT_SE_GGSN_RESET 0
      FAIL_PDP_ACT_DUE_NO_RESP 0
      PAPU_INDEX 36
      SUCC_IMPL_DEACT_SE_COLLISIONS 0

I have found another topic about this [HTML]http://ubuntuforums.org/showthread.php?t=1897438[/HTML], but couldn't tweak it to fit to what I want.

Thanks,
Srdjan

---

### Post by DarkAmbient on 2012-08-06
Walkthrough for sed:

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by Vaphell on 2012-08-06
> **Srdjan01 said:**
> Hi,

I have found another topic about this [HTML]http://ubuntuforums.org/showthread.php?t=1897438[/HTML], but couldn't tweak it to fit to what I want.

```
ed -s input.txt <<< $'g/PAPU_INDEX/-42,+144d\n,p'
``` did't work?

---

### Post by steeldriver on 2012-08-06
modifying Peteris Krumins' one-liner #75 ('delete last 10 lines of file') 

```
sed -e :a -e '$d;N;2,10ba' -e 'P;D'
```[http://www.catonmat.net/blog/sed-one-liners-explained-part-three/](http://www.catonmat.net/blog/sed-one-liners-explained-part-three/)

slightly, could you do

```
sed -e :a -e '/*pattern*/,+144d;N;2,43ba' -e 'P;D' *yourfile*
```(basically it maintains a moving buffer of 43 lines in the pattern space, and deletes it plus the next 144 lines if it matches *pattern*)

---

### Post by Srdjan01 on 2012-08-07
Thanks everyone for your responses, much appreciated.

There are basically 2 different problems here. First one is altering one file by removing the pattern. Code

ed -s input.txt <<< $'g/PAPU_INDEX 36/-42,+144d\n,p' > output.txt

worked fine. Thanks Vaphell.

Secondly, I have to put in a script that can automatically apply changes to numerous files that all have "P_SGSN_SESSION_MANAGEMENT" in file name. When i was applying simple sed that script looked like this

#!/bin/sh
. /etc/profile
/usr/bin/perl -e "
s/      MGW_NAME 401/    MGW_NAME MNS01/g;
s/      MGW_NAME 402/    MGW_NAME MNS02/g;
s/      MGW_NAME 403/    MGW_NAME MNS03/g;
s/      MGW_NAME 404/    MGW_NAME MNS04/g" -pi $(find /appl/virtuo/gways/spool/nokia/MGW/U4.1/temp/ -type f)
mv /appl/virtuo/gways/spool/nokia/MGW/U4.1/temp/* /appl/virtuo/gways/spool/nokia/MGW/U4.1/output_d/

Command **ed -s input.txt <<< $'g/PAPU_INDEX 36/-42,+144d\n,p'** prints result to a screen. Is it possible to apply change and return in to the same file? Something similar to this **s/      MGW_NAME 401/    MGW_NAME MNS01/g;**. 

Thanks,
Srdjan

---

### Post by Vaphell on 2012-08-07
```
s/ MGW_NAME 401/ MGW_NAME MNS01/g;
s/ MGW_NAME 402/ MGW_NAME MNS02/g;
s/ MGW_NAME 403/ MGW_NAME MNS03/g;
s/ MGW_NAME 404/ MGW_NAME MNS04/g"
```
this can be simplified to a variant of *'s/( MGW_NAME )4(0[1-4])/**\1**MNS**\2**/g'*


```
while read -r -d$'\0' file
do
  ed -s "$file" <<< 'g/PAPU_INDEX 36/-42,+144d
                     ,s/\( MGW_NAME \)4\(0[1-4]\)/\1MNS\2/g
                     w' 
done < <( find /appl/virtuo/gways/spool/nokia/MGW/U4.1/temp/ -iname '*P_SGSN_SESSION_MANAGEMENT*' -type f -print0 )
```
is there a reason to run the script with sh and not bash? Bash in general is more feature rich.


PS. damn it, there is next to no ed know-how on the internet, pretty much only dry man pages -_-

---

### Post by Srdjan01 on 2012-08-07
> **Vaphell said:**
> 
is there a reason to run the script with sh and not bash? Bash in general is more feature rich.

Not really. Will use bash from now on.

I will test this out and let you know how it went.

Thanks so much, I am really grateful for this.

BR,
Srdjan

---

### Post by Srdjan01 on 2012-08-07
I have tried using this, it didn't delete the pattern.

```
#!/bin/bash
. /etc/profile
/usr/bin/perl -e "
s/    SGSN_ID 223572/    SGSN_ID SBZ01/g;
s/    SGSN_ID 223571/    SGSN_ID SBG01/g" -pi $(find /appl/virtuo/gways/config/ericsson-hlr/sg7/test/temp/ -type f)
while read -r -d$'\0' file
do
  ed -s "$file" <<< 'g/PAPU_INDEX 36/-42,+144d
                     w'
done < <( find /appl/virtuo/gways/config/ericsson-hlr/sg7/test/temp/ -iname '*P_SGSN_SESSION_MANAGEMENT*' -type f -print0 )
mv /appl/virtuo/gways/config/ericsson-hlr/sg7/test/temp/* /appl/virtuo/gways/config/ericsson-hlr/sg7/test/output_d/
```

---

### Post by Vaphell on 2012-08-07
my bad
```
while read -r **-d $'\0'** file
do
  echo 'g/PAPU_INDEX 36/-42,+144d
        w' | ed -s "$file"
done < <( find /appl/virtuo/gways/config/ericsson-hlr/sg7/test/temp/ -iname '*P_SGSN_SESSION_MANAGEMENT*' -type f -print0 )

```
<<< "string" inside while loop doesn't seem work too well (probably ed gobbled up all input or sometghing - no wonder nobody uses it anymore, it's pita;) ), so i replaced it with piped echo.


```
-pi $(find /appl/virtuo/gways/config/ericsson-hlr/sg7/test/temp/ -type f)
``` i guess there are no spaces in filenames - it would blow up spectacularly if there were. Are these files scattered in different directories that you have to resort to find?

---

### Post by Srdjan01 on 2012-08-07
> **Vaphell said:**
> Are these files scattered in different directories that you have to resort to find?

Files do not have spaces in their names and they are placed in one folder. Script should apply changes and move files to a different folder.

I'll try to test test this tonight and get back to you.

Many thanks,
Srdjan

---

### Post by Vaphell on 2012-08-07
if that's the case, why bother with find at all?
```
sed/perl -i 's/.../.../g; s/.../.../g' /appl/virtuo/gways/config/ericsson-hlr/sg7/test/temp/*
```

same thing with the ed part
```
for file in /appl/virtuo/gways/config/ericsson-hlr/sg7/test/temp/*P_SGSN_SESSION_MANAGEMENT*
do
  ed -s "$file" <<< 'g/PAPU_INDEX 36/-42,+144d
                     w'
done
```

---

### Post by Srdjan01 on 2012-08-08
Vaphell,

You made my life so much easier. :)
This works great.

```
#!/bin/bash
. /etc/profile
for file in /appl/virtuo/gways/config/ericsson-hlr/sg7/test/temp/*P_SGSN_SESSION_MANAGEMENT*
do
  ed -s "$file" <<< 'g/PAPU_INDEX 36/-42,+144d
                     w'
done
```

This problem is solved, I can't find Thread Tools menu to change status.

Thanks,
Srdjan

---

### Post by Vaphell on 2012-08-08
it's just above the first post on the bar with 'Search this thread' and 'Display modes'

---

### Post by Srdjan01 on 2012-08-08
I have another question, if that's ok.

What is the best way to apply the same change to pattern PAPU_INDEX 37 as well? Is it possible to squeeze it into this line

ed -s "$file" <<< 'g/PAPU_INDEX 36/-42,+144d

BR,
Srdjan

---

