---
title: "Compiling and installing/running Eclipse 3.3"
date: 2012-04-28
forum: Packaging and Compiling Programs
---

### Post by PkgMafaw on 2012-04-28
I'm trying to install/run Eclipse 3.3 on Ubuntu 12.04 to set up an Android Dev Environ. I tried 3.7 but it didn't show that Android ADT installed. I've read all kinds of articles that point to Eclipse 3.3 but I have no idea how to install a program from source. I have read and tried to follow the tutorials on compiling source code for Ubuntu but no cigar. I've just tried to run eclipse by typing "Eclipse" in the directory where it's been extracted, but Ubuntu 12.04 says it's not installed and then offers to install 3.7 which I'm trying to avoid.

If there is a way to establish an Android Dev. Environment on Ubuntu 12.04 then PLEASE show me how. If there is a step by step tutorial that shows the most ultimate noob how to install and run from source code then PLEASE point me to it. I am so willing to learn and not bug people over things that should move toward common knowledge, but like I said I'm needing a good walk thru if at all possible. Ive read the read me files in trying to follow install instructions but I don't find instructions. I'm at a total loss on where to go from here. :confused:

---

### Post by newbie-user on 2012-04-29
Yes, you can set up an Android dev environment in 12.04. 

Install eclipse 3.7
```
apt-get install eclipse
```

Then open eclipse, go to Help --> Install New Software
In the "Work With" field, enter:
```
https://dl-ssl.google.com/android/eclipse/
```
Then click Add. Check the boxes for the developer tools you want to install, then click Finish. You will go through a few dialog boxes to set up which Android platforms you want to program for, then the installation will be finished and you can get on with your Android development.

Just FYI, when you download eclipse from eclipse.org and extract the files, you may have to ```
chmod +x eclipse
``` and then run it from the command line using ./eclipse to get it going. No need to compile from source.

I don't know if you'll be able to find the ADT for eclipse 3.3 anymore. I was trying to set up eclipse galileo for Android, but the ADT wasn't available so I had to switch to eclipse indigo (3.7)

---

### Post by PkgMafaw on 2012-04-29
Thank you so much for your help. I'll give 3.7 another try.

Okay I've tried 3.7 and tried to install the Android software but I'm getting this message:
Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Development Tools 18.0.0.v201203301601-306762 (com.android.ide.eclipse.adt.feature.group 18.0.0.v201203301601-306762)
  Missing requirement: Android Development Tools 18.0.0.v201203301601-306762 (com.android.ide.eclipse.adt.feature.group 18.0.0.v201203301601-306762) requires 'org.eclipse.wst.sse.core 0.0.0' but it could not be found

There are 4 items that Eclipse is trying to install but the error pops up and doesn't allow it to.

Any advice?

---

### Post by newbie-user on 2012-04-29
Maybe try running eclipse as root just to install the adt. Also, I used eclipse classic 3.7.2. I don't know if that would make a difference.

---

### Post by Arwen17evenstar on 2012-05-29
> **newbie-user said:**
> Maybe try running eclipse as root just to install the adt. Also, I used eclipse classic 3.7.2. I don't know if that would make a difference.

You don't want to run eclipse as root to install ADT. I ran into major problems later on because of that.
Solution:
Run eclipse as a normal user. If you're running eclipse **indigo** version,
Add [http://download.eclipse.org/releases/**indigo**]("http://download.eclipse.org/releases/")  to the install new software list. That will fix the *requires 'org.eclipse.wst.sse.core 0.0.0'*dependency issue. Now you should be able to install the ADT without getting the "missing requirement" error.

---

