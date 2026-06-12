---
title: "ADT plugin problem after upgrade to Maverick"
date: 2012-01-07
forum: Programming Talk
---

### Post by Vistz on 2012-01-07
I recently upgraded to Maverick (10.10) and now my ADT plugin in Eclipse for Android development doesn't work. I try installing it from "https://dl-ssl.google.com/android/eclipse" by going to "Install Software" in Eclipse. However, I get the error message saying: 

```
Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Traceview 16.0.1.v201112150204-238534 (com.android.ide.eclipse.traceview.feature.group 16.0.1.v201112150204-238534)
  Missing requirement: Android Traceview 16.0.1.v201112150204-238534 (com.android.ide.eclipse.traceview.feature.group 16.0.1.v201112150204-238534) requires 'org.eclipse.ui 3.6.2' but it could not be found
```

---

### Post by ofnuts on 2012-01-07
> **Vistz said:**
> I recently upgraded to Maverick (10.10) and now my ADT plugin in Eclipse for Android development doesn't work. I try installing it from "https://dl-ssl.google.com/android/eclipse" by going to "Install Software" in Eclipse. However, I get the error message saying: 

```
Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Traceview 16.0.1.v201112150204-238534 (com.android.ide.eclipse.traceview.feature.group 16.0.1.v201112150204-238534)
  Missing requirement: Android Traceview 16.0.1.v201112150204-238534 (com.android.ide.eclipse.traceview.feature.group 16.0.1.v201112150204-238534) requires 'org.eclipse.ui 3.6.2' but it could not be found
```
What version of Eclipse are you running? The one from the Ubuntu rep is likely a bit outdated. If you are doing serious eclipse development, install directly from the eclipse site.

---

### Post by KdotJ on 2012-01-07
If it's Indigo, you need to add this repo to the "Add new software..." (or whatever its called exactly) menu in Eclipse:

```
http://download.eclipse.org/releases/indigo
```

Then try and install/update the android plugin

---

### Post by Vistz on 2012-01-08
> **ofnuts said:**
> What version of Eclipse are you running? The one from the Ubuntu rep is likely a bit outdated. If you are doing serious eclipse development, install directly from the eclipse site.

I have now updated my eclipse version to indigo
> **KdotJ said:**
> If it's Indigo, you need to add this repo to the "Add new software..." (or whatever its called exactly) menu in Eclipse:

```
http://download.eclipse.org/releases/indigo
```

Then try and install/update the android plugin
I am able to get the SDK reinstalled along with most of the AVD's I previously had.

I have run this in the terminal:
```
./android update sdk

```

However, I previously had Google API's 8/9 installed and now it says that they failed to load. And they don't appear when I refresh the AVD manager.

---

### Post by Vistz on 2012-01-08
*Update*

After restarting, I was able to install/fix the Google 8 SDK properly. Thanks again.

---

