---
title: "Brother MFC-J285DW printer"
date: 2015-03-02
forum: New to Ubuntu
---

### Post by francisco17 on 2015-03-02
Hi all,

I am a new to unbuntu, i have just installed it on my older thinkpad . The one major problem i am having is trying to install my printer. I have found instructions but i still dont quite
understand. Would appreciate a little help if anyone has time. Thank You!

---

### Post by Bucky Ball on 2015-03-02
Welcome. Download the Driver Install tool from [here]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj285dw_us&os=128"), double click the .deb file on your machine. That should open Software Centre and install it. You may need to restart the machine.

Go to Printers>Add Printer. How are you connecting to the printer? Through your network (plugged into a router or wirelessly) or via USB?

---

### Post by francisco17 on 2015-03-02
So i downloaded the tool, and double clicked the file. It opened Softwarecentre and i clicked install. I restarted and i went to printers and add printer. I have a network printer and am connecting wirelessly. IT sees the printer but there are no compatible drivers.

---

### Post by gifford on 2015-03-02
Go to this link and download the appropriate drivers. [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj285dw_us&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj285dw_us&os=128)
You will need to download printer driver, scanner driver and then follow the instructions given after the download.
Brother will list what other packages you need for the install. 
Welcome to the forum and take this as an opportunity to learn to use the command line. By following the instructions you will be able
to connect via wireless.

---

### Post by Bucky Ball on 2015-03-02
> **gifford said:**
> Go to this link and download the appropriate drivers. [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj285dw_us&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj285dw_us&os=128)
You will need to download printer driver, scanner driver and then follow the instructions given after the download.
Brother will list what other packages you need for the install. 
Welcome to the forum and take this as an opportunity to learn to use the command line. By following the instructions you will be able
to connect via wireless.

Please see post #2. 

@OP: IT can see it? Don't follow. But the printer is installed an working on your local machine?

---

### Post by plucky on 2015-03-03
> **francisco17 said:**
> So i downloaded the tool, and double clicked the file. It opened Softwarecentre and i clicked install. I restarted and i went to printers and add printer. I have a network printer and am connecting wirelessly. IT sees the printer but there are no compatible drivers.

The "Driver Install Tool" cannot use the Ubuntu Software Centre to install the drivers,you need to follow the instructions given on the Brother website to use the tool.

Also I have found that to get the scanner driver installed and working,you have to have csh or tcsh installed first.

```
sudo apt-get install csh tcsh
``` should work to install those.

Good Luck

---

### Post by francisco17 on 2015-03-03
I am at the terminal now, i have switched to the directory. I am following the instructions from the brother website and entering the command it says to enter but i keep getting the error message "No such file or directory"

---

### Post by plucky on 2015-03-03
> **francisco17 said:**
> I am at the terminal now, i have switched to the directory. I am following the instructions from the brother website and entering the command it says to enter but i keep getting the error message "No such file or directory"

```
ls
``` should show the file if you are in the correct directory.

---

### Post by francisco17 on 2015-03-03
Finally got it to install, thanks everyone for your help.

---

### Post by Bucky Ball on 2015-03-03
Good news. Please share how and mark the thread as solved to help others (see second link in my signature). Thanks and enjoy the OS and the forums. ;)

---

### Post by pdc on 2015-03-03
a guess:

open a terminal

```
cd Downloads
```

```
gunzip linux-brprinter-installer-2.0.0-1.gz
```

```
sudo bash linux-brprinter-installer-2.0.0-1 MFC-J285DW
```

---

