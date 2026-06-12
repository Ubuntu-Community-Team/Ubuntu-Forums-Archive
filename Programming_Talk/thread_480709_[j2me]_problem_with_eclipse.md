---
title: "[j2me] problem with eclipse"
date: 2007-06-21
forum: Programming Talk
---

### Post by robgr85 on 2007-06-21
Hi!

Just wanted to configure eclipse on my linux and got following error in 'Device Management'

> An error (eclipseme.core.persistence.PersistenceException: Attribute "version" was already specified for element "deviceRegistry".) occurred reading the device registry.
Please consult the error log for more information.

please help me with that :( I like eclipse and do not want to swap to NetBeans. My eclipse version is 3.2 and I got wtk2.5.1 installed,

Thanks for any response,

Robert

---

### Post by ahvargas on 2007-06-22
How do you install eclipse in your machine?
you installed via apt-get?

---

### Post by robgr85 on 2007-06-22
> **ahvargas said:**
> How do you install eclipse in your machine?
you installed via apt-get?

Yeah, I've installed it via apt-get. 

Regards,
Robert

---

### Post by ahvargas on 2007-06-22
Can you post your log file?

---

### Post by robgr85 on 2007-06-22
> **ahvargas said:**
> Can you post your log file?

Here You have my full eclipse error log

---

### Post by ahvargas on 2007-06-22
That is a very large log file. :P

Well it seem that your configuration get someway bad. I think if you delete the configuration it make work.
Try  in your home

rm -rf .eclipse

If that doesnt do the job you can try to remove the config files in yoyr worksapce directory.

---

### Post by robgr85 on 2007-06-22
> **ahvargas said:**
> That is a very large log file. :P

Well it seem that your configuration get someway bad. I think if you delete the configuration it make work.
Try  in your home

rm -rf .eclipse

If that doesnt do the job you can try to remove the config files in yoyr worksapce directory.

I've tried removing eclipse with 

dpkg -P

and installing again through apt but it didn't help.
didn't checked if it removed .eclipse directory, I'll try remove it manually tomorrow, as You adviced me. 

Robert

---

### Post by robgr85 on 2007-06-23
I removed eclipse with dpkg -P, then manually removed .eclipse directory, installed again.

the same place error
> 
An error (gnu.xml.dom.ls.DomLSException: duplicate attribute: "version") occurred reading the device registry.
Please consult the error log for more information.


log for this error:

exception stack trace:
> 
gnu.xml.dom.ls.DomLSException: duplicate attribute: "version"
at gnu.xml.dom.ls.DomLSParser.doParse(libgcj.so.70)
at gnu.xml.dom.ls.DomLSParser.parse(libgcj.so.70)
at gnu.xml.dom.DomDocumentBuilder.parse(libgcj.so.70)
at javax.xml.parsers.DocumentBuilder.parse(libgcj.so.70)
at eclipseme.core.internal.utils.XMLUtils.readDocument(XMLUtils.java:227)
at eclipseme.core.model.device.DeviceRegistry.load(DeviceRegistry.java:235)
at eclipseme.ui.internal.preferences.DeviceManagementPreferencePage.createContents(DeviceManagementPreferencePage.java:225)
at org.eclipse.jface.preference.PreferencePage.createControl(PreferencePage.java:233)
at org.eclipse.jface.preference.PreferenceDialog.createPageControl(PreferenceDialog.java:1403)
at org.eclipse.jface.preference.PreferenceDialog$12.run(PreferenceDialog.java:1162)
at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
at org.eclipse.core.runtime.Platform.run(Platform.java:843)
at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:44)
at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:149)
at org.eclipse.jface.preference.PreferenceDialog.showPage(PreferenceDialog.java:1156)
at org.eclipse.ui.internal.dialogs.FilteredPreferenceDialog.showPage(FilteredPreferenceDialog.java:438)
at org.eclipse.jface.preference.PreferenceDialog$8.selectionChanged(PreferenceDialog.java:661)
at org.eclipse.jface.viewers.StructuredViewer$3.run(StructuredViewer.java:839)
at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
at org.eclipse.core.runtime.Platform.run(Platform.java:843)
at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:44)
at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:149)
at org.eclipse.jface.viewers.StructuredViewer.firePostSelectionChanged(StructuredViewer.java:837)
at org.eclipse.jface.viewers.StructuredViewer.handlePostSelect(StructuredViewer.java:1143)
at org.eclipse.jface.viewers.StructuredViewer$5.widgetSelected(StructuredViewer.java:1163)
at org.eclipse.jface.util.OpenStrategy.firePostSelectionEvent(OpenStrategy.java:236)
at org.eclipse.jface.util.OpenStrategy.access$4(OpenStrategy.java:230)
at org.eclipse.jface.util.OpenStrategy$3.run(OpenStrategy.java:404)
at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
at org.eclipse.jface.window.Window.runEventLoop(Window.java:820)
at org.eclipse.jface.window.Window.open(Window.java:796)
at org.eclipse.ui.internal.OpenPreferencesAction.run(OpenPreferencesAction.java:65)
at org.eclipse.jface.action.Action.runWithEvent(Action.java:499)
at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:539)
at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:400)
at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3180)
at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2856)
at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1930)
at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1894)
at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
at java.lang.reflect.Method.invoke(libgcj.so.70)
at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
at org.eclipse.core.launcher.Main.run(Main.java:977)
at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.xml.sax.SAXParseException: duplicate attribute: "version"
at gnu.xml.stream.SAXParser.parse(libgcj.so.70)
at gnu.xml.dom.ls.DomLSParser.doParse(libgcj.so.70)
...57 more
Caused by: javax.xml.stream.XMLStreamException: duplicate attribute: "version"
at gnu.xml.stream.XMLParser.error(libgcj.so.70)
at gnu.xml.stream.XMLParser.readAttribute(libgcj.so.70)
at gnu.xml.stream.XMLParser.readStartElement(libgcj.so.70)
at gnu.xml.stream.XMLParser.next(libgcj.so.70)
at gnu.xml.stream.XMLParser.hasNext(libgcj.so.70)
at gnu.xml.stream.SAXParser.parse(libgcj.so.70)
...58 more

-Session data:
> 
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=pl_PL
Command-line arguments:  -os linux -ws gtk -arch x86


help please, until it is not properly installed I must work on winshit :/

Robert

---

### Post by robgr85 on 2007-06-24
noone knows the solution to my problem?

robert

---

### Post by robgr85 on 2007-06-26
if noone know how to solve that problem, maybe any suggestions which ide should I choose for j2me programming under linux (but please do not tell me to use netbeans...)

Robert

---

### Post by ahvargas on 2007-06-29
You can try, to install eclipse downloading it of the oficial site instead of usuing the deb.

---

### Post by robgr85 on 2007-06-29
> **ahvargas said:**
> You can try, to install eclipse downloading it of the oficial site instead of usuing the deb.

i solved my problem, with help of j2me-mailing list subscribers. What was wrong? I got installed gnu java, and sun-java - the problem was that even if I set paths to sun-java my kubuntu was using gnu java. I removed gnu java and set sun-java as default.

Robert

---

### Post by gorgo on 2007-07-02
> **robgr85 said:**
> i solved my problem, with help of j2me-mailing list subscribers. What was wrong? I got installed gnu java, and sun-java - the problem was that even if I set paths to sun-java my kubuntu was using gnu java. I removed gnu java and set sun-java as default.

Robert

i have the same problem robgr85. could you please tell me how did you removed gnu java and set sun-java as default?

thanks

---

### Post by robgr85 on 2007-07-03
Hi!

Remove gnujava with aptitude, then use it to install sun-java :>

if You have sun-java installed and do not want to remove gnu java, You can still try to set sun-java as default with this command

sudo update-java-alternatives -s java-1.6.0-sun [depending on sun-java's version installed on Your ubuntu]


more:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

hope it helps if not ask, I'll help.
Robert

---

### Post by gorgo on 2007-07-03
thanks** robgr85** !!! it finally works!! Thanks so much!
now its time to program :cool:

---

### Post by naughtykid on 2007-08-15
Thanks, this really helps me too. I have googled a lot but was in vain. Appreciate a lot.

---

### Post by erlguta on 2008-02-18
I have the same problem with the same error message.
I have removed java-gcj-compat java-gcj-compat-dev eclipse-gcj and set sun-java with:
sudo update-java-alternatives -s java-6-sun but the error still persist if i go to Eclipse > Preferences > J2ME > Device Management:

```

An error (eclipseme.core.persistence.PersistenceException: Attribute "version" was already specified for element "deviceRegistry".) occurred reading the device registry.
Please consult the error log for more information.

```

What i am doing wrong? I only have sun-java6 installed
:(

---

### Post by erlguta on 2008-02-20
I solved the problem. In eclipse i must put the PATH in preferences > j2me and in WTK root i put /opt/j2me/bin (where i installed the wireless toolkits) i i must put "obviously" the root directory: only /opt/root

---

