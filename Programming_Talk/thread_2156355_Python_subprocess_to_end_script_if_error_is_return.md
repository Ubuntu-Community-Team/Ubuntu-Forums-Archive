---
title: "Python subprocess to end script if error is returned"
date: 2013-06-21
forum: Programming Talk
---

### Post by josiahrulez on 2013-06-21
Hey all,

I'm writing a python script to download a bunch of urls from an xml file. I have it working with wget, but how can i get it to write a log file and stop the script if any errors are returned?

```
import subprocess
downloadlocation = r'c:\users\public\downloads\test.exe'
url = 'http://downloads.sourceforge.net/project/gnuwin32/wget/1.11.4-1/wget-1.11.4-1-setup.exe'
wget = r'C:\Program Files (x86)\GnuWin32\bin\wget.exe'


subprocess.call([wget, '-O', downloadlocation, url, '--progress=bar:force'])
```

How can i do this?

Thanks

---

### Post by Vaphell on 2013-06-21
```
if subprocess.call( ... ) != 0:
  exit(1)
```

---

### Post by MadCow108 on 2013-06-21
or subprocess.check_call which will throw an exception on error

---

### Post by josiahrulez on 2013-06-22
> **Vaphell said:**
> ```
if subprocess.call( ... ) != 0:
  exit(1)
```


Thanks, thats exactly what i wanted

```
import subprocess 

wget = r'C:\Program Files (x86)\GnuWin32\bin\wget.exe'
dl = r'c:\users\public\lol.exe'
url = 'http://downloads.sourceforge.net/project/gnuwin32/wget/1.11.4-1/wget-1.11.4-1-seeeeeerwrwretup.exe'


log = open('log.txt','w')


if subprocess.call([wget, '-O', r"c:\users\public\test.exe", url, '--progress=bar:force']) != 0:
    log.write("Something went wrong with: "+url+"\n\nmore text")
    log.close()
    exit(1)
```

When i run this it fails to download and writes the log file successfully, but in the console it spits out this error 

```
SYSTEM_WGETRC = c:/progra~1/wget/etc/wgetrcsyswgetrc = C:\Program Files (x86)\GnuWin32/etc/wgetrc
--2013-06-22 15:10:23--  http://downloads.sourceforge.net/project/gnuwin32/wget/1.11.4-1/wget-1.11.4-1-seeeeeetup.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-06-22 15:10:24 ERROR 404: Not Found.
```

How can i include the error message given by console in my log file?

---

