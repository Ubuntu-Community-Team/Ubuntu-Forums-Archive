---
title: "Glassfish JSP not compiling."
date: 2009-04-15
forum: Programming Talk
---

### Post by Can+~ on 2009-04-15
I'm a total newb to Java, but I read the documentation and I could get the idea of the language quickly, since I already used C#, C++, Python, etc.

The thing is, I'm working on a homework that demands a webpage made in jsp in netbeans.

So I download netbeans from de repository, glassfish V2, sun-java6-jre/bin/doc, download all the necessary plugins from netbeans (JSF, JavaEE, Visual JSF, Glassfish V2).

I set the server with default values, create a new webpage, I add a single "Hello world!" label on it, and run it.

The server sets up fine, but when firefox opens it shoots a 500 Internal Error.

```
----Log File Rotated---
Apr 15, 2009 7:03:59 PM com.sun.enterprise.admin.servermgmt.launch.ASLauncher buildCommand
INFO: 
/usr/lib/jvm/java-6-sun/bin/java
-Dcom.sun.aas.instanceRoot=/home/canxp/Programming/glassfish
-Dcom.sun.aas.ClassPathPrefix=
-Dcom.sun.aas.ClassPathSuffix=
-Dcom.sun.aas.ServerClassPath=
-Dcom.sun.aas.classloader.appserverChainJars.ee=
-Dcom.sun.aas.classloader.appserverChainJars=admin-cli.jar,admin-cli-ee.jar,j2ee-svc.jar
-Dcom.sun.aas.classloader.excludesList=admin-cli.jar,appserv-upgrade.jar,sun-appserv-ant.jar
-Dcom.sun.aas.classloader.optionalOverrideableChain.ee=
-Dcom.sun.aas.classloader.optionalOverrideableChain=webservices-rt.jar,webservices-tools.jar
-Dcom.sun.aas.classloader.serverClassPath.ee=/lib/hadbjdbc4.jar,/usr/share/glassfishv2/lib/SUNWjdmk/5.1/lib/jdmkrt.jar,/lib/dbstate.jar,/lib/hadbm.jar,/lib/hadbmgt.jar,/lib/mfwk_instrum_tk.jar
-Dcom.sun.aas.classloader.serverClassPath=/usr/share/glassfishv2/lib/install/applications/jmsra/imqjmsra.jar,/usr/share/glassfishv2/imq/lib/jaxm-api.jar,/usr/share/glassfishv2/imq/lib/fscontext.jar,/usr/share/glassfishv2/imq/lib/imqbroker.jar,/usr/share/glassfishv2/imq/lib/imqjmx.jar,/usr/share/ant/lib/ant.jar,/usr/share/ant/lib/ant-launcher.jar,/usr/share/glassfishv2/lib/SUNWjdmk/5.1/lib/jdmkrt.jar
-Dcom.sun.aas.classloader.sharedChainJars.ee=appserv-se.jar,appserv-ee.jar,jesmf-plugin.jar,/lib/dbstate.jar,/lib/hadbjdbc4.jar,jgroups-all.jar,/lib/mfwk_instrum_tk.jar
-Dcom.sun.aas.classloader.sharedChainJars=javaee.jar,/usr/lib/jvm/java-6-sun/lib/tools.jar,install/applications/jmsra/imqjmsra.jar,com-sun-commons-launcher.jar,com-sun-commons-logging.jar,/usr/share/glassfishv2/imq/lib/jaxm-api.jar,/usr/share/glassfishv2/imq/lib/fscontext.jar,/usr/share/glassfishv2/imq/lib/imqbroker.jar,/usr/share/glassfishv2/imq/lib/imqjmx.jar,/usr/share/glassfishv2/imq/lib/imqxm.jar,webservices-rt.jar,webservices-tools.jar,mail.jar,appserv-jstl.jar,jmxremote_optional.jar,/usr/share/glassfishv2/lib/SUNWjdmk/5.1/lib/jdmkrt.jar,activation.jar,appserv-rt.jar,appserv-admin.jar,appserv-cmp.jar,/usr/share/glassfishv2/updatecenter/lib/updatecenter.jar,/usr/share/glassfishv2/jbi/lib/jbi.jar,/usr/share/glassfishv2/imq/lib/imqjmx.jar,/usr/share/ant/lib/ant.jar,/usr/share/ant/lib/ant-launcher.jar,dbschema.jar
-Dcom.sun.aas.configName=server-config
-Dcom.sun.aas.configRoot=/usr/share/glassfishv2/config
-Dcom.sun.aas.defaultLogFile=/home/canxp/Programming/glassfish/logs/server.log
-Dcom.sun.aas.domainName=glassfish
-Dcom.sun.aas.installRoot=/usr/share/glassfishv2
-Dcom.sun.aas.instanceName=server
-Dcom.sun.aas.processLauncher=SE
-Dcom.sun.aas.promptForIdentity=true
-Dcom.sun.appserv.pluggable.features=com.sun.enterprise.ee.server.pluggable.EEPluggableFeatureImpl
-Dcom.sun.enterprise.config.config_environment_factory_class=com.sun.enterprise.config.serverbeans.AppserverConfigEnvironmentFactory
-Dcom.sun.enterprise.overrideablejavaxpackages=javax.help,javax.portlet
-Dcom.sun.enterprise.taglibs=appserv-jstl.jar,jsf-impl.jar
-Dcom.sun.enterprise.taglisteners=jsf-impl.jar
-Dcom.sun.updatecenter.home=/usr/share/glassfishv2/updatecenter
-Ddomain.name=glassfish
-Djava.endorsed.dirs=/usr/share/glassfishv2/lib/endorsed
-Djava.ext.dirs=/usr/lib/jvm/java-6-sun/lib/ext:/usr/lib/jvm/java-6-sun/jre/lib/ext:/home/canxp/Programming/glassfish/lib/ext:/usr/share/javadb/lib:/usr/share/glassfishv2/lib/jdbcdrivers
-Djava.library.path=:/usr/share/glassfishv2/lib:/usr/share/glassfishv2/lib
-Djava.security.auth.login.config=/home/canxp/Programming/glassfish/config/login.conf
-Djava.security.policy=/home/canxp/Programming/glassfish/config/server.policy
-Djava.util.logging.manager=com.sun.enterprise.server.logging.ServerLogManager
-Djavax.management.builder.initial=com.sun.enterprise.ee.admin.AppServerMBeanServerBuilder
-Djavax.net.ssl.keyStore=/home/canxp/Programming/glassfish/config/keystore.jks
-Djavax.net.ssl.trustStore=/home/canxp/Programming/glassfish/config/cacerts.jks
-Djdbc.drivers=org.apache.derby.jdbc.ClientDriver
-Djmx.invoke.getters=true
-Dsun.rmi.dgc.client.gcInterval=3600000
-Dsun.rmi.dgc.server.gcInterval=3600000
-client
-XX:+UnlockDiagnosticVMOptions
-XX:MaxPermSize=192m
-Xmx512m
-XX:NewRatio=2
-XX:+LogVMOutput
-XX:LogFile=/home/canxp/Programming/glassfish/logs/jvm.log
-cp
/usr/share/glassfishv2/lib/jhall.jar:/usr/share/glassfishv2/lib/appserv-launch.jar
com.sun.enterprise.server.PELaunch
start
Starting Sun Java System Application Server 9.1_01 (build local) ...
MBeanServer started: com.sun.enterprise.interceptor.DynamicInterceptor
CORE5076: Using [Java HotSpot(TM) Client VM, Version 1.6.0_10] from [Sun Microsystems Inc.]
SEC1002: Security Manager is OFF.
Using MQ RA for Broker lifecycle control
/home/canxp/Programming/glassfish/config/.__com_sun_appserv_pid
ADM0001:SunoneInterceptor is now enabled
SEC1143: Loading policy provider com.sun.enterprise.security.provider.PolicyWrapper.
WEB0114: SSO is disabled in virtual server [server]
WEB0114: SSO is disabled in virtual server [__asadmin]
EJBSCLookup:: sc.getEjbContainerAvailabilityEnabledFromConfig() ==> false
JTS5014: Recoverable JTS instance, serverId = [3748]
ADM1079: Initialization of AMX MBeans started
ADM1504: Here is the JMXServiceURL for the Standard JMXConnectorServer: [service:jmx:rmi:///jndi/rmi://asgard:8734/jmxrmi].  This is where the remote administrative clients should connect using the standard JMX connectors
ADM1506: Status of Standard JMX Connector: Active = [true]
JMS Service Connection URL is :mq://asgard:7724/
MQJMSRA_RA1101: SJSMQ JMS Resource Adapter starting...
MQJMSRA_EB1101: EMBEDDED broker started with code =0
MQJMSRA_RA1101: SJSMQ JMSRA Started:DIRECT
[AutoDeploy] Selecting file /usr/share/glassfishv2/lib/install/applications/__ejb_container_timer_app.ear for autodeployment.
Dynamic deployment is ON
deployed with moduleid = __ejb_container_timer_app
[AutoDeploy] Successfully autodeployed : /usr/share/glassfishv2/lib/install/applications/__ejb_container_timer_app.ear.
[AutoDeploy] Selecting file /usr/share/glassfishv2/lib/install/applications/__JWSappclients.ear for autodeployment.
Dynamic deployment is ON
deployed with moduleid = __JWSappclients
[AutoDeploy] Successfully autodeployed : /usr/share/glassfishv2/lib/install/applications/__JWSappclients.ear.
[AutoDeploy] Selecting file /usr/share/glassfishv2/lib/install/applications/MEjbApp.ear for autodeployment.
Dynamic deployment is ON
deployed with moduleid = MEjbApp
[AutoDeploy] Successfully autodeployed : /usr/share/glassfishv2/lib/install/applications/MEjbApp.ear.
EJB5090: Exception in creating EJB container [java.lang.ClassNotFoundException: com.sun.ejb.containers.TimerBean_2100919770_ConcreteImpl]
appId=__ejb_container_timer_app moduleName=ejb_jar ejbName=TimerBean
LDR5004: UnExpected error occured while creating ejb container
java.lang.ClassNotFoundException: com.sun.ejb.containers.TimerBean_2100919770_ConcreteImpl
        at com.sun.enterprise.loader.EJBClassLoader.findClassData(EJBClassLoader.java:737)
        at com.sun.enterprise.loader.EJBClassLoader.findClass(EJBClassLoader.java:627)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at com.sun.ejb.containers.BaseContainer.<init>(BaseContainer.java:423)
        at com.sun.ejb.containers.EntityContainer.<init>(EntityContainer.java:246)
        at com.sun.ejb.containers.TimerBeanContainer.<init>(TimerBeanContainer.java:72)
        at com.sun.ejb.containers.ContainerFactoryImpl.createContainer(ContainerFactoryImpl.java:293)
        at com.sun.enterprise.server.AbstractLoader.loadEjbs(AbstractLoader.java:536)
        at com.sun.enterprise.server.ApplicationLoader.doLoad(ApplicationLoader.java:188)
        at com.sun.enterprise.server.TomcatApplicationLoader.doLoad(TomcatApplicationLoader.java:126)
        at com.sun.enterprise.server.AbstractLoader.load(AbstractLoader.java:244)
        at com.sun.enterprise.server.AbstractManager.loadOneSystemApp(AbstractManager.java:393)
        at com.sun.enterprise.server.AbstractManager$SystemAppStarter.doRun(AbstractManager.java:642)
        at com.sun.appserv.management.util.misc.RunnableBase.runSync(RunnableBase.java:304)
        at com.sun.appserv.management.util.misc.RunnableBase._submit(RunnableBase.java:176)
        at com.sun.appserv.management.util.misc.RunnableBase.submit(RunnableBase.java:192)
        at com.sun.enterprise.server.AbstractManager.loadSystem(AbstractManager.java:320)
        at com.sun.enterprise.server.SystemAppLifecycle.loadSystemApps(SystemAppLifecycle.java:162)
        at com.sun.enterprise.server.SystemAppLifecycle.onStartup(SystemAppLifecycle.java:108)
        at com.sun.enterprise.server.ApplicationServer.onStartup(ApplicationServer.java:442)
        at com.sun.enterprise.server.ondemand.OnDemandServer.onStartup(OnDemandServer.java:120)
        at com.sun.enterprise.server.PEMain.run(PEMain.java:411)
        at com.sun.enterprise.server.PEMain.main(PEMain.java:338)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.sun.enterprise.server.PELaunch.main(PELaunch.java:412)
CORE5021: Application NOT loaded: [__ejb_container_timer_app]
POARemoteRefFactory checking if SFSBVersionPolicy need to be added
EJBSCLookup:: sc.getEjbContainerAvailabilityEnabledFromConfig() ==> false
POARemoteRefFactory addSFSBVersionPolicy? false
POARemoteRefFactory checking if SFSBVersionPolicy need to be added
EJBSCLookup:: sc.getEjbContainerAvailabilityEnabledFromConfig() ==> false
POARemoteRefFactory addSFSBVersionPolicy? false
LDR5010: All ejb(s) of [MEjbApp] loaded successfully!
JBIFW0010: JBI framework ready to accept requests.
WEB0302: Starting Sun-Java-System/Application-Server.
No Principals mapped to Role [noaccess].
WEB0712: Starting Sun-Java-System/Application-Server HTTP/1.1 on 8128
WEB0712: Starting Sun-Java-System/Application-Server HTTP/1.1 on 8229
WEB0712: Starting Sun-Java-System/Application-Server HTTP/1.1 on 4896
SMGT0007: Self Management Rules service is enabled
EJBLifeCycle: Automatic  timer migration component not enabled  for DAS instance
Application server startup complete.
deployed with moduleid = webexperimento1
Initializing Sun's JavaServer Faces implementation (1.2_04-b20-p03) for context '/webexperimento1'
java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
ApplicationDispatcher[/webexperimento1] PWC1231: Servlet.service() for servlet jsp threw exception
java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
WebModule[/webexperimento1]org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
javax.faces.FacesException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:413)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
Caused by: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:601)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        ... 43 more
Caused by: java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        ... 59 more
executePhase(RENDER_RESPONSE 6,com.sun.faces.context.FacesContextImpl@821522) threw exception
com.sun.rave.web.ui.appbase.ApplicationException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.cleanup(ViewHandlerImpl.java:594)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:325)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
Caused by: javax.faces.FacesException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:413)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        ... 40 more
Caused by: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:601)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        ... 43 more
Caused by: java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        ... 59 more
phase(RENDER_RESPONSE 6,com.sun.faces.context.FacesContextImpl@821522) threw exception: com.sun.rave.web.ui.appbase.ApplicationException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.cleanup(ViewHandlerImpl.java:594)
com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.afterPhase(ViewHandlerImpl.java:470)
com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:280)
com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
StandardWrapperValve[Faces Servlet]: PWC1406: Servlet.service() for servlet Faces Servlet threw exception
com.sun.rave.web.ui.appbase.ApplicationException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.cleanup(ViewHandlerImpl.java:594)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:325)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
Caused by: javax.faces.FacesException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:413)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        ... 40 more
Caused by: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:601)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        ... 43 more
Caused by: java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        ... 59 more
java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
ApplicationDispatcher[/webexperimento1] PWC1231: Servlet.service() for servlet jsp threw exception
java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
WebModule[/webexperimento1]org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
javax.faces.FacesException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:413)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
Caused by: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:601)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        ... 43 more
Caused by: java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        ... 59 more
executePhase(RENDER_RESPONSE 6,com.sun.faces.context.FacesContextImpl@5ebd39) threw exception
com.sun.rave.web.ui.appbase.ApplicationException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.cleanup(ViewHandlerImpl.java:594)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:325)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
Caused by: javax.faces.FacesException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:413)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        ... 40 more
Caused by: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:601)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        ... 43 more
Caused by: java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        ... 59 more
phase(RENDER_RESPONSE 6,com.sun.faces.context.FacesContextImpl@5ebd39) threw exception: com.sun.rave.web.ui.appbase.ApplicationException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.cleanup(ViewHandlerImpl.java:594)
com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.afterPhase(ViewHandlerImpl.java:470)
com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:280)
com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
StandardWrapperValve[Faces Servlet]: PWC1406: Servlet.service() for servlet Faces Servlet threw exception
com.sun.rave.web.ui.appbase.ApplicationException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.cleanup(ViewHandlerImpl.java:594)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:325)
        at com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)
        at com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)
        at com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)
        at com.sun.faces.extensions.avatar.lifecycle.PartialTraversalLifecycle.render(PartialTraversalLifecycle.java:106)
        at javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at com.sun.webui.jsf.util.UploadFilter.doFilter(UploadFilter.java:267)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:288)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:271)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:202)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:94)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:206)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:150)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:632)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:577)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:571)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:1080)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:272)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.invokeAdapter(DefaultProcessorTask.java:637)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.doProcess(DefaultProcessorTask.java:568)
        at com.sun.enterprise.web.connector.grizzly.DefaultProcessorTask.process(DefaultProcessorTask.java:813)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.executeProcessorTask(DefaultReadTask.java:341)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:263)
        at com.sun.enterprise.web.connector.grizzly.DefaultReadTask.doTask(DefaultReadTask.java:214)
        at com.sun.enterprise.web.portunif.PortUnificationPipeline$PUTask.doTask(PortUnificationPipeline.java:380)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:265)
        at com.sun.enterprise.web.connector.grizzly.ssl.SSLWorkerThread.run(SSLWorkerThread.java:106)
Caused by: javax.faces.FacesException: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:413)
        at com.sun.faces.application.ViewHandlerImpl.executePageToBuildView(ViewHandlerImpl.java:442)
        at com.sun.faces.application.ViewHandlerImpl.renderView(ViewHandlerImpl.java:115)
        at com.sun.rave.web.ui.appbase.faces.ViewHandlerImpl.renderView(ViewHandlerImpl.java:320)
        ... 40 more
Caused by: org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:601)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:344)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:470)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:364)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:831)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:411)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:317)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:390)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:230)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:198)
        at org.apache.catalina.core.ApplicationDispatcher.doInvoke(ApplicationDispatcher.java:853)
        at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:703)
        at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:542)
        at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:474)
        at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:366)
        at com.sun.faces.context.ExternalContextImpl.dispatch(ExternalContextImpl.java:408)
        ... 43 more
Caused by: java.lang.NullPointerException
        at org.apache.jasper.compiler.Jsr199JavaCompiler.compile(Jsr199JavaCompiler.java:172)
        at org.apache.jasper.compiler.Compiler.generateClass(Compiler.java:342)
        at org.apache.jasper.compiler.Compiler.compile(Compiler.java:411)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:592)
        ... 59 more
```

Which leaves me... wondering, what the **** went wrong?

---

### Post by Can+~ on 2009-04-15
Oh man, after hours of useless googling; I ended up checking every sun-java6-* installed, and I realized that the JDK was missing.

Installed the JDK, restarted netbeans and everything is working now.

[FONT="Courier New"][COLOR="RoyalBlue"]class[/COLOR] Face [COLOR="RoyalBlue"]implements[/COLOR] Palm[/FONT]

---

### Post by txcrackers on 2009-04-16
> **Can+~ said:**
> 
[FONT="Courier New"][COLOR="RoyalBlue"]class[/COLOR] Face [COLOR="RoyalBlue"]implements[/COLOR] Palm[/FONT]

You're still not getting the OO-ness here...

[php]
class Face {
   void smackForehead(Palm palm) {
      // implement action here
    }
}
[/php]

---

### Post by Can+~ on 2009-04-16
> **txcrackers said:**
> You're still not getting the OO-ness here...

[php]
class Face {
   void smackForehead(Palm palm) {
      // implement action here
    }
}
[/php]

I understand the "OO-ness" of Java; the text wasn't supposed to be valid in any sense, just word play.

But! my problems are far from over; I started the ["helloweb" tutorial]("http://www.netbeans.org/kb/55/vwp-helloweb.html") in netbeans, and so far so good.

I added all the requested forms and saved them, then proceeded to add the actual behaviour, and seems that it's unable to recognize any of the forms created:

**For example, this form has the proper name:**
[IMG]http://img.photobucket.com/albums/v517/CanXp/Screenshots/screenshot2.png[/IMG]

**Although, after saving and compiling multiple times, it does not recognize it:**
[IMG]http://img.photobucket.com/albums/v517/CanXp/Screenshots/screenshot3.png[/IMG]

**The application fails to compile with the following error:**
```
symbol  : variable nameField
location: class hostilityweb.Page1
                String name = (String)nameField.getText();
                                      ^
1 error
```

---

