---
title: "7-zip file compressed, can't open."
date: 2012-09-03
forum: New to Ubuntu
---

### Post by KL_72_TR on 2012-09-03
Hello
Yesterday in WindowsXP I compressed some files with 7-zip
Today in Ubuntu I can't open them. The files have .7z extension.
I installed 7-zip:
```
sudo apt-get install p7zip
```And than tried to open them:
```
p7zip -d filename.7z
```But instead i got this error while loading the archive

Command line output
> 7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Error: /media/USB_2/filename.7z: Can not open file as archive

Errors: 1Can not open file as archive - How can I open it, what can I do?

---

### Post by ajgreeny on 2012-09-03
You need to install **p7zip-full** not **7-zip** as you said, and should then be able to open a compressed file of that type.

Unless, of course, a file 7zipped in windows is different from one 7zipped in Linux.

Is there even a **7-zip** package available?  Perhaps that was a typo in your post?

---

### Post by KL_72_TR on 2012-09-03
> **ajgreeny said:**
> You need to install **p7zip-full** not **7-zip** as you said, and should then be able to open a compressed file of that type.I beg your pardon, for not showing I did that too.
Now I'm looking at Synaptic Package Manager, under **p7zip** it gives me five packages installed:
p7zip, p7zip-rar, p7zip-full, liblzma5, liblzma-dev.
But yet Archive Manager or command line can't open these files.
> Is there even a **7-zip** package available?  Perhaps that was a typo in your post?You are right. My mistake. Sorry.

---

### Post by NikTh on 2012-09-03
Hello, 

did you try ```
7z e filename.7z
```

or 

right click on the file and "Extract here" 

Thanks

---

### Post by jerome1232 on 2012-09-03
I'm firing in the dark but try running a test on the archive as well

```
7z t *archive.7z*
```

---

### Post by KL_72_TR on 2012-09-03
```
7z e filename.7z
```and also Right Click > Extraclt Here, all keep producing the same output:
> me@computer:/media/USB_2$ 7z e filename.7z*

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: filename.7z

Error: Can not open file as archiveI was thinking about what _**ajgreeny**_ said. Maybe in Windows compression is different from Linux
I experimented with some other files here, both from the command line and GUI.
And I was able to compress > open-view > extract without problems at all.
```
7z t archive.7z
```I'll try it right away.
OK I did it, but unfortunately with the same result: Error: Can not open file as archive.

---

### Post by KL_72_TR on 2012-09-03
Sorry for mentioning this now.
When compressing in Windows I changed some of the options: Word size = 250, Dictionary size ~ 64MB (I think so, or maybe more).
Do they have any effect on this problem?

---

### Post by jerome1232 on 2012-09-03
p7zip is a port of 7zip for windows, I would think their capabilities are the same.

Have you verified that the archive was in working order from Windows? The archive could simply be corrupt.

---

