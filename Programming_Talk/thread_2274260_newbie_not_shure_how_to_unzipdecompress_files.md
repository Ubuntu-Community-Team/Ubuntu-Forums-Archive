---
title: "newbie not shure how to unzip/decompress files"
date: 2015-04-19
forum: Programming Talk
---

### Post by lance bermudez on 2015-04-19
The code is for 3 different python 3.4 scripts that compress/zip a file called hello.pdf on a windows 7 computer. I can get the file to compress/zip but have not been able to figure out how to uncompress/unzip the file. I want to use python to compress and decompress files/directories because the windows computer is locked and I can not install 7zip but it has python 3.4 installed on it. I seen that python could be used to compress files using the "import lzma, bz2, gzip" modules. I have read the man and it went right over my head so I was hopping that someone could show me an example of how to unzip/decompress at least one of the files below please.

for gzip
```

import gzip
with open(r"C:\Users\l_bermudez\Music\hello.pdf", "rb") as file_in:
    # Open output file.
    with gzip.open(r"C:\Users\l_bermudez\Music\hello.gzb") as file_out:
        # Write output.
        file_out.writelines(file_in)

```

for lzma
```

import lzma
with open(r"C:\Users\l_bermudez\Music\hello.pdf", "rb") as file_in:
    # Open output file.
    with lzma.open(r"C:\Users\l_bermudez\Music\hello.lzmab") as file_out:
        # Write output.
        file_out.writelines(file_in)

```

for bz2
```

import lzma, bz2, gzip
with open(r"C:\Users\l_bermudez\Music\hello.pdf", "rb") as file_in:
    # Open output file.
    with bz2.open(r"C:\Users\l_bermudez\Music\hello.bz2", "wb") as file_out:
        # Write output.
        file_out.writelines(file_in)

```

---

### Post by lance bermudez on 2015-04-20
Below is what I was trying to do.

for compressing
```

import lzma, bz2, gzip, zipfile

# Open source file.
with open(r"C:\Users\l_bermudez\Music\hello.pdf", "rb") as file_in:
    # Open output file.
    with gzip.open(r"C:\Users\l_bermudez\Music\hello.gz", "wb") as file_out:
        # Write output.
        file_out.writelines(file_in)

with open(r"C:\Users\l_bermudez\Music\hello.pdf", "rb") as file_in:
    # Open output file.
    with lzma.open(r"C:\Users\l_bermudez\Music\hello.lzma", "wb") as file_out:
        # Write output.
        file_out.writelines(file_in)

with open(r"C:\Users\l_bermudez\Music\hello.pdf", "rb") as file_in:
    # Open output file.
    with bz2.open(r"C:\Users\l_bermudez\Music\hello.bz2", "wb") as file_out:
        # Write output.
        file_out.writelines(file_in)
#
'''making zip file'''
#
file_name = "hello.zip"
items = (r"C:\Users\l_bermudez\Music\hello.pdf")
#write file
zip_archive = zipfile.ZipFile(file_name, "w", compression=ZIP_DEFLATED, allowZip64=True)
#follows the whole tree in items path name
zip_archive.write(items)
zip_archive.close()


```


for decompressing
```

import bz2, gzip, lzma

#for bz2
#for compressed file
inF = bz2.open(r"C:\Users\l_bermudez\Music\hello.bz2", 'rb')
#file after decompressed
outF = open(r"C:\Users\l_bermudez\Music\hello_bz2.pdf", 'wb')
outF.write( inF.read() )
inF.close()
outF.close()

#for gzip
#for compressed file
inF = gzip.open(r"C:\Users\l_bermudez\Music\hello.gz", 'rb')
#file after decompressed
outF = open(r"C:\Users\l_bermudez\Music\hello_gz.pdf", 'wb')
outF.write( inF.read() )
inF.close()
outF.close()

#for lzma
#for compressed file
inF = lzma.open(r"C:\Users\l_bermudez\Music\hello.lzma", 'rb')
#file after decompressed
outF = open(r"C:\Users\l_bermudez\Music\hello_lzma.pdf", 'wb')
outF.write( inF.read() )
inF.close()
outF.close()

#for zip
    #in dir ware zip file is
file_name = "hello.zip"
    #read file
zip_archive = zipfile.ZipFile(file_name, "r")
    #extract single file
zip_archive.extract("Users/l_bermudez/Music/hello.pdf", r"C:\Users\l_bermudez\Music\1hello")
zip_archive.close()


```

---

### Post by spjackson on 2015-04-21
By simply changing the filenames, your code works for me on Linux.
```

$ cat compress.py 
import gzip
with open(r"in.sql", "rb") as file_in:
    # Open output file.
    with gzip.open(r"out.sql.gz", "wb") as file_out:
        # Write output.
        file_out.writelines(file_in)
$ python3 compress.py 
$ ls -l
total 16184
-rw-r--r-- 1 spj users      189 Apr 21 08:54 compress.py
-rw-r--r-- 1 spj users      198 Apr 21 08:58 decompress.py
-rw-r--r-- 1 spj users 15375558 Apr 21 08:51 in.sql
-rw-r--r-- 1 spj users  1187797 Apr 21 09:03 out.sql.gz
$ cat decompress.py 
import bz2, gzip, lzma

#for gzip
#for compressed file
inF = gzip.open(r"out.sql.gz", 'rb')
#file after decompressed
outF = open(r"out.sql", 'wb')
outF.write( inF.read() )
inF.close()
outF.close()

$ python3 decompress.py 
$ ls -l
total 31200
-rw-r--r-- 1 spj users      189 Apr 21 08:54 compress.py
-rw-r--r-- 1 spj users      198 Apr 21 08:58 decompress.py
-rw-r--r-- 1 spj users 15375558 Apr 21 08:51 in.sql
-rw-r--r-- 1 spj users 15375558 Apr 21 09:03 out.sql
-rw-r--r-- 1 spj users  1187797 Apr 21 09:03 out.sql.gz

```
You haven't said what problems you get when you run your code. I don't have a Windows machine with python3 on it, so I can't try it on there. Maybe your problem is the backslashes, but you say that compression works.

Here are some examples from my working code of dealing with pathnames on Windows in python2.
```

    os.chdir("C:/Documents and Settings/All Users/Application Data")
    archive = os.environ['HOMEDRIVE'] + os.environ['HOMEPATH'] + "\\Desktop\\" + archive
    ZipPath      = "C:\\bin\\zip"

```

I hope this helps.

---

