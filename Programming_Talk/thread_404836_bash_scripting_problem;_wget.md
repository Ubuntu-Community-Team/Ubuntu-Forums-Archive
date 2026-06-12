---
title: "bash scripting problem; wget"
date: 2007-04-08
forum: Programming Talk
---

### Post by weldan on 2007-04-08
Hi,

I want to build a little script which performs to get a mirror lists from two servers and compares it with original one on my box. 

my question is, how to know if wget was failed to get the mirror lists ( no internet connection, servers was down, etc ) . I had try to put return codes but to no avail. here is my script:

```

#!/bin/bash

ROOT_DIR=$(pwd)
PHAILED=666

check() {
bash md5check
}

belek () {
if [ $? -ne 0 ]; then
        echo "return exit, DONE!"
        exit
        else
        echo "return exit, FAILED!"
        exit
fi
}

[ ! -d "dl" ] && mkdir -p dl

cd dl

wget -q --ftp-user=myuser --ftp-password=mypasswd -c -i ../mirror.lst

belek

cd $ROOT_DIR

if [ -f "./dl/update.txt" ]; then
        while read f; do
                MD5=
                FILE=
                MD5=$(echo $f |cut -d ' ' -f 1)
                FILE=$(echo $f |cut -d ' ' -f 2)
                NM=
                if [ -f "dl/$FILE" ]; then
                        echo "OK"
                        NM=$(md5sum ./dl/$FILE)
                fi
                echo "==> $FILE $NM"
        done < ./dl/update.txt
        else
        exit $PHAILED
fi

if [ -f "./dl/mirror.lst" ]; then
        mv mirror.lst mirror.lst.old
        cp -v ./dl/mirror.lst mirror.lst
        else
        exit $PHAILED
fi

check
exit 0

```

can anyone tell me what is wrong with my script? :confused:

---

### Post by bashologist on 2007-04-08
Maybe the following:
```
if ! wget -q --ftp-user=myuser --ftp-password=mypasswd -c -i ../mirror.lst; then exit 1; fi
```
I don't know if that's what you're looking for. Also, you could replace "$(pwd)" with "$PWD". Looks good. What's the error message? I don't understand your use of belek; You execute your function without any parameters? I don't get it. I'm not exactly an expert tho. 

Another way might be:
```
wget -q --ftp-user=myuser --ftp-password=mypasswd -c -i ../mirror.lst || { echo "wget returned false"; exit 666; }
```

---

### Post by weldan on 2007-04-09
how to know if the wget gets an error? such if the files can't be downloaded, or else?

---

