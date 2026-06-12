---
title: "LibreOffice"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by arno48 on 2012-10-23
Hello,
I have just upgraded Ubuntu 12.10 (from 12.04). 
Some LibreOffice Writer files (not all) do not show Menu bar anymore.
Thanks

---

### Post by mag1strate on 2012-10-23
Would you be so kind as to provide a picture or more specific detail as to your problem?

---

### Post by arno48 on 2012-10-24
> **mag1strate said:**
> Would you be so kind as to provide a picture or more specific detail as to your problem?

  	 	 	 	 	 	   My problem is that when I open a LibreOffice Writer file, the Menu bar (File  Edit View Insert Format Table Tools Window Help) does not appear on  the screen top.
Menu bar does not appear even if I move the cursor up to the screen top.
 As a consequence I am not able to modify this file.
This began two days ago, as I upgraded 12.04 to 12.10
Thanks.

---

### Post by alphacrucis2 on 2012-10-24
> **arno48 said:**
> My problem is that when I open a LibreOffice Writer file, the Menu bar (File  Edit View Insert Format Table Tools Window Help) does not appear on  the screen top.
Menu bar does not appear even if I move the cursor up to the screen top.
 As a consequence I am not able to modify this file.
This began two days ago, as I upgraded 12.04 to 12.10
Thanks.

Probably related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1064962](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1064962)

Same thing happens if you open a second file under recent documents. The menu fails to display for the second doc.

---

### Post by grahammechanical on 2012-10-24
I find that this does not happen if I open Libreoffice Calc first and load recent documents from that.

---

### Post by Herby Pepper on 2012-10-24
Make sure LibreOffice is the program that opens your file when you double click on it. It might be some small text editor that doesn’t  have as much menu as LibreOffice. 
/silly but happen to my friend/ 
If so, make your .odt file to be open in LibreOffice in default or open LibreOffice first and then open your file, as [grahammechanical]("http://ubuntuforums.org/member.php?u=1087323") suggested .

---

### Post by alphacrucis2 on 2012-10-24
The libreoffice/global menu integration in 12.10 is borked. There are workarounds yes but the workarounds don't work in all situations. Try opening a document under recent documents when you already have a document open as an example.


Edit: I just noticed the guy that is responsible for the LO menu integration has just responded to the launchpad bug report I posted earlier in the thread. Looks like at least a partial fix isn't far away:



[QUOTE=Antonio]@Peter

I am the guy responsible for the LO's Unity menubar implementation, and I apologize for all problems you are having. I commited a fix for this issue some days ago, but I don't know when it would be released, but it should be soon.

I know that implementation is far from perfect, but trust me that we did our best to integrate LO with Unity, but things went a little bit difficult in the process. I know that there are some issues with the menubar and I am working to fix all of them as soon as possible.

Hope this helps you in some way :)
[/QUOTE]

---

### Post by arno48 on 2012-10-24
Yes, you are right:
If I open LibreOffice first, then file A, Menubar appears.
If I open file B, then file A, Manubar does not appear.

I think we have to wait for Antonio.
Thanks a lot.

---

