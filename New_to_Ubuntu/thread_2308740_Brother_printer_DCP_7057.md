---
title: "Brother printer DCP 7057"
date: 2016-01-05
forum: New to Ubuntu
---

### Post by zak14 on 2016-01-05
Hi to all,i am new here and this is my first post...yes and for first time use Ubuntu 15.10.All is new with ubuntu for me.Need someone help me how to install Brother DCP 7057(printer) step by step.My computer is 32 bit.(sorry for bad english)

---

### Post by ajgreeny on 2016-01-05
Have you installed any of the brother cups or lpr driver packages available in the repos?

If they are not helping you see if you can find any .deb driver packages for that printer at [http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on)

I used a Brother printer a long time ago and it needed drivers installed separately from Brother, but I think things have changed now and many Brother printers are supported by repository packages.

---

### Post by Bucky Ball on 2016-01-05
Welcome. [Go here]("http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=dcp7057_eu&os=128"). You want the Driver Install Tool. First on the list. That should do everything for you. 

And [here's the instructions]("http://support.brother.com/g/b/downloadhowto.aspx?c=eu_ot&lang=en&prod=dcp7057_eu&os=128&dlid=dlf006893_000&flang=4&type3=625") for running the tool to install the drivers once you have downloaded.

After that's finished, you should be able to 'Add Printer' from 'Printers' and when you get to the part that asks you to select a driver, the driver for the DCP-7057 should be available under the 'Brother' category. If not, something's amiss.

PS: Better to [start off here]("http://support.brother.com/g/b/downloadtop.aspx?c=eu_ot&lang=en&prod=dcp7057_eu") just to make sure it sees you are running 32bit and gives you that driver (not sure if there are 32 and 64bit drivers, but just to make sure).

---

### Post by zak14 on 2016-01-05
uf...i not installing anithing..please step by step...i am first user in ubuntu...need help...

---

### Post by zak14 on 2016-01-05
tried couple time and nothing well
[IMG]http://i.imgur.com/c18dUrW.png[/IMG]

---

### Post by Geoffrey_Arndt on 2016-01-05
OK Zak . . . here's what to do:

>   Go to the folder (using your file manager) where you downloaded the compressed/zipped file (the installer file) (usually it is downloaded and placed in the downloads folder of your home directory.
>   Next,  right-click on the file and from the drop down menu, select "extract here" (this is how Nautilus handles it).   Your download file will then be unzipped.
>   Right-Click on the unzipped file (the installer script - - looks like a page symbol).   Scroll down to properties option and select it to bring up the properties window.
>   Goto the "permissions" tab - find the checkbox that says something like "executible" . . . . check it and close the properties windows.
>   Now, go back and double-click the script (normally it starts).   Some file managers on right-clicking the file also allow for option to run it.
>   Follow the on-screen instructions.

---

### Post by zak14 on 2016-01-06
> **Geoffrey_Arndt said:**
> OK Zak . . . here's what to do:

>   Go to the folder (using your file manager) where you downloaded the compressed/zipped file (the installer file) (usually it is downloaded and placed in the downloads folder of your home directory.
>   Next,  right-click on the file and from the drop down menu, select "extract here" (this is how Nautilus handles it).   Your download file will then be unzipped.
>   Right-Click on the unzipped file (the installer script - - looks like a page symbol).   Scroll down to properties option and select it to bring up the properties window.
>   Goto the "permissions" tab - find the checkbox that says something like "executible" . . . . check it and close the properties windows.
>   Now, go back and double-click the script (normally it starts).   Some file managers on right-clicking the file also allow for option to run it.
>   Follow the on-screen instructions.

thank you for reply....I've done all that you wrote,but script open just with gedit,no run archive manager or ubuntu software center.I do not know where the mistake.(sorry for bad english).
[IMG]http://i.imgur.com/9KVgwWp.png[/IMG]

---

### Post by zak14 on 2016-01-06
SOLVED....i am very happy... find very goog tutorial ...[http://tutorialforlinux.com/2015/12/15/how-to-install-brother-printers-drivers-on-ubuntu-15-10-wily-linux-easy-guide/](http://tutorialforlinux.com/2015/12/15/how-to-install-brother-printers-drivers-on-ubuntu-15-10-wily-linux-easy-guide/)

thanks to all,

---

### Post by ajgreeny on 2016-01-06
Great!
Please go to the "Thread Tools" menu above your original post and mark the thread as SOLVED.

---

