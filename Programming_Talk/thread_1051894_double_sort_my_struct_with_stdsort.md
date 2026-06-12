---
title: "double sort my struct with std::sort"
date: 2009-01-27
forum: Programming Talk
---

### Post by monkeyking on 2009-01-27
I have structs like
[PHP]
struct dat{
    int chr; \\not unique
    double pos; \\not unique
    int id;
};
[/PHP]
I need to sort these structs twice. First sort them by .chr and for each group of chr sort them by their .pos

I can do a manual sort, but is it possible to use std::sort

thanks.

---

### Post by geirha on 2009-01-27
Just make sure the comparison function checks both fields. I.e First check if the chr fields are equal. If the chr fields are equal, return the comparison between the pos fields. If the chr fields are not equal, return the comparison of the chr fields.

---

### Post by Zugzwang on 2009-01-27
> **geirha said:**
> Just make sure the comparison function checks both fields. I.e First check if the chr fields are equal. If the chr fields are equal, return the comparison between the pos fields. If the chr fields are not equal, return the comparison of the chr fields.

That's the correct idea. See [here]("http://www.cplusplus.com/reference/algorithm/sort.html") for an example of custom comparators for sorting.

---

### Post by monkeyking on 2009-01-27
> **geirha said:**
> Just make sure the comparison function checks both fields. I.e First check if the chr fields are equal. If the chr fields are equal, return the comparison between the pos fields. If the chr fields are not equal, return the comparison of the chr fields.

Thanks, a very nice idea

---

