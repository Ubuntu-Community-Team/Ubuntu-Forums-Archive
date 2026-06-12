---
title: "Eclipse Initilization Error"
date: 2007-11-03
forum: Programming Talk
---

### Post by NS2-10 on 2007-11-03
I get the following error when starting Eclipse. I have removed, installed and reinstalled it multiple times and that has no effect. It has nothing to do with JAVA because I can compile and run from terminal. It seems to be an error in Eclipse but I have so far had no luck finding a solution at their site.


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
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.getLineDelimiterPreference(TextFileBufferManager.java:651)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.createEmptyDocument(TextFileBufferManager.java:300)
   at org.eclipse.core.internal.filebuffers.JavaTextFileBuffer.initializeFileBufferContent(JavaTextFileBuffer.java:357)
   at org.eclipse.core.internal.filebuffers.JavaFileBuffer.create(JavaFileBuffer.java:70)
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

---

### Post by pbrockway2 on 2007-11-03
> at java.lang.ClassLoader.loadClass(libgcj.so.81)

Make sure you are using Sun's runtime - or another that works - to run Eclipse, and **not** GNU's (which doesn't).

---

### Post by jmike72 on 2007-11-05
Hi.

I've been trying to run Eclipse using Iced Tea JDK but Eclipse allways complain that a jvm can't be found! I've tried with a parameter to indicate the path to Iced Tea jvm but it's the same!

How can I make it work with Iced Tea? I don't want to have two Java's installed on my x64 Ubuntu.

Miguel

---

### Post by liquidpele on 2007-11-05
Instructions to fix here:
[http://www.aptana.com/trac/ticket/6559](http://www.aptana.com/trac/ticket/6559)

from the link above:

install sun's java VM:
apt-get install sun-java6-jdk

Then configure default VM as sun's:
from [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

If you want to use Sun's Java instead of the open source GIJ (GNU Java bytecode interpreter) you need to set it as default. To list installed JVMs:

update-java-alternatives -l

To select, for example, Sun's JVM as provided in Ubuntu 6.06, run:

sudo update-java-alternatives -s java-1.5.0-sun

You should also edit /etc/jvm and move /usr/lib/jvm/java-1.5.0-sun to the top of JVMs offered.


However, when I did the above it still did not work.
I had to set Eclipse to use the sun jvm in it's own java_home configuration file located here:
/etc/eclipse/java_home

Open up the java_home file, and set the sun jvm above the gcj jvm and it then works!
Becuase of that, not sure if updating the /etc/jvm and update-java-alternatives is necessary or not.

---

### Post by NS2-10 on 2007-11-07
Thanks so much for all the help!

The key things for me was to edit java_home for Eclipse, all the other things where already correct. Wonder why that becomes an issue, it should be solved automaticly if you edit java-alternatives in my opinion. Dunno that much about programming but to me it seems like a relatively simple thing.

---

### Post by Defrector on 2007-11-07
Kudos for the fix. 

I confirm the java_home reordering; that did the trick for me as well.

---

### Post by Cappy on 2007-11-21
This fixed my problem! Somehow this was broken after I upgraded to Gutsy on my laptop.

---

