---
title: "Chromiun crashing"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by yajnamurti on 2012-12-18
Please help!  Chromium is crashing often.

I have opened it last time in the terminal and here is the report:  

yajnamurti@yajnamurti-AO725:~$ chromium-browser
Segmentation fault (core dumped)
yajnamurti@yajnamurti-AO725:~$

---

### Post by HarveyRM on 2012-12-18
This problem creeps up from time to time.
An upgrade should solve it.
If you have the latest version, and still have the problem, then this might be helpful
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/965314/comments/7](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/965314/comments/7)

---

### Post by yajnamurti on 2012-12-19
This is what I got today:


```
yajnamurti@yajnamurti-AO725:~$ chromium-browser
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[3210:3210:4466670232:ERROR:x11_util.cc(1221)] X Error detected: serial 126808, error_code 10 (BadAccess (attempt to access private resource denied)), request_code 139, minor_code 1 (X_ShmAttach)
[3210:3210:4466672616:ERROR:x11_util.cc(1221)] X Error detected: serial 126809, error_code 145 (BadShmSeg (invalid shared segment parameter)), request_code 139, minor_code 5 (X_ShmCreatePixmap)
[3210:3210:4466677089:ERROR:x11_util.cc(1221)] X Error detected: serial 126810, error_code 9 (BadDrawable (invalid Pixmap or Window parameter)), request_code 148, minor_code 4 (RenderCreatePicture)
[3210:3210:4466736478:ERROR:x11_util.cc(1221)] X Error detected: serial 126811, error_code 160 (RenderBadPicture (invalid Picture parameter)), request_code 148, minor_code 8 (RenderComposite)
[3210:3210:4466739570:ERROR:x11_util.cc(1221)] X Error detected: serial 126819, error_code 145 (BadShmSeg (invalid shared segment parameter)), request_code 139, minor_code 2 (X_ShmDetach)
[3210:3210:4466754827:ERROR:x11_util.cc(1221)] X Error detected: serial 126821, error_code 160 (RenderBadPicture (invalid Picture parameter)), request_code 148, minor_code 7 (RenderFreePicture)
[3210:3210:4466755687:ERROR:x11_util.cc(1221)] X Error detected: serial 126822, error_code 4 (BadPixmap (invalid Pixmap parameter)), request_code 54, minor_code 0 (X_FreePixmap)
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
```

---

### Post by HarveyRM on 2012-12-19
If you are using the latest version of Chromium-browser and still have frequent crashes, then I think you should file a bug report.
[http://www.chromium.org/for-testers/bug-reporting-guidelines](http://www.chromium.org/for-testers/bug-reporting-guidelines)
[http://code.google.com/p/chromium/issues/list](http://code.google.com/p/chromium/issues/list)[]("https://launchpad.net/ubuntu/+source/chromium-browser")

---

### Post by yajnamurti on 2012-12-19
> **HarveyRM said:**
> If you are using the latest version of Chromium-browser and still have frequent crashes, then I think you should file a bug report.
[http://www.chromium.org/for-testers/bug-reporting-guidelines](http://www.chromium.org/for-testers/bug-reporting-guidelines)
[http://code.google.com/p/chromium/issues/list](http://code.google.com/p/chromium/issues/list)[]("https://launchpad.net/ubuntu/+source/chromium-browser")

Dear Harvey,

Thank you for your reply. Chromium automatically upgrades when there is a new version, as far as I know.

---

### Post by yajnamurti on 2012-12-20
Today report,


[HTML]yajnamurti@yajnamurti-AO725:~$ chromium-browser
[4581:4581:16833842638:ERROR:x11_util.cc(1221)] X Error detected: serial 96182, error_code 10 (BadAccess (attempt to access private resource denied)), request_code 139, minor_code 1 (X_ShmAttach)
[4581:4581:16833844969:ERROR:x11_util.cc(1221)] X Error detected: serial 96183, error_code 145 (BadShmSeg (invalid shared segment parameter)), request_code 139, minor_code 5 (X_ShmCreatePixmap)
[4581:4581:16833851683:ERROR:x11_util.cc(1221)] X Error detected: serial 96184, error_code 9 (BadDrawable (invalid Pixmap or Window parameter)), request_code 148, minor_code 4 (RenderCreatePicture)
[4581:4581:16833855334:ERROR:x11_util.cc(1221)] X Error detected: serial 96185, error_code 160 (RenderBadPicture (invalid Picture parameter)), request_code 148, minor_code 8 (RenderComposite)
[4581:4581:16833858888:ERROR:x11_util.cc(1221)] X Error detected: serial 96192, error_code 145 (BadShmSeg (invalid shared segment parameter)), request_code 139, minor_code 2 (X_ShmDetach)
[4581:4581:16833863488:ERROR:x11_util.cc(1221)] X Error detected: serial 96261, error_code 160 (RenderBadPicture (invalid Picture parameter)), request_code 148, minor_code 7 (RenderFreePicture)
[4581:4581:16833873001:ERROR:x11_util.cc(1221)] X Error detected: serial 96262, error_code 4 (BadPixmap (invalid Pixmap parameter)), request_code 54, minor_code 0 (X_FreePixmap)
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory[/HTML]

---

### Post by yajnamurti on 2012-12-21
Help Please!

---

### Post by Ymurti on 2012-12-22
I am marking this thread as solved because I have installed Chrome and so far no problem. Thank you all that have posted in this thread.


:KS

---

### Post by lisati on 2012-12-22
> **Ymurti said:**
> I am marking this thread as solved because I have installed Chrome and so far no problem. Thank you all that have posted in this thread.


:KS

To mark a thread as "solved", you can use the "thread tools" drop-down menu.

---

### Post by Temporarily on 2012-12-22
Well , Chrome and Chromium are different projects as far as I know. You didn't manage to solve the problem with Chromium and Installed a new browser . This is not exactly a solved problem. 

The best approach (IMO) would be to insist to solve the problem with Chromium or fill a bug like @HarveyRM suggested. 

Thank you.

---

