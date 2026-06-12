---
title: "ATI driver install error in Ubuntu 8.10"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by piyushp_20 on 2008-11-03
hi guys,
i use ATI radeon 3400 series graphic card and i recently upgraded to 8.10, now the problem which i am facing is that when i try to install the drivers for my card i get the error message as

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.27-7-generic; make sure that the version is being correctly set by --iscurrentdistro

i am providing the screenshot also, kindly take a look at it and pls help me out with this.

[[IMG]http://img217.imageshack.us/img217/2585/screenshotse6.th.png[/IMG]](http://img217.imageshack.us/my.php?image=screenshotse6.png)

[http://img217.imageshack.us/img217/2585/screenshotse6.png](http://img217.imageshack.us/img217/2585/screenshotse6.png)

---

### Post by talsemgeest on 2008-11-04
You can always try install the latest driver manually. It might even give you better performance.

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by piyushp_20 on 2008-11-04
Buddy i tried it manually also from the same site you mentioned but that is also not helping.

---

### Post by talsemgeest on 2008-11-04
Ok, can you be more specific about what commands you ran to install the driver?

---

### Post by piyushp_20 on 2008-11-05
i downloaded the package and i allowed the file to be executed as program and then ran the file and finally got the output as shown in the screenshot which i gave in my first post....

please guys m facing a lot of problem, help me out.

---

### Post by Yashiro on 2008-11-05
What driver is running at the moment?

What is the EXACT filename of this new driver you are trying to install?

---

### Post by piyushp_20 on 2008-11-05
> **Yashiro said:**
> What driver is running at the moment?

What is the EXACT filename of this new driver you are trying to install?

The file is: ati-driver-installer-8-10-x86.x86_64.run

---

### Post by I3roknI3ottle on 2008-11-05
mine is doing the same thing aswell, im using an ati radeon mobile x1250

---

### Post by talsemgeest on 2008-11-05
Here we go, this is what I was looking for! If this doesn't help you out, I don't know what will.

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Just run through the "Manual" part of the tutorial and you should be good.

---

### Post by Yashiro on 2008-11-05
And you are running the 64bit Ubuntu, I assume?

If not, it could be some stupid setup script bug, or perhaps you lack something the script requires.

You could try the above mentioned manual install, or install these and try the auto installer again.
 
[COLOR="Green"]sudo apt-get install ia32-libs 
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)[/COLOR]

---

### Post by talsemgeest on 2008-11-05
If using 64 bit ubuntu, the drivers I mentioned were wrong, since they were for 32 bit Ubuntu.

Can you please confirm which version you are using?

---

### Post by nelio2k on 2008-11-06
> **talsemgeest said:**
> Here we go, this is what I was looking for! If this doesn't help you out, I don't know what will.

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Just run through the "Manual" part of the tutorial and you should be good.

I followed through the manual part of the tutorial because everything else isn't working. Now, when I ask run fglrxinfo, it gives me:

 X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

I haven't found anyone with the same problem as me. 
Any help is appreciated! Thanks very much.

---

### Post by talsemgeest on 2008-11-06
Did you get any error messages when you were following through the instructions?

---

### Post by mapes12 on 2008-11-06
Here's another HowTo that may help:

[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

Best wishes.

Mark

---

### Post by nelio2k on 2008-11-07
I think the problem was solved from an Ubuntu update... :confused: 
Sooo i don't reali know how it got fixed but it's fixed... thanks! haha

---

### Post by talsemgeest on 2008-11-07
Cool, glad you got it working. Now just hope it stays that way ;)

---

