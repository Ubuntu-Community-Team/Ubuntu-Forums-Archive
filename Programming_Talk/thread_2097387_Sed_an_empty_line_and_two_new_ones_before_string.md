---
title: "Sed an empty line and two new ones before string"
date: 2012-12-23
forum: Programming Talk
---

### Post by Intrepid Ibex on 2012-12-23
Hey,

What I'd like to do is to make the ending in the [[COLOR="Blue"]Google Earth script[/COLOR]](http://pastebin.com/Ltnptt5j) look like so (preferably by specifying to add the bolded lines before the line with the string 'googleearth-bin'):

```
[...]

cd $script_path;
[B]
# Fix coordinates for non-US locales
export LC_NUMERIC=en_US.UTF-8[/B]

LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH ./googleearth-bin "$@"


```

Thanks.

---

### Post by Intrepid Ibex on 2012-12-23
Lolness. Well it was just:

```
sed -i "/googleearth-bin/i\# Fix coordinates for non-US locales\nexport LC_NUMERIC=en_US.UTF-8\n" googleearth

```

---

