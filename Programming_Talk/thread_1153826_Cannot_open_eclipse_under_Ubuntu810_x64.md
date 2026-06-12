---
title: "Cannot open eclipse under Ubuntu810 x64"
date: 2009-05-09
forum: Programming Talk
---

### Post by zephyrgong on 2009-05-09
Hanging while loading workbench. Workspace could be opened if I made another eclipse instance or re-build the workspace. But even I opened it, I will hang a long time for opening any files.

Belowing is the log file.


!SESSION 2009-05-09 20:21:15.600 -----------------------------------------------
eclipse.buildId=M20090211-1700
java.version=1.6.0_10
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_AU
Command-line arguments:  -os linux -ws gtk -arch x86_64 -debug

!ENTRY org.eclipse.ui.workbench.texteditor 4 0 2009-05-09 20:21:23.749
!MESSAGE The 'org.eclipse.wst.jsdt.web.ui.internal.hyperlink.script.JSPJavaHyperlinkDetector' extension from plug-in 'org.eclipse.wst.jsdt.web.ui' to the 'org.eclipse.ui.workbench.texteditor.hyperlinkDetectors' extension point will be ignored because it contains invalid attributes.

!ENTRY org.eclipse.ui.workbench.texteditor 4 0 2009-05-09 20:21:23.749
!MESSAGE The 'org.eclipse.wst.jsdt.web.ui.internal.hyperlink.script.event.JSPJavaHyperlinkDetector' extension from plug-in 'org.eclipse.wst.jsdt.web.ui' to the 'org.eclipse.ui.workbench.texteditor.hyperlinkDetectors' extension point will be ignored because it contains invalid attributes.

---

### Post by baizon on 2009-05-09
Eclipse installed from source?
This might help: [http://ubuntuforums.org/showthread.php?t=542056)]("http://ubuntuforums.org/showthread.php?t=542056)")

---

