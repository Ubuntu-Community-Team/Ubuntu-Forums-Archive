---
title: "Python - extract string between two parameters"
date: 2018-03-11
forum: Programming Talk
---

### Post by jsmith613 on 2018-03-11
Hi 

I have the following code in python:
```
start = '<description>'end = '</description>'
s = """
<description>This is the website description</description>
<description>This is the second description</description>
"""
print (s[s.find("<description>")+len("<description>"):s.find("</description>")])



```

How do I extract BOTH the first and second descriptions without the tags? thanks

btw I do not want to use the BeautifulSoup module.
I want to understand the code

---

### Post by norobro on 2018-03-11
For your simple example, the second description can be extracted by changing find to rfind: [https://docs.python.org/3/library/stdtypes.html#str.rfind](https://docs.python.org/3/library/stdtypes.html#str.rfind)


For more complicated searches use re.findall() with a capture group: [https://docs.python.org/3/library/re.html#re.findall](https://docs.python.org/3/library/re.html#re.findall)

---

### Post by jsmith613 on 2018-03-12
Thanks

---

