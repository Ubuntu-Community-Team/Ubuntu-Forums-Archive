---
title: "Can't seem to get sh installed through terminal"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by oldstumpy on 2011-10-18
Hi: Everyone this is what i get when i try to install sh in the terminal these are my scanner drivers for my canon pixma420 all in one i try to scan but all the scanner programs do is try and find scanner but can't.Any help would be appreciated Thanks oldstumpy:( An error occurred. The package management system cannot be identified. 
/home/john/Linux IJ Scanner Driver MX420/scangearmp-mx420series-1.70-1-deb/install.sh: line 337: [: =: unary operator expected 
================================================== 

ScanGear MP Ver.1.70-1 for Linux 
Copyright CANON INC. 2007-2011 
All Rights Reserved. 

================================================== 
dirname: extra operand `IJ' 
Try `dirname --help' for more information. 
An error occurred. The package management system cannot be identified.

---

### Post by surfer on 2011-10-18
did you try to run the script with bash instead? i mean:
```

$ bash install.sh

```

or could you post the first line of the script?

---

### Post by dethorpe on 2011-10-18
> **oldstumpy said:**
>  
================================================== 
dirname: extra operand `IJ' 
Try `dirname --help' for more information. 
An error occurred. The package management system cannot be identified.
 
This error makes me think the install script isn't handling the directory having spaces in it. 
 
Try renaming "/home/john/Linux IJ Scanner Driver MX420" to remove the spaces. e.g. to just "/home/john/LinuxIJScannerDriverMX420"

---

### Post by oldstumpy on 2011-10-18
yes i did try bash also here is the first line of the script i **Think**  /home/john/Linux IJ Scanner Driver MX420/scangearmp-mx420series-1.70-1-deb/install.sh

---

### Post by CharlesA on 2011-10-18
Run this in a terminal please:

```
cat "/home/john/Linux IJ Scanner Driver MX420/scangearmp-mx420series-1.70-1-deb/install.sh" | head -n 1
```

It's probably having a problem cuz of the spaces in the path.

---

### Post by oldstumpy on 2011-10-18
Hi: CharlesA ran what you said and this is what i got Thanks for the try john@john-desktop:~$ cat "/home/john/Linux IJ Scanner Driver MX420/scangearmp-mx420series-1.70-1-deb/install.sh" | head -n 1
cat: /home/john/Linux IJ Scanner Driver MX420/scangearmp-mx420series-1.70-1-deb/install.sh: No such file or directory
john@john-desktop:~$

---

### Post by oldstumpy on 2011-10-18
Also tried to run with bash this is what i got john@john-desktop:~$ bash'/home/john/install.sh' 
bash: bash/home/john/install.sh: No such file or directory
john@john-desktop:~$

---

### Post by CharlesA on 2011-10-18
Hrm, not sure why that error showed up.

Does the file exist in that directory?

---

### Post by oldstumpy on 2011-10-18
Yes it is in my home folder

---

