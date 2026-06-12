---
title: "Restrict result on ls and use this on array"
date: 2017-09-01
forum: New to Ubuntu
---

### Post by sed_faster on 2017-09-01
Hello folks,

How can I restrict search through command ls and put this content on array?
I have this code
```

array=($(ls !(*.sh) ))
for (( i=0; i<${#array[@]}; i++ ));
do
    echo ${array[$i]}
    echo $name_image$i.${array#*.}
    
done


```
but when I try use array inside the loop I received this message error:
```

./script.sh: command substitution: line 34: syntax error near unexpected token `('
./script.sh: command substitution: line 34: `ls !(*.sh) )'

```

How can I solve this error?
Thanks

---

### Post by SeijiSensei on 2017-09-02
```
ls | grep -v \.sh$
```
returns files not ending in .sh.  You might want to add the "-1" switch to ls to get one filename per line.

Also, do you have files with embedded spaces?  They need special treatment in code like this.

---

