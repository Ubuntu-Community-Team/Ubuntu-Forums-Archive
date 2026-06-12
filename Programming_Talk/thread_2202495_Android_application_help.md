---
title: "Android application help?"
date: 2014-01-29
forum: Programming Talk
---

### Post by TheodoreP on 2014-01-29
I was creating a java stand-alone app for computers. But since I upgraded to an android phone I decided to switch gears and go after a mobile android application for my website first. However I have a few errors in my R.java file that I have no clue how to fix. Please keep in mind that this is a work in progress and the functionality is not present. I'm starting with a nice ui a present then I'll work on login screen images, followed by the functionality. If your experienced in java and android application development I invite you to check my code in the [github]("https://github.com/Teds-Unique-Area-Graphics/SocialCooking") repo. I myself am using eclipse for the coding and my samsung galaxy rugby pro to test. But eclipse wont allow me to run the application until all errors are fixed.

P.S. 

I'm using an online tutorial to guide me through the process and altering certain areas of code to create a uniquely styled application. To view the tutorial please visit [http://www.androidhive.info/2011/10/android-login-and-registration-screen-design/](http://www.androidhive.info/2011/10/android-login-and-registration-screen-design/)

As well I believe the only error is positioned in the R.java gen folder file.

Ok, I just realized that the gen folder is ignored when pushing to github. So I'll post the two lines that are triggering errors.

first error line

public static final int Email**/**Username=0x7f050011;

second error line

public static final int New **to** Social Cooking**?** **Register** here=0x7f050014;

The bold characters and words are the bold because eclipse is underlining them. I'm almost certain that the error is something simple that my inexperienced eye isn't catching. Thank you for your help.

---

### Post by niney on 2014-01-29
It's your declarations in login.xml

```
android:text="@+string/New to Social Cooking? Register here"
```
this should be a string reference such as
```
android:text="@string/link_to_register"
```

then add the appropriate text in your strings.xml (which you already have in res/values/)

you can also just inline it ```
android:text="New to Social Cooking? Register here"
``` but that's not recommended and gives out a warning (I think)

---

### Post by TheodoreP on 2014-01-29
Thanks for the help niney. That helped get the application working again. However if you'll indulge me with one more problem. I launched the application assuming it would start by displaying the login screen. However, when I launched the app I found that it was still launching with the previous one text field from the android.com beginners tutorial. What might I need to change to call the login screen display instead of the original enter a message text field?

Ok, taking a closer look at the code I figured it out. it's the activity_main.xml that needs work. It's calling a text field instead of the login.xml. How might I call the login.xml file?

Ok, I figured I try changing a line in the MainActivity.java file and it worked but would still appreciate the help in spotting any bugs I might of missed. Currently though I'll focus getting the background to a decent color and images.

---

### Post by niney on 2014-01-30
The startup activity is in your AndroidManifest.xml.
You can see one of the <activity> tags has an <intent-filter> block with MAIN and LAUNCHER in it. Just move that one to the one you want to start up with.

---

### Post by TheodoreP on 2014-01-30
Thanks niney, after reading your post I opened the android manifest file and noticed that but, thinking on it I will keep that set to main so that I can use a session tracking system to determine when to display the login screen and when to show the recipes, more on that later though.

I am however still having a little trouble with text link below the login form in login.xml. It's supposed to send you to a registration page a.k.a the RegisterActivity.java file.

---

