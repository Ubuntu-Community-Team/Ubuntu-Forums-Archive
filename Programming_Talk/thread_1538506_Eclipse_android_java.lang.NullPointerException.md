---
title: "Eclipse android java.lang.NullPointerException"
date: 2010-07-25
forum: Programming Talk
---

### Post by dantibb on 2010-07-25
Trying to use eclipse with android sdk and plugin. All was working OK yesterday, Nothing has changed as far as am aware, but whenever I try to create new android project, if I go into res/values/strings.xml I get this error every time:[INDENT]An error has occurred. See error log for more details.
java.lang.NullPointerException

Problems occurred when invoking code from plug-in: "org.eclipse.jface".

java.lang.NullPointerException
at org.eclipse.wst.xml.core.internal.document.ElementImpl.getDefaultValue(ElementImpl.java:259)
at org.eclipse.wst.xml.core.internal.document.ElementImpl.getAttributeNS(ElementImpl.java:329)
at com.android.ide.eclipse.adt.internal.editors.uimodel.UiElementNode.getShortDescription(Unknown Source)
at com.android.ide.eclipse.adt.internal.editors.ui.tree.UiModelTreeLabelProvider.getText(Unknown Source)
at org.eclipse.jface.viewers.WrappedViewerLabelProvider.getText(WrappedViewerLabelProvider.java:10
at org.eclipse.jface.viewers.WrappedViewerLabelProvider.update(WrappedViewerLabelProvider.java:164)
at org.eclipse.jface.viewers.ViewerColumn.refresh(ViewerColumn.java:152)
at org.eclipse.jface.viewers.AbstractTreeViewer.doUpdateItem(AbstractTreeViewer.java:934)
at org.eclipse.jface.viewers.AbstractTreeViewer$UpdateItemSafeRunnable.run(AbstractTreeViewer.java:102)
at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:42)
at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:49)
at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:175)
at org.eclipse.jface.viewers.AbstractTreeViewer.doUpdateItem(AbstractTreeViewer.java:1014)
at org.eclipse.jface.viewers.StructuredViewer$UpdateItemSafeRunnable.run(StructuredViewer.java:481)
at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:42)
at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:49)
at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:175)
at org.eclipse.jface.viewers.StructuredViewer.updateItem(StructuredViewer.java:2141)
at org.eclipse.jface.viewers.AbstractTreeViewer.updateChildren(AbstractTreeViewer.java:2689)
at org.eclipse.jface.viewers.AbstractTreeViewer.internalRefreshStruct(AbstractTreeViewer.java:1867)
at org.eclipse.jface.viewers.TreeViewer.internalRefreshStruct(TreeViewer.java:721)
at org.eclipse.jface.viewers.AbstractTreeViewer.internalRefresh(AbstractTreeViewer.java:1842)
at org.eclipse.jface.viewers.AbstractTreeViewer.internalRefresh(AbstractTreeViewer.java:1799)
at org.eclipse.jface.viewers.AbstractTreeViewer.internalRefresh(AbstractTreeViewer.java:1785)
at org.eclipse.jface.viewers.StructuredViewer$7.run(StructuredViewer.java:1487)
at org.eclipse.jface.viewers.StructuredViewer.preservingSelection(StructuredViewer.java:1422)
at org.eclipse.jface.viewers.TreeViewer.preservingSelection(TreeViewer.java:403)
at org.eclipse.jface.viewers.StructuredViewer.preservingSelection(StructuredViewer.java:1383)
at org.eclipse.jface.viewers.StructuredViewer.refresh(StructuredViewer.java:1485)
at org.eclipse.jface.viewers.ColumnViewer.refresh(ColumnViewer.java:537)
at org.eclipse.jface.viewers.StructuredViewer.refresh(StructuredViewer.java:1444)
at org.eclipse.jface.viewers.ContentViewer.setContentProvider(ContentViewer.java:252)
at org.eclipse.jface.viewers.StructuredViewer.setContentProvider(StructuredViewer.java:1641)
at org.eclipse.jface.viewers.AbstractTreeViewer.setContentProvider(AbstractTreeViewer.java:2317)
at org.eclipse.jface.viewers.TreeViewer.setContentProvider(TreeViewer.java:972)
at com.android.ide.eclipse.adt.internal.editors.ui.tree.UiTreeBlock.changeRootAndDescriptors(Unknown Source)
at com.android.ide.eclipse.adt.internal.editors.ui.tree.UiTreeBlock.createTreeViewer(Unknown Source)
at com.android.ide.eclipse.adt.internal.editors.ui.tree.UiTreeBlock.createMasterPart(Unknown Source)
at org.eclipse.ui.forms.MasterDetailsBlock.createContent(MasterDetailsBlock.java:161)
at org.eclipse.ui.forms.MasterDetailsBlock.createContent(MasterDetailsBlock.java:142)
at com.android.ide.eclipse.adt.internal.editors.resources.ResourcesTreePage.createFormContent(Unknown Source)
at org.eclipse.ui.forms.editor.FormPage$1.run(FormPage.java:152)
at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
at org.eclipse.ui.forms.editor.FormPage.createPartControl(FormPage.java:150)
at org.eclipse.ui.forms.editor.FormEditor.pageChange(FormEditor.java:471)
at com.android.ide.eclipse.adt.internal.editors.AndroidEditor.pageChange(Unknown Source)
at org.eclipse.ui.part.MultiPageEditorPart.setActivePage(MultiPageEditorPart.java:1067)
at org.eclipse.ui.forms.editor.FormEditor.setActivePage(FormEditor.java:603)
at org.eclipse.ui.part.MultiPageEditorPart.createPartControl(MultiPageEditorPart.java:352)
at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:670)
at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:465)
at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:313)
at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:180)
at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:270)
at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:473)
at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1254)
at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1207)
at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1606)
at org.eclipse.ui.internal.PartStack.add(PartStack.java:497)
at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:103)
at org.eclipse.ui.internal.PartStack.add(PartStack.java:483)
at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:112)
at org.eclipse.ui.internal.EditorSashContainer.addEditor(EditorSashContainer.java:63)
at org.eclipse.ui.internal.EditorAreaHelper.addToLayout(EditorAreaHelper.java:225)
at org.eclipse.ui.internal.EditorAreaHelper.addEditor(EditorAreaHelper.java:213)
at org.eclipse.ui.internal.EditorManager.createEditorTab(EditorManager.java:778)
at org.eclipse.ui.internal.EditorManager.openEditorFromDescriptor(EditorManager.java:677)
at org.eclipse.ui.internal.EditorManager.openEditor(EditorManager.java:638)
at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2860)
at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2768)
at org.eclipse.ui.internal.WorkbenchPage.access$11(WorkbenchPage.java:2760)
at org.eclipse.ui.internal.WorkbenchPage$10.run(WorkbenchPage.java:2711)
at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2707)
at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2691)
at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2682)
at org.eclipse.ui.ide.IDE.openEditor(IDE.java:651)
at org.eclipse.ui.ide.IDE.openEditor(IDE.java:610)
at org.eclipse.jdt.internal.ui.javaeditor.EditorUtility.openInEditor(EditorUtility.java:365)
at org.eclipse.jdt.internal.ui.javaeditor.EditorUtility.openInEditor(EditorUtility.java:168)
at org.eclipse.jdt.ui.actions.OpenAction.run(OpenAction.java:229)
at org.eclipse.jdt.ui.actions.OpenAction.run(OpenAction.java:20
at org.eclipse.jdt.ui.actions.SelectionDispatchAction.dispatchRun(SelectionDispatchAction.java:274)
at org.eclipse.jdt.ui.actions.SelectionDispatchAction.run(SelectionDispatchAction.java:250)
at org.eclipse.jdt.internal.ui.packageview.PackageExplorerActionGroup.handleOpen(PackageExplorerActionGroup.java:373)
at org.eclipse.jdt.internal.ui.packageview.PackageExplorerPart$4.open(PackageExplorerPart.java:526)
at org.eclipse.ui.OpenAndLinkWithEditorHelper$InternalListener.open(OpenAndLinkWithEditorHelper.java:4
at org.eclipse.jface.viewers.StructuredViewer$2.run(StructuredViewer.java:845)
at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:42)
at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:49)
at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:175)
at org.eclipse.jface.viewers.StructuredViewer.fireOpen(StructuredViewer.java:843)
at org.eclipse.jface.viewers.StructuredViewer.handleOpen(StructuredViewer.java:1131)
at org.eclipse.jface.viewers.StructuredViewer$6.handleOpen(StructuredViewer.java:1235)
at org.eclipse.jface.util.OpenStrategy.fireOpenEvent(OpenStrategy.java:264)
at org.eclipse.jface.util.OpenStrategy.access$2(OpenStrategy.java:258)
at org.eclipse.jface.util.OpenStrategy$1.handleEvent(OpenStrategy.java:298)
at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1258)
at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3552)
at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3171)
at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2629)
at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2593)
at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2427)
at org.eclipse.ui.internal.Workbench$7.run(Workbench.java:670)
at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:663)
at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:115)
at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:369)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
at java.lang.reflect.Method.invoke(Method.java:597)
at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:619)
at org.eclipse.equinox.launcher.Main.basicRun(Main.java:574)
at org.eclipse.equinox.launcher.Main.run(Main.java:1407)
[/INDENT]I have tried deleting ecplise and downloading again (i downloaded the package rather than install through package manager), also deleting and re-installing android sdk, and re-installing java packages, all to no avail.

Can anyone point me in the right direction, its pretty frustrating!

Thanks!

---

### Post by mainerror on 2010-07-25
Which Java version do you use? I mean where did you get it from?

---

### Post by dantibb on 2010-07-28
From package manager - Java 6

---

### Post by auxbuss on 2010-07-29
I'm saw exactly the same thing. I left strings.xml open, then restarted eclipse, and it went away. I'm not confident that it won't come back, but thought you might like to know that you are not alone.

---

### Post by dantibb on 2010-08-02
Hi,

Am still unable to get eclipse back running. Has anyone seen this anywhere else on the internet. I have tried clean install of java, eclipse etc, but not getting anywhere.

Here is a bit more information on the java currently installed. Sorry if info is a bit sparse, I do not have access to this machine all the time.

[HTML]
$ sudo update-alternatives --config java
[sudo] password for daniel: 
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
* 1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice
[*], or type selection number: ^C[/HTML]

---

### Post by gophergun on 2010-08-03
I'm having exactly the same issue. Admittedly, I'm on Windows at the moment, but I suspect the cause is the same.

---

### Post by sealskej on 2010-08-06
Same here, running Windows 7.

---

### Post by lilyruo on 2010-08-11
I have same issue. I also tried leave strings.xml open and restart, and it works fine after that.

---

### Post by WitchCraft on 2010-08-11
Try IDA Pro Advances for Linux.
It now comes with the android plugin preinstalled.

You then only need to configure the emulator.

---

### Post by dantibb on 2010-08-15
Hi,

Still haven't got to the bottom of what happened, but I started eclipse up with a new workspace and this appears to have resolved......

Thanks.

---

### Post by mulpuru on 2010-08-15
Navigate to 

Window -> Preferences -> XML -> XML Files -> Editor 

and uncheck "Use Inferred grammar ................"

---

### Post by syed.rakib.al.hasan on 2010-12-22
i just reinstalled the already installed java packages from the Synaptic Package manager (JDK - JRE - bin - etc).
and that seemed to have worked out perfectly.

---

### Post by peterlwl on 2011-01-15
i tell you the solution:

---

### Post by peterlwl on 2011-01-15
try this: project->clean-> clean all projects
good luck

---

