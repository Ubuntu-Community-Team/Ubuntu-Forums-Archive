---
title: "Android app demo with processing."
date: 2011-07-26
forum: Programming Talk
---

### Post by kaspar_silas on 2011-07-26
Hi All,

Just thought I would give a little tutorial of one way to make and publish Android apps using ubuntu. This is by no means the only way, I know there are far more ways to do it (using app-inventor, the "right way" with eclipse etc etc). This is solely the way I happened to do it first time. Feel free to comment, correct, damn or improve as you wish.

This way is based around the excellent open source and free processing "language". Basically processing is a nice way to simplify android development (well at least at the beginning). 
[COLOR="red"]
[B]
TO SET UP:[/B][/COLOR]
1. Download Processing from:[http://code.google.com/p/processing/downloads/list]("http://code.google.com/p/processing/downloads/list")
you need a quite recent version for the android bits. I use v1.99
2. Extract the downloaded file to the directory of your choice.
3. Download the android sdk from:[http://developer.android.com/sdk/index.html]("http://developer.android.com/sdk/index.html")
once it's finished again extract it where ever you like.
4. Go into the extracted android-SDK folder, into the tools subfolder and run "android"
5. Through the gui that launches, update and install all available packages. 
See:[http://developer.android.com/sdk/installing.html]("http://developer.android.com/sdk/installing.html")
for details if you get stuck. You really don't need all packages but it does no harm for now and you can remove them once all is up and running fine.
6. Next add the android tools to your bash path by editing bashrc. So open a terminal and type:
```
$ gedit ~/.bashrc
```
and then in the text editor add this line at the end.

export PATH=${PATH}:[THE_EXTRACTED_SDK_LOCATION]/tools:[THE_EXTRACTED_SDK_LOCATION]/platform-tools.

[COLOR="Red"]
[B]
SET UP PROCESSING:[/B][/COLOR]
7. Open a terminal, cd into the processing folder and run "processing" 
8. Processing will probably ask you where you want to set your save folder for sketchs (Programs/Apps). Pick where ever you like. The default is ~/sketchbook
9. Once processing opens look in the right hand corner. If it doesn't say android, click it and select android.
10. You might get a warning message that processing can't find the Android SDK if so just navigate to what ever folder you extracted the SDK to and click okay.

[B][COLOR="red"]
WRITE THE APP:[/COLOR][/B]
11. Okay this is pretty much up to you. However to begin processing has some nice built in examples we can use. Every example or command is explained in detail at processing.org. For now open the constrain example:[I]
File->Examples->Input->Constrain[/I]
12. Once the example opens click the play icon in the top left corner. This will lauch the app on an Android emulator.
13. **[Bloody important step]** Go and get a coffee. No really lauching the emulator can take ages.
14. When the emulator eventually loads the app should lauch. 

Note: If you are testing your app in the emulator do not close the emulator until you are totally finished. Otherwise you have to endure the slow emulator loading every time you hit run.

[B][COLOR="red"]
RUNNING ON A PHONE:[/COLOR][/B]
15: Set your phone for development which basically involves turning on "USB debugging","stay awake on USB" and selecting "allow installation from unknown sources". 
Note: For security you probably want to disable that last option when you are finished. 
See:
[URL="http://appinventor.googlelabs.com/learn/setup/phone.html"]
http://appinventor.googlelabs.com/learn/setup/phone.html[/URL]
if you get stuck.
16. Plug in your phone to the USB on your computer but do not mount the SD card.
17. Check your phone is detected by running 
```
$ adb devices
```
18. If you get a series of question marks you can fix this using the solutions found here:
[http://ubuntuforums.org/showthread.php?t=1164359]("http://ubuntuforums.org/showthread.php?t=1164359")
or
[http://www.google.com/support/forum/p/android/thread?tid=08945730bbd7b22b]("http://www.google.com/support/forum/p/android/thread?tid=08945730bbd7b22b")
19: Go back to (or reload) the processing constraint example.
20: This time select *Sketch->Run On Device.*
21: The sketch should install on your phone (assuming there is space)
You can delete it after via any normal android uninstall method.

[B][COLOR="red"]
PUBLISHING AN APP:[/COLOR][/B]
22: In processing Save the constrain example as TEST. ( *File->Save_as *)
23: Next export the android project. *File->Export Android Project*
Note: The *export signed project* option below doesn't actually work yet but I guess in future releases you could just use this and skip below
24: Open a terminal and cd into the exported folder it should be located at:
[your_sketchbook_location]/TEST/android/ 
25: Now generate a key to sign your app:```

$ keytool -genkey -v -keystore [KEYFILE_NAME] -alias [YOUR_ALIAS] -keyalg RSA -keysize 2048 -validity 100000
```
answer all the questions (don't forget your answers).
24: Next build the apk```

$ ant release
```
25: Sign the app```

$ jarsigner -verbose -keystore [YOUR_KEYIFLE_NAME] [SKETCHBOOK_LOCATION]/TEST/android/bin/TEST-unsigned.apk [YOUR_ALIAS]
```
26: Finally Zipalign:```

$ zipalign -v 4 [SKETCHBOOK_LOCATION]/TEST/android/bin/TEST-unsigned.apk TEST.apk
```

The resultant APK file can now be distributed and installed as normal on any android phone set up to allow installs from unknown locations. 
The APK is also now suitable for upload to android market place and hence onto all android phones (well maybe not all, it's obviously dependent on the features you use in the code). You also have to take some screen shots and make some cover art as described on the upload page but you can work on those yourself.

To upload to android marketplace you need to sign up as an android developer. Registering as a developer costs a one of registering fee of $25. Which is really not that bad at all. For comparison it's $99 a year for the privilege of releasing free apps on Apple's store.

Note: If you want to see a pure processing example on the market place search for Radiobiology. The resultant app (The RadioBiology Game) was my first attempt and whilst far from perfect at least it worked ( mostly :-) ).

---

### Post by lykeion on 2011-08-03
Thanks for this clear and concise howto. However using processing-0199 I cannot get a single example to run on the emulator. After installing SDK 2.1 + Google API int the AVD Manager, I try to run an example on the emulator. But after the obligatory coffee break the app is never installed on the emulator. When trying to run again from Processing I need to quit the emulator (it complains that the AVD already exists) which is really frustrating because it should be able to "re-use" the running emulator.

Any suggestions?

EDIT
Managed to install the Easing example on emulator but I had to do it manually. From the terminal output of processing I could gather that the compiled .apk file was compiled to /tmp/android2230329634265415539.pde/bin/Easing-debug.apk
So from the platform-tools directory under the Android SDK install location I ran:
```
./adb install /tmp/android2230329634265415539.pde/bin/Easing-debug.apk
```
and the example was installed successfully. 

Processing 1.99 is not stable yet, but at least it works with a bit of fiddling.

---

