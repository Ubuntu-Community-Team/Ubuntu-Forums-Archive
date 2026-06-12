---
title: "Javascript how to chech with Javascript if browser is using openjre ?"
date: 2012-09-09
forum: Programming Talk
---

### Post by jaho22 on 2012-09-09
how to check with javascript, if browser is starting openjre when with applets.

I want to disable openjre and icedtea-plugin.

---

### Post by ofnuts on 2012-09-09
I don't think you can do it with JS alone, but you can write a small applet that returns values from the System properties, so you can find which runtime is used for applets. See [here]("http://docs.oracle.com/javase/tutorial/deployment/applet/invokingAppletMethodsFromJavaScript.html") for how to communicate between JS and Java applets.

This may let you know which runtime is used but won't let you disable or change it. At best you can avoid loading your applets.

---

### Post by jaho22 on 2012-09-10
Does anyone have any information about OpenJRE or icedtea-plugin bug.

My problem is that when i use OpenJRE and icedtea-plugin with browsers, and if i load any applet.

Then, when i resize the browser window applet size, then use of openjre and icedtea-plugin will cause my cpu rate to jump to 100% at once, this wont happen with oracle when resizing applet.

The cpu rate will stay on 100% even if i close the browser and so the applet too.

a very big problem, so i would like to avoid loading my applets with openjre.

is there any proper solution for this problem ?

---

### Post by ofnuts on 2012-09-10
> **jaho22 said:**
> Does anyone have any information about OpenJRE or icedtea-plugin bug.

My problem is that when i use OpenJRE and icedtea-plugin with browsers, and if i load any applet.

Then, when i resize the browser window applet size, then use of openjre and icedtea-plugin will cause my cpu rate to jump to 100% at once, this wont happen with oracle when resizing applet.

The cpu rate will stay on 100% even if i close the browser and so the applet too.

a very big problem, so i would like to avoid loading my applets with openjre.

is there any proper solution for this problem ?
Running the applets is delegated to a plugin-container process.

This looks like a JRE bug and could be fixed in more recent versions... if this happens on any applet then I doubt you'll find many users using that (version of the) JRE wigth such a blatant problem. If it happens only with your applets then you have a bug and that wouldn't make a good excuse to exclude a specific JRE.

---

