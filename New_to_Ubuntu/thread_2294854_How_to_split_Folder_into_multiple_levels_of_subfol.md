---
title: "How to split Folder into multiple levels of subfolders?"
date: 2015-09-14
forum: New to Ubuntu
---

### Post by Zack_Zeals on 2015-09-14
I have found how to split a single folder into several subfolders here -- [http://ubuntuforums.org/showthread.php?t=976447](http://ubuntuforums.org/showthread.php?t=976447) .
I need to be able to do just this but have it split the folder into several levels of subfolders. I have over 3+ million files, and even if I were to only split it into just a single level of subfolders, it's still far too many folders in the parent folder.

Is there a way I can modify the referenced script to also set a limit of only 1500 folders allowed within each level, and have it simply create a new level of subfolders when the threshold of 1500 folders is reached?

;; referenced script ;;
let fileCount=3000
let dirNum=1

for f in *
do
[ -d $f ] && continue
[ $fileCount -eq 3000 ] && {
dir=$(printf "%03d" $dirNum)
mkdir $dir
let dirNum=$dirNum+1
let fileCount=0
}

mv $f $dir
let fileCount=$fileCount+1
done

---

