---
title: "Launchpad: signing the Ubuntu Code of Conduct; could be easier."
date: 2012-11-18
forum: New to Ubuntu
---

### Post by MFSOT on 2012-11-18
New to Linux and trying to sign to be part of the bug team as I feel it will help me learn the internals and make me a better end user. 

I have made it as far as: 

[LIST=1]
[*]                                            In a terminal, run the command:[INDENT]                       gpg --clearsign UbuntuCodeofConduct-1.1.txt                       [/INDENT](or whatever filename you gave to the code).                       This will create a file with a name like                       UbuntuCodeofConduct-1.1.txt.asc.
[*]                                            Open that new file,                       and copy and paste its contents into this box.                       Then click &#8220;Continue&#8221;.
[/LIST]
I have changed the file type to the .asc and have tried to copy and paste yet I get this error:


There is 1 error.
          (7, 58, u'No data')


Any help would be much appreciated!

*using 12.10

---

### Post by Elfy on 2012-11-18
*Post moved to new thread **Absolute Beginners Section**.*

---

### Post by Frogs Hair on 2012-11-18
This may help and you may need to install Inigmail for Thunderbird if I remember correctly for any encoded email in the future .[http://www.wikihow.com/Sign-the-Ubuntu-Code-of-Conduct](http://www.wikihow.com/Sign-the-Ubuntu-Code-of-Conduct)

---

### Post by MFSOT on 2012-11-22
> **Frogs Hair said:**
> This may help and you may need to install Inigmail for Thunderbird if I remember correctly for any encoded email in the future .[http://www.wikihow.com/Sign-the-Ubuntu-Code-of-Conduct](http://www.wikihow.com/Sign-the-Ubuntu-Code-of-Conduct)

Thank you for your reply - I already had thunderbird and inigmail installed for the reasons you stated. 

My issue remains the same - when I cut and paste the document I get the error above.

Anyone have any ideas?

---

### Post by Elfy on 2012-11-22
> I have changed the file type to the .asc and have tried to copy and paste yet I get this error:You shouldn't be doing that.

Running 

```
gpg --clearsign UbuntuCodeofConduct-1.1.txt 
```

should leave you with both

UbuntuCodeofConduct-1.1.txt
UbuntuCodeofConduct-1.1.txt.asc

Then open the UbuntuCodeofConduct-1.1.txt.asc file and copy paste that.

---

### Post by activision78 on 2013-01-31
I may be having a similar problem;

When I try to open the UbuntuCodeofConduct-2.0.txt.asc  I get an error message telling me that 

"There is no application installed for PGP/MIME-encrypted message header files.
Do you want to search for an application to open this file?"

I searched for an application like it said and installed a plugin for seahorse that it suggested. Now when I try to open the file I get an error message reading "No data"

Sorry if this is the wrong place for this.

---

