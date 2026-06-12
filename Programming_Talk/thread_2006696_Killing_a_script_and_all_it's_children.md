---
title: "Killing a script and all it's children"
date: 2012-06-19
forum: Programming Talk
---

### Post by milasch on 2012-06-19
I have a script that I call wget to manage the download of large files.

the script is called download.sh

```

#! /bin/bash
wget --quiet --output-document - --tries=1 --timeout=20 $1 > $2

```

when I kill download.sh while wget is still downloading a file, wget won't be killed.

To be more specific, I call download.sh through a python script using:
```

process = subprocess.Popen ...

``` 
and
```

process.terminate

```

to kill it under certain circumstances, but wget doesn't die together with download.sh it.

Help?

---

### Post by milasch on 2012-06-19
Nevermind, I figured that I don't need an external script to be able to pipe to file:

```

        download_script = ['/usr/bin/wget', '--quiet', '--output-document', '-', '--tries=1', '--timeout=20', 'http://some_source/some_file']
        file = open('/some/path/', 'w')
        p = subprocess.Popen(download_script, stdout=file)


```

---

