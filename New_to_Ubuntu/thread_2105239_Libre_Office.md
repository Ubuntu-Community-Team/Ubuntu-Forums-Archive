---
title: "Libre Office"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by ianb72 on 2013-01-15
Can anyone help me, I have put a clean install of Ubuntu 12.10 on my laptop but LibreOffice Calc will not load up, either by clicking directly on the sidebar icon or trying to open an document, an Open Office or Excel document.

Is there anyway of getting this sorted out as I really need a working spreadsheet program, I did try and download the latest version of OpenOffice, but I do not know how to install the file: *Apache_OpenOffice_incubating_3.4.1_Linux_x86_install-deb_en-GB.tar.gz*

Can anyone please help me
Ian

---

### Post by Cheesemill on 2013-01-15
Try opening a terminal and running...
```
libreoffice --calc
```

Do you get any error messages?

---

### Post by ianb72 on 2013-01-15
> **Cheesemill said:**
> Try opening a terminal and running...
```
libreoffice --calc
```

Do you get any error messages?

This is what I get:
[I]ian@ian-Satellite-L300:~$ libreoffice --calc
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected[/I]

---

### Post by Cheesemill on 2013-01-15
Try installing Java...
```
sudo apt-get install openjdk-7-jre
```

---

### Post by ianb72 on 2013-01-15
> **Cheesemill said:**
> Try installing Java...
```
sudo apt-get install openjdk-7-jre
```

I did that and run *libreoffice --calc* again
and I got this:
[I]ian@ian-Satellite-L300:~$ libreoffice --calc
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected
[/I]

---

### Post by ianb72 on 2013-01-16
Can anyone help please?

---

### Post by ianb72 on 2013-01-16
> **ianb72 said:**
> This is what I get:
[I]ian@ian-Satellite-L300:~$ libreoffice --calc
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected[/I]

How do I go about opening this file *"/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf"* as I think I have found the problem:

Here is the first 16 lines of the file:
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "/etc/fonts/conf.d/fonts.dtd">
<fontconfig>

	<!-- Alias similar/metric-compatible families from various sources: -->

	<alias binding="same">
	  <family>Liberation Sans Narrow</family>
	  <family>Arial Narrow</family>
	  <default>
	  **<family>Arial Narrow</family>** ***Line 13***
	  </default>
	</alias>

---

### Post by GordThompson on 2013-01-16
You should be able to modify that file by using

```
gksudo gedit
```

but I'm not so sure that the highlighted line is the problem: I checked my copy and it looks just the same, and LibreOffice Calc runs okay for me.

---

### Post by ianb72 on 2013-01-16
> **GordThompson said:**
> You should be able to modify that file by using

```
gksudo gedit
```

but I'm not so sure that the highlighted line is the problem: I checked my copy and it looks just the same, and LibreOffice Calc runs okay for me.

I removed the [HTML]<family>Arial Narrow</family>[/HTML] on line 13 and I never got any error messages on Terminal, but still it never loaded.

---

### Post by GordThompson on 2013-01-16
> **ianb72 said:**
> I removed the [HTML]<family>Arial Narrow</family>[/HTML] on line 13 and I never got any error messages on Terminal, but still it never loaded.
Probably a good idea to put it back, then (since removing it didn't solve the problem).

I've had another look at my system and I notice that I do not have `openjdk-7-jre` installed. I'm guessing here, but you could perhaps try removing `openjdk-7-jre` and installing `default-jre` to see if that helps any. (The `default-jre` package includes a couple of different variants of the Java Runtime Environment.)

---

### Post by ianb72 on 2013-01-16
> **GordThompson said:**
> Probably a good idea to put it back, then (since removing it didn't solve the problem).

I've had another look at my system and I notice that I do not have `openjdk-7-jre` installed. I'm guessing here, but you could perhaps try removing `openjdk-7-jre` and installing `default-jre` to see if that helps any. (The `default-jre` package includes a couple of different variants of the Java Runtime Environment.)

How do I go about removing the `openjdk-7-jre` package?

---

### Post by GordThompson on 2013-01-16
> **ianb72 said:**
> How do I go about removing the `openjdk-7-jre` package?
```
sudo apt-get purge openjdk-7-jre
```Then, to install `default-jre`...

```
sudo apt-get install default-jre
```

---

### Post by ianb72 on 2013-01-16
> **GordThompson said:**
> ```
sudo apt-get purge openjdk-7-jre
```Then, to install `default-jre`...

```
sudo apt-get install default-jre
```

That done it :p

Thank you

---

### Post by GordThompson on 2013-01-16
> **ianb72 said:**
> That done it :p

Thank you
You're welcome. Please remember to mark this thread as '[SOLVED]' using the "Thread Tools" link near the top of the page.

---

### Post by ianb72 on 2013-01-16
> **GordThompson said:**
> You're welcome. Please remember to mark this thread as '[SOLVED]' using the "Thread Tools" link near the top of the page.

All done

---

### Post by ianb72 on 2013-01-17
Everything was great and working fine until today when I installed the latest updates now Calc will not load up again.

Is there any way of going back to the old open office or getting this to work as in Terminal I am still getting the same error message [HTML]ian@ian-Satellite-L300:~$ libreoffice --calc
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected
ian@ian-Satellite-L300:~$ 
[/HTML]

This is driving me mad now

---

### Post by vasa1 on 2013-01-17
Look in /usr/share/applications for stuff beginning with LibreOffice.
I see a file for Calc which has this (in part):
```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice3.6-calc
Type=Application
Categories=Office;Spreadsheet;X-Red-Hat-Base;X-MandrivaLinux-Office-Spreadsheets;
Exec=libreoffice3.6 --calc %U
MimeType=application/vnd.oasis.opendocument.spreadsheet; ...
Name=LibreOffice 3.6 Calc
GenericName=Spreadsheet
``` 

So I would try what's in the Exec line (without the %U).

---

### Post by ianb72 on 2013-01-17
> **vasa1 said:**
> Look in /usr/share/applications for stuff beginning with LibreOffice.
I see a file for Calc which has this (in part):
```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice3.6-calc
Type=Application
Categories=Office;Spreadsheet;X-Red-Hat-Base;X-MandrivaLinux-Office-Spreadsheets;
Exec=libreoffice3.6 --calc %U
MimeType=application/vnd.oasis.opendocument.spreadsheet; ...
Name=LibreOffice 3.6 Calc
GenericName=Spreadsheet
``` 

So I would try what's in the Exec line (without the %U).

I looked in the folder and could only find this, but not sure how to open it to get the file you showed:
[https://docs.google.com/file/d/0B1HEquw5ZAKBS1ZHZnBnVTZHb00/edit]("https://docs.google.com/file/d/0B1HEquw5ZAKBS1ZHZnBnVTZHb00/edit")

---

### Post by GordThompson on 2013-01-17
> **ianb72 said:**
> I looked in the folder and could only find this, but not sure how to open it to get the file you showed:
[https://docs.google.com/file/d/0B1HEquw5ZAKBS1ZHZnBnVTZHb00/edit](https://docs.google.com/file/d/0B1HEquw5ZAKBS1ZHZnBnVTZHb00/edit)
Try launching `gedit` and then use **File > Open** to open the file.

---

### Post by ianb72 on 2013-01-17
> **GordThompson said:**
> Try launching `gedit` and then use **File > Open** to open the file.

Done that but I am still getting the same problem and the same error in Terminal:
[HTML]ian@ian-Satellite-L300:~$ libreoffice --calcFontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected
ian@ian-Satellite-L300:~$[/HTML]

---

### Post by GordThompson on 2013-01-17
Okay, I just installed 12.10 onto a VMware virtual machine and when I run...

```
libreoffice --calc
```...in a Terminal window I get the same messages as you: a bunch of stuff about no JRE and then the Fontconfig warning. BUT, LibreOffice Calc does open. I didn't mess with it too much more because 12.10 is agonizingly slow under that particular setup.

My recommendation would be for you to back up your documents, etc., blow away 12.10 and do a clean install of 12.04 LTS.

---

### Post by ianb72 on 2013-01-17
> **GordThompson said:**
> Okay, I just installed 12.10 onto a VMware virtual machine and when I run...

```
libreoffice --calc
```...in a Terminal window I get the same messages as you: a bunch of stuff about no JRE and then the Fontconfig warning. BUT, LibreOffice Calc does open. I didn't mess with it too much more because 12.10 is agonizingly slow under that particular setup.

My recommendation would be for you to back up your documents, etc., blow away 12.10 and do a clean install of 12.04 LTS.

You know I will give that a go tomorrow, still got 99% of my stuff backed up from when I last done a clean install of 12.10

---

