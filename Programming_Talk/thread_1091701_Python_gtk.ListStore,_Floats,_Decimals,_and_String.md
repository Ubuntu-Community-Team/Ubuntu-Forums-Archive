---
title: "Python: gtk.ListStore, Floats, Decimals, and Strings"
date: 2009-03-09
forum: Programming Talk
---

### Post by davidcaiazzo on 2009-03-09
Hi I currently have a problem with a list of floats that I want to display in a tree view in a gtk application I am writing. When ever I pass a rounded float to the Liststore it is trailed with 5 or 6 zeros. I understand round isn't a accurate representation of a rounded number so 00001 or 0005 or something to that tune will be added when I return a function that gets the float in question. Passing it as a string to the LinkStore gets rid of this problem, but when I sort the list in my tree view any number larder than 9 begins at the top. For example it would display like this:
.5
.6
.10
13.32
1.55
2.66
4.23
I was told, and after reading some articles online, that I should try decimals, however whenever I try to add a Decimal to the gtk link store it gives me a error on a unknown type. Does anyone know how I might solve this problem?

---

### Post by simeon87 on 2009-03-09
I'm not familiar with gtk.ListStore but perhaps you can manually handle the sorting, i.e., sort the content yourself by the numerical value, then convert to string and insert them in the correct order (and maintain this order while actions are performed on the data).

---

### Post by davidcaiazzo on 2009-03-09
Sorry, when I meant sort it was so the user can display the data in increasing or decreasing order by clicking the colum title.

---

### Post by WW on 2009-03-09
Disclaimer:  This "answer" is based on a preliminary reading of some of the pygtk docs, not actual experience.

According to the [gtk.ListStore documentation](http://www.pygtk.org/docs/pygtk/class-gtkliststore.html), it implements the [gtk.TreeSortable](http://www.pygtk.org/docs/pygtk/class-gtktreesortable.html) interface. This means you can use the [gtk.TreeSortable.set_sort_func](http://www.pygtk.org/docs/pygtk/class-gtktreesortable.html#method-gtktreesortable--set-sort-func) function to define your own sort function.  Your sort function could do something like
```

    if float(string1) < float(string2):
        return -1
    elif float(string1) > float(string2):
        return 1
    else
        return 0

```

---

