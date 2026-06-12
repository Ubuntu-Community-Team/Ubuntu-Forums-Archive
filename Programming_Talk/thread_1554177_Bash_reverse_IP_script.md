---
title: "Bash: reverse IP script"
date: 2010-08-16
forum: Programming Talk
---

### Post by PryGuy on 2010-08-16
Hello!
I wrote the following piece of code in bash that I need for my script:```
#!/bin/bash

reverseIP() {
  OLD_IFS="$IFS"
  IFS="."
  ARRAY=($1)
  IFS="$OLD_IFS"
  r=0
  for (( i=${#ARRAY[@]}; i>=0; i-- ));
  do
    f[$r]=${ARRAY[$i]}
    ((r++))
  done
  echo ${f[@]} | tr " " "."
}
echo `reverseIP 192.168.0`
```Is there a way to poish it? Thanks in advance!

---

### Post by geirha on 2010-08-16
```
#!/bin/bash

reverseIp() {
    local a i n
    IFS=. read -r -a a <<< "$1"
    n=${#a[@]}
    for (( i = n-1; i > 0; i-- )); do
        printf '%s.' "${a[i]}"
    done
    printf '%s' "${a[0]}"
}
reverseIp 192.168.0

```

---

### Post by soltanis on 2010-08-17
```

reverseIp() {
echo "$1" | awk 'BEGIN{FS=".";ORS="."} {for (i = NF; i > 0; i--){print $i}}'
}

```

---

### Post by PryGuy on 2010-08-17
> **geirha said:**
> ```
#!/bin/bash

reverseIp() {
    local a i n
    IFS=. read -r -a a <<< "$1"
    n=${#a[@]}
    for (( i = n-1; i > 0; i-- )); do
        printf '%s.' "${a[i]}"
    done
    printf '%s' "${a[0]}"
}
reverseIp 192.168.0

```
Thanks a lot!

---

### Post by PryGuy on 2010-08-17
> **soltanis said:**
> ```

reverseIp() {
echo "$1" | awk 'BEGIN{FS=".";ORS="."} {for (i = NF; i > 0; i--){print $i}}'
}

```
Great solution, thanks!

---

### Post by ghostdog74 on 2010-08-17
here's a one liner for you
```


$ echo "192.168.10.2"|awk -F"." '{for(i=NF;i>0;i--) printf i!=1?$i".":"%s",$i}'
2.10.168.192


```

---

### Post by va.vworker on 2011-07-30
really it is great solution on    [reverse ip]("http://www.ipfingerprints.com/reverseip.php") topic :)

---

