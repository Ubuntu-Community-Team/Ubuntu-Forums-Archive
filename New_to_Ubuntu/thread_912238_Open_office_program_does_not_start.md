---
title: "Open office program does not start"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by krusna on 2008-09-06
Hai,
I have ubuntu 8.04 installed.
When i clik on icon openoffice.org wodprocessor or spreadsheet
i get the info "application can not be started. User interface language can not be determined."
I do not understand what to do.

Can some one help me with a copy to my personal mail id
[email]krusna@gmail.com[/email]

tnx
sivaraman

---

### Post by hyper_ch on 2008-09-06
"application can not be started. User interface language can not be determined."

--> what language do you use in ubuntu?

---

### Post by krusna on 2008-09-06
> **hyper_ch said:**
> "application can not be started. User interface language can not be determined."

--> what language do you use in ubuntu?
I am from India. the language installed are US english, British english, Hindi and Tamil.
I use the OS in english only.
sivaraman

---

### Post by hyper_ch on 2008-09-07
that is trange... run openoffice from the terminal:

```

ooffice -writer %U

```

and look what error it produces in the terminal window.

---

### Post by krusna on 2008-09-07
If i give this command
ooffice -writer %U
I get a reply 
/home/bedetached/%U doesnotexist

How ever if I give the same command without "%U"
it works fine.
How can set this problem at rest?

---

### Post by hyper_ch on 2008-09-07
then alter the OOo entries in your menu to not start with %U

---

### Post by acidsolution on 2008-09-07
Have u used some theme or something in your ubuntu ???
some gtk theme doesnot allow open the openoffice. I faced same problem when i was using different gtk theme

---

### Post by krusna on 2008-09-07
I installed kde-4 using synaptic package manager.

---

### Post by hyper_ch on 2008-09-07
kde4 or kde4.1?

---

### Post by bobromeo on 2008-09-24
> **hyper_ch said:**
> then alter the OOo entries in your menu to not start with %U
My install is Dutch, but I get the following
henk@hbvnb:~$ ooffice -writer %U
[Java framework] Error in function createSettingsDocument (elements.cxx).javaldx failed! 
[Java framework] Error in function createSettingsDocument (elements.cxx).henk@hbhenk@hbvnb:~$ ooffice -writer
[Java framework] Error in function createSettingsDocument (elements.cxx).javaldx failed! 
[Java framework] Error in function createSettingsDocument (elements.cxx).henk@hbvnb:~$

Solved:[UFpost]("http://ubuntuforums.org/showthread.php?p=5846067#post5846067")

---

### Post by Hagar Delest on 2008-09-24
> **krusna said:**
> application can not be started. User interface language can not be determined.
Try to rename the OOo user profile (~/.openoffice.org2).

---

### Post by quinnten83 on 2008-09-24
Henk,
Have you tried installing java from the restricted extras?
in terminal type:

```
sudo apt-get install ubuntu-restricted-extras
```

be careful, because java will ask you to configure in the terminal. Do not close this windows without finishing the installation, because it might break your package manager.

---

### Post by SivaneshR on 2008-10-01
Its better to reinstall your Ubuntu. Its always not recommended to uses GNOME and KDE side by side. If you want to use KDE you can always request for a KUBUNTU CD. Never Use GNOME and KDE together.:guitar:

---

