---
title: "[python] Code critique?"
date: 2011-02-24
forum: Programming Talk
---

### Post by j.bell730 on 2011-02-24
I've just applied for a job. The company applied for sent back a Python test for me to complete. I believe I have finished it, but I would just like to be sure. Can someone please critique my code?

Code here: [http://python.pastebin.com/9vNrbTQV](http://python.pastebin.com/9vNrbTQV)

If you see something that does not function correctly, or unused variables, please tell me.

Thanks.

---

### Post by juancarlospaco on 2011-02-24
Code is great, but they evaluate how it is wrote there ?

like: SheBang, Encoding Declaration, 1 Import per Line, 
More DocStrings and less # comments, 4 blank Lines between Functions are too much i think

---

### Post by johnl on 2011-02-24
Small problem:
```


    if not 'www.' in site:
        # what if site is http://example.com ?           
        site = 'http://www.' + site
        # now we have http://www.http://example.com

```

Big problem:
```

    params = os.environ['QUERY_STRING'].split('&')

    registertime = cursor.execute('SELECT Regtime FROM %s WHERE Email LIKE %s') % (dbname, params[0].split('=')[1])

    # .. more SQL using params via string formatting


```

this looks like a huge SQL injection hole to me.

---

