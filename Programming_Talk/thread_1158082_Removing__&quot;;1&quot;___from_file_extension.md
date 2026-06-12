---
title: "Removing  &quot;;1&quot;   from file extension"
date: 2009-05-13
forum: Programming Talk
---

### Post by kulkarniniraj on 2009-05-13
Hello
   Help me in writing a shell script cause it's been long time since I used to write shell scripts so i forgot linux commands.

 Actually I just downloaded a game setup (which runs on windows).I want to run it through wine on ubuntu.

The problem is that every file in that setup has an extra symbol ';1' after filename eg AUTORUN.exe;1  setup.exe;1 etc. I dont know if windows recognises it but wine is not. 

    So I want to write a shell script which would remove these 2 extra characters from each filename, recursively from subfolders also.

  Can anybody help me please.

---

### Post by apmcd47 on 2009-05-13
```
for f in *\;1
do
   mv ${f} ${f%;1}
done
```

Note the \ to escape the semicolon, otherwise it assumes a second command on the command line. If the semicolon suffix contains other characters change the 1 to a * in both the for and mv lines.

Andrew

---

### Post by Elfy on 2009-05-13
Duplicate here - [http://ubuntuforums.org/showthread.php?p=7271073](http://ubuntuforums.org/showthread.php?p=7271073)

Please do not post duplicates

---

