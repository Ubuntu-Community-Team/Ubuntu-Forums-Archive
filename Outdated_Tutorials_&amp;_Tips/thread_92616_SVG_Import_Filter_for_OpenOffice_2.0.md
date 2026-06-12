---
title: "SVG Import Filter for OpenOffice 2.0"
date: 2005-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-11-20
This is for making Open Office 2.0 SVG ready.
Requirements:
**Your OpenOffice installation must use a Java 5.0 runtime environment**. The filter will not work with Java versions 1.4.X or below. 
Before installing the filter, please check in the Tools-->Options Dialog the settings in the category OpenOffice.org-->Java, if a Java version 1.5.X is activated.
if u dont have java 1.5, use [automatix]("http://ubuntuforums.org/showthread.php?t=66563") to install it and then set the java environment in OO as 1.5
now open up terminal and do  the following:
[PHP]wget -c http://www.ipd.uni-karlsruhe.de/~hauma/svg-import/svg-import-r2009.uno.zip[/PHP]
after the file gets downloaded,
install the package into your OpenOffice using the package manager. 
Open Tools-->Package Manager and select **My Packages** from the dialog. Then click the **Add** button to install the downloaded file.

Now u are all set to open SVG graphics in Open Office.

---

### Post by moment on 2005-11-20
This is a great tip! I always hated saving my pictures in PNG and importing them in OpenOffice impress.

---

### Post by kaamos on 2005-12-24
This looks great, I have really missed the feature to add svg-images. But I can't get this to work. :(

My java runtime is set to sun java 1.5, and I added to zip file in package manager. I also checked that the package is in use. In what way should I import svg files? Add->File or Add->Image->From file (these are translated from finnish..) do not work, and neither does a simple copy-paste. I tried this with both OOo 2.0.0 and 2.0.1.

Or is this only for Draw and not to Writer?

Thanks in advance for any help or replies.

---

