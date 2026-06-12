---
title: "html text from netbeans itself not rendering"
date: 2009-05-20
forum: Programming Talk
---

### Post by glok_twen on 2009-05-20
i've installed netbeans 6.5 on ubuntu jaunty. the displaying doesn't work right at all. i keep getting this exception:

java.lang.NoClassDefFoundError: javax.swing.text.html.HTMLEditorKit

then, many of the menu options will not come up when i click on them. for others, they will pop up, but the text shows native, marked up html, not rendered text. for example, when checking for updates i get:

<br><b>Welcome to the NetBeans IDE Plugin Installer</b> <br>The installer will download, verify and then install the selected plugins.

the exact display from my help->about screen looks like this (which also shows my jvm as 1.6.0_13) - html, not rendered text:

<div style="font-size: 12pt; font-family: Verdana, Verdana CE,  Arial, Arial CE, Lucida Grande CE, lucida, Helvetica CE, sans-serif;"><p style="margin: 0"><b>Product Version:</b> NetBeans IDE 6.5 (Build 090407)</p>
 <p style="margin: 0"><b>Java:</b> 1.6.0_13; Java HotSpot(TM) Client VM 11.3-b02</p>
 <p style="margin: 0"><b>System:</b> Linux version 2.6.28-11-generic running on i386; UTF-8; en_US (nb)</p>
 <p style="margin: 0"><b>Userdir:</b> /home/glok/.netbeans/6.5</p></div>
 
 suggestions?
 
 thanks,
 gt

---

### Post by Reiger on 2009-05-20
Are you using the gcj as default java?

---

### Post by glok_twen on 2009-05-20
the jvm default is -

1.6.0_13; Java HotSpot(TM) Client VM 11.3-b02

checked, double checked, removed, re-installed, selected in the alternatives update.

---

