---
title: "Lotus Symphony"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by hikujk123 on 2008-05-04
I am trying to install LotusSymphony on ubuntu 8.04.

I downloaded the .bin file typed this in the terminal:
```

chmod +x IBM_Lotus_Symphony_linux.bin
./IBM_Lotus_Symphony_linux.bin

```/

First, it wouldn't open the graphical installer, so I told it to run via -console.  Then, everything seemed to be going fine, but then I got a error log as a file.  Note that this was not an output from the terminal.  I typed it as a code so it wouldn't take up the whole page.
```

(May 4, 2008 6:49:44 AM), RCPCore-Install, com.ibm.pvc.install.wizard.CheckJVMAction, msg1, Set RCP_JVM_LOCATION = $N($N($P(absoluteInstallLocation)/framework,/)/rcp/eclipse/plugins/com.ibm.rcp.j2se.linux.x86_1.5.0.SR6-200801251400, /)
(May 4, 2008 6:49:44 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set manifestSize = 639877
(May 4, 2008 6:49:44 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set manifestDownloadSize = 213294
(May 4, 2008 6:49:44 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_RESTART_PERSONALITY = 
(May 4, 2008 6:49:44 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_INSTALL_FEATURES = RCP Platform Extension
IBM Productivity Tools
(May 4, 2008 6:49:44 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_STATIC_PROVISIONING = true
(May 4, 2008 6:49:44 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = 0
(May 4, 2008 6:49:44 AM), RCPCore-Install, com.installshield.product.service.legacyregistry.LegacyPureJavaRegistryServiceImpl, dbg.registry, reading VPD from /home/ubuntuuser/vpd.properties
(May 4, 2008 6:49:44 AM), RCPCore-Install, com.installshield.product.service.legacyregistry.LegacyPureJavaRegistryServiceImpl, dbg.registry, reading VPD from /home/ubuntuuser/vpd.properties
(May 4, 2008 6:50:15 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-16-generic;arch=x86;parent=
(May 4, 2008 6:50:15 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Linux Platform;name=Linux;version=.*;arch=.*;parent=
(May 4, 2008 6:50:15 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-16-generic;arch=x86;parent=
(May 4, 2008 6:50:15 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Linux Platform;name=Linux;version=.*;arch=.*;parent=
(May 4, 2008 6:50:15 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-16-generic;arch=x86;parent=
(May 4, 2008 6:50:15 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Windows (All);name=Windows .*;version=.*;arch=.*;parent=
(May 4, 2008 6:50:15 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-16-generic;arch=x86;parent=
(May 4, 2008 6:50:15 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Windows (All);name=Windows .*;version=.*;arch=.*;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-16-generic;arch=x86;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Linux Platform;name=Linux;version=.*;arch=.*;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-16-generic;arch=x86;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Linux Platform;name=Linux;version=.*;arch=.*;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-16-generic;arch=x86;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Windows (All);name=Windows .*;version=.*;arch=.*;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-16-generic;arch=x86;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Windows (All);name=Windows .*;version=.*;arch=.*;parent=
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.ibm.pvc.install.wizard.GenerateInstallIDAction, msg1, Set RCP_WORKSPACE_LOCATION = ${env.HOME}/Lotus/XPD
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set manifestSize = 639877
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set manifestDownloadSize = 213294
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_RESTART_PERSONALITY = 
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_INSTALL_FEATURES = RCP Platform Extension
IBM Productivity Tools
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_STATIC_PROVISIONING = true
(May 4, 2008 6:51:30 AM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = 0
(May 4, 2008 6:52:25 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Cleanup Install Files Action (cleanupInstallFiles): free=7321272 total=15086080
(May 4, 2008 6:52:25 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Cleanup Install Files Action (cleanupInstallFiles)
(May 4, 2008 6:52:25 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Cleanup Install Files Action (cleanupInstallFiles): free=7255456 total=15086080
(May 4, 2008 6:52:25 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean9): free=7187872 total=15086080
(May 4, 2008 6:52:25 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Uninstall Product Action (bean9)
(May 4, 2008 6:52:25 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean9): free=7118240 total=15086080
(May 4, 2008 6:52:25 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Files (linuxJCLDesktopFiles): free=7118240 total=15086080
(May 4, 2008 6:52:25 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Files (linuxJCLDesktopFiles)
(May 4, 2008 6:52:27 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Files (linuxJCLDesktopFiles): free=5647704 total=15086080
(May 4, 2008 6:52:27 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean3): free=5568056 total=15086080
(May 4, 2008 6:52:27 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Uninstall Product Action (bean3)
(May 4, 2008 6:52:27 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean3): free=5509744 total=15086080
(May 4, 2008 6:52:27 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Files (commonCoreFiles): free=5499816 total=15086080
(May 4, 2008 6:52:27 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Files (commonCoreFiles)
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Files (commonCoreFiles): free=4883160 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createEclipseLinkFile): free=4883160 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Write Java Properties Action (createEclipseLinkFile)
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createEclipseLinkFile): free=4753392 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createRCPLinkFile): free=4710592 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Write Java Properties Action (createRCPLinkFile)
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createRCPLinkFile): free=4586152 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createSharedLinkFile): free=4538080 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Write Java Properties Action (createSharedLinkFile)
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createSharedLinkFile): free=4422904 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Create Directory (deployDir): free=4365520 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Create Directory (deployDir)
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Create Directory (deployDir): free=4307968 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Generate Install Info Action (bean4): free=4241240 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Generate Install Info Action (bean4)
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Generate Install Info Action (bean4): free=3627448 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (writeRCPLauncherProps): free=3612592 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Write Java Properties Action (writeRCPLauncherProps)
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (writeRCPLauncherProps): free=3289024 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean5): free=3238064 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Uninstall Product Action (bean5)
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean5): free=3172432 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Files (group1RCPFiles): free=3125544 total=15069696
(May 4, 2008 6:52:30 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Files (group1RCPFiles)
(May 4, 2008 6:52:32 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Files (group1RCPFiles): free=6988872 total=15069696
(May 4, 2008 6:52:32 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean6): free=6904904 total=15069696
(May 4, 2008 6:52:32 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Uninstall Product Action (bean6)
(May 4, 2008 6:52:32 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean6): free=6904904 total=15069696
(May 4, 2008 6:52:32 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Files (group2CoreFiles): free=6818888 total=15069696
(May 4, 2008 6:52:32 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Files (group2CoreFiles)
(May 4, 2008 6:52:34 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Files (group2CoreFiles): free=512160 total=15069696
(May 4, 2008 6:52:34 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean7): free=445536 total=15069696
(May 4, 2008 6:52:34 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Uninstall Product Action (bean7)
(May 4, 2008 6:52:34 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean7): free=346136 total=15069696
(May 4, 2008 6:52:34 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Files (group3CoreFiles): free=343976 total=15069696
(May 4, 2008 6:52:34 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Files (group3CoreFiles)
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Files (group3CoreFiles): free=1334288 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean8): free=1225616 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Uninstall Product Action (bean8)
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean8): free=1171576 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Files (linuxCoreFiles): free=1117536 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Files (linuxCoreFiles)
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Files (linuxCoreFiles): free=5690016 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Process Keystore Action (processKeystore): free=5628152 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Process Keystore Action (processKeystore)
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.ibm.pvc.install.product.ProcessKeystoreAction, dbg, copying /tmp/symphony.tmp177911209901745/deploy/.keystore.JCEKS.IBM_J9_VM.install to /home/ubuntuuser/lotus/Symphony/framework/rcp/deploy
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Process Keystore Action (processKeystore): free=5478024 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform): free=5429400 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform)
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.ibm.pvc.install.product.CopyFileToFromPluginAction, msg1, RETURNING  /home/ubuntuuser/lotus/Symphony/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.2.200801251400
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform): free=5209784 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Merge INI Action (mergePluginCustomization): free=5170984 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Merge INI Action (mergePluginCustomization)
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Merge INI Action (mergePluginCustomization): free=4998096 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Delete File (deletePlatformPluginCustomization): free=4940752 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Delete File (deletePlatformPluginCustomization)
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Delete File (deletePlatformPluginCustomization): free=4886096 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (updateVMInRCPLauncherProps): free=4826632 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Write Java Properties Action (updateVMInRCPLauncherProps)
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (updateVMInRCPLauncherProps): free=4653432 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Process Install Manifest Action (processInstallManifest): free=4615992 total=14316544
(May 4, 2008 6:52:36 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Process Install Manifest Action (processInstallManifest)
(May 4, 2008 6:52:37 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory after installing Process Install Manifest Action (processInstallManifest): free=3908920 total=14316544
(May 4, 2008 6:52:37 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Provisioning Action (provisioning): free=3855872 total=14316544
(May 4, 2008 6:52:37 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Provisioning Action (provisioning)
(May 4, 2008 6:52:37 AM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, msg1, Getting rcp.data from /home/ubuntuuser/lotus/Symphony/framework/rcp/rcplauncher.properties
(May 4, 2008 6:52:59 AM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, err, CWPIM0013E: No .provisioning_rc file found after provisioning process returned.
(May 4, 2008 6:52:59 AM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = -99
(May 4, 2008 6:52:59 AM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, msg1, Set RCP_PROVISIONING_STATUS = Provisioning process failed.  Process failed to launch or was terminated before status could be determined.
(May 4, 2008 6:52:59 AM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, err, could not delete file /home/ubuntuuser/lotus/Symphony/framework/framework/rcp/deploy/uninstall.hotfix.xml
(May 4, 2008 6:52:59 AM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, err, An error occurred and product installation failed.  Look at the log file /home/ubuntuuser/lotus/Symphony/framework/rcp_install.log for details.
(May 4, 2008 6:52:59 AM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, err, ProductException: (error code = 601; message="err"; additional data = [Provisioning process failed.  Process failed to launch or was terminated before status could be determined.])
STACK_TRACE: 25
ProductException: (error code = 601; message="err"; additional data = [Provisioning process failed.  Process failed to launch or was terminated before status could be determined.])
	at com.ibm.pvc.install.ProductUtil.failInstall(ProductUtil.java:43)
	at com.ibm.pvc.install.ProductUtil.failAction(ProductUtil.java:51)
	at com.ibm.pvc.install.product.ProvisioningAction.executeProvisioning(ProvisioningAction.java:346)
	at com.ibm.pvc.install.product.ProvisioningAction.install(ProvisioningAction.java:141)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProductAction(PureJavaProductServiceImpl.java:2969)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.getResultForProductAction(PureJavaProductServiceImpl.java:8048)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitComponent(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitInstallableComponents(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitProductBeans(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(PureJavaProductServiceImpl.java:7199)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProduct(PureJavaProductServiceImpl.java:2637)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:79)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:618)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.installProduct(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installAssembly(PureJavaProductServiceImpl.java:5523)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.access$900(PureJavaProductServiceImpl.java:119)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(PureJavaProductServiceImpl.java:5378)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:810)

(May 4, 2008 6:52:59 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, uninstalling Write Java Properties Action (updateVMInRCPLauncherProps)
(May 4, 2008 6:52:59 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, uninstalling Process Install Manifest Action (processInstallManifest)
(May 4, 2008 6:52:59 AM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, uninstalling Provisioning Action (provisioning)

```

I am pretty new to linux, so I need you to be specific when telling me commands.

---

### Post by atomkarinca on 2008-05-04
If it's still in Beta, I had written a howto months ago, you can try that. It's [here]("http://blog.filibos.com/2007/11/18/taking-my-chances-on-ibm-lotus-symphony/").

---

### Post by hikujk123 on 2008-05-04
How exactly do you do this:
"make the file executable."

Also, I got the installer to run.  It messed up, while installing.  I'd like to try your howto to make sure that I did it correctly.

---

### Post by atomkarinca on 2008-05-04
> **hikujk123 said:**
> How exactly do you do this:
"make the file executable."

Right-click the file, go to Permissions tab and select "Allow file as program"

or

open up a terminal Applications > Accessories > Terminal and type:

```
chmod +x filename.bin
```

---

### Post by hikujk123 on 2008-05-04
I can't run in the terminal.  I double click it and don't get that option.

---

### Post by atomkarinca on 2008-05-04
What's the error you're getting when you try to run it in the terminal?

---

### Post by hikujk123 on 2008-05-04
Couldn't display "/home/ubuntuuser/Desktop/IBM_Lotus_Symphony_linux.bin".
There is no application installed for this file type

---

### Post by atomkarinca on 2008-05-04
Alright, try this: open up a terminal (Applications > Accessories > Terminal) and type one line at a time:

```
cd /home/ubuntuuser/Desktop/
chmod +x IBM_Lotus_Symphony_linux.bin
sudo ./IBM_Lotus_Symphony_linux.bin
```

---

### Post by hikujk123 on 2008-05-05
I went through the install and was able to open the Lotus writer, but when I restarted my computer and clicked on the Lotus Symphony Shortcut under Application > Office, nothing happens.  The shortcut is dead.  What went wrong?

---

### Post by atomkarinca on 2008-05-05
You should run it in a terminal to see what the problem is. First right-click the menu and select edit menu, then find that shortcut and from properties note down the command it's calling. Paste that command to a terminal and give us the output.

---

### Post by hikujk123 on 2008-05-05
```

"/home/ubuntuuser/lotus/framework/shared/eclipse/plugins/com.ibm.productivity.tools.standalone.addin_3.0.1.20080229-1700/apps/IBM Lotus Symphony" %U

```
The command is above.  When I type in the terminal I get no output. :( :(

---

### Post by uantuzri on 2008-06-09
I have a similar issue here. Have a look here, it might help: [http://www.futuredesktop.com/Lotus%20Symphony%20on%20Linux.html]("http://www.futuredesktop.com/Lotus%20Symphony%20on%20Linux.html")

---

### Post by munzli on 2008-06-17
the solution to your problem is probably to change the file permissions.

since you installed as root, only root is allowed to run it.


in the terminal try
```
sudo "/home/ubuntuuser/lotus/framework/shared/eclipse/plugins/com.ibm.productivity.tools.standalone.addin_3.0.1.20080229-1700/apps/IBM Lotus Symphony"
```

if that works then go to /home/ubuntuuser/ in a terminal and change the permissions to your user
```
sudo chown -R youruser:youruser lotus
```

make sure that if you have a folder in your home directory called ".lotus" to do the same
hope that was your problem

[edit]
just noticed that uantuzri has the same solution on his site, seems that it's enough to change ~/.lotus permissions
[/edit]

---

