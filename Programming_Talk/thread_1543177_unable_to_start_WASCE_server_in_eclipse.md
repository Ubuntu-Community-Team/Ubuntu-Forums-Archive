---
title: "unable to start WASCE server in eclipse"
date: 2010-07-31
forum: Programming Talk
---

### Post by nbulchandani on 2010-07-31
Hello,
i installed wasce and eclipse(as well as wasce plugin for eclipse).now when in OPEN PERSPECTIVE i go to start a server i get this error
:
Starting IBM WASCE v2.1 Server at localhost
Invalid username and/or password.
Invalid login


and the console output is as:

Booting Server Kernel (in Java 1.6.0_1
Module  1/71 org.apache.geronimo.framework/gshell-framework/2.1.5/car              started in   .000s
Module  2/71 org.apache.geronimo.framework/gshell-geronimo/2.1.5/car               started in   .001s
Module  3/71 org.apache.geronimo.framework/j2ee-system/2.1.5/car                   started in   .000s
Module  4/71 org.apache.geronimo.framework/transformer-agent/2.1.5/car             started in   .000s
Module  5/71 com.ibm.wasce.configs/collector-tool-config/2.1.1.4/car               started in   .000s
Module  6/71 org.apache.geronimo.framework/jee-specs/2.1.5/car                     started in   .000s
Module  7/71 org.apache.geronimo.framework/rmi-naming/2.1.5/car                    started in   .231s
Module  8/71 org.apache.geronimo.configs/j2ee-server/2.1.5/car                     started in   .042s
Module  9/71 org.apache.geronimo.framework/j2ee-security/2.1.5/car                 started in   .226s
Module 10/71 org.apache.geronimo.framework/server-security-config/2.1.5/car        started in   .058s
Module 11/71 org.apache.geronimo.configs/transaction/2.1.5/car                     started in   .156s
Module 12/71 org.apache.geronimo.configs/jasper/2.1.5/car                          started in   .001s
Module 13/71 org.apache.geronimo.framework/xmlbeans/2.1.5/car                      started in   .000s
Module 14/71 org.apache.geronimo.configs/webservices-common/2.1.5/car              started in   .000s
Module 15/71 org.apache.geronimo.configs/tomcat6/2.1.5/car                        2010-08-01 01:47:13,491 FATAL [EmbeddedServletOptions] The scratchDir you specified: /opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/TomcatWebContainer is unusable.
 started in  1.465s
Module 16/71 com.ibm.wasce.configs/collector-tool-agent-config/2.1.1.4/car        2010-08-01 01:47:14,088 FATAL [EmbeddedServletOptions] The scratchDir you specified: /opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/collector-tool-agent is unusable.
 started in   .181s
Module 17/71 org.apache.geronimo.framework/plugin/2.1.5/car                        started in   .093s
Module 18/71 org.apache.geronimo.framework/geronimo-gbean-deployer/2.1.5/car       started in   .424s
Module 19/71 org.apache.geronimo.configs/derby/2.1.5/car                           started in   .000s
Module 20/71 org.apache.geronimo.configs/system-database/2.1.5/car                 started in  2.226s
Module 21/71 org.apache.geronimo.configs/openjpa/2.1.5/car                         started in   .004s
Module 22/71 org.apache.geronimo.configs/openejb/2.1.5/car                         started in   .479s
Module 23/71 org.apache.geronimo.configs/axis/2.1.5/car                            started in   .074s
Module 24/71 org.apache.geronimo.configs/axis2/2.1.5/car                           started in   .001s
Module 25/71 org.apache.geronimo.configs/axis2-ejb/2.1.5/car                       started in   .000s
Module 26/71 org.apache.geronimo.configs/j2ee-corba-yoko/2.1.5/car                 started in   .744s
Module 27/71 org.apache.geronimo.configs/tomcat6-no-ha/2.1.5/car                   started in   .000s
Module 28/71 org.apache.geronimo.configs/clustering/2.1.5/car                      started in   .008s
Module 29/71 org.apache.geronimo.configs/j2ee-deployer/2.1.5/car                   started in   .130s
Module 30/71 org.apache.geronimo.configs/connector-deployer/2.1.5/car              started in   .088s
Module 31/71 org.apache.geronimo.configs/tomcat6-deployer/2.1.5/car                started in   .040s
Module 32/71 org.apache.geronimo.configs/tomcat6-clustering-builder-wadi/2.1.5/car started in   .030s
Module 33/71 org.apache.geronimo.configs/activemq-broker/2.1.5/car                 started in  1.858s
Module 34/71 org.apache.geronimo.configs/activemq-ra/2.1.5/car                     started in   .324s
Module 35/71 org.apache.geronimo.configs/javamail/2.1.5/car                        started in   .022s
Module 36/71 org.apache.geronimo.configs/jasper-deployer/2.1.5/car                 started in   .013s
Module 37/71 org.apache.geronimo.configs/myfaces/2.1.5/car                         started in   .012s
Module 38/71 org.apache.geronimo.configs/myfaces-deployer/2.1.5/car                started in   .014s
Module 39/71 org.apache.geronimo.configs/openejb-deployer/2.1.5/car                started in   .057s
Module 40/71 org.apache.geronimo.configs/openejb-corba-deployer/2.1.5/car          started in   .077s
Module 41/71 org.apache.geronimo.configs/persistence-jpa10-deployer/2.1.5/car      started in   .048s
Module 42/71 org.apache.geronimo.configs/axis-deployer/2.1.5/car                   started in   .047s
Module 43/71 org.apache.geronimo.configs/jaxws-deployer/2.1.5/car                  started in   .000s
Module 44/71 org.apache.geronimo.configs/axis2-deployer/2.1.5/car                  started in   .033s
Module 45/71 org.apache.geronimo.configs/jaxws-ejb-deployer/2.1.5/car              started in   .000s
Module 46/71 org.apache.geronimo.configs/axis2-ejb-deployer/2.1.5/car              started in   .029s
Module 47/71 org.apache.geronimo.configs/client-deployer/2.1.5/car                 started in   .038s
Module 48/71 org.apache.geronimo.configs/hot-deployer/2.1.5/car                   2010-08-01 01:47:21,878 ERROR [GBeanInstanceState] Error while starting; GBean is now in the FAILED state: abstractName="org.apache.geronimo.configs/hot-deployer/2.1.5/car?ServiceModule=org.apache.geronimo.configs/hot-deployer/2.1.5/car,j2eeType=GBean,name=HotDeployer"
java.lang.IllegalStateException: Hot deploy directory /opt/IBM/WebSphere/AppServerCommunityEdition/deploy does not exist and cannot be created!
    at org.apache.geronimo.deployment.hot.DirectoryHotDeployer.doStart(DirectoryHotDeployer.java:151)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.createInstance(GBeanInstance.java:99
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.attemptFullStart(GBeanInstanceState.java:272)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.start(GBeanInstanceState.java:106)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.startRecursive(GBeanInstanceState.java:12
    at org.apache.geronimo.gbean.runtime.GBeanInstance.startRecursive(GBeanInstance.java:555)
    at org.apache.geronimo.kernel.basic.BasicKernel.startRecursiveGBean(BasicKernel.java:379)
    at org.apache.geronimo.kernel.config.ConfigurationUtil.startConfigurationGBeans(ConfigurationUtil.java:456)
    at org.apache.geronimo.kernel.config.KernelConfigurationManager.start(KernelConfigurationManager.java:18
    at org.apache.geronimo.kernel.config.SimpleConfigurationManager.startConfiguration(SimpleConfigurationManager.java:562)
    at sun.reflect.GeneratedMethodAccessor39.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.apache.geronimo.gbean.runtime.ReflectionMethodInvoker.invoke(ReflectionMethodInvoker.java:34)
    at org.apache.geronimo.gbean.runtime.GBeanOperation.invoke(GBeanOperation.java:124)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.invoke(GBeanInstance.java:832)
    at org.apache.geronimo.gbean.runtime.RawInvoker.invoke(RawInvoker.java:57)
    at org.apache.geronimo.kernel.basic.RawOperationInvoker.invoke(RawOperationInvoker.java:35)
    at org.apache.geronimo.kernel.basic.ProxyMethodInterceptor.intercept(ProxyMethodInterceptor.java:96)
    at org.apache.geronimo.gbean.GBeanLifecycle$$EnhancerByCGLIB$$4f8c2f20.startConfiguration(<generated>)
    at org.apache.geronimo.system.main.EmbeddedDaemon.doStartup(EmbeddedDaemon.java:20
    at org.apache.geronimo.system.main.EmbeddedDaemon.execute(EmbeddedDaemon.java:91)
    at org.apache.geronimo.kernel.util.MainConfigurationBootstrapper.main(MainConfigurationBootstrapper.java:45)
    at org.apache.geronimo.cli.AbstractCLI.executeMain(AbstractCLI.java:67)
    at org.apache.geronimo.cli.daemon.DaemonCLI.main(DaemonCLI.java:30)
Server startup failed

org.apache.geronimo.kernel.config.LifecycleException: start of org.apache.geronimo.configs/hot-deployer/2.1.5/car failed
    at org.apache.geronimo.kernel.config.SimpleConfigurationManager.startConfiguration(SimpleConfigurationManager.java:579)
    at sun.reflect.GeneratedMethodAccessor39.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.apache.geronimo.gbean.runtime.ReflectionMethodInvoker.invoke(ReflectionMethodInvoker.java:34)
    at org.apache.geronimo.gbean.runtime.GBeanOperation.invoke(GBeanOperation.java:124)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.invoke(GBeanInstance.java:832)
    at org.apache.geronimo.gbean.runtime.RawInvoker.invoke(RawInvoker.java:57)
    at org.apache.geronimo.kernel.basic.RawOperationInvoker.invoke(RawOperationInvoker.java:35)
    at org.apache.geronimo.kernel.basic.ProxyMethodInterceptor.intercept(ProxyMethodInterceptor.java:96)
    at org.apache.geronimo.gbean.GBeanLifecycle$$EnhancerByCGLIB$$4f8c2f20.startConfiguration(<generated>)
    at org.apache.geronimo.system.main.EmbeddedDaemon.doStartup(EmbeddedDaemon.java:20
    at org.apache.geronimo.system.main.EmbeddedDaemon.execute(EmbeddedDaemon.java:91)
    at org.apache.geronimo.kernel.util.MainConfigurationBootstrapper.main(MainConfigurationBootstrapper.java:45)
    at org.apache.geronimo.cli.AbstractCLI.executeMain(AbstractCLI.java:67)
    at org.apache.geronimo.cli.daemon.DaemonCLI.main(DaemonCLI.java:30)
Caused by: org.apache.geronimo.kernel.config.InvalidConfigException: Unknown start exception
    at org.apache.geronimo.kernel.config.ConfigurationUtil.startConfigurationGBeans(ConfigurationUtil.java:522)
    at org.apache.geronimo.kernel.config.KernelConfigurationManager.start(KernelConfigurationManager.java:18
    at org.apache.geronimo.kernel.config.SimpleConfigurationManager.startConfiguration(SimpleConfigurationManager.java:562)
    ... 15 more
Caused by: org.apache.geronimo.gbean.InvalidConfigurationException: Configuration org.apache.geronimo.configs/hot-deployer/2.1.5/car failed to start due to the following reasons:
  The service ServiceModule=org.apache.geronimo.configs/hot-deployer/2.1.5/car,j2eeType=GBean,name=HotDeployer did not start because Hot deploy directory /opt/IBM/WebSphere/AppServerCommunityEdition/deploy does not exist and cannot be created!

    at org.apache.geronimo.kernel.config.ConfigurationUtil.startConfigurationGBeans(ConfigurationUtil.java:485)
    ... 17 more
2010-08-01 01:47:27,324 ERROR [ManagerBase] IOException while saving persisted sessions: java.io.FileNotFoundException: /opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/collector-tool-agent/SESSIONS.ser (No such file or directory)
java.io.FileNotFoundException: /opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/collector-tool-agent/SESSIONS.ser (No such file or directory)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:99)
    at org.apache.catalina.session.StandardManager.doUnload(StandardManager.java:489)
    at org.apache.catalina.session.StandardManager.unload(StandardManager.java:463)
    at org.apache.catalina.session.StandardManager.stop(StandardManager.java:667)
    at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4676)
    at org.apache.geronimo.tomcat.GeronimoStandardContext.kill(GeronimoStandardContext.java:23
    at org.apache.geronimo.tomcat.TomcatContainer.removeContext(TomcatContainer.java:382)
    at org.apache.geronimo.tomcat.TomcatWebAppContext.doStop(TomcatWebAppContext.java:529)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.destroyInstance(GBeanInstance.java:1161)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.attemptFullStop(GBeanInstanceState.java:367)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:192)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.kernel.config.KernelConfigurationManager$ShutdownHook.run(KernelConfigurationManager.java:336)
    at org.apache.geronimo.kernel.basic.BasicKernel.notifyShutdownHooks(BasicKernel.java:66
    at org.apache.geronimo.kernel.basic.BasicKernel.shutdown(BasicKernel.java:645)
    at org.apache.geronimo.system.main.EmbeddedDaemon.shutdownKernel(EmbeddedDaemon.java:266)
    at org.apache.geronimo.system.main.EmbeddedDaemon.doStartup(EmbeddedDaemon.java:230)
    at org.apache.geronimo.system.main.EmbeddedDaemon.execute(EmbeddedDaemon.java:91)
    at org.apache.geronimo.kernel.util.MainConfigurationBootstrapper.main(MainConfigurationBootstrapper.java:45)
    at org.apache.geronimo.cli.AbstractCLI.executeMain(AbstractCLI.java:67)
    at org.apache.geronimo.cli.daemon.DaemonCLI.main(DaemonCLI.java:30)
2010-08-01 01:47:27,325 ERROR [ManagerBase] Exception unloading sessions to persistent storage
java.io.FileNotFoundException: /opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/collector-tool-agent/SESSIONS.ser (No such file or directory)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:99)
    at org.apache.catalina.session.StandardManager.doUnload(StandardManager.java:489)
    at org.apache.catalina.session.StandardManager.unload(StandardManager.java:463)
    at org.apache.catalina.session.StandardManager.stop(StandardManager.java:667)
    at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4676)
    at org.apache.geronimo.tomcat.GeronimoStandardContext.kill(GeronimoStandardContext.java:23
    at org.apache.geronimo.tomcat.TomcatContainer.removeContext(TomcatContainer.java:382)
    at org.apache.geronimo.tomcat.TomcatWebAppContext.doStop(TomcatWebAppContext.java:529)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.destroyInstance(GBeanInstance.java:1161)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.attemptFullStop(GBeanInstanceState.java:367)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:192)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.kernel.config.KernelConfigurationManager$ShutdownHook.run(KernelConfigurationManager.java:336)
    at org.apache.geronimo.kernel.basic.BasicKernel.notifyShutdownHooks(BasicKernel.java:66
    at org.apache.geronimo.kernel.basic.BasicKernel.shutdown(BasicKernel.java:645)
    at org.apache.geronimo.system.main.EmbeddedDaemon.shutdownKernel(EmbeddedDaemon.java:266)
    at org.apache.geronimo.system.main.EmbeddedDaemon.doStartup(EmbeddedDaemon.java:230)
    at org.apache.geronimo.system.main.EmbeddedDaemon.execute(EmbeddedDaemon.java:91)
    at org.apache.geronimo.kernel.util.MainConfigurationBootstrapper.main(MainConfigurationBootstrapper.java:45)
    at org.apache.geronimo.cli.AbstractCLI.executeMain(AbstractCLI.java:67)
    at org.apache.geronimo.cli.daemon.DaemonCLI.main(DaemonCLI.java:30)
2010-08-01 01:47:27,357 ERROR [ManagerBase] IOException while saving persisted sessions: java.io.FileNotFoundException: /opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/TomcatWebContainer/SESSIONS.ser (No such file or directory)
java.io.FileNotFoundException: /opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/TomcatWebContainer/SESSIONS.ser (No such file or directory)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:99)
    at org.apache.catalina.session.StandardManager.doUnload(StandardManager.java:489)
    at org.apache.catalina.session.StandardManager.unload(StandardManager.java:463)
    at org.apache.catalina.session.StandardManager.stop(StandardManager.java:667)
    at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4676)
    at org.apache.catalina.core.ContainerBase.stop(ContainerBase.java:109
    at org.apache.catalina.core.ContainerBase.stop(ContainerBase.java:109
    at org.apache.catalina.core.StandardEngine.stop(StandardEngine.java:44
    at org.apache.catalina.startup.Embedded.stop(Embedded.java:867)
    at org.apache.geronimo.tomcat.TomcatContainer.doStop(TomcatContainer.java:259)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.destroyInstance(GBeanInstance.java:1161)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.attemptFullStop(GBeanInstanceState.java:367)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:192)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.kernel.config.KernelConfigurationManager$ShutdownHook.run(KernelConfigurationManager.java:336)
    at org.apache.geronimo.kernel.basic.BasicKernel.notifyShutdownHooks(BasicKernel.java:668)
    at org.apache.geronimo.kernel.basic.BasicKernel.shutdown(BasicKernel.java:645)
    at org.apache.geronimo.system.main.EmbeddedDaemon.shutdownKernel(EmbeddedDaemon.java:266)
    at org.apache.geronimo.system.main.EmbeddedDaemon.doStartup(EmbeddedDaemon.java:230)
    at org.apache.geronimo.system.main.EmbeddedDaemon.execute(EmbeddedDaemon.java:91)
    at org.apache.geronimo.kernel.util.MainConfigurationBootstrapper.main(MainConfigurationBootstrapper.java:45)
    at org.apache.geronimo.cli.AbstractCLI.executeMain(AbstractCLI.java:67)
    at org.apache.geronimo.cli.daemon.DaemonCLI.main(DaemonCLI.java:30)
2010-08-01 01:47:27,367 ERROR [ManagerBase] Exception unloading sessions to persistent storage
java.io.FileNotFoundException: /opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/TomcatWebContainer/SESSIONS.ser (No such file or directory)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:99)
    at org.apache.catalina.session.StandardManager.doUnload(StandardManager.java:489)
    at org.apache.catalina.session.StandardManager.unload(StandardManager.java:463)
    at org.apache.catalina.session.StandardManager.stop(StandardManager.java:667)
    at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4676)
    at org.apache.catalina.core.ContainerBase.stop(ContainerBase.java:109
    at org.apache.catalina.core.ContainerBase.stop(ContainerBase.java:109
    at org.apache.catalina.core.StandardEngine.stop(StandardEngine.java:44
    at org.apache.catalina.startup.Embedded.stop(Embedded.java:867)
    at org.apache.geronimo.tomcat.TomcatContainer.doStop(TomcatContainer.java:259)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.destroyInstance(GBeanInstance.java:1161)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.attemptFullStop(GBeanInstanceState.java:367)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:192)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.gbean.runtime.GBeanInstanceState.stop(GBeanInstanceState.java:184)
    at org.apache.geronimo.gbean.runtime.GBeanInstance.stop(GBeanInstance.java:563)
    at org.apache.geronimo.kernel.basic.BasicKernel.stopGBean(BasicKernel.java:423)
    at org.apache.geronimo.kernel.config.KernelConfigurationManager$ShutdownHook.run(KernelConfigurationManager.java:336)
    at org.apache.geronimo.kernel.basic.BasicKernel.notifyShutdownHooks(BasicKernel.java:668)
    at org.apache.geronimo.kernel.basic.BasicKernel.shutdown(BasicKernel.java:645)
    at org.apache.geronimo.system.main.EmbeddedDaemon.shutdownKernel(EmbeddedDaemon.java:266)
    at org.apache.geronimo.system.main.EmbeddedDaemon.doStartup(EmbeddedDaemon.java:230)
    at org.apache.geronimo.system.main.EmbeddedDaemon.execute(EmbeddedDaemon.java:91)
    at org.apache.geronimo.kernel.util.MainConfigurationBootstrapper.main(MainConfigurationBootstrapper.java:45)
    at org.apache.geronimo.cli.AbstractCLI.executeMain(AbstractCLI.java:67)
    at org.apache.geronimo.cli.daemon.DaemonCLI.main(DaemonCLI.java:30)


Please tell  me where i am wrong.is it anything related to profilers?i havent configured any yet.if yes,how to do that?
Thanks

---

### Post by Some Penguin on 2010-07-31
You should probably resolve the FileNotFoundExceptions.  The odds seem quite high that you need to set either an environmental variable or a JVM system property to tell it where you installed Websphere, because it's looking for

/opt/IBM/WebSphere/AppServerCommunityEdition/var/catalina/work/TomcatWebContainer/SESSIONS.ser 

and not finding it.

---

### Post by nbulchandani on 2010-07-31
Hello,
I resolved those errors by changing permissions of subfiles and folders.but still some problem is there.
The error i am getting is as
:
Starting IBM WASCE v2.1 Server at localhost
Invalid username and/or password.
Invalid login
Failed to stop server
Stopping of module failed.  See log for details.




The console output is as:

Booting Server Kernel (in Java 1.6.0_18)...
Module  1/71 org.apache.geronimo.framework/gshell-framework/2.1.5/car              started in   .000s
Module  2/71 org.apache.geronimo.framework/gshell-geronimo/2.1.5/car               started in   .000s
Module  3/71 org.apache.geronimo.framework/j2ee-system/2.1.5/car                   started in   .000s
Module  4/71 org.apache.geronimo.framework/transformer-agent/2.1.5/car             started in   .000s
Module  5/71 com.ibm.wasce.configs/collector-tool-config/2.1.1.4/car               started in   .000s
Module  6/71 org.apache.geronimo.framework/jee-specs/2.1.5/car                     started in   .001s
Module  7/71 org.apache.geronimo.framework/rmi-naming/2.1.5/car                    started in   .226s
Module  8/71 org.apache.geronimo.configs/j2ee-server/2.1.5/car                     started in   .056s
Module  9/71 org.apache.geronimo.framework/j2ee-security/2.1.5/car                 started in   .199s
Module 10/71 org.apache.geronimo.framework/server-security-config/2.1.5/car        started in   .052s
Module 11/71 org.apache.geronimo.configs/transaction/2.1.5/car                     started in   .164s
Module 12/71 org.apache.geronimo.configs/jasper/2.1.5/car                          started in   .002s
Module 13/71 org.apache.geronimo.framework/xmlbeans/2.1.5/car                      started in   .000s
Module 14/71 org.apache.geronimo.configs/webservices-common/2.1.5/car              started in   .001s
Module 15/71 org.apache.geronimo.configs/tomcat6/2.1.5/car                         started in  1.449s
Module 16/71 com.ibm.wasce.configs/collector-tool-agent-config/2.1.1.4/car         started in   .163s
Module 17/71 org.apache.geronimo.framework/plugin/2.1.5/car                        started in   .102s
Module 18/71 org.apache.geronimo.framework/geronimo-gbean-deployer/2.1.5/car       started in   .414s
Module 19/71 org.apache.geronimo.configs/derby/2.1.5/car                           started in   .000s
Module 20/71 org.apache.geronimo.configs/system-database/2.1.5/car                 started in  1.698s
Module 21/71 org.apache.geronimo.configs/openjpa/2.1.5/car                         started in   .005s
Module 22/71 org.apache.geronimo.configs/openejb/2.1.5/car                         started in   .565s
Module 23/71 org.apache.geronimo.configs/axis/2.1.5/car                            started in   .104s
Module 24/71 org.apache.geronimo.configs/axis2/2.1.5/car                           started in   .000s
Module 25/71 org.apache.geronimo.configs/axis2-ejb/2.1.5/car                       started in   .000s
Module 26/71 org.apache.geronimo.configs/j2ee-corba-yoko/2.1.5/car                 started in  1.032s
Module 27/71 org.apache.geronimo.configs/tomcat6-no-ha/2.1.5/car                   started in   .000s
Module 28/71 org.apache.geronimo.configs/clustering/2.1.5/car                      started in   .008s
Module 29/71 org.apache.geronimo.configs/j2ee-deployer/2.1.5/car                   started in   .144s
Module 30/71 org.apache.geronimo.configs/connector-deployer/2.1.5/car              started in   .104s
Module 31/71 org.apache.geronimo.configs/tomcat6-deployer/2.1.5/car                started in   .047s
Module 32/71 org.apache.geronimo.configs/tomcat6-clustering-builder-wadi/2.1.5/car started in   .029s
Module 33/71 org.apache.geronimo.configs/activemq-broker/2.1.5/car                 started in  1.986s
Module 34/71 org.apache.geronimo.configs/activemq-ra/2.1.5/car                     started in   .381s
Module 35/71 org.apache.geronimo.configs/javamail/2.1.5/car                        started in   .027s
Module 36/71 org.apache.geronimo.configs/jasper-deployer/2.1.5/car                 started in   .013s
Module 37/71 org.apache.geronimo.configs/myfaces/2.1.5/car                         started in   .014s
Module 38/71 org.apache.geronimo.configs/myfaces-deployer/2.1.5/car                started in   .017s
Module 39/71 org.apache.geronimo.configs/openejb-deployer/2.1.5/car                started in   .063s
Module 40/71 org.apache.geronimo.configs/openejb-corba-deployer/2.1.5/car          started in   .088s
Module 41/71 org.apache.geronimo.configs/persistence-jpa10-deployer/2.1.5/car      started in   .054s
Module 42/71 org.apache.geronimo.configs/axis-deployer/2.1.5/car                   started in   .052s
Module 43/71 org.apache.geronimo.configs/jaxws-deployer/2.1.5/car                  started in   .000s
Module 44/71 org.apache.geronimo.configs/axis2-deployer/2.1.5/car                  started in   .033s
Module 45/71 org.apache.geronimo.configs/jaxws-ejb-deployer/2.1.5/car              started in   .000s
Module 46/71 org.apache.geronimo.configs/axis2-ejb-deployer/2.1.5/car              started in   .042s
Module 47/71 org.apache.geronimo.configs/client-deployer/2.1.5/car                 started in   .042s
Module 48/71 org.apache.geronimo.configs/hot-deployer/2.1.5/car                    started in   .296s
Module 49/71 com.ibm.wasce.configs/welcome-tomcat/2.1.1.4/car                      started in   .053s
Module 50/71 org.apache.geronimo.configs/spring/2.1.5/car                          started in   .000s
Module 51/71 org.apache.geronimo.plugins/pluto-support/2.1.5/car                   started in   .010s
Module 52/71 org.apache.geronimo.plugins/console-tomcat/2.1.5/car                  started in  2.422s
Module 53/71 org.apache.geronimo.plugins/plugin-console-tomcat/2.1.5/car           started in   .282s
Module 54/71 org.apache.geronimo.configs/dojo-legacy-tomcat/2.1.5/car              started in   .030s
Module 55/71 org.apache.geronimo.plugins/debugviews-console-tomcat/2.1.5/car       started in   .171s
Module 56/71 org.apache.geronimo.plugins/sysdb-console-tomcat/2.1.5/car            started in   .400s
Module 57/71 org.apache.geronimo.plugins/activemq-console-tomcat/2.1.5/car         started in   .280s
Module 58/71 org.apache.geronimo.plugins/plancreator-console-tomcat/2.1.5/car      started in   .157s
Module 59/71 org.apache.geronimo.configs/remote-deploy-tomcat/2.1.5/car            started in   .057s
Module 60/71 org.apache.geronimo.configs/uddi-tomcat/2.1.5/car                     started in   .358s
Module 61/71 org.apache.geronimo.configs/ca-helper-tomcat/2.1.5/car                started in   .074s
Module 62/71 org.apache.geronimo.configs/sharedlib/2.1.5/car                       started in   .006s
Module 63/71 org.apache.geronimo.configs/mejb/2.1.5/car                            started in   .187s
Module 64/71 org.apache.geronimo.configs/dojo-tomcat/2.1.5/car                     started in   .031s
Module 65/71 org.apache.geronimo.plugins/agent-ds/2.1.5/car                        started in   .538s
Module 66/71 org.apache.geronimo.plugins.monitoring/agent-car-jmx/2.1.5/car        started in   .020s
Module 67/71 org.apache.geronimo.plugins/mconsole-ds/2.1.5/car                     started in   .071s
Module 68/71 org.apache.geronimo.plugins/mconsole-tomcat/2.1.5/car                 started in   .805s
Module 69/71 com.ibm.wasce.configs/db2v82/2.1.1.4/car                              started in   .000s
Module 70/71 com.ibm.wasce.configs/db2v91/2.1.1.4/car                              started in   .000s
Module 71/71 com.ibm.wasce.configs/db2v95/2.1.1.4/car                              started in   .000s
Startup completed in 17.827s seconds
  Listening on Ports:
    1050 0.0.0.0 CORBA Naming Service
    1099 0.0.0.0 RMI Naming
    1527 0.0.0.0 Derby Connector
    2001 0.0.0.0 OpenEJB ORB Adapter
    4201 0.0.0.0 OpenEJB Daemon
    6882 0.0.0.0 OpenEJB ORB Adapter
    8009 0.0.0.0 Tomcat Connector AJP AJP
    8080 0.0.0.0 Tomcat Connector HTTP BIO HTTP
    8443 0.0.0.0 Tomcat Connector HTTPS BIO HTTPS
    9999 0.0.0.0 JMX Remoting Connector
   61613 0.0.0.0 ActiveMQ Transport Connector
   61616 0.0.0.0 ActiveMQ Transport Connector

  Started Application Modules:
    EAR: org.apache.geronimo.configs/uddi-tomcat/2.1.5/car
    EAR: org.apache.geronimo.plugins/console-tomcat/2.1.5/car
    JAR: org.apache.geronimo.configs/mejb/2.1.5/car
    RAR: org.apache.geronimo.configs/activemq-ra/2.1.5/car
    RAR: org.apache.geronimo.configs/system-database/2.1.5/car
    RAR: org.apache.geronimo.plugins/agent-ds/2.1.5/car
    RAR: org.apache.geronimo.plugins/mconsole-ds/2.1.5/car
    WAR: com.ibm.wasce.configs/collector-tool-agent-config/2.1.1.4/car
    WAR: com.ibm.wasce.configs/welcome-tomcat/2.1.1.4/car
    WAR: org.apache.geronimo.configs/ca-helper-tomcat/2.1.5/car
    WAR: org.apache.geronimo.configs/dojo-legacy-tomcat/2.1.5/car
    WAR: org.apache.geronimo.configs/dojo-tomcat/2.1.5/car
    WAR: org.apache.geronimo.configs/remote-deploy-tomcat/2.1.5/car
    WAR: org.apache.geronimo.plugins/activemq-console-tomcat/2.1.5/car
    WAR: org.apache.geronimo.plugins/debugviews-console-tomcat/2.1.5/car
    WAR: org.apache.geronimo.plugins/mconsole-tomcat/2.1.5/car
    WAR: org.apache.geronimo.plugins/plancreator-console-tomcat/2.1.5/car
    WAR: org.apache.geronimo.plugins/plugin-console-tomcat/2.1.5/car
    WAR: org.apache.geronimo.plugins/sysdb-console-tomcat/2.1.5/car

  Web Applications:
    /
    /CAHelper
    /activemq
    /collector-tool-agent
    /console
    /console-base
    /debug-views
    /dojo
    /dojo/0.4
    /juddi
    /monitoring
    /plan-creator
    /plugin
    /remote-deploy
    /system-database

Server started.


Now what is the problem with username and password?
Thanks

---

### Post by nbulchandani on 2010-08-01
Anyone has any idea on the topic.

---

### Post by akanksha on 2011-04-04
I am getting a similar problem as mentioned by u earlier.. what all file permissions did u change..??

---

