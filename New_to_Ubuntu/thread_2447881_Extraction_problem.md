---
title: "Extraction problem"
date: 2020-07-27
forum: New to Ubuntu
---

### Post by Joe_Linux on 2020-07-27
I have downloaded an iso file of 24.8 gigabytes. From the download site it comes in six files.
STC_VOL1_BR.iso.zip.001.part
STC_VOL1_BR.iso.zip.002.part
STC_VOL1_BR.iso.zip.003.part
STC_VOL1_BR.iso.zip.004.part
STC_VOL1_BR.iso.zip.005.part
STC_VOL1_BR.iso.zip.006.part

The extraction option does not come up for opening any of the zip files when I try to open the file I get the error
Could not display STC_VOL1_BR.iso.zip.001.part
There is no application for "Partially downloaded file" files then it asks if I want to search for another application to open the file

Help would be appreciated thank you in advance 
BTW this is NOT a pirated blu ray iso see URL [https://www.startrekcontinues.com/downloads.html](https://www.startrekcontinues.com/downloads.html)

Thank you (this is a re post It should not have been put in jail)

---

### Post by Joe_Linux on 2020-07-27
If I am doing this incorrectly admin please let me know

---

### Post by jeremy31 on 2020-07-27
Moved to New to Ubuntu as the Resolution Center is not for Ubuntu support

---

### Post by Joe_Linux on 2020-07-27
If I am doing this incorrectly admin please let me know

---

### Post by Joe_Linux on 2020-07-27
jeremy31 
Am I able to re post and get help the blu ray iso is not pirated

---

### Post by wildmanne39 on 2020-07-27
I say wait until an admin posts please.

---

### Post by SeijiSensei on 2020-07-27
Use something like this to concatenate the files, then use unzip.

```

cat test.zip.* >test.zip
zip -FF test.zip --out test-full.zip
unzip test-full.zip

```

See [https://unix.stackexchange.com/questions/40480/how-to-unzip-a-multipart-spanned-zip-on-linux/40481](https://unix.stackexchange.com/questions/40480/how-to-unzip-a-multipart-spanned-zip-on-linux/40481)

Most any question like this can be answered using a Google search.

Apparently 7-Zip, which is available for Linux, can also do this: [https://sourceforge.net/projects/p7zip/](https://sourceforge.net/projects/p7zip/)

---

### Post by GhX6GZMB on 2020-07-27
As it's .iso files, I expect they belong on DVDs. The idea is, that you burn the 6 DVDs. When inserting the first one it will have an indexing mechanism for the rest. Trying to treat this as a multispan .zip will most likely lead nowhere.

---

