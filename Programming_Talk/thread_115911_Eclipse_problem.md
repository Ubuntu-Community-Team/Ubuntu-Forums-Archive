---
title: "Eclipse problem"
date: 2006-01-11
forum: Programming Talk
---

### Post by 0x001A4 on 2006-01-11
Ok so I'm used to using on windows at school. I thought I would get it at home so I did. The first thing I noticed is that Eclipse is horribly slow here. I dont know this is, but it takes alot longer to load and in general is very sluggish.

Not only that but when I start ecplise I get this message in either the main window or the package explorer:
```
Unable to create this part due to an internal error. Reason for the failure: The editor class could not be instantiated. This usually indicates that the editor's class name was mistyped in plugin.xml.
```

If I click on details this is what shows up:
```
java.lang.ClassNotFoundException: org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitEditor
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.WorkbenchPlugin$1.run() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(org.eclipse.swt.widgets.Display, java.lang.Runnable) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.WorkbenchPlugin.createExtension(org.eclipse.core.runtime.IConfigurationElement, java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.registry.EditorDescriptor.createEditor() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.EditorManager.createPart(org.eclipse.ui.internal.registry.EditorDescriptor) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.EditorReference.createPartHelper() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.EditorReference.createPart() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.WorkbenchPartReference.getPart(boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(org.eclipse.ui.IEditorReference, boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.EditorManager.setVisibleEditor(org.eclipse.ui.IEditorReference, boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.EditorManager$5.run() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.runtime.InternalPlatform.run(org.eclipse.core.runtime.ISafeRunnable) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.runtime.Platform.run(org.eclipse.core.runtime.ISafeRunnable) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.ui.internal.EditorManager.restoreState(org.eclipse.ui.IMemento) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
```

So if I go ahead with whatever I'm doing, the message goes away and eclipse seems ok. When I try to run a program I get an error even though I know the program works because I just it going at school an hour ago:
```
** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
```

Anyone have any idea what might be causing either of these?

---

### Post by Leif on 2006-01-11
you could try using sun's jdk instead. do a search in the forums, there are plenty of threads that show how to install it. I'd recommend one of these two :

[http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories.html](http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories.html)
[http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories_26.html](http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories_26.html)

---

### Post by 0x001A4 on 2006-01-11
Well I tried what you said, and I still get the same errors.

---

### Post by orbit on 2006-01-12
[QUOTE=0x001A4]Well I tried what you said, and I still get the same errors.[/QUOTE]

That's because Eclipse doesn't follow your prefered java vm setting.  To make eclipse use Sun's Java VM follow these simple steps:

Open your eclipse settings file:
```
gedit ~/.eclipse/eclipserc
```

Add your prefered Java VM.  You need to know Jave Home directory for the Java VM you want to use.  For example, I added this to the end of my eclipserc file:
```
JAVA_HOME=/usr/lib/j2sdk1.5-sun/
```

Save the file and restart eclipse.  It should be using your prefered Java VM.  


Happy coding,
orbit

---

