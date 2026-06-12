---
title: "[SOLVED] install java jvm 1.6  aka  debian package management"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Bartee on 2008-07-13
I got this downloaded

jdk-6u7-linux-x64.bin 

I found a post about debian packages that gave told me to to this:

[SIZE="4"]apt-get install fakeroot java-package[/SIZE]

and this

[SIZE="4"]fakeroot make-jpkg jdk-6u7-linux-x64.bin [/SIZE]

Which gave me this output

xxxxx@xxxxx-linux:~/MyDownloads/jdk67$ fakeroot make-jpkg jdk-6u7-linux-x64.bin 
Creating temporary directory: /tmp/make-jpkg.Gceur15984
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: amd64
Detected Debian GNU type: x86_64-linux-gnu

No matching plugin was found.
Removing temporary directory: done
xxxxx@xxxxx-linux:~/MyDownloads/jdk67$ 

------------------- end of clip -------------------

So 2 questions how do I get this to install?

and where do I find out out the package manager and how tocreate entries in it?

---

### Post by TSS on 2008-07-13
I think there is an easier way to get you what you want:

```
sudo apt-get install sun-java6-jdk
```

---

### Post by Bartee on 2008-07-13
WOW... what a great answer

yes, this really makes this easy...

With your reply I now know I need to use the "search" feature in the package manager instead of looking for a name.  A search of "java" brought back the listing you provided.

And
Thanks...

What a great group of people.. There are SOOOOOO many messages on this board, someday I hope I can payback ....

---

