---
title: "Cannot download file"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by vegas89 on 2013-01-01
I am running ubuntu 12.04. I have been trying to download a hplip 3.12.11 driver package to run the new HP3512E deskjet all-in-one printer I just purchased. I keep getting this error report as shown on the attachment. I cannot get the file to run. What must I do to correct this problem. I already have a version of hplip on my OS that I installed from the Ubuntu software center. Do I need to uninstall this first.

---

### Post by Cheesemill on 2013-01-01
You don't want to open the run file in a text editor, instead right-click on the link and save the file in your Downloads folder. Then open a terminal and run the following commands:
```
cd ~/Downloads
chmod +x hplip-3.12.11.run
sudo sh hplip-3.12.11.run
```

It's probably a good idea to remove the older version using the software centre first.

---

### Post by vegas89 on 2013-01-01
Thanks for the help. I removed the hplip I had installed then did I think as you said and this is what I have now.  ](*,)

---

### Post by ajgreeny on 2013-01-01
Full instructions are on the hplip site.
[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

---

### Post by ajgreeny on 2013-01-01
> **vegas89 said:**
> Thanks for the help. I removed the hplip I had installed then did I think as you said and this is what I have now.  ](*,)
It was a bad download so you need to download the installer again.

---

### Post by vegas89 on 2013-01-01
Wow , that is a lot to digest for a beginner. I will have a go at it and get back with you later  :confused:

---

### Post by Cheesemill on 2013-01-01
No need to follow the page that ajgreeny linked to, those instructions are for building hplip from source instead of using the run file.

You were spot on with the commands that you tried earlier, just your download was corrupted. Delete the hplip-3.12.11.run file and download it again, then repeat the commands I posted earlier.

---

### Post by vegas89 on 2013-01-01
Got through step 2, but seem to have issues with the terminal commands . Don't know what to do now   ](*,)

---

### Post by vegas89 on 2013-01-01
Thanks cheesemill, How do I delete the corrupted downloads and where do you suggest  I get a good one from to download

---

### Post by ajgreeny on 2013-01-01
> **Cheesemill said:**
> No need to follow the page that ajgreeny linked to, those instructions are for building hplip from source instead of using the run file.

You were spot on with the commands that you tried earlier, just your download was corrupted. Delete the hplip-3.12.11.run file and download it again, then repeat the commands I posted earlier.
Sorry; my mistake with the wrong link.

This is the one I meant.
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by vegas89 on 2013-01-01
Thanks ajgreeny for the help, When I download the hplip from that site I keep getting a corrupted download that will not run. I don't know how to get past this issue. See the attachment below.     ](*,)

---

### Post by t0p on 2013-01-01
From that last screenshot, it appears to me that you are trying it to open it with a text editor (gedit) when you should be running the file as an executable.

Try this: open terminal then run command:

```
cd ~/Downloads
```

then

```
./hplip-3.12.11.run
```

---

### Post by vegas89 on 2013-01-01
Tried That and this is what I get

---

### Post by vegas89 on 2013-01-03
Thanks everyone for your help!!   Problem solved, the download works great.   ):P

---

