---
title: "Eclipse is returnig error"
date: 2006-10-30
forum: Programming Talk
---

### Post by Desi-Tek.com on 2006-10-30
```
!SESSION 2006-10-28 09:36:11.717 -----------------------------------------------
eclipse.buildId=I20050401-1645
java.fullversion=GNU libgcj 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_IN
Command-line arguments:  -os linux -ws gtk -arch x86 -data /home/dheeraj/workspace

!ENTRY org.eclipse.osgi 2006-10-28 09:36:11.718
!MESSAGE Application error
!STACK 1
java.lang.RuntimeException: Application "org.eclipse.ui.ide.workbench" could not be found in the registry. The applications available are: org.eclipse.update.core.standaloneUpdate, org.eclipse.pde.junit.runtime.uitestapplication, org.eclipse.pde.junit.runtime.coretestapplication, org.eclipse.pde.junit.runtime.legacyUItestapplication, org.eclipse.pde.junit.runtime.legacyCoretestapplication, org.eclipse.help.base.infocenterApplication, org.eclipse.help.base.helpApplication, org.eclipse.help.base.indexTool, org.eclipse.jdt.core.JavaCodeFormatter, org.eclipse.pde.build.BuildScriptGenerator, org.eclipse.pde.build.FetchScriptGenerator, org.eclipse.ant.core.antRunner.
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:218)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:156)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:315)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:269)
   at org.eclipse.core.launcher.Main.run(Main.java:943)
   at org.eclipse.core.launcher.Main.main(Main.java:926)

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.282
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.team.bugzilla_0.1.0/ [3] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.282
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.283
!MESSAGE Missing required bundle org.eclipse.team.bugs_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.283
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.283
!MESSAGE Missing required bundle org.eclipse.team.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.285
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.team.bugs_0.1.0/ [4] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.285
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.285
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.285
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.287
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.managedbuilder.core_3.0.0/ [5] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.287
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.291
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.debug.mi.ui_3.0.0/ [11] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.291
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.291
!MESSAGE Missing required bundle org.eclipse.cdt.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.291
!MESSAGE Missing required bundle org.eclipse.cdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.291
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.300
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.debug.ui_3.0.0/ [12] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.300
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.300
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.300
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.300
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.300
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.300
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.301
!MESSAGE Missing required bundle org.eclipse.cdt.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.306
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.launch_3.0.0/ [14] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.306
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.306
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.307
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.307
!MESSAGE Missing required bundle org.eclipse.cdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.307
!MESSAGE Missing required bundle org.eclipse.cdt.debug.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.313
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.make.ui_3.0.0/ [16] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.313
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.313
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.313
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.313
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.313
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.314
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.314
!MESSAGE Missing required bundle org.eclipse.cdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.314
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.325
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.pde.ui_3.1.0/ [17] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.325
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.325
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.325
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.326
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.326
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.326
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.326
!MESSAGE Missing required bundle org.eclipse.jdt.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.326
!MESSAGE Missing required bundle org.eclipse.jdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.326
!MESSAGE Missing required bundle org.eclipse.search_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.326
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.326
!MESSAGE Missing required bundle org.eclipse.ant.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.327
!MESSAGE Missing required bundle org.eclipse.jdt.junit_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.327
!MESSAGE Missing required bundle org.eclipse.ui.intro_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.327
!MESSAGE Missing required bundle org.eclipse.ui.cheatsheets_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.328
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.managedbuilder.gnu.ui_3.0.0/ [19] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.328
!MESSAGE Missing required bundle org.eclipse.cdt.managedbuilder.core_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.332
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.managedbuilder.ui_3.0.0/ [20] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.332
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.332
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.332
!MESSAGE Missing required bundle org.eclipse.cdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.332
!MESSAGE Missing required bundle org.eclipse.cdt.managedbuilder.core_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.338
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.refactoring_3.0.0/ [21] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.338
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.338
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.338
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.338
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.338
!MESSAGE Missing required bundle org.eclipse.ltk.ui.refactoring_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.338
!MESSAGE Missing required bundle org.eclipse.search_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.382
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt.ui_3.0.0/ [22] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.382
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.383
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.383
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.383
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.383
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.383
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.383
!MESSAGE Missing required bundle org.eclipse.search_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.383
!MESSAGE Missing required bundle org.eclipse.compare_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.383
!MESSAGE Missing required bundle org.eclipse.ui.console_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.385
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.cdt_3.0.0/ [23] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.385
!MESSAGE Missing required bundle org.eclipse.ui.intro_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.385
!MESSAGE Missing required bundle org.eclipse.ui.cheatsheets_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.395
!MESSAGE Bundle update@/usr/share/eclipse/plugins/com.redhat.eclipse.changelog.core_2.0.1/ [24] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.395
!MESSAGE Missing required bundle org.eclipse.jdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.395
!MESSAGE Missing optionally required bundle org.eclipse.cdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.395
!MESSAGE Missing required bundle org.eclipse.team.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.395
!MESSAGE Missing required bundle org.eclipse.compare_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.395
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.395
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.395
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.396
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.396
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.396
!MESSAGE Missing optionally required bundle org.python.pydev_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.404
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.jdt.debug.ui_3.1.0/ [27] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.404
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.404
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.404
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.404
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.404
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.405
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.405
!MESSAGE Missing required bundle org.eclipse.jdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.405
!MESSAGE Missing required bundle org.eclipse.ui.console_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.414
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.jdt.junit_3.1.0/ [32] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.414
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.414
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.414
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.414
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.414
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.414
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.415
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.415
!MESSAGE Missing required bundle org.eclipse.jdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.415
!MESSAGE Missing required bundle org.eclipse.jdt.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.415
!MESSAGE Missing required bundle org.eclipse.compare_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.424
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.jdt.ui_3.1.0/ [34] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.424
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.424
!MESSAGE Missing required bundle org.eclipse.ui.console_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.search_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.compare_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.425
!MESSAGE Missing required bundle org.eclipse.ltk.ui.refactoring_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.427
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.jdt_3.1.0/ [35] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.427
!MESSAGE Missing required bundle org.eclipse.ui.intro_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.427
!MESSAGE Missing required bundle org.eclipse.ui.cheatsheets_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.428
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.pde.runtime_3.1.0/ [42] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.428
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.428
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.435
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ant.ui_3.1.0/ [48] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.435
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing optionally required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing optionally required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing optionally required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing optionally required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing required bundle org.eclipse.ui.externaltools_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing required bundle org.eclipse.ui.console_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.436
!MESSAGE Missing required bundle org.eclipse.jdt.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.437
!MESSAGE Missing required bundle org.eclipse.jdt.debug.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.477
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.compare_3.1.0/ [49] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.478
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.478
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.478
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.478
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.478
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.482
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.debug.ui_3.1.0/ [61] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.483
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.483
!MESSAGE Missing required bundle org.eclipse.ui.console_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.483
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.483
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.483
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.483
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.485
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.help.ui_3.1.0.jar [64] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.485
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.486
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.presentations.r21_3.1.0.jar [67] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.486
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.489
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ltk.ui.refactoring_3.1.0/ [68] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.489
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.490
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.490
!MESSAGE Missing required bundle org.eclipse.compare_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.490
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.491
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.platform.doc.isv_3.1.0/ [72] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.491
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.492
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.sdk_3.1.0/ [75] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.492
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.492
!MESSAGE Missing required bundle org.eclipse.help.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.495
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.search_3.1.0/ [76] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.495
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.496
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.496
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.496
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.496
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.497
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.team.cvs.ssh2_3.1.0/ [80] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.497
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.504
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.team.cvs.ui_3.1.0/ [82] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.504
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.504
!MESSAGE Missing optionally required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.504
!MESSAGE Missing optionally required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.504
!MESSAGE Missing optionally required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.505
!MESSAGE Missing optionally required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.505
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.505
!MESSAGE Missing required bundle org.eclipse.ui.console_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.505
!MESSAGE Missing required bundle org.eclipse.team.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.505
!MESSAGE Missing required bundle org.eclipse.compare_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.507
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.team.ui_3.1.0/ [83] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.507
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.507
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.508
!MESSAGE Missing required bundle org.eclipse.compare_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.508
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.browser_3.1.0/ [86] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.509
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.511
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.cheatsheets_3.0.0/ [87] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.511
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.513
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.console_3.1.0/ [88] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.513
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.513
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.514
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.516
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.editors_3.1.0/ [89] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.517
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.517
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.517
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.517
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.519
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.externaltools_3.1.0/ [90] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.519
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.520
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.520
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.523
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.ide_3.1.0.jar [92] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.523
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.523
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.523
!MESSAGE Missing required bundle org.eclipse.update.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.525
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.intro_3.1.0.jar [93] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.525
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.526
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.workbench_3.1.0.jar [94] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.526
!MESSAGE Missing required bundle org.eclipse.jface_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.527
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.views_3.1.0.jar [95] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.527
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.528
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.workbench.compatibility_3.1.0/ [96] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.529
!MESSAGE Missing host org.eclipse.ui.workbench_[3.0.0,4.0.0).

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.530
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui.workbench.texteditor_3.1.0/ [97] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.530
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.530
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.531
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.ui_3.1.0.jar [98] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.531
!MESSAGE Missing required bundle org.eclipse.jface_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.531
!MESSAGE Missing required bundle org.eclipse.ui.workbench_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.533
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.update.scheduler_3.1.0.jar [102] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.533
!MESSAGE Missing required bundle org.eclipse.update.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.533
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.535
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.eclipse.update.ui_3.1.0.jar [103] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.535
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.541
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.python.pydev.debug_0.9.3/ [106] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.541
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.578
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.578
!MESSAGE Missing required bundle org.eclipse.ui.externaltools_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.578
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.578
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.578
!MESSAGE Missing required bundle org.eclipse.debug.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.578
!MESSAGE Missing required bundle org.python.pydev_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.578
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.578
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.579
!MESSAGE Missing required bundle org.eclipse.ui.console_[0.0.0,null.

!ENTRY org.eclipse.osgi 2006-10-28 09:36:12.582
!MESSAGE Bundle update@/usr/share/eclipse/plugins/org.python.pydev_0.9.3/ [108] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.582
!MESSAGE Missing required bundle org.eclipse.ui_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.582
!MESSAGE Missing required bundle org.eclipse.ui.editors_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.582
!MESSAGE Missing required bundle org.eclipse.ui.views_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.582
!MESSAGE Missing required bundle org.eclipse.ui.ide_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.582
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[0.0.0,null.
!SUBENTRY 1 org.eclipse.osgi 2006-10-28 09:36:12.583
!MESSAGE Missing required bundle org.eclipse.jface.text_[0.0.0,null.

```

how to fix this error?

---

### Post by FyreBrand on 2006-10-30
How did you install eclipse and all of the plug-ins?  What version of JDK did you install.  Does your installed version of eclipse (GCJ or std Sun Java compile) did you install and did you make sure it matches the JRE that's running it?

My recommendation:

1. remove eclipse.

2. Install Sun Java SDK 1.5.0 via this HowTo: [**Java**]("https://help.ubuntu.com/community/Java")
Read that page carefully and make sure you have Sun's JDK and the JRE installed and configured properly.  It tells you everything you need to do.

3. Now install eclipse from the repositories.  Search Synaptic with the keyword "eclipse".  Select the eclipse main packages and the plug-ins you need (such as CDT or PyDev).  Make sure you install the _standard not the GCJ_ packages.  If you need a localization for a language other than english then select the appropriate localization packages.

4. Note that the eclipse updater has never worked well for me in Linux.  I don't use eclipse much anymore so maybe that functionality has improved, but if you are using it and getting problems that could be the reason.

It might help to search the forums for "eclipse" as well and read some other people's problems and solutions as well as their install tips.

---

