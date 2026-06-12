---
title: "Can't open matlab after installed it."
date: 2014-04-06
forum: New to Ubuntu
---

### Post by peng2 on 2014-04-06
Hi , I'm a beginner for ubuntu. I've tried install and unstall Matlab R2013a several times, but still can't open it. 
Here is the way I install it:
1. sudo su #enter the password
2.  cd <the address of the .iso file>
      mkdir matlabTmp
    mount -o loop Matlab801_MacUnix.iso matlabTmp
3. chmod +x install_auto_linux
      ./install_auto_linux

After that matlab automaticaly installed to **/usr/local/MATLAB/R2013a/bin** 
when I using **./matlab** , it appears the error message:[ATTACH=CONFIG]251769[/ATTACH]

If I run it with **sudo ./matlab**, matlab can open and I can use in-built functions. But the I can't my own functions properly.

---

