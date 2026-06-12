---
title: "PDF documents not recognized as such when downloading"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-08-09
I attempted to download my phone bill online ( PDF file) on my acer 4315 laptop running hardy heron 8.04. I got an error message to call customer care. I then right-clicked on the download button for the file and it did not show it as a .PDF but rather as a .gif (just the picture of the bill). 

I thought it may be a lack of a .PDF document saver for Linux so I tried to download the same file on my iMac desktop (with Preview) and it downloaded as a .PDF file without a problem. 

I know I can click on PDF files on the internet on my Ubuntu laptop and they open without a problem. 

My question is what is a good program to use to save PDF documents to my computer. Or is it that I'm missing an add-on for Firefox?

---

### Post by starcannon on 2008-08-09
```
sudo apt-get install acroread acroread-plugins
```

that should do it, if not, then right click the file, and use open with.

---

### Post by Brian_Newbie on 2008-08-09
I tried the command line and got the following in terminal

brian@brian-laptop:~$ sudo apt-get install acroread acroread-plugins
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acroread-escript gcc-3.3-base libstdc++5
Suggested packages:
  mozilla-acroread
The following NEW packages will be installed:
  acroread acroread-escript acroread-plugins gcc-3.3-base libstdc++5
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 46.1MB of archives.
After this operation, 115MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free acroread 8.1.2-0medibuntu6.2
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe gcc-3.3-base 1:3.3.6-15ubuntu6 [151kB]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free acroread-escript 8.1.2-0medibuntu6.2
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free acroread-plugins 8.1.2-0medibuntu6.2
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe libstdc++5 1:3.3.6-15ubuntu6 [292kB]
Fetched 443kB in 1s (237kB/s)   
Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.2-0medibuntu6.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.2-0medibuntu6.2_amd64.deb) 503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_8.1.2-0medibuntu6.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_8.1.2-0medibuntu6.2_amd64.deb) 503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_8.1.2-0medibuntu6.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_8.1.2-0medibuntu6.2_amd64.deb) 503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
brian@brian-laptop:~$ 

Something is missing, it seems?

---

### Post by starcannon on 2008-08-09
In the: 
System->Administration->Software Sources
menu try a different mirror(server) to "Download from:".

then try again, sounds like the server(mirror) that your using is down at the moment, likely for some administrative reason. It'll likely be back up within the day.

P.S. also be sure to try the last line in your dialog:
```
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
```

---

### Post by Brian_Newbie on 2008-08-09
Awesome!!

Thanks a lot starcannon! It worked. The file shows as a PDF now when I downloaded it after I restarted firefox. The file though has a ".do" file extension, whatever that is. 

The important thing though is PDF files (all of my bills) with that file extension .do now download without a problem. 

Thanks again for your advice

---

### Post by starcannon on 2008-08-09
Anytime Brian, and I know its egotistical, but if one of us really helps be sure to click our little blue medal(if you help someone they will click yours as well).

If you need anything else don't hesitate to ask, feel free to PM me if your stuck. If I can help I will, sometimes you may have to wait till I have time, but I always answer my PM's.

---

### Post by Brian_Newbie on 2008-08-09
I just found and clicked on your blue metal/star icon to show my appreciation for your help. 

And yes, I'll definitely keep you in mind if I'm stumped with a problem in the future.

Brian

---

