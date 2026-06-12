---
title: "File not found in ubuntu (Firefox, it's alright in chrome but chrome sucks in ubuntu"
date: 2022-08-22
forum: New to Ubuntu
---

### Post by rirelguvatbaohagh on 2022-08-22
So  here's what happens.


I boot on my computer.


I read pdfs located in other drives i.e D;, E;, F: drives where the OS isn't installed.


Then I either bookmark the pdf in bookmark or set the browser "open the last opened pages on startup".


Then I close the computer.


Now, I again start the computer next day.


Now the files don't open. It shows this error.


> File not found


Firefox can’t find the file at /media/username/2A84B1604F54EF23/myfolder/myfile/mytopic/mysubtopic/mybookname.pdf.


Check the file name for capitalization or other typing errors.
Check to see if the file was moved, renamed or deleted.




Ofc, Neither the name is error, nor the file has been moved. That's why I'm asking the question.


How to fix this error?








Edit: The problem with chrome is that it absolutely suck in Ubuntu. So, please also give me a code terminal about how to download chromium browser for ubuntu. I'll uninstall chrome then.

---

### Post by mIk3_08 on 2022-08-23
> **rirelguvatbaohagh said:**
> So  here's what happens.


I boot on my computer.


I read pdfs located in other drives i.e D;, E;, F: drives where the OS isn't installed.


Then I either bookmark the pdf in bookmark or set the browser "open the last opened pages on startup".


Then I close the computer.


Now, I again start the computer next day.


Now the files don't open. It shows this error.






Ofc, Neither the name is error, nor the file has been moved. That's why I'm asking the question.


How to fix this error?








Edit: The problem with chrome is that it absolutely suck in Ubuntu. So, please also give me a code terminal about how to download chromium browser for ubuntu. I'll uninstall chrome then.
Just try the command below to install chromium browser. Regards and cheers
```
sudo apt install chromium-browser
```

---

### Post by Impavidus on 2022-08-23
It looks like the partition with that file wasn't mounted automatically at boot time. You can click it in the file manager to mount it. For a more convenient solution, assuming these partitions are on internal hard drives, you can mount them automatically at boot time: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Normally, fstab isn't used to mount things in /media/username, as it can confuse other tools. Unfortunately, on the latest releases of Ubuntu, Firefox is (for security reasons) very restricted in the directories it can access, so if you mount those partitions in a sensible place, Firefox may not be able to access them.

---

