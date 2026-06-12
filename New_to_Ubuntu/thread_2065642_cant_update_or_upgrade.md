---
title: "cant update or upgrade"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by doctor bob on 2012-10-02
i want to install proxychains on my ubuntu virtual machine but it wont install, i have also tried to update and uppgrade with no success not to mention trawling through google for hours on end for answers, please help, this is so frustrating

---

### Post by cortman on 2012-10-02
Please post the output of

```
sudo apt-get update
```

and

```
cat /etc/apt/apt.conf
```

So we can see what exactly the problem is.

---

### Post by snowpine on 2012-10-02
We can't help unless you show us the errors:

```
sudo apt-get update
sudo apt-get install proxychains
```

---

### Post by doctor bob on 2012-10-02
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i19n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i19n/Translation-en)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname

E: Some index files failed to download.  They have been ignored, or old ones used instead.

and

bash: cat etc/apt/apt.conf: No such file directory

---

### Post by snowpine on 2012-10-02
it should be '/i8n/' not '/i9n/'.

You can fix in your software sources:

```
gksu gedit /etc/apt/sources.list
```

---

### Post by doctor bob on 2012-10-02
bash: cat etc/apt/apt.conf: No such file directory[/QUOTE]

or should i say

cat: /etc/apt/apt.conf: No such file directory

---

### Post by doctor bob on 2012-10-02
> **snowpine said:**
> it should be '/i8n/' not '/i9n/'.

You can fix in your software sources:

```
gksu gedit /etc/apt/sources.list
```

ok can you explain a little more i am totally new to this

---

### Post by doctor bob on 2012-10-02
> **snowpine said:**
> it should be '/i8n/' not '/i9n/'.

You can fix in your software sources:

```
gksu gedit /etc/apt/sources.list
```

/i9n/ was a type error it is /i8n/

---

### Post by snowpine on 2012-10-02
Press Alt+F2 and paste the following command:

```
gksu gedit /etc/apt/sources.list
```

Press Ctrl+H to find & replace. Change:

```
i9n
```

to

```
i8n
```

so instead of:

```
http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i19n/Translation-en
```

it says:

```
http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en
```

Save the file and quit Gedit. Try your update again:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by doctor bob on 2012-10-02
> **doctor bob said:**
> /i9n/ was a type error it is /i8n/

sorry

---

### Post by snowpine on 2012-10-02
Use Edit->Copy and Edit->Paste to avoid typos.

---

### Post by doctor bob on 2012-10-02
what should i do???

---

### Post by snowpine on 2012-10-02
Run the following commands in Terminal and Copy & Paste the complete output back here:

```
sudo apt-get update
sudo apt-get install proxychains
```

---

### Post by Wim Sturkenboom on 2012-10-02
and please put it between code tags like this

[noparse]```
paste the stuff here
```[/noparse]

---

### Post by doctor bob on 2012-10-02
> **snowpine said:**
> Run the following commands in Terminal and Copy & Paste the complete output back here:

```
sudo apt-get update
sudo apt-get install proxychains
```

```
Ign http://security.ubuntu.com precise-security/restricted TranslationIndex  
Ign http://security.ubuntu.com precise-security/universe TranslationIndex    
Err http://extras.ubuntu.com precise/main Sources                            
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com precise/main i386 Packages                      
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com precise/main Translation-en_GB                  
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Err http://extras.ubuntu.com precise/main Translation-en
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://gb.archive.ubuntu.com precise/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com precise/universe TranslationIndex
Ign http://gb.archive.ubuntu.com precise-updates/main TranslationIndex       
Ign http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex 
Ign http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Ign http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Ign http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Err http://security.ubuntu.com precise-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/main Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com precise-security/universe Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-updates/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com precise-backports/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_GB  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_GB  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_GB  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_GB  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_GB  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_GB  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by doctor bob on 2012-10-02
> **snowpine said:**
> Run the following commands in Terminal and Copy & Paste the complete output back here:

```
sudo apt-get update
sudo apt-get install proxychains
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package proxychains
```

---

### Post by snowpine on 2012-10-02
The errors suggest a network problem. Is your virtual machine guest connected to the internet?

---

### Post by doctor bob on 2012-10-02
> **snowpine said:**
> The errors suggest a network problem. Is your virtual machine guest connected to the internet?

yes the VM is fully connected but i access the internet through Tor if that makes any difference

---

### Post by snowpine on 2012-10-02
> **doctor bob said:**
> yes the VM is fully connected but i access the internet through Tor if that makes any difference

Maybe, maybe not--I do not know anything about Tor. The error messages suggest it makes a difference. :)

---

### Post by cortman on 2012-10-02
If you're using tor you need to make sure your system proxy is set- go to System Settings>Network>Proxy and be sure to set it there.
If that doesn't fix it we need to add a line to /etc/apt/apt.conf telling it to use the proxy.

---

### Post by Bufeu on 2012-10-02
> **doctor bob said:**
> yes the VM is fully connected but i access the internet through Tor if that makes any difference
Is the host or VM using Tor?

---

### Post by doctor bob on 2012-10-02
yea thats sorted it, thanks you very much for your help!!

---

### Post by cortman on 2012-10-02
> **doctor bob said:**
> yea thats sorted it, thanks you very much for your help!!

You're welcome. :) Please mark the thread [SOLVED] using the thread tools in the upper right. 
Good luck!

---

