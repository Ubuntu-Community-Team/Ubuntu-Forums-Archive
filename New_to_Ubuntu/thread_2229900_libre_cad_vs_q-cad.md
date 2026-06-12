---
title: "libre cad v/s q-cad"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by Timothy_Cota on 2014-06-16
I am running ubuntu 14.04 on aToshiba tecra M10 g7 notebook with 4g of ram and a 2.4g processor.  I have been trying to install q-cad for some time.  I thought that I had finally installed it but it turned out to be libre cad.  I was trying to open the examples file in q-cad and got a message that I needed to search for something to open the file with.  the search resulted in a request to install some files. The result was Libre cad.    It say q-cad on the toolbar at the top of the screen but the desktop is libre cad.   this Libre software is completely different from therTurbocad Pro that I used on windows.  To make matters worse When I tried to open Help All it said was that they could not provide the manual due to licensing issues.  This software is useless to me without a manual.   Where do I go from here?  ( don't tell me "you can't get there from here.")    unktim

---

### Post by brantcgardner on 2014-06-16
I don't have any experience with any of these packages, but based on your descriptions it sounds to me like you used the software center to install LibreCAD which tried to open your Qcad files (which may have sort-of worked), but I would guess that you actually want to get Qcad installed to get at your files.

Just to try to get you going, go [here]("http://qcad.org/en/qcad-downloads-trial") and see if that is what you need.

---

### Post by Timothy_Cota on 2014-06-16
Hi Brant,  The link you gave me is the one I downloaded q-cad from.  I tried following the instructions from _compilation how to_. I created a user directory and installed the compilation tools as directed in how to step 1.  I was thrilled  Because It was the first time I ever got a terminal to do anything .  Step 2 was a different story and one that I am painfully familiar with.  The computer didn't recognize the command and said that q-cad did not exist.  I tried a few slight variations of the command with no better results.  Later I opened q-cad and clicked on read-me.  It contained about 50 words that were apparently written by Captain Obvious.  I tried a different file and was given the option to search for a program to open the file with.  The search result was a request to download the necessary software.  I gave permission and apparently libre cad was downloaded to the q-cad folder.  That is where I stand.  I thought about going back to windows Vista and using my old Turbocad Pro but the software is 32 bit and I do not want to go back to 32 bit.  Thanks for your response.   unktim

---

### Post by brantcgardner on 2014-06-17
Looking over the Q-CAD website, it appears to me like you downloaded the source package and tried to install that.  I don't know how far you got with that, but I'm thinking you would have been better off downloading the 64-bit binary package ([this]("http://qcad.org/archives/qcad/qcad-3.5.1-linux-x86_64.tar.gz") link, from the Q-CAD download page).

Once you have it downloaded, go to where you saved it and run this command in a terminal to open it up:

```

tar xvf qcad-3.5.1-linux-x86_64.tar.gz

```

This will give you a folder named "qcad-3.5.1-linux-x86_64".  Move into it with:

```

cd qcad-3.5.1-linux-x86_64

```

Then, according to the Q-CAD documentation, run it with:

```

./qcad

```

Try that and see how it goes for you.

---

### Post by Timothy_Cota on 2014-06-22
Brant,  still no luck.  Terminal continues to deny existence of q-cad.  I am doing more research.  Thanks for all your help.  I will let you know when I have success.  My birthday is coming up in a few days.  Maybe I will give myself the q-cad pro CD.   unktim

---

