---
title: "Python: Reading From Resource"
date: 2010-11-27
forum: Programming Talk
---

### Post by Sailor5 on 2010-11-27
Ahoy Sailors!

So I'm developing some Python built software intended for public use. The user will input some preferences which are saved in the Py2Exe built exe as a text resource. Now we're just needed to get the executable to find in itself the stored preferences.

The stored data is in between some tags ```
<0161ENTEREDDATA0161>
```The way I've tried is to get the file to open a handle to itself and use find() to look for these tags and attempt to extract the data. For some unknown reason the script I made using this method didn't work.

Can anyone give an example of how to read text from a resource in a file?

Thanks bye!

---

### Post by mo.reina on 2010-11-27
what are you trying to do?  extract whatever is between the tags?

---

### Post by Sailor5 on 2010-11-27
> **mo.reina said:**
> what are you trying to do?  extract whatever is between the tags?

Yes. Which is stored in the file as a text resource.

---

### Post by debsankha on 2010-11-28
> **Sailor5 said:**
> Ahoy Sailors!

So I'm developing some Python built software intended for public use. The user will input some preferences which are saved in the Py2Exe built exe as a text resource. Now we're just needed to get the executable to find in itself the stored preferences.

The stored data is in between some tags ```
<0161ENTEREDDATA0161>
```The way I've tried is to get the file to open a handle to itself and use find() to look for these tags and attempt to extract the data. For some unknown reason the script I made using this method didn't work.

Can anyone give an example of how to read text from a resource in a file?

Thanks bye!

This will do what you want:
```

import re
re.findall("<0161(.*?)0161>",your_string)

```

---

### Post by DaithiF on 2010-11-28
@Sailor5, your approach seems a little strange to me ... you want to store user preferences within a python script that you're compiling into an exe ... why are you compiling it into an exe, and why wouldn't you use a (separate) config text file?

I ask because your approach seems to me like maybe you're coming from a windows c/c++ programming background where you have resource bundles compiled into exe files.  That isn't typical for python though ... maybe you have good reason for doing it this way but it just seems strange to me.

---

