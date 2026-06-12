---
title: "Read a text file column  by column  in bash loop"
date: 2010-12-10
forum: Programming Talk
---

### Post by aliahsan81 on 2010-12-10
Hi All

I have file xxxx.txt i want to read file column by column in bash loop up till  now i have done

```

##### merge two file by column 
paste file1 file2 > xxxx.txt 



for i in ` cat $xxxx.txt `
        do
        

#echo $i
    live=$(echo $i | awk -F " " '{print $1}')
    home=$(echo $i | awk -F " " '{print $2}')

echo $live

done

```


but its not working as i suppose.Can any one help me out

file formate is


AAAAAAAAA      BBBBBBBB
CCCCCCCCC      DDDDDDDDD

---

### Post by DaithiF on 2010-12-10
```
while read live home
do
  echo "Live is $live"
  echo "Home is $home"
done < xxxx.txt

```

---

