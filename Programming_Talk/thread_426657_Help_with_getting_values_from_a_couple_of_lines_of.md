---
title: "Help with getting values from a couple of lines of grep output."
date: 2007-04-28
forum: Programming Talk
---

### Post by musther on 2007-04-28
I've currently got a loop looking like this:

```
for i in $( mountread | grep --regexp="/dev/hd" --regexp="/dev/sd" ); do
sudo tune2fs -l /dev/sda2 | grep --regexp="Mount count:" --regexp="Maximum mount count:"
done
```

It outputs these two lines (pure loop iteration):

```
Mount count:              15
Maximum mount count:      25

```

What I need to do is get those numbers into variables so that I can compare them with an if statement.


Thanks

---

### Post by raja on 2007-04-28
Someone who know bash better may come along to help us better. However, I think the following should do what you want

```
mountcount=$(sudo tune2fs -l /dev/sda2 | grep --regexp="Mount count:" | tr -d "Mount count:")

if [ "mountcount" -le 20 ]
  then
     echo "mount count is smaller than 21"
fi
```

---

### Post by musther on 2007-04-29
Thankyou, I need the tr command!

---

