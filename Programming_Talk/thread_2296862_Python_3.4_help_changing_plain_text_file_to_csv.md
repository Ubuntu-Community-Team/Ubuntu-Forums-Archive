---
title: "Python 3.4 help changing plain text file to csv"
date: 2015-09-29
forum: Programming Talk
---

### Post by lance bermudez on 2015-09-29
Using python3.4

I have 2 plain text file looks like this
```

=========================================================
Starting Quick Hash V 1.2, Ptyhon-Forensics.org

Investigator: Jon Doe
Organization: some place
Case Number : test1
Hash Type   : SHA256
Start Path  : /tmp/rent
System Type : linux
Version     : 3.4.3 (default, Mar 26 2015, 22:03:40) 
[GCC 4.9.2]

Start Time  : Mon Sep 28 14:24:43 2015
Output Selected: /tmp/rent/1424

====================================
File : /tmp/rent/Backup
Size : 179 bytes
SHA256: CBFAFDACDF50B1FDC44C7B458C9F2237F604596D0B8ABF25F68D29B6D120C130
Last Modified : Wed May 13 02:10:21 2015
Last Access   : Mon Sep 28 14:22:43 2015
Created Time  : Mon Sep 28 14:22:43 2015
================================

File : /tmp/rent/Backup_all
Size : 2454 bytes
SHA256: 2027010224997C59B74D103918623046A03E5272E84A781C33D6B8C9C75F4132
Last Modified : Tue Aug 11 23:00:24 2015
Last Access   : Mon Sep 28 14:22:43 2015
Created Time  : Mon Sep 28 14:22:43 2015
================================

```

I have two files with the same info layout as shown above. I need it in csv so I can use excel to search if the Size: SHA256:, Last Modified:, Last Access:, and Created Time: Values have changed for the File:.

How do I go about it? If my thinking is wrong and you have a better idea then please let me know.

---

### Post by codonnel on 2015-09-29
Hi lance,

The first thing you'll need to do is parse your file to extract the information you're interested in. There are a few ways to do this, but probably the most straightforward is to use regular expressions. If you're not familiar with them, you should look through a tutorial like this one: [http://www.regular-expressions.info/tutorial.html](http://www.regular-expressions.info/tutorial.html). Once you have a handle on the **very** basics of regular expressions, take a look at how it's done in python. The first example in [https://docs.python.org/3/library/re.html#re.match.group](https://docs.python.org/3/library/re.html#re.match.group) should be quite similar to what you need.

As an example, you might get the SHA256 attribute with (after reading the file into a string, which I've called contents):
```
sha_regex = re.compile(r"SHA: ([A-F0-9]+)")
sha = re.match(sha_regex, contents).group(1)
```
**Disclaimer: **I didn't test the above code; it might not work perfectly.

I'm not convinced you need to write to a csv file, but I also don't know why you're doing this. If that is what you want to do, you can use a csv writer, which has a couple nice examples in the documentation here: [https://docs.python.org/3/library/csv.html#writer-objects](https://docs.python.org/3/library/csv.html#writer-objects).

---

### Post by Vaphell on 2015-09-30
> I need it in csv **so I can use excel to search** if the Size: SHA256:, Last Modified:, Last Access:, and Created Time: Values have changed for the File:.

wut? Why on earth would you want to use excel? Can't your prog check it for you directly?

---

### Post by lance bermudez on 2015-10-01
Vaphell
Thank your for your help. As shown above I have 2 different file that look like the one given above and I want to be able to search then to find what is the same and what is different. I don't know how to get my program to do that directly that is why I thought to use excel but I have been trying to use the regular expressions. That is unless you know something better.

script code
```

import re
file = open(r'C:\Users\S00019479\Desktop\text0.txt', 'r')
contents = file.read()
file.close()
print(type(contents))
sha_regex = re.compile(r"SHA: ([A-F0-9]+)")
sha = re.match(sha_regex, contents).group(1)

```

script error
```

<class 'str'>
Traceback (most recent call last):
  File "C:\Users\S00019479\Desktop\retest.py", line 7, in <module>
    sha = re.match(sha_regex, contents).group(1)
AttributeError: 'NoneType' object has no attribute 'group'

```

---

### Post by Vaphell on 2015-10-01
```
#!/usr/bin/env python3

import re
import sys

def parse_entry(text):
    result = {}
    lines = [ x for x in text.split('\n') if x ]
    for line in lines:
        try:
            key, value = [ x.strip() for x in line.split(':', 1) ] 
        except ValueError:
            continue  
        result[key] = value 
    return result  


def property_changed(info, prop):
    uniques = {i[1][prop] for i in info}
    return len(uniques) != 1


def item_changed(info): 
     return any(property_changed(info, prop) for prop in info[0][1])


if __name__ == '__main__':
    logfiles = sys.argv[1:] 
    if len(logfiles) != 2:
        print('fail')
        sys.exit()

    items = {}
    for fname in logfiles:
        with open(fname) as f:
            entries = [ x for x in re.split('={10,}', f.read()) if x.strip() ]
            hdr, body = entries[0], entries[1:]
            info = parse_entry(hdr)
            log_ts = info['Start Time'] 
            for entry in body:
                file_info = parse_entry(entry)
                path = file_info['File']
                del file_info['File']
                # del other superfluous properties here
                items.setdefault(path, []).append([log_ts, file_info]) 

    print('changes:')
    for path, info in items.items():
        if item_changed(info):
            print(path)
 

```

example output.

```
$ ./changes.py log*.txt
changes:
/tmp/rent/Backup
```

Requires 2 params and should parse everything there is to parse and produce dicts for each individual entry. It is generalized for any change so any property can trigger message (which means you might want to get rid of some/most properties like times in the appropriate place marked with the comment)

---

### Post by lance bermudez on 2015-10-01
Thank you Vaphell that is what I was trying to do.

---

