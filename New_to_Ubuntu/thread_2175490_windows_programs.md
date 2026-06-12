---
title: "windows programs"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by David_LaRose on 2013-09-19
How do I access and use WINE in Ubuntu 12?

---

### Post by Jonathan Precise on 2013-09-19
Try:

```
sudo apt-get install wine
```

to install WINE. Then right-click on the EXE, or MSI file, and select "Open with" --> "WINE windows program loader"

---

### Post by deadflowr on 2013-09-19
Follow the advice above on installing wine and then the program.
If no issues arise(which might happen) then the app should show up like any other program.

When done right, you really shouldn't notice the app is running in wine.

---

### Post by whitesmith on 2013-09-19
If you can't get a certain application to work under Wine, and availability of that application is a make-or-break issue for Ubuntu, consider the using paid version (CrossOver) which comes with phone and email support.

---

### Post by grahammechanical on 2013-09-19
We can install wine through the Ubuntu Software Centre. Search for wine and select Microsoft Windows Compatibility Layer (meta package) wine then click install and wait. At some point you will get a dialog asking you to confirm your acceptance of Microsoft's terms and conditions for installing Windows TrueType Core fonts. Your application may not work too well without these installed. The dialog box will appear behind the Software Centre window. So, you will not see it and you will think as I always do that Software Centre is not working. It isn't. It is waiting for input. So, move the Software Centre window to one side.

Once Wine is installed search for wine in the Dash and two icons will appear. Configure Wine and Uninstall Wine Software. Click Uninstall Wine Software. I know it sounds stupid but stay with me on this. A dialog will appear informing you that wine is being configured. It takes awhile to do this. Then you get a Windows type Add/Remove dialog. Click Install and follow the usual Windows method of installing software - browse to the setup.exe/install.exe file of the relevant program.

Regards.

---

### Post by Mark Phelps on 2013-09-19
Once you get Wine installed, then visit the WineHQ website, the application compatibility page, to see the ratings for the apps and versions you want to run.  The ratings range from Platinum (everything works) to Garbage (nothing works, or won't install).  If you see no ratings, then the app/version has not been tested and it's likely NOT to work.  Also, the latest versions of "standard" stuff in Windows (e.g., Office 2013, Internet Explorer 10) do NOT work -- so there's no point in struggling with them.

---

