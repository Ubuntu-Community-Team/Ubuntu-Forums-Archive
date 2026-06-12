---
title: "converting a couple of files using switch case loop ?"
date: 2010-07-26
forum: Programming Talk
---

### Post by Doxxer on 2010-07-26
Hi guys 
at first im totally new to programming and linux stuff.

I need help with a switch case loop that should convert some files (.jpg .png etc to .pdf) using the imagemagick convert command and later on convert doc, xls etc to pdf using the JODConverter.
i am using the shell of ubuntu ("bash" i think)

so the basic script should somewhat look like:

 #!/bin/bash
for i in "/my_folder"
switch "no idea"

case .jpg  
do    convert  test.jpg  basename.pdf 
#if not do nothing

case .png

do convert test2.png basename.pdf
#if not do nothing

done
 
and so on ...

sorry i dont have much exp. with programming and stumbled my way through some of the tutorials but none of them referred to such a problem

i would be really glad if you could help me with the syntax 
all i was said is that it should be a for i in / do  switch  case script that should convert those files into .pdf
(folder if this or another doesnt matter... i think i can change that afterwards)

sorry for my bad english 
and thanks for any help in advance 
Greets Doxxer

---

### Post by ghostdog74 on 2010-07-26
```

#!/bin/bash
cd /tmp/myfoler
shopt -s nullglob
shopt -s nocaseglob
for file in *.jpg *.png
do
  convert "$file" "${file%.???}.pdf"  #check the syntax yourself
done

```

---

### Post by Doxxer on 2010-07-26
Wow that was fast and so easy ive tried so many things with basename to keep the original name.. had errors that he took just one file and converted it and ... yeah ..

well it works perfectly now 

thank you again for the fast reply 

greets Doxxer

---

