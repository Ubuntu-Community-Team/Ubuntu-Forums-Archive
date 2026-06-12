---
title: "how to search without order in this way?"
date: 2018-04-10
forum: Programming Talk
---

### Post by zerop2 on 2018-04-10
since
row1 = "search key     words today"
searchresult = re.findall(re.sub(r' ', ' *', r'key wrods', flags=re.IGNORECASE), row1, re.DOTALL)

r and o are exchanged,

then i search without order with (?=


searchresult = re.findall(re.sub(r' ', ' *', r'(?=k)(?=e)(?=y)(?=\ )(?=w)(?=r)(?=o)(?=d)(?=s)', flags=re.IGNORECASE), row1, re.DOTALL)
searchresult
[]

return null

---

### Post by &amp;wP*!) on 2018-04-11
> **zerop2 said:**
> since
row1 = "search key     words today"
searchresult = re.findall(re.sub(r' ', ' *', r'key wrods', flags=re.IGNORECASE), row1, re.DOTALL)

r and o are exchanged,

Is that what you want to achieve above, just to swap two ASCII characters 'r' and 'o' in your text and nothing more? Does following code help you?
```
>>> x = 'search key words today'
>>> re.sub('(o)(r)', r'\2\1', x, count=0, flags=0)
'search key wrods today'
```
It is very difficult to understand from your text below what do you want to do.. Please explain in detail
```
then i search without order with (?=


searchresult = re.findall(re.sub(r' ', ' *', r'(?=k)(?=e)(?=y)(?=\ )(?=w)(?=r)(?=o)(?=d)(?=s)', flags=re.IGNORECASE), row1, re.DOTALL)
searchresult
[]

return null


```

---

### Post by zerop2 on 2018-04-14
i succeed to do

---

