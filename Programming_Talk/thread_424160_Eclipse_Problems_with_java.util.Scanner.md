---
title: "Eclipse Problems with java.util.Scanner"
date: 2007-04-26
forum: Programming Talk
---

### Post by tonyr1988 on 2007-04-26
Whenever I try anything such as:

> import java.util.Scanner;

in Eclipse, it always complains that "The import java.util.Scanner cannot be resolved". I recently upgraded from Edgy to Feisty, and this is the first time this has happened. Files that worked perfectly under my Edgy Eclipse are now broken in Feisty Eclipse.

I'm sure I just need to install an extra package or two, but I'm not sure which ones.

Also, I just did a fresh install of Feisty on my laptop, and I'm having the same problems with Eclipse.

---

### Post by ssodhi on 2007-04-26
Have you updated your JDK?

-Sanjay Sodhi

---

### Post by tonyr1988 on 2007-04-26
I haven't touched my JDK. I just updated what the Update Manager told me to when I went from Edgy -> Feisty.

---

### Post by kaamos on 2007-04-26
You need Java 1.5 or newer and make sure code compatibility in your eclipse project is also set to 1.5. You can also select which JRE a project uses.

---

### Post by tonyr1988 on 2007-04-26
It looks like I had 1.4.2. Changed to 1.5 and it works perfectly.

I just don't know why it worked before the update, but Feisty broke it? Did it downgrade my JRE? I dunno, but it works, so I'm happy. :)

---

### Post by Todd Bealmear on 2007-04-26
Yeah, it downgrades your JRE - Feisty comes with 1.4 and will replace whatever JRE you were using pre-upgrade.

---

### Post by nick937 on 2008-03-17
I am using Hardy heron and I have the same problem 

```


nick@t00r:~$ java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b24)
IcedTea 64-Bit Server VM (build 1.7.0-b24, mixed mode)

```

---

### Post by nick937 on 2008-03-17
and my JRE is


java-1.5.0-gcj-4.2-1.5.0.0 


can anyone help?

---

### Post by bruce89 on 2008-03-17
The wee error icon on the left of the wrong line might be interesting if you click on it.

---

### Post by nick937 on 2008-03-17
```

Severity and Description	Path	Resource	Location	Creation Time	Id
Scanner cannot be resolved to a type	Lab17b	Lab17.java	line 8	1205809595681	220

```
I have also tried
import java.*;
import java.util.*
import java.util.Scanner
...... when I click the icon it says "rename in file"

Also, when I start up Eclipse it give me this:
```

Unable to create this part due to an internal error. Reason for the failure: An exception was thrown during initialization

java.lang.ClassNotFoundException: org.eclipse.core.runtime.Plugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.core.runtime.Platform.getPlugin(Platform.java:737)
   at org.eclipse.core.internal.preferences.legacy.InitLegacyPreferences.init(InitLegacyPreferences.java:43)
   at org.eclipse.core.internal.preferences.PreferenceServiceRegistryHelper.applyRuntimeDefaults(PreferenceServiceRegistryHelper.java:146)
   at org.eclipse.core.internal.preferences.PreferencesService.applyRuntimeDefaults(PreferencesService.java:337)
   at org.eclipse.core.internal.preferences.DefaultPreferences.applyRuntimeDefaults(DefaultPreferences.java:162)
   at org.eclipse.core.internal.preferences.DefaultPreferences.loadDefaults(DefaultPreferences.java:231)
   at org.eclipse.core.internal.preferences.DefaultPreferences.load(DefaultPreferences.java:227)
   at org.eclipse.core.internal.preferences.EclipsePreferences.create(EclipsePreferences.java:307)
   at org.eclipse.core.internal.preferences.EclipsePreferences.internalNode(EclipsePreferences.java:543)
   at org.eclipse.core.internal.preferences.EclipsePreferences.node(EclipsePreferences.java:662)
   at org.eclipse.core.internal.preferences.PreferencesService.getNodes(PreferencesService.java:588)
   at org.eclipse.core.internal.preferences.PreferencesService.getString(PreferencesService.java:635)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.getLineDelimiterPreference(TextFileBufferManager.java:645)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.createEmptyDocument(TextFileBufferManager.java:300)
   at org.eclipse.core.internal.filebuffers.ResourceTextFileBuffer.initializeFileBufferContent(ResourceTextFileBuffer.java:268)
   at org.eclipse.core.internal.filebuffers.ResourceFileBuffer.create(ResourceFileBuffer.java:242)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.connect(TextFileBufferManager.java:108)
   at org.eclipse.ui.editors.text.TextFileDocumentProvider.createFileInfo(TextFileDocumentProvider.java:561)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitDocumentProvider.createFileInfo(CompilationUnitDocumentProvider.java:909)
   at org.eclipse.ui.editors.text.TextFileDocumentProvider.connect(TextFileDocumentProvider.java:482)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitDocumentProvider.connect(CompilationUnitDocumentProvider.java:1069)
   at org.eclipse.ui.texteditor.AbstractTextEditor.doSetInput(AbstractTextEditor.java:3063)
   at org.eclipse.ui.texteditor.StatusTextEditor.doSetInput(StatusTextEditor.java:173)
   at org.eclipse.ui.texteditor.AbstractDecoratedTextEditor.doSetInput(AbstractDecoratedTextEditor.java:1512)
   at org.eclipse.jdt.internal.ui.javaeditor.JavaEditor.internalDoSetInput(JavaEditor.java:2371)
   at org.eclipse.jdt.internal.ui.javaeditor.JavaEditor.doSetInput(JavaEditor.java:2344)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitEditor.doSetInput(CompilationUnitEditor.java:1428)
   at org.eclipse.ui.texteditor.AbstractTextEditor$5.run(AbstractTextEditor.java:2396)
   at org.eclipse.jface.operation.ModalContext.runInCurrentThread(ModalContext.java:369)
   at org.eclipse.jface.operation.ModalContext.run(ModalContext.java:313)
   at org.eclipse.jface.window.ApplicationWindow$1.run(ApplicationWindow.java:763)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.jface.window.ApplicationWindow.run(ApplicationWindow.java:760)
   at org.eclipse.ui.internal.WorkbenchWindow.run(WorkbenchWindow.java:2283)
   at org.eclipse.ui.texteditor.AbstractTextEditor.internalInit(AbstractTextEditor.java:2414)
   at org.eclipse.ui.texteditor.AbstractTextEditor.init(AbstractTextEditor.java:2441)
   at org.eclipse.ui.internal.EditorManager.createSite(EditorManager.java:842)
   at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:583)
   at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:372)
   at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)
   at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:263)
   at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1474)
   at org.eclipse.ui.internal.EditorManager$5.run(EditorManager.java:1008)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.core.runtime.Platform.run(Platform.java:858)
   at org.eclipse.ui.internal.EditorManager.restoreState(EditorManager.java:1003)
   at org.eclipse.ui.internal.WorkbenchPage.restoreState(WorkbenchPage.java:2843)
   at org.eclipse.ui.internal.WorkbenchWindow.restoreState(WorkbenchWindow.java:1936)
   at org.eclipse.ui.internal.Workbench.doRestoreState(Workbench.java:2873)
   at org.eclipse.ui.internal.Workbench.access$14(Workbench.java:2821)
   at org.eclipse.ui.internal.Workbench$19.run(Workbench.java:1697)
   at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)
   at org.eclipse.ui.internal.Workbench.restoreState(Workbench.java:1695)
   at org.eclipse.ui.internal.Workbench.access$12(Workbench.java:1666)
   at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1545)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.ui.internal.Workbench.restoreState(Workbench.java:1489)
   at org.eclipse.ui.internal.WorkbenchConfigurer.restoreState(WorkbenchConfigurer.java:183)
   at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:702)
   at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)
   at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)
   at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
   at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

```

---

### Post by nick937 on 2008-03-18
so I'm pretty sure that Icon wont help me

---

### Post by jespdj on 2008-03-18
> **nick937 said:**
> I am using Hardy heron and I have the same problem 

```


nick@t00r:~$ java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b24)
IcedTea 64-Bit Server VM (build 1.7.0-b24, mixed mode)

```
Try using Sun Java 6 instead of IcedTea. IcedTea is an alpha / beta / development version of Java 7, so you can expect that not everything works perfectly.
```
sudo apt-get install sun-java6-jdk
sudo update-alternatives --config java
```
Select Sun Java 6 in the menu that the update-alternatives command shows.

---

### Post by TreeFinger on 2008-03-18
Have you attempted compiling from the command line and not through your IDE? Maybe that will help you decide if it is your IDE or your java SDK install that needs to be fixed.

---

### Post by twodayslate on 2008-08-03
```
import java.util.*;
public class twod {
	public static void  main(String[] args) 
	{
		Scanner in = new Scanner(System.in);
		System.out.println("How many rows?");
		int rows = in.nextInt();
		System.out.println("How many columns?");
		int columns = in.nextInt();
		double[][] table = new double[rows][columns];
		
		double input;
	
		for(int r = 0; r < rows; r++)
		{
			for(int c = 0; c < columns; c++)
			{
				System.out.println(r + "," + c + " :");
				input = in.nextDouble();
				table[r][c] = input;
			}
		}
	
		for(double[] e : table)
		{
			System.out.print(e);
		}
		}//end main
}//end

```
error: ```
Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
	Scanner cannot be resolved to a type
	Scanner cannot be resolved to a type

   at twod.main(twod.java:5)
```
```
~$ java -versionjava version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```
What should I choose?
```
 sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/lib/jvm/java-gcj/jre/bin/java
 +        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java

```I hope I did the 2D arrays right.

edit:// Is it my SDK?

---

### Post by twodayslate on 2008-08-09
no help?

---

### Post by tinny on 2008-08-10
> **twodayslate said:**
> no help?

Your answer lies in this thread

[http://ubuntuforums.org/showthread.php?t=874500](http://ubuntuforums.org/showthread.php?t=874500) (same problem as yours)

In summary:

1. Install Sun Java 6 JDK

2. Make sure Sun Java 6 JDK is setup as your default system Java runtime.

3. Make sure that eclipse is using the correct Java runtime.

---

### Post by twodayslate on 2008-08-10
Thanks for the reply!> **tinny said:**
> 3. Make sure that eclipse is using the correct Java runtime.Ok I compiled in command line 
```
javac file.java
```
It did not do anything so I assume it compiled with no errors.

So how do you do #3?

---

### Post by tinny on 2008-08-10
> **twodayslate said:**
> Thanks for the reply!Ok I compiled in command line 
```
javac file.java
```
It did not do anything so I assume it compiled with no errors.

So how do you do #3?

For #2

```

java -version
javac -version

```

Post back the output.

For #3

[http://ubuntuforums.org/showthread.php?t=874500&page=2](http://ubuntuforums.org/showthread.php?t=874500&page=2)

Posts: 16, 17 and 18

---

### Post by twodayslate on 2008-08-10
> **tinny said:**
> For #2

```

java -version
javac -version

```

Post back the output.

For #3

[http://ubuntuforums.org/showthread.php?t=874500&page=2](http://ubuntuforums.org/showthread.php?t=874500&page=2)

Posts: 16, 17 and 18

```
~/Programming/8.6$ javac -version
javac 1.6.0_0-internal
~/Programming/8.6$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

```

Thanks for the link! It fixed everything!

---

### Post by tinny on 2008-08-10
I see that your system is still using the OpenJDK as default (Eclipse is working fine because it overrides this).

To setup the system Java environment correctly

```

sudo update-alternatives --config java

```

Choose the "/usr/lib/jvm/java-6-sun/jre/bin/java" option.

---

### Post by wei2912 on 2010-11-06
I have this problem too.

I installed Eclipse from the Software Center and i selected Java 1.5

However, i cannot import java.util.Scanner

I get this error when i insert Scanner scan = new Scanner(System.in);
Scanner cannot be resolved to a type.
Scanner cannot be resolved to a type.

When i compile my program, i get:
Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
    Scanner cannot be resolved to a type
    Scanner cannot be resolved to a type

Edit: Problem solved, i was supposed to use the default java.

---

