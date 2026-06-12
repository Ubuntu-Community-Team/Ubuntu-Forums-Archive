---
title: "How to install winrar4.0.1.tar.gz"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by SkyLinePH on 2011-11-29
Hi, can i ask how to install winrar4.0.1.tar.gz, I download the file but I don't know how to install it. I'll wait for your comments, Thanks. :popcorn:

---

### Post by wolfen69 on 2011-11-29
Can I ask why you want winrar on linux? If you install **p7zip-full** and **p7zip-rar**, you will have pretty much everything you will need for unzipping and unraring.

---

### Post by sadaruwan12 on 2011-11-29
If you just want extract .rar files then you can use the free unrar tool which is available in the repo's you can install it by running the below code.

```
$ sudo apt-get install unrar
```

If you want to create rar files you can the CLI tool p7zip or you can peazip which is a good archive program available for linux. Can get a .deb file from their website.

---

### Post by SkyLinePH on 2011-11-30
I want winrar because i have a license of it.

---

### Post by dolphin194 on 2011-11-30
I think i understand you completely: you want to be able to *compress* items in RAR format under Linux. There actually is no need to install this application. Go ahead and open a Terminal, you're going to need it.

1) Unzip the tarball (Either with GUI or Terminal)
```
cd ~/Downloads
tar -zxvf winrar4.0.1.tar.gz
```2) Change the permissions of the RAR file to allow execution
```
cd RAR
chmod +x RAR
```3) You can now execute the RAR file
```
./rar
```

---

