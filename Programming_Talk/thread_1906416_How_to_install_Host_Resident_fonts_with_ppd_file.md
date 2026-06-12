---
title: "How to install Host Resident fonts with ppd file?"
date: 2012-01-09
forum: Programming Talk
---

### Post by Gurmeet Singh on 2012-01-09
Hi Experts,

I am developing a driver for 24 pin DMP using cups. I want to install some fonts in the system when driver installed and these fonts should show in office writer's combo box when my printer selected as default printer and if my printer not selected as default printer then installed fonts should not show up.
Where in the PPD file i can give reference to such fonts and how?
or
alternative?

Thanks in advance.

---

### Post by Zugzwang on 2012-01-09
It's written in the PPD file format specifications. It is linked in the section "Introduction" on [this]("http://www.cups.org/documentation.php/spec-ppd.html") page.

---

### Post by Gurmeet Singh on 2012-01-09
Hi Zugzwang,

I have gone through the PPD file Specification document. section 5.20 describing lot many things about fonts but it is not solving my purpose.

Can i use FontList or FontQuery?

or Please provide any other link (Source code or alternative Method) which will be helpful.

I want to load all the fonts in a folder say myfonts folder when my printer selected as default printer and if my printer is not default then font should be unloaded.:confused:


Thanks.
__[]("http://ubuntuforums.org/member.php?u=403348")

---

### Post by Zugzwang on 2012-01-09
You question was: "Where in the PPD file i can give reference to such fonts and how?

This question is answered in Section 5.2 of the document. The "*Font" command appears to do what you want: declare that a font may be available on the device.

This thing with the default printer shouldn't be of relevance to making a .PPD file for the printer as such a functionality has to be added on a different level. A PPD file *cannot* add fonts to the system it is installed on, as these things are handled by different components in Linux, namely the font manager, which in turn has nothing to do with the printing subsystem. However, note that I pointed out in a different thread that it is not a good idea to rely on something like a default printer since the notion of a default printer is highly system-dependent and should not relied upon anyway.

---

