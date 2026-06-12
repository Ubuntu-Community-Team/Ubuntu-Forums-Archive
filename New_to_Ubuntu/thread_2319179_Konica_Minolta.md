---
title: "Konica Minolta"
date: 2016-04-01
forum: New to Ubuntu
---

### Post by CAMERON_SIEGEL on 2016-04-01
Does anyone here have experience installing KM drivers?

Here's a link to the driver I'm trying to install
[http://onyxweb.mykonicaminolta.com/OneStopProductSupport/SearchResults?products=1486&fileTypes=0&OSs=16](http://onyxweb.mykonicaminolta.com/OneStopProductSupport/SearchResults?products=1486&fileTypes=0&OSs=16) 


I'm a linux noob. I've been able to extract the file, but I cannot seem to point the terminal to the directory where the .install.pl file is located, once I get that installed I think I just add the printer like normal?

---

### Post by alex_32 on 2016-04-01
After having extracted the archive, you can go into the newly created directory right click on an empty space, and press open in terminal then:
```
sudo install.pl
```

If you do not have that option to open a terminal in a specific directory through your file manager. You can navigate to the necessary folder manually.
For example, you extracted your archive in the Downloads folder, and it is named something like cupsdriver you can open a terminal and write:
```
cd Downloads/cupsdriver
sudo install.pl
```

---

### Post by sisco311 on 2016-04-01
Hi, CAMERON_SIEGEL and welcome to the forums!

To get the full path to the directory you can simply drag and drop the directory in the terminal window. 

You can change the current working directory in the terminal with the **cd** command
So, type:
```
cd 
```and a space after it. Drag the directory where the files were extracted and press enter.

To install the drivers:
```
sudo ./install.pl
```

You will be asked for your password. Your password will not be shown on the screen as you type it, not even as a row of stars. 

After you install the drivers, you have to restart cups:```
sudo service cups restart
```

Now you should be able to install the printer with the cups web interface or any other cups printer administration tool.

---

