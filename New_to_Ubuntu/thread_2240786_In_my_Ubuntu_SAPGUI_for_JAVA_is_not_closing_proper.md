---
title: "In my Ubuntu SAPGUI for JAVA is not closing properly"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by slkamath on 2014-08-22
Hi All,


I am using Ubuntu 14.04LTS in my Desktop and I installed SAPGUI in that. 

I can use SAPGUI too. After my work if I try to close the window it will not get close. So my question is how to close? Else anyone tell how to install SAPGUI in ubuntu directly?

Thanks in advance

Lokesh Kamath

Hi,

One more error i am geting is:

```
############################# ERROR #############################
23.08. 11:24:07.463 ERROR: Please don't start com.sap.platin.base.logon.GuiImpl but use com.sap.platin.Gui like:
23.08. 11:24:07.463 ERROR:    java -cp GuiStartS.jar com.sap.platin.Gui
############################# ERROR #############################
```

SAPGUI is not opening

---

### Post by bizhat on 2014-08-23
Have you tried running 

```

java -cp GuiStartS.jar com.sap.platin.Gui

```

If applet, try changing code like

```

ARCHIVE="GuiStartS.jar" CODE="com.sap.platin.Gui"

```

---

### Post by slkamath on 2014-08-25
Thanks for reply.

Could you please tell me where i need to put this java -cp GuiStartS.jar com.sap.platin.Gui (in sudo terminal?)

Thanks & Regards
Lokesh Kamath

---

### Post by slkamath on 2014-08-27
Also If i type any T-code in SAP frontend it's hanging.. I need to restart or i need to kill the process.

Anyone have solution for this?

Lokesh Kamath

---

### Post by slkamath on 2014-09-04
Friends Can anyone help me to solve my above problems?

Lokesh Kamath

---

