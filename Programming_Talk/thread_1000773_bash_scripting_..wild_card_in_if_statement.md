---
title: "bash scripting ..wild card in if statement"
date: 2008-12-03
forum: Programming Talk
---

### Post by b-boy on 2008-12-03
Hi everyone I writing a simple bash script and the problem I am having is: 
I need to search a file with ip addresses and exec a command for each **excluding the ip address that ends with .254 **which in most cases is the router 
```
for ip in `cat /home/tux/Desktop/file`
do
if [ $ip  = *.254 ];then
echo this is a router
 
done
```
this is not what my script must do but if this works my script will work

---

### Post by ghostdog74 on 2008-12-03
how does your file look like? also describe how you want the output.

---

### Post by b-boy on 2008-12-03
> **ghostdog74 said:**
> how does your file look like? also describe how you want the output.

the file is something like this 
```
10.0.0.1
10.0.0.2
10.0.0.3
10.4.5.12

```

and it goes on


the output i want is if on of those ips end with 254 i must get a msg "this is a router

---

### Post by ghostdog74 on 2008-12-03
```

# awk -F"." '$NF==254{print $0 " is a router"}' file
10.202.101.254 is a router


```

---

### Post by loomsen on 2008-12-03
*.*.*.254 will match any file of this form ending on 254.

---

### Post by geirha on 2008-12-03
You can also use a case statement
```

while read ip; do
  case "$ip" in
    *.254)
      echo "$ip is a router"
      ;;
    *)
      echo "$ip is not a router"
      ;;
  esac
done < /home/tux/Desktop/file

```

---

### Post by slavik on 2008-12-03
the below will produce all lines that do not end with 254

for i in [grep -v "254$" file]; do
  ping -c 1 $i
done

---

### Post by ghostdog74 on 2008-12-03
> **slavik said:**
> the below will produce all lines that do not end with 254

for i in [grep -v "254$" file]; do
  ping -c 1 $i
done

that's wrong syntax
```

for i in `grep -v "254$"` file`
# for i in $(grep -v "254$" file)

```

---

### Post by b-boy on 2008-12-05
sorry about the late reply but thanks for the help

---

