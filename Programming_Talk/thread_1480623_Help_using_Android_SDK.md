---
title: "Help using Android SDK"
date: 2010-05-11
forum: Programming Talk
---

### Post by Axilus on 2010-05-11
Hey guys,

I'm currently trying to get the android sdk setup with Netbeans 6.8 . I have downloaded the sdk and have gotten it setup in Eclipse with the ADT plugin, however I much prefer Netbeans since Eclipse is extremely buggy.

I have downloaded the nbandroid plugin and have setup a AVD, and have added the android platform, but when I go to create a new android application it either:
[LIST]
[*]Doesn't recognize that I have added the android platforms
[*]Sends me to an unknown file browsing menu that I have no idea what to do with. Whenever I select or try to add something it says the file already exists, or the file doesn't exist
[*]Doesn't do anything
[/LIST]

Can anyone help me with this problem? Thanks.

Here are the screenshots:

---

### Post by Axilus on 2010-05-11
I just noticed that it also gives me this exception message:
```
java.lang.NullPointerException
	at org.netbeans.modules.android.platform.DalvikPlatform$Creator.findTarget(DalvikPlatform.java:85)
	at org.netbeans.modules.android.platform.DalvikPlatform$Creator.build(DalvikPlatform.java:105)
	at org.netbeans.modules.android.platform.PlatformConvertor.createPlatform(PlatformConvertor.java:155)
	at org.netbeans.modules.android.platform.PlatformConvertor.instanceCreate(PlatformConvertor.java:147)
	at org.netbeans.modules.android.platform.PlatformConvertor.instanceCreate(PlatformConvertor.java:49)
	at org.netbeans.modules.java.platform.DefaultJavaPlatformProvider.getInstalledPlatforms(Unknown Source)
	at org.netbeans.api.java.platform.JavaPlatformManager.getInstalledPlatforms(Unknown Source)
	at org.netbeans.api.java.platform.JavaPlatformManager.getPlatforms(Unknown Source)
	at org.netbeans.modules.android.project.ui.customizer.PlatformUiSupport$PlatformComboBoxModel.getPlatformNames(PlatformUiSupport.java:411)
	at org.netbeans.modules.android.project.ui.customizer.PlatformUiSupport$PlatformComboBoxModel.<init>(PlatformUiSupport.java:364)
	at org.netbeans.modules.android.project.ui.customizer.PlatformUiSupport.createPlatformComboBoxModel(PlatformUiSupport.java:70)
	at org.netbeans.modules.android.project.ui.wizards.PanelOptionsVisual.<init>(PanelOptionsVisual.java:102)
	at org.netbeans.modules.android.project.ui.wizards.PanelConfigureProjectVisual.<init>(PanelConfigureProjectVisual.java:70)
	at org.netbeans.modules.android.project.ui.wizards.PanelConfigureProject.getComponent(PanelConfigureProject.java:41)
	at org.netbeans.modules.android.project.ui.wizards.NewAndroidProjectWizardIterator.initialize(NewAndroidProjectWizardIterator.java:227)
	at org.openide.loaders.TemplateWizard$InstantiatingIteratorBridge.initialize(Unknown Source)
	at org.openide.loaders.TemplateWizardIterImpl.setIterator(Unknown Source)
	at org.openide.loaders.TemplateWizardIteratorWrapper.setIterator(Unknown Source)
	at org.openide.loaders.TemplateWizard.setTemplateImpl(Unknown Source)
	at org.openide.loaders.TemplateWizard.setTemplate(Unknown Source)
	at org.netbeans.modules.project.ui.TemplatesPanel.storeSettings(Unknown Source)
	at org.netbeans.modules.project.ui.TemplatesPanel.storeSettings(Unknown Source)
	at org.openide.WizardDescriptor.setValueOpen(Unknown Source)
	at org.openide.WizardDescriptor.setValue(Unknown Source)
	at org.netbeans.core.windows.services.NbPresenter$ButtonListener.actionPerformed(Unknown Source)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:2012)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2335)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:404)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:259)
	at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:253)
	at java.awt.Component.processMouseEvent(Component.java:6108)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
	at java.awt.Component.processEvent(Component.java:5873)
	at java.awt.Container.processEvent(Container.java:2105)
	at java.awt.Component.dispatchEventImpl(Component.java:4469)
	at java.awt.Container.dispatchEventImpl(Container.java:2163)
	at java.awt.Component.dispatchEvent(Component.java:4295)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4461)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4125)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4055)
	at java.awt.Container.dispatchEventImpl(Container.java:2149)
	at java.awt.Window.dispatchEventImpl(Window.java:2478)
	at java.awt.Component.dispatchEvent(Component.java:4295)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:604)
	at org.netbeans.core.TimableEventQueue.dispatchEvent(Unknown Source)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:194)
	at java.awt.Dialog$1.run(Dialog.java:1072)
	at java.awt.Dialog$3.run(Dialog.java:1126)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Dialog.show(Dialog.java:1124)
	at org.netbeans.core.windows.services.NbPresenter.superShow(Unknown Source)
	at org.netbeans.core.windows.services.NbPresenter.doShow(Unknown Source)
	at org.netbeans.core.windows.services.NbPresenter.run(Unknown Source)
	at org.netbeans.core.windows.services.NbPresenter.run(Unknown Source)
	at org.openide.util.Mutex.doEventAccess(Mutex.java:1355)
	at org.openide.util.Mutex.readAccess(Mutex.java:268)
	at org.netbeans.core.windows.services.NbPresenter.show(Unknown Source)
	at java.awt.Component.show(Component.java:1464)
	at java.awt.Component.setVisible(Component.java:1416)
	at java.awt.Window.setVisible(Window.java:842)
	at java.awt.Dialog.setVisible(Dialog.java:1011)
	at org.openide.loaders.TemplateWizard.instantiateImpl(Unknown Source)
	at org.openide.loaders.TemplateWizard.instantiate(Unknown Source)
[catch] at org.netbeans.modules.project.ui.actions.NewProject$2.run(Unknown Source)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
	at org.netbeans.core.TimableEventQueue.dispatchEvent(Unknown Source)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
```

---

