---
title: "Eclipse missing export &quot;Runnable JAR&quot;"
date: 2010-08-03
forum: Programming Talk
---

### Post by devanl on 2010-08-03
Hello,

I installed Eclipse from Synaptic and things seemed to be going well.  I was coding and debugging but then I went to export the executable.  It seems when I open the Export dialog there is no option in there to create a Runnable JAR.  Is this indicating that there is something missing in my configuration?

Thanks,
Devan


Ubuntu 8.04

---

### Post by kahumba on 2010-08-03
1) You should post a screenshot or so about what exactly is Eclipse indicating as "missing".
2) Upgrading to Java 1.6, and/or to NetBeans 6.9 and/or to Ubuntu 10.04 could help.

---

### Post by devanl on 2010-08-03
Sorry about leaving out the details.  There are no errors reported by Eclipse, the option to export to a Runnable JAR just is not there.

Here's the Eclipse config info:

*** Date: Tue Aug 03 13:23:24 MDT 2010

*** Platform Details:

*** System properties:
eclipse.buildId=M20070212-1330
eclipse.commands=-os
linux
-ws
gtk
-arch
x86
-launcher
/usr/lib/eclipse/eclipse
-name
Eclipse
-showsplash
600
-exitdata
8000f
-install
/usr/lib/eclipse
-vm
/usr/lib/jvm/java-6-sun/bin/java
eclipse.ee.install.verify=false
eclipse.product=org.eclipse.sdk.ide
eclipse.startTime=1280523531949
eclipse.vm=/usr/lib/jvm/java-6-sun/bin/java
eclipse.vmargs=-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar
/usr/lib/eclipse/startup.jar
eof=eof
file.encoding=UTF-8
file.encoding.pkg=sun.io
file.separator=/
gnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
gnu.gcj.runtime.VMClassLoader.library_control=never
java.awt.graphicsenv=sun.awt.X11GraphicsEnvironment
java.awt.printerjob=sun.print.PSPrinterJob
java.class.path=/usr/lib/eclipse/startup.jar
java.class.version=50.0
java.endorsed.dirs=/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/endorsed
java.ext.dirs=/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/ext:/usr/java/packages/lib/ext
java.home=/usr/lib/jvm/java-6-sun-1.6.0.20/jre
java.io.tmpdir=/tmp
java.library.path=/usr/lib/jni
java.runtime.name=Java(TM) SE Runtime Environment
java.runtime.version=1.6.0_20-b02
java.specification.name=Java Platform API Specification
java.specification.vendor=Sun Microsystems Inc.
java.specification.version=1.6
java.vendor=Sun Microsystems Inc.
java.vendor.url=http://java.sun.com/
java.vendor.url.bug=http://java.sun.com/cgi-bin/bugreport.cgi
java.version=1.6.0_20
java.vm.info=mixed mode, sharing
java.vm.name=Java HotSpot(TM) Client VM
java.vm.specification.name=Java Virtual Machine Specification
java.vm.specification.vendor=Sun Microsystems Inc.
java.vm.specification.version=1.0
java.vm.vendor=Sun Microsystems Inc.
java.vm.version=16.3-b01
line.separator=

org.eclipse.jdt.debug.ui.debuggerActive=false
org.eclipse.jdt.debug.ui.instanceof.IJavaStackFrame=false
org.osgi.framework.bootdelegation=*
org.osgi.framework.executionenvironment=OSGi/Minimum-1.0,OSGi/Minimum-1.1,JRE-1.1,J2SE-1.2,J2SE-1.3,J2SE-1.4,J2SE-1.5,JavaSE-1.6
org.osgi.framework.language=en
org.osgi.framework.os.name=Linux
org.osgi.framework.os.version=2.6.24-28-generic
org.osgi.framework.processor=i386
org.osgi.framework.system.packages=javax.accessibility,javax.activity,javax.crypto,javax.crypto.interfaces,javax.crypto.spec,javax.imageio,javax.imageio.event,javax.imageio.metadata,javax.imageio.plugins.bmp,javax.imageio.plugins.jpeg,javax.imageio.spi,javax.imageio.stream,javax.management,javax.management.loading,javax.management.modelmbean,javax.management.monitor,javax.management.openmbean,javax.management.relation,javax.management.remote,javax.management.remote.rmi,javax.management.timer,javax.naming,javax.naming.directory,javax.naming.event,javax.naming.ldap,javax.naming.spi,javax.net,javax.net.ssl,javax.print,javax.print.attribute,javax.print.attribute.standard,javax.print.event,javax.rmi,javax.rmi.CORBA,javax.rmi.ssl,javax.security.auth,javax.security.auth.callback,javax.security.auth.kerberos,javax.security.auth.login,javax.security.auth.spi,javax.security.auth.x500,javax.security.cert,javax.security.sasl,javax.sound.midi,javax.sound.midi.spi,javax.sound.sampled,javax.sound.sampled.spi,javax.sql,javax.sql.rowset,javax.sql.rowset.serial,javax.sql.rowset.spi,javax.swing,javax.swing.border,javax.swing.colorchooser,javax.swing.event,javax.swing.filechooser,javax.swing.plaf,javax.swing.plaf.basic,javax.swing.plaf.metal,javax.swing.plaf.multi,javax.swing.plaf.synth,javax.swing.table,javax.swing.text,javax.swing.text.html,javax.swing.text.html.parser,javax.swing.text.rtf,javax.swing.tree,javax.swing.undo,javax.transaction,javax.transaction.xa,javax.xml,javax.xml.datatype,javax.xml.namespace,javax.xml.parsers,javax.xml.transform,javax.xml.transform.dom,javax.xml.transform.sax,javax.xml.transform.stream,javax.xml.validation,javax.xml.xpath,org.ietf.jgss,org.omg.CORBA,org.omg.CORBA_2_3,org.omg.CORBA_2_3.portable,org.omg.CORBA.DynAnyPackage,org.omg.CORBA.ORBPackage,org.omg.CORBA.portable,org.omg.CORBA.TypeCodePackage,org.omg.CosNaming,org.omg.CosNaming.NamingContextExtPackage,org.omg.CosNaming.NamingContextPackage,org.omg.Dynamic,org.omg.DynamicAny,org.omg.DynamicAny.DynAnyFactoryPackage,org.omg.DynamicAny.DynAnyPackage,org.omg.IOP,org.omg.IOP.CodecFactoryPackage,org.omg.IOP.CodecPackage,org.omg.Messaging,org.omg.PortableInterceptor,org.omg.PortableInterceptor.ORBInitInfoPackage,org.omg.PortableServer,org.omg.PortableServer.CurrentPackage,org.omg.PortableServer.POAManagerPackage,org.omg.PortableServer.POAPackage,org.omg.PortableServer.portable,org.omg.PortableServer.ServantLocatorPackage,org.omg.SendingContext,org.omg.stub.java.rmi,org.w3c.dom,org.w3c.dom.bootstrap,org.w3c.dom.events,org.w3c.dom.ls,org.xml.sax,org.xml.sax.ext,org.xml.sax.helpers
org.osgi.framework.vendor=Eclipse
org.osgi.framework.version=1.3.0
org.osgi.supports.framework.extension=true
os.arch=i386
os.name=Linux
os.version=2.6.24-28-generic
osgi.arch=x86
osgi.bundles=org.eclipse.equinox.common@2:start, org.eclipse.update.configurator@3:start, org.eclipse.core.runtime@start
osgi.bundlestore=/home/devanl/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles
osgi.configuration.area=file:/home/devanl/.eclipse/org.eclipse.platform_3.2.0/configuration/
osgi.framework=file:/usr/lib/eclipse/plugins/org.eclipse.osgi_3.2.2.R32x_v20070118.jar
osgi.framework.beginningstartlevel=1
osgi.framework.shape=jar
osgi.framework.version=3.2.2.R32x_v20070118
osgi.install.area=file:/usr/lib/eclipse/
osgi.instance.area=file:/home/devanl/workspace/
osgi.instance.area.default=file:/home/devanl/workspace/
osgi.locking=none
osgi.logfile=/home/devanl/workspace/.metadata/.log
osgi.manifest.cache=/home/devanl/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/manifests
osgi.nl=en_US
osgi.os=linux
osgi.sharedConfiguration.area=file:/usr/lib/eclipse/configuration/
osgi.splashLocation=/usr/lib/eclipse/plugins/org.eclipse.platform_3.2.2.r322_v20070117b/splash.bmp
osgi.splashPath=platform:/base/plugins/org.eclipse.platform
osgi.syspath=/usr/lib/eclipse/plugins
osgi.ws=gtk
path.separator=:
sun.arch.data.model=32
sun.boot.class.path=/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/resources.jar:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/rt.jar:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/sunrsasign.jar:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/jsse.jar:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/jce.jar:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/charsets.jar:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/classes
sun.boot.library.path=/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/i386
sun.cpu.endian=little
sun.cpu.isalist=
sun.desktop=gnome
sun.io.unicode.encoding=UnicodeLittle
sun.java.launcher=SUN_STANDARD
sun.jnu.encoding=UTF-8
sun.management.compiler=HotSpot Client Compiler
sun.os.patch.level=unknown
user.country=US
user.dir=/home/devanl
user.home=/home/devanl
user.language=en
user.name=devanl
user.timezone=America/Denver

*** Features:
org.eclipse.jdt (3.2.2.r322_v20070104-R4CR0Znkvtfjv9-) "Eclipse Java Development Tools"
org.eclipse.pde (3.2.1.r321_v20060823-6vYLLdQ3Nk8DrFG) "Eclipse Plug-in Development Environment"
org.eclipse.platform (3.2.2.r322_v20070119-CXMbUe9K_WF26uA) "Eclipse Platform"
org.eclipse.rcp (3.2.2.r322_v20070104-iwP0VLKnfFC923K) "Eclipse RCP"
org.eclipse.sdk (3.2.2.r322_v20070104-OIsEN15kfLend_i) "Eclipse Project SDK"

*** Plug-in Registry:
com.ibm.icu (3.4.5.20061213) "International Components for Unicode for Java (ICU4J)" [Active]
com.ibm.icu.source (3.4.5.20061213) "International Components for Unicode for Java (ICU4J) source plug-in" [Resolved]
com.jcraft.jsch (0.1.28) "JSch" [Resolved]
org.apache.ant (1.6.5) "Apache Ant" [Resolved]
org.apache.lucene (1.4.103.v20060601) "Apache Lucene" [Resolved]
org.eclipse.ant.core (3.1.100.v20060531) "Ant Build Tool Core" [Resolved]
org.eclipse.ant.ui (3.2.1.r321_v20060828) "Ant UI" [Active]
org.eclipse.compare (3.2.1.M20060711) "Compare Support" [Active]
org.eclipse.core.boot (3.1.100.v20060603) "Core Boot" [Resolved]
org.eclipse.core.commands (3.2.0.I20060605-1400) "Commands" [Resolved]
org.eclipse.core.contenttype (3.2.0.v20060603) "Eclipse Content Mechanism" [Active]
org.eclipse.core.expressions (3.2.2.r322_v20070109a) "Expression Language" [Active]
org.eclipse.core.filebuffers (3.2.1.r321_v20060721) "File Buffers" [Active]
org.eclipse.core.filesystem (1.0.0.v20060603) "Core File Systems" [Resolved]
org.eclipse.core.filesystem.linux.x86 (1.0.0.v20060603) "Core File System for Linux" [Resolved]
org.eclipse.core.jobs (3.2.0.v20060603) "Eclipse Jobs Mechanism" [Active]
org.eclipse.core.resources (3.2.2.R32x_v20061218) "Core Resource Management" [Active]
org.eclipse.core.resources.compatibility (3.2.0.v20060603) "Core Resource Management Compatibility Fragment" [Resolved]
org.eclipse.core.runtime (3.2.0.v20060603) "Core Runtime" [Active]
org.eclipse.core.runtime.compatibility (3.1.100.v20060603) "Core Runtime Plug-in Compatibility" [Active]
org.eclipse.core.runtime.compatibility.auth (3.2.0.v20060601) "Authorization Compatibility Plug-in" [Active]
org.eclipse.core.runtime.compatibility.registry (3.2.1.R32x_v20060907) "Eclipse Registry Compatibility Fragment" [Resolved]
org.eclipse.core.variables (3.1.100.v20060605) "Core Variables" [Active]
org.eclipse.debug.core (3.2.1.v20060823) "Debug Core" [Active]
org.eclipse.debug.ui (3.2.2.r322_v20070202) "Debug UI" [Active]
org.eclipse.equinox.common (3.2.0.v20060603) "Common Eclipse Runtime" [Active]
org.eclipse.equinox.preferences (3.2.1.R32x_v20060717) "Eclipse Preferences Mechanism" [Active]
org.eclipse.equinox.registry (3.2.1.R32x_v20060814) "Extension Registry Support" [Active]
org.eclipse.help (3.2.2.R322_v20061213) "Help System Core" [Active]
org.eclipse.help.appserver (3.1.100.v20060602) "Help Application Server" [Resolved]
org.eclipse.help.base (3.2.2.R322_v20061207) "Help System Base" [Resolved]
org.eclipse.help.ui (3.2.0.v20060602) "Help System UI" [Resolved]
org.eclipse.help.webapp (3.2.2.R322_v20061114) "Help System Webapp" [Resolved]
org.eclipse.jdt (3.2.1.r321_v20060823) "Eclipse Java Development Tools" [Resolved]
org.eclipse.jdt.core (3.2.3.v_686_R32x) "Java Development Tools Core" [Active]
org.eclipse.jdt.core.manipulation (1.0.1.r321_v20060721) "Java Code Manipulation Functionality" [Active]
org.eclipse.jdt.debug (3.2.2.r322_v20070130) "JDI Debug Model" [Active]
org.eclipse.jdt.debug.ui (3.2.2.r322_v20061205) "JDI Debug UI" [Active]
org.eclipse.jdt.junit (3.2.1.r321_v20060810) "Java Development Tools JUnit support" [Active]
org.eclipse.jdt.junit.runtime (3.2.1.r321_v20060721) "Java Development Tools JUnit runtime support" [Resolved]
org.eclipse.jdt.junit4.runtime (1.0.1.r321_v20060905) "Java Development Tools JUnit4 runtime support" [Resolved]
org.eclipse.jdt.launching (3.2.2.r322_v20061114) "Java Development Tools Launching Support" [Active]
org.eclipse.jdt.ui (3.2.2.r322_v20070124) "Java Development Tools UI" [Active]
org.eclipse.jface (3.2.2.M20061214-1200) "JFace" [Resolved]
org.eclipse.jface.databinding (1.0.0.I20060605-1400) "JFace Data Binding" [Resolved]
org.eclipse.jface.text (3.2.2.r322_v20070104) "JFace Text" [Resolved]
org.eclipse.ltk.core.refactoring (3.2.1.r321_v20060823) "Refactoring Core" [Active]
org.eclipse.ltk.ui.refactoring (3.2.2.r322_v20070124) "Refactoring UI" [Active]
org.eclipse.osgi.services (3.1.100.v20060601) "OSGi Release 3 Services" [Resolved]
org.eclipse.osgi.util (3.1.100.v20060601) "OSGi R3 Utility Classes" [Resolved]
org.eclipse.pde (3.2.1.v20060810-0800) "Eclipse Plug-in Development Environment" [Resolved]
org.eclipse.pde.build (3.2.1.r321_v20060823) "Plug-in Development Environment Build Support" [Resolved]
org.eclipse.pde.core (3.2.1.v20060915-0800) "Plug-in Development Core" [Active]
org.eclipse.pde.junit.runtime (3.2.0.v20060605) "PDE JUnit Plug-in Test" [Resolved]
org.eclipse.pde.runtime (3.2.0.v20060605) "Plug-in Development Environment Runtime" [Resolved]
org.eclipse.pde.ui (3.2.1.v20060816-0800) "Plug-in Development UI" [Active]
org.eclipse.platform (3.2.2.r322_v20070117b) "Eclipse Platform" [Resolved]
org.eclipse.rcp (3.2.0.v20060605) "Eclipse RCP" [Resolved]
org.eclipse.sdk (3.2.2.r322_v20070212) "Eclipse Project SDK" [Resolved]
org.eclipse.search (3.2.1.r321_v20060726) "Search Support" [Resolved]
org.eclipse.swt (3.2.2.v3236b) "Standard Widget Toolkit" [Resolved]
org.eclipse.swt.gtk.linux.x86 (3.2.2.v3236) "Standard Widget Toolkit for GTK 2.0" [Resolved]
org.eclipse.team.core (3.2.2.M20061114) "Team Support Core" [Active]
org.eclipse.team.cvs.core (3.2.2.M20061205) "CVS Team Provider Core" [Resolved]
org.eclipse.team.cvs.ssh (3.2.1.M20061205) "CVS SSH Core" [Resolved]
org.eclipse.team.cvs.ssh2 (3.2.1.M20061205) "CVS SSH2" [Resolved]
org.eclipse.team.cvs.ui (3.2.2.M20061121) "CVS Team Provider UI" [Resolved]
org.eclipse.team.ui (3.2.1.M200608151725) "Team Support UI" [Resolved]
org.eclipse.text (3.2.0.v20060605-1400) "Text" [Resolved]
org.eclipse.tomcat (5.5.17) "Tomcat Wrapper" [Resolved]
org.eclipse.ui (3.2.1.M20061108) "Eclipse UI" [Active]
org.eclipse.ui.browser (3.2.0.v20060602) "Browser Support" [Resolved]
org.eclipse.ui.cheatsheets (3.2.1.R321_v20060720) "Cheat Sheets" [Resolved]
org.eclipse.ui.console (3.1.100.v20060605) "Console" [Active]
org.eclipse.ui.editors (3.2.1.r321_v20060721) "Default Text Editor" [Active]
org.eclipse.ui.externaltools (3.1.101.r321_v20060802) "External Tools" [Active]
org.eclipse.ui.forms (3.2.0.v20060602) "Eclipse Forms" [Active]
org.eclipse.ui.ide (3.2.1.M20060915-1030) "Eclipse IDE UI" [Active]
org.eclipse.ui.intro (3.2.2.R322_v20061214) "Welcome Framework" [Resolved]
org.eclipse.ui.intro.universal (3.2.1.R321_v20060905) "Universal Welcome" [Resolved]
org.eclipse.ui.navigator (3.2.1.M20060913-0800) "Common Navigator View" [Resolved]
org.eclipse.ui.navigator.resources (3.2.1.M20060906-0800b) "Navigator Workbench Components" [Resolved]
org.eclipse.ui.presentations.r21 (3.2.0.I20060605-1400) "R21 Presentation Plug-in" [Resolved]
org.eclipse.ui.views (3.2.1.M20060906-0800) "Views" [Active]
org.eclipse.ui.views.properties.tabbed (3.2.1.M20060830-0800) "Tabbed Properties View" [Resolved]
org.eclipse.ui.workbench (3.2.2.M20070119-0800) "Workbench" [Active]
org.eclipse.ui.workbench.compatibility (3.2.0.I20060605-1400) "Workbench Compatibility" [Resolved]
org.eclipse.ui.workbench.texteditor (3.2.0.v20060605-1400) "Text Editor Framework" [Active]
org.eclipse.update.configurator (3.2.2.R32x_v20070111) "Install/Update Configurator" [Active]
org.eclipse.update.core (3.2.3.R32x_v20070118) "Install/Update Core" [Active]
org.eclipse.update.core.linux (3.2.0.v20060605) "Install/Update Core for Linux" [Resolved]
org.eclipse.update.scheduler (3.2.2.R32x_v20061214) "Automatic Updates Scheduler" [Active]
org.eclipse.update.ui (3.2.2.R32x_v20070111) "Install/Update UI" [Resolved]
org.junit (3.8.1) "JUnit Testing Framework" [Resolved]
org.junit4 (4.1.0.1) "JUnit Testing Framework Version 4" [Resolved]
system.bundle (3.2.2.R32x_v20070118) "OSGi System Bundle" [Active]

*** User Preferences:
#Tue Aug 03 13:23:27 MDT 2010
/instance/org.eclipse.help.ui/browser.maximized=false
/instance/org.eclipse.jdt.ui/tabWidthPropagated=true
/instance/org.eclipse.jdt.debug.ui/org.eclipse.debug.ui.ExpressionView.org.eclipse.jdt.debug.ui.show_null_entries=true
/instance/org.eclipse.debug.ui/org.eclipse.debug.ui.switch_perspective_on_suspend=always
/instance/org.eclipse.jdt.ui/useQuickDiffPrefPage=true
/instance/org.eclipse.jdt.ui/org.eclipse.jdt.ui.editor.tab.width=
/instance/org.eclipse.ui.ide/platformState=1278795825006
@org.eclipse.help.ui=3.2.0.v20060602
file_export_version=3.0
/instance/org.eclipse.debug.ui/pref_state_memento.org.eclipse.debug.ui.VariableView=<?xml version\="1.0" encoding\="UTF-8"?>\n<VariablesViewMemento org.eclipse.debug.ui.SASH_DETAILS_PART\="315" org.eclipse.debug.ui.SASH_VIEW_PART\="684">\n<COLUMN_SIZES IMemento.internal.id\="org.eclipse.debug.ui.VARIALBE_COLUMN_PRESENTATION.COL_VAR_NAME" SIZE\="132"/>\n<COLUMN_SIZES IMemento.internal.id\="org.eclipse.debug.ui.VARIALBE_COLUMN_PRESENTATION.COL_VAR_VALUE" SIZE\="247"/>\n</VariablesViewMemento>
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.userLibrary.log4j=<?xml version\="1.0" encoding\="UTF-8"?>\n<userlibrary systemlibrary\="false" version\="1">\n\t<archive path\="/usr/share/java/log4j-1.2.jar"/>\n</userlibrary>\n
@org.eclipse.pde.core=3.2.1.v20060915-0800
/instance/org.eclipse.ui.workbench/ColorsAndFontsPreferencePage.expandedCategories=Torg.eclipse.ui.workbenchMisc\tTorg.eclipse.jdt.ui.presentation
/instance/org.eclipse.jdt.ui/internal.default.compliance=default
@org.eclipse.jdt.ui=3.2.2.r322_v20070124
/instance/org.eclipse.jdt.ui/org.eclipse.jdt.ui.text.templates_migrated=true
/instance/org.eclipse.core.resources/version=1
/instance/org.eclipse.pde.core/platform_path=/usr/lib/eclipse
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.codeComplete.visibilityCheck=enabled
/instance/org.eclipse.ui.workbench/org.eclipse.jface.dialogfont=1|Sans|8|0|GTK|1|;
@org.eclipse.jdt.launching=3.2.2.r322_v20061114
/instance/org.eclipse.jdt.ui/org.eclipse.jdt.ui.text.code_templates_migrated=true
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.compiler.source=1.5
/instance/org.eclipse.ui.workbench/ColorsAndFontsPreferencePage.selectedElement=Forg.eclipse.jface.textfont
/instance/org.eclipse.ui.ide/tipsAndTricks=true
/instance/org.eclipse.jdt.debug.ui/org.eclipse.debug.ui.VariableView.org.eclipse.jdt.debug.ui.show_null_entries=true
/instance/org.eclipse.ui.editors/overviewRuler_migration=migrated_3.1
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.compiler.compliance=1.5
@org.eclipse.debug.core=3.2.1.v20060823
@org.eclipse.debug.ui=3.2.2.r322_v20070202
/instance/org.eclipse.ui/showIntro=false
/configuration/org.eclipse.ui.ide/MAX_RECENT_WORKSPACES=5
@org.eclipse.jdt.core=3.2.3.v_686_R32x
/configuration/org.eclipse.ui.ide/RECENT_WORKSPACES=/home/devanl/workspace
/instance/org.eclipse.help.ui/browser.y=25
/instance/org.eclipse.help.ui/browser.x=0
/configuration/org.eclipse.ui.ide/SHOW_WORKSPACE_SELECTION_DIALOG=false
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.compiler.problem.assertIdentifier=error
/instance/org.eclipse.help.ui/browser.w=1024
/instance/org.eclipse.debug.ui/pref_state_memento.org.eclipse.debug.ui.ExpressionView=<?xml version\="1.0" encoding\="UTF-8"?>\n<VariablesViewMemento org.eclipse.debug.ui.SASH_DETAILS_PART\="243" org.eclipse.debug.ui.SASH_VIEW_PART\="756"/>
/instance/org.eclipse.jdt.ui/proposalOrderMigrated=true
/instance/org.eclipse.jdt.ui/org.eclipse.jdt.ui.text.custom_code_templates=<?xml version\="1.0" encoding\="UTF-8" standalone\="no"?><templates/>
@org.eclipse.ui.ide=3.2.1.M20060915-1030
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.builder.resourceCopyExclusionFilter=*.launch
/instance/org.eclipse.jdt.ui/fontPropagated=true
@org.eclipse.core.resources=3.2.2.R32x_v20061218
@org.eclipse.ui=3.2.1.M20061108
@org.eclipse.jdt.debug.ui=3.2.2.r322_v20061205
/instance/org.eclipse.jdt.launching/org.eclipse.jdt.launching.PREF_VM_XML=<?xml version\="1.0" encoding\="UTF-8" standalone\="no"?>\n<vmSettings defaultVM\="57,org.eclipse.jdt.internal.debug.ui.launcher.StandardVMType13,1278796384578" defaultVMConnector\="">\n<vmType id\="org.eclipse.jdt.internal.debug.ui.launcher.StandardVMType">\n<vm id\="1278796384578" name\="java-6-sun-1.6.0.20" path\="/usr/lib/jvm/java-6-sun-1.6.0.20"/>\n</vmType>\n</vmSettings>\n
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.compiler.problem.enumIdentifier=error
/configuration/org.eclipse.ui.ide/RECENT_WORKSPACES_PROTOCOL=2
/instance/org.eclipse.help.ui/browser.h=718
@org.eclipse.ui.workbench=3.2.2.M20070119-0800
/instance/org.eclipse.jdt.ui/org.eclipse.jdt.ui.text.custom_templates=<?xml version\="1.0" encoding\="UTF-8" standalone\="no"?><templates/>
@org.eclipse.ui.editors=3.2.1.r321_v20060721
/instance/org.eclipse.jdt.ui/org.eclipse.jdt.ui.javadoclocations.migrated=true
/instance/org.eclipse.jdt.ui/org.eclipse.jdt.ui.formatterprofiles.version=10
\!/=
/instance/org.eclipse.ui.workbench/org.eclipse.ui.workbench.VIEW_MESSAGE_TEXT_FONT=1|Sans|8|0|GTK|1|;
/instance/org.eclipse.debug.core/prefWatchExpressions=<?xml version\="1.0" encoding\="UTF-8" standalone\="no"?>\n<watchExpressions>\n<expression enabled\="true" text\="cell"/>\n<expression enabled\="true" text\="id"/>\n<expression enabled\="true" text\="task"/>\n</watchExpressions>\n
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.compiler.codegen.targetPlatform=1.5
/instance/org.eclipse.debug.ui/org.eclipse.debug.ui.user_view_bindings=<?xml version\="1.0" encoding\="UTF-8" standalone\="no"?>\n<viewBindings>\n<view id\="org.eclipse.debug.ui.ExpressionView">\n<perspective id\="org.eclipse.debug.ui.DebugPerspective" userAction\="opened"/>\n</view>\n<view id\="org.eclipse.ui.console.ConsoleView">\n<perspective id\="org.eclipse.jdt.ui.JavaPerspective" userAction\="opened"/>\n</view>\n</viewBindings>\n
/instance/org.eclipse.ui.workbench/org.eclipse.jface.textfont=1|Monospace|8|0|GTK|1|;
/instance/org.eclipse.jdt.ui/org.eclipse.jface.textfont=1|Monospace|8|0|GTK|1|;
/instance/org.eclipse.jdt.core/org.eclipse.jdt.core.compiler.codegen.inlineJsrBytecode=enabled
/instance/org.eclipse.jdt.ui/content_assist_lru_history=<?xml version\="1.0" encoding\="UTF-8" standalone\="no"?><history maxLHS\="100" maxRHS\="10"/>
/instance/org.eclipse.jdt.ui/useAnnotationsPrefPage=true

*** Current Install Configuration:
Install configuration:
 Last changed on Jul 10, 2010
 Location: file:/home/devanl/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.update/platform.xml

 Configured sites:
  platform:/base/
  file:/usr/local/lib/eclipse/

 Configured features:
  ID: org.eclipse.sdk, Version: 3.2.2.r322_v20070104-OIsEN15kfLend_i
  ID: org.eclipse.platform, Version: 3.2.2.r322_v20070119-CXMbUe9K_WF26uA
  ID: org.eclipse.rcp, Version: 3.2.2.r322_v20070104-iwP0VLKnfFC923K
  ID: org.eclipse.pde, Version: 3.2.1.r321_v20060823-6vYLLdQ3Nk8DrFG
  ID: org.eclipse.jdt, Version: 3.2.2.r322_v20070104-R4CR0Znkvtfjv9-

 Configured plug-ins:
  file:/usr/lib/eclipse/plugins/org.eclipse.core.runtime.compatibility.auth_3.2.0.v20060601.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.cheatsheets_3.2.1.R321_v20060720.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.platform_3.2.2.r322_v20070117b/
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt_3.2.1.r321_v20060823.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.junit4_4.1.0.1/
  file:/usr/lib/eclipse/plugins/org.eclipse.core.filesystem.linux.x86_1.0.0.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.sdk_3.2.2.r322_v20070212/
  file:/usr/lib/eclipse/plugins/org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.resources.compatibility_3.2.0.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.ide_3.2.1.M20060915-1030.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.update.core_3.2.3.R32x_v20070118.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.editors_3.2.1.r321_v20060721.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.workbench.texteditor_3.2.0.v20060605-1400.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.contenttype_3.2.0.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.views_3.2.1.M20060906-0800.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.navigator.resources_3.2.1.M20060906-0800b.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.intro_3.2.2.R322_v20061214.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.junit_3.2.1.r321_v20060810/
  file:/usr/lib/eclipse/plugins/org.eclipse.text_3.2.0.v20060605-1400.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.expressions_3.2.2.r322_v20070109a.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.commands_3.2.0.I20060605-1400.jar
  file:/usr/lib/eclipse/plugins/org.junit_3.8.1/
  file:/usr/lib/eclipse/plugins/org.eclipse.team.cvs.core_3.2.2.M20061205.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.presentations.r21_3.2.0.I20060605-1400.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.help.base_3.2.2.R322_v20061207.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.pde_3.2.1.v20060810-0800.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.search_3.2.1.r321_v20060726.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.navigator_3.2.1.M20060913-0800.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.debug.core_3.2.1.v20060823.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.team.cvs.ssh2_3.2.1.M20061205.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.pde.runtime_3.2.0.v20060605.jar
  file:/usr/lib/eclipse/plugins/org.apache.ant_1.6.5/
  file:/usr/lib/eclipse/plugins/org.eclipse.pde.core_3.2.1.v20060915-0800.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ant.core_3.1.100.v20060531.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.variables_3.1.100.v20060605.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ltk.core.refactoring_3.2.1.r321_v20060823.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.console_3.1.100.v20060605.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ltk.ui.refactoring_3.2.2.r322_v20070124.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.update.scheduler_3.2.2.R32x_v20061214.jar
  file:/usr/lib/eclipse/plugins/com.ibm.icu_3.4.5.20061213.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.compare_3.2.1.M20060711.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.launching_3.2.2.r322_v20061114.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.views.properties.tabbed_3.2.1.M20060830-0800.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.intro.universal_3.2.1.R321_v20060905/
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.junit.runtime_3.2.1.r321_v20060721/
  file:/usr/lib/eclipse/plugins/org.eclipse.team.cvs.ssh_3.2.1.M20061205.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.team.core_3.2.2.M20061114.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.help.webapp_3.2.2.R322_v20061114/
  file:/usr/lib/eclipse/plugins/org.eclipse.help.ui_3.2.0.v20060602.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.update.core.linux_3.2.0.v20060605.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.help_3.2.2.R322_v20061213.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.tomcat_5.5.17/
  file:/usr/lib/eclipse/plugins/org.eclipse.team.cvs.ui_3.2.2.M20061121.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.boot_3.1.100.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.filesystem_1.0.0.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.workbench.compatibility_3.2.0.I20060605-1400/
  file:/usr/lib/eclipse/plugins/org.eclipse.jface_3.2.2.M20061214-1200.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.equinox.preferences_3.2.1.R32x_v20060717.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.osgi.services_3.1.100.v20060601.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.runtime.compatibility.registry_3.2.1.R32x_v20060907/
  file:/usr/lib/eclipse/plugins/org.eclipse.pde.build_3.2.1.r321_v20060823/
  file:/usr/lib/eclipse/plugins/org.eclipse.ui_3.2.1.M20061108.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ant.ui_3.2.1.r321_v20060828.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.externaltools_3.1.101.r321_v20060802.jar
  file:/usr/lib/eclipse/plugins/org.apache.lucene_1.4.103.v20060601/
  file:/usr/lib/eclipse/plugins/org.eclipse.pde.junit.runtime_3.2.0.v20060605.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.swt_3.2.2.v3236b.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.debug.ui_3.2.2.r322_v20070202.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.help.appserver_3.1.100.v20060602.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jface.text_3.2.2.r322_v20070104.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.junit4.runtime_1.0.1.r321_v20060905.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.debug.ui_3.2.2.r322_v20061205.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.filebuffers_3.2.1.r321_v20060721.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.debug_3.2.2.r322_v20070130/
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.core_3.2.3.v_686_R32x.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.team.ui_3.2.1.M200608151725.jar
  file:/usr/lib/eclipse/plugins/com.ibm.icu.source_3.4.5.20061213/
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.forms_3.2.0.v20060602.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.resources_3.2.2.R32x_v20061218.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.update.ui_3.2.2.R32x_v20070111.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jface.databinding_1.0.0.I20060605-1400.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.ui.browser_3.2.0.v20060602.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.core.manipulation_1.0.1.r321_v20060721.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.core.jobs_3.2.0.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.osgi_3.2.2.R32x_v20070118.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.jdt.ui_3.2.2.r322_v20070124.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.rcp_3.2.0.v20060605.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.osgi.util_3.1.100.v20060601.jar
  file:/usr/lib/eclipse/plugins/com.jcraft.jsch_0.1.28.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.equinox.common_3.2.0.v20060603.jar
  file:/usr/lib/eclipse/plugins/org.eclipse.pde.ui_3.2.1.v20060816-0800.jar

---

### Post by myrtle1908 on 2010-08-03
Not sure why you don't have the "Runnable JAR" option listed there.  You can always simply create the manifest file yourself.  It's very simple.  Google it.

[http://www.crazysquirrel.com/computing/java/basics/runnable-jar.jspx](http://www.crazysquirrel.com/computing/java/basics/runnable-jar.jspx)

---

### Post by devanl on 2010-08-04
Thanks myrtle1908 you're totally right on how easy the manifest is.

Here's a pretty good howto I found:
[http://wiki.eclipse.org/FAQ_How_do_I_create_an_executable_JAR_file_for_a_stand-alone_SWT_program%3F](http://wiki.eclipse.org/FAQ_How_do_I_create_an_executable_JAR_file_for_a_stand-alone_SWT_program%3F)

---

