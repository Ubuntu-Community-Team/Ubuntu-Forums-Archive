---
title: "How to Use windows COM DLL based application"
date: 2018-01-19
forum: New to Ubuntu
---

### Post by kmkmahesh2 on 2018-01-19
Hi,

I am new to ubuntu, I am searching an way how i can use an application(C#) which has dependent on a COM DLL(which is ActiveX Control) and some other windows dll's.

I actually want to use ZKTECO dlls from ubuntu.
Please provide the way how i can do that.

Sorry if i posted on wrong forum.

Thanks,
K Mahesh Kumar

---

### Post by Mark Phelps on 2018-01-19
Natively in Linux, there is no way you can do that -- as those are Windows components.

There are however, Wine, and PlayOnLinux, both of which install middleware that allows SOME Windows stuff to run.

You would need to do more reading at the Wine website to find out if it will work for you:  [https://www.winehq.org/]("https://www.winehq.org/")

---

### Post by kmkmahesh2 on 2018-03-21
while i am tyring to regsvr32 zkemkeeper.dll 
i am getting regsvr32: Failed to load DLL 'zkemkeeper.dll'
I tried everything what i can
some one help me

---

### Post by Autodave on 2018-03-21
Are you running the program in WINE?

---

### Post by kmkmahesh2 on 2018-03-21
yes

---

### Post by Mark Phelps on 2018-03-22
I already told you about this -- not everything works in Wine.

---

