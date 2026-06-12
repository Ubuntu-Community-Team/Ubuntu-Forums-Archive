---
title: "Batch/Script Program Help"
date: 2010-05-20
forum: Programming Talk
---

### Post by Hosmion on 2010-05-20
Hello everyone!  I am writing a batch (or as I was informed a "script") file that takes the input from the user and writes a text document in a specific folder for a specific employee.  Every time the program attempts to make the text document it says, "Cannot find designated folder."  Here is the code:

```
@echo off
title Hour Recorder
cd DESKTOP LOCATION
ping localhost -n 2 >nul 
ping localhost -n 2 >nul
ping localhost -n 2 >nul
cls
echo Do you need to create a new folder for a new employee?  
set Choice1=
set /p Choice1=(y/n):
if %Choice1% == y goto NewFolder
if %Choice1% == n goto NoNewFolder
:NewFolder
set Choice2=
set /p Choice2=Name: (One word.  I.E. RandomName.  Or, if you are saving something in a already made folder, type in the name again.  There will be an error; ignore it.):
cd DESKTOP FOLDER LOCATION
md %Choice2%
ping localhost -n 2 >nul
echo Created!
pause
cls
:NoNewFolder
echo Now we are working on adding the information into a text document!
set Date=
set /p Date=Date:
set JobSite1=
set /p Location1=Location:
set Hours1=
set /p Hours1=Hours:
pause
echo Creating File!
cd DESKTOP FOLDER LOCATION/%Choice2%
echo <li>Date: %Date% <li>Job Site: %Location1% <li>Hours: %Hours1% >> %Choice3%.txt
pause
```Also, is there a way that I can make it so you don't have to re-enter the name and it will just make the text document go where it needs to go?

**NOTE**
The "DESKTOP LOCATION" is the actual location of the desktop (i.e. C:\Users\(Name)\Desktop\...

---

### Post by lavinog on 2010-05-26
This is for windows, correct?

---

### Post by Hosmion on 2010-05-31
Yes, this is for Windows.

---

### Post by cheway on 2010-09-01
Hi everyone, could somebody please explain to me how to defrag a hard drive, create a system restore, rename my C: drive to D: drive, and install anti-virus software?

---

### Post by lordhaworth on 2010-09-01
> 

**NOTE**
The "DESKTOP LOCATION" is the actual location of the desktop (i.e. C:\Users\(Name)\Desktop\... 


Where are you running this from (e.g. an admin machine)? If you are on a network you will have to make sure you include the network name when you specify that in the DESKTOP LOCATION. 

e.g. you might have "WorkNetwork" as J: but will have to refer to it as WorkNetwork\... 



Just a guess - given the info above
> 
Hi everyone, could somebody please explain to me how to defrag a hard drive, create a system restore, rename my C: drive to D: drive, and install anti-virus software? 


In my limited experience, these forums usually offer the best/quickest advice on the web

---

