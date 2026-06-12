---
title: "python substring to instance [i should know this]"
date: 2009-12-22
forum: Programming Talk
---

### Post by Hume's doona on 2009-12-22
I know I should knoow this. I have a large xml file to convert to plain text, I just havve a simple question about substrings. Given the example:

[HTML]<greeting>hello world</greeting><greeting>hello mars</greeting><greeting>hello jupiter</greeting><greeting>hello saturn</greeting><greeting>hello neptune</greeting>[/HTML]

How do I extract the second substring between the same brckets of <greeting>?

For the first, I knoow I use:

[PHP]y=str(x)[str(x).find("<greeting>")+1:str(x).find("</greeting>")]
[/PHP]

How do I then extract the second <greeting> to assign it to an instancce of the object greeting()?

I feel really stoopid asking this :oops:

Thanks for any help and happy holidays.

---

### Post by ghostdog74 on 2009-12-22
split on "</greeting>" , and the second index will be your second instance.

---

### Post by Can+~ on 2009-12-22
Or use one of the many XML parsing modules available for Python.

But if it's a one-shot procedure, then I agree with ghostdog.

---

### Post by DaithiF on 2009-12-23
i would use a regex:
```
>>> import re                                                                   
>>> example_string = "<greeting>hello world</greeting><greeting>hello mars</gree
ting><greeting>hello jupiter</greeting><greeting>hello saturn</greeting><greeting>hello neptune</greeting>"
>>> matches = re.findall(r'<greeting>(.*?)</greeting>', example_string)     
>>> matches[1]    
'hello mars'
>>> matches
['hello world', 'hello mars', 'hello jupiter', 'hello saturn', 'hello neptune']

```

---

