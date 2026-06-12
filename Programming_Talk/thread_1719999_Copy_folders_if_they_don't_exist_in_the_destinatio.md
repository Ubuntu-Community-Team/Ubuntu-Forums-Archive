---
title: "Copy folders if they don't exist in the destination?"
date: 2011-04-02
forum: Programming Talk
---

### Post by Coume on 2011-04-02
Hello,

I am trying to cleanup all my files and consolidate them on my NAS...

I have Music on several computers right now and many are duplicates.

Let's say:
Computer1
Dir_A
Dir_C
Dir_E
Dir_F
Dir_H

Computer2
Dir_A
Dir_B
Dir_D
Dir_F
Dir_G
Dir_H

How could I copy folders from Computer2 to Computer1 only if foldername from Comp2 doesn't exist on Computer1?

So basically, only the following would get copied
Computer2
Dir_A - Not copied as exist
Dir_B - Copied to Computer 1
Dir_D - Copied to Computer 1
Dir_F  - Not copied as exist
Dir_G - Copied to Computer 1
Dir_H - Not copied as exist

Thanks in advance.
Ludo

---

### Post by hakermania on 2011-04-02
NOt tested, but it should work....
```
#!/bin/bash
ls /PATH/TO/THE/1ST/COMPUTER > 1st_cmp_all_folders #writing the folders to a file (the ones of the 1st computer)
ls /PATH/TO/THE/2ND/COMPUTER > 2nd_cmp_all_folders #writing the folders to a file (the ones of the 2nd computer)
lines_1st_cmp=$(wc -l < 1st_cmp_all_folders) #getting the lines of the file containing the folders of the 1st computer so as to create a loop between them
for ((i=1; i<=$lines_1st_cmp; i++)); do
folder_name_1st_cmp=$(sed -n "${i}p;${i}q" 1st_cmp_all_folders) #take the 1st, 2nd.... $i line of the file containing the folders of the 1st computer
if [ X"$(grep "$folder_name_1st_cmp" 2nd_cmp_all_folders)" = X"" ]; then #if the line doesn't exist to the file of the 2nd computer's folder, copy it there...
cp -r "$folder_name_1st_cmp" /PATH/TO/THE/2ND/CMP
fi
done
#remove the tmp files used...
rm 1st_cmp_all_folders 2nd_cmp_all_folders
```
Note that you should make the example as you wish (i think I placed cmp_1 and cmp_2 oppositely), so be careful and correct the paths.
Test it first as an example, then _***create a backup***_ of the folders and after this run the script!

---

### Post by Coume on 2011-04-03
Thanks a lot.

It was just missing the source dir in the following line:
```
 cp -r "$folder_name_1st_cmp" /PATH/TO/THE/2ND/CMP
```

I have expended the script to enter arguments etc so it will save me hours!!!

Thanks

---

### Post by hakermania on 2011-04-03
No problem, please mark the thread as solved

---

