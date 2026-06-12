---
title: "Install Brother Printer"
date: 2015-10-17
forum: New to Ubuntu
---

### Post by capemayal on 2015-10-17
MFC-J6520DW

I have tried the gunzip command - following the instructions - from Brother's website.

No matter what I do, I get "no such file directory found", or "suffix ignored"

I've changed into the Downloads directory.

I've sudo su

I've sudo

I ensured that the driver name is entered instead of the wild cards.

I tried unzipping with the archive manager, and that just gives me the same file.

I'm at a loss, and just can't get it to work.

Any help appreciated.

---

### Post by ajgreeny on 2015-10-17
Tell us what file you downloaded and where it is in your home, then we can tell you how to unzip it.
Why not just double click on it to open it in the archive-manager and then extract it using that?

I suspect your problem is because the downloaded file is either somewhere other than Downloads, eg Desktop, or you are not using the full pathway in terminal to unzip it, or you are perhaps not aware that Linux is case sensitive.

Make sure you are certain where the file is sitting, exactly what it is called, including character case, and if using terminal you use the correct full pathway.

---

### Post by Geoffrey_Arndt on 2015-10-17
+1 for AJ's post. In addition, if using Ubuntu's standard file manager, you can also use it (nautilius) to decompress the file via a "right-mouse" click.   You get the option for extracting in that drop down menu    You can then do another right click on the installer file to make sure it's executable (goto properties - - permissions tab).

Then run the install script exactly as instructed in the very good & clear Brother instructions you listed.    Use cut & paste so you don't make more typos (remember, Linux is case sensitive . . l is not same as L).

BTW:   in Ubuntu, never use "sudo su" for anything.   Brother is advising general Linux users (more than Ubuntu)

---

### Post by SeijiSensei on 2015-10-18
I recommend using the "driver install tool" for your printer here: [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj6520dw_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj6520dw_us_eu_as&os=128)

Follow these steps in the directory where the download was stored:
```

gunzip linux-brprinter-installer-2.0.0-1.gz
chmod a+x linux-brprinter-installer-2.0.0-1
sudo ./linux-brprinter-installer-2.0.0-1

```

It will ask you a few questions, then download and install the appropriate drivers.

---

