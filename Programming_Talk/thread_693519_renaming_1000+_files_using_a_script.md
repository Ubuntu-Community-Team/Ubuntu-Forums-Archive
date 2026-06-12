---
title: "renaming 1000+ files using a script"
date: 2008-02-11
forum: Programming Talk
---

### Post by mkendall on 2008-02-11
I have a folder with 1000+ files. I want to rename each file by *pre-*pending (appending to the front) a code nique to each file, while otherwise keeping the file name. The pre-pend would be "a1-", "b1-", "c1-", ... , "z1-", "a2-", "b2-", .... So that if the first three files were **File1**, **File2**, and **File3**, afterwards they would be named **a1-File1**, **b1-File2**, and **c1-File3**, while the 54th file would be **b3-File54**. 

Any help on this will be greatly appreciated; I'm *really* not looking forward to the prospect of renaming "by hand."

Matthew

---

### Post by ghostdog74 on 2008-02-11
```

#!/bin/sh
awk 'BEGIN{
    cmd = "ls -1 | wc -l"  #get count of total files in directory
    cmd | getline count
    close(cmd)
   # this part creates the a1, b1 ...and store in array
   # ----------------------------------------------------------------------------
    l="abcdefghijklmnopqrstuvwxyz"
    n=split(l,letters,"")
    for ( i=1;i<=count;i++ ) {
        for ( j=1;j<=n;j++){
            array[++c]=letters[j] i         
        }
    }  
    # end creating a1, b1.....
    #--------------------------------------------------------------------
    # main
    while (( "ls -1" | getline file ) > 0 ) {
      d++
      cmd = "mv \047" file "\047 \047"  array[d] "-" file "\047" #create the command to rename file
      print cmd #check command is correct
      #system(cmd) #uncomment to rename files
    }
    close("ls -1")
}' 


```

read the 3rd link ( especially Appendix C.2 ) from my sig.

---

### Post by mkendall on 2008-02-11
Script worked beautifully and link is bookmarked for further perusal. Thank you very much.

Matthew

---

