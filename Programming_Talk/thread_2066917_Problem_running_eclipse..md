---
title: "Problem running eclipse."
date: 2012-10-05
forum: Programming Talk
---

### Post by Mohammad_Khalid_Hussain on 2012-10-05
Assalamu'alaikum,
and Hi! to everyone else.

I have trouble getting Eclipse IDE to run. I installed it from the Terminal using this:
```
sudo apt-get install eclipse-platform
```

It installs fine but when I run it from the Dash, it gives me an error and the details are stored in a log file whose contents are:
```
!SESSION 2012-10-06 05:15:35.593 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0_07
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 4 0 2012-10-06 05:15:38.196
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
	no swt-gtk-3740 in java.library.path
	no swt-gtk in java.library.path
	Can't load library: /home/khalid/.swt/lib/linux/x86_64/libswt-gtk-3740.so
	Can't load library: /home/khalid/.swt/lib/linux/x86_64/libswt-gtk.so

	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:285)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
	at org.eclipse.swt.internal.C.<clinit>(C.java:21)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:695)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:153)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:95)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:601)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1410)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1386)
```

Can anyone please tell me what's wrong and how I may rectify this problem?

Thanks for your time.

---

### Post by mevun on 2012-10-05
I found my libswt* libraries in this location: /usr/lib/jni/
Assuming yours are in the same location, you can use this command:
```

ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64

```

I wonder if this is fixed for Eclipse Juno.  I am using Eclipse Indigo and ran into the exact same problem you have.

---

### Post by Mohammad_Khalid_Hussain on 2012-10-07
Thank you so much for this, it worked.

But could you please explain to me what the command does exactly?

---

### Post by mevun on 2012-10-07
> **Mohammad_Khalid_Hussain said:**
> Thank you so much for this, it worked.

But could you please explain to me what the command does exactly?

You're welcome.

The command "ln" makes a link between two files.  In other OSes, this might be called a "shortcut" (Windows) or "alias" (Mac OS), although those OSes also provide graphical icons for that purpose.  Basically, the link provides a pointer to the real file.  So Eclipse is looking in one directory and the link makes it seem like that file is in that directory when really the file contents would be in a different directory.

As for the "-s" option, that makes the link "symbolic" which has some explanation in the man page for the ln command.

Just to let you know, one could also copy the files from their original directory to the directory in which Eclipse is searching.  The difference is that the symbolic link means if you replace the real files (maybe due to an upgrade), then Eclipse would also see the replacement files.  If you use a "hard" link (opposite of "symbolic"), then I think that the link gets broken/deleted if you were to replace the original files.  I'm not entirely sure about the differences between hard and symbolic links though.

---

### Post by Mohammad_Khalid_Hussain on 2012-10-07
Thank you very much.

---

### Post by nowashburn on 2012-11-18
> **mevun said:**
> I found my libswt* libraries in this location: /usr/lib/jni/
Assuming yours are in the same location, you can use this command:
```

ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64

```

I wonder if this is fixed for Eclipse Juno.  I am using Eclipse Indigo and ran into the exact same problem you have.

thank you, this worked for me also. i was trying to run compass.app and was getting the same type of error. i had to delete the existsing files in the ~/.swt/lib/linux/x86_64 folder first and after that everything is now working as expected.

not sure if it matters, but i originally had openJDK installed and then switched to the true oracle version and removed openJDK.

---

### Post by mevun on 2012-11-19
> **nowashburn said:**
> thank you, this worked for me also. i was trying to run compass.app and was getting the same type of error. i had to delete the existsing files in the ~/.swt/lib/linux/x86_64 folder first and after that everything is now working as expected.

not sure if it matters, but i originally had openJDK installed and then switched to the true oracle version and removed openJDK.

I think Ubuntu has openJDK installed by default when you install Eclipse through the Software Centre in Ubuntu 12.  For me, I first installed Eclipse through the Software Centre, then I read that for Android development I should use the Oracle JDK.  So after installing Oracle JDK, I ran into the Eclipse won't start problem and googled to find someone else who had fixed it with symbolic linking.

I don't remember if I had existing files/links such that I had to delete them first.  I did a little research on the "ln" command and there is a way to either force (-f, which would delete existing links/files) or an interactive mode (-i, which would ask if you wanted to overwrite).  Still, it is probably best to inspect the existing files when we're not really sure what we might be deleting.

---

