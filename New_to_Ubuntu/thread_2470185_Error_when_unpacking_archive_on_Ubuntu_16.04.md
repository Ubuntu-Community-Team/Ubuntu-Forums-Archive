---
title: "Error when unpacking archive on Ubuntu 16.04"
date: 2021-12-21
forum: New to Ubuntu
---

### Post by ross-da on 2021-12-21
I am new to Ubuntu and I face a very strange problem. 
I use Ubuntu 16.04 via wsl 2 on Windows 10.


When I download an archive using wget e.g.,


```
wget https://github.com/protocolbuffers/protobuf/releases/tag/v3.19.1/protoc-3.19.1-linux-x86_64.zip

```

I cannot unpack the file, because
```
unzip protoc-3.19.1-linux-x86_64.zip

```yields


```
Archive:  protoc-3.19.1-linux-x86_64.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of protoc-3.19.1-linux-x86_64.zip or
        protoc-3.19.1-linux-x86_64.zip.zip, and cannot find protoc-3.19.1-linux-x86_64.zip.ZIP, period.

```

Unpacking with
```
jar xvf protoc-3.19.1-linux-x86_64.zip

```

produces even less informative error
```
Ick! 0xa0a0a0a

```

I am sure that the archive is not damaged, because I can download and open it on Windows.


What else I have tried:
- Downloading the archive with curl
- Ubuntu 18.04 and 20.04
- Setting wsl to the version 1
- ...


Maybe the problem is not in Ubuntu but in some Windows or wsl settings... 
If some additional information needed - I will provide. 


Thank you!

---

### Post by Holger_Gehrke on 2021-12-22
'End-of-central-directory signature not found' _usually_ means a broken or incomplete download. But when I tried to download from the URL you gave and examined the file carefully, I found that it's actually a html file containing an error message. Basically: you've got the wrong URL. The right one should be [https://github.com/protocolbuffers/protobuf/releases/download/v3.19.1/protoc-3.19.1-linux-x86_64.zip](https://github.com/protocolbuffers/protobuf/releases/download/v3.19.1/protoc-3.19.1-linux-x86_64.zip)

Holger

---

### Post by ross-da on 2021-12-27
You are right! Thank you for the help!

---

