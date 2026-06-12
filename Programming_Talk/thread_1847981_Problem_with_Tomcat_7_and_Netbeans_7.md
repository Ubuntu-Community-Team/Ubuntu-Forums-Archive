---
title: "Problem with Tomcat 7 and Netbeans 7"
date: 2011-09-21
forum: Programming Talk
---

### Post by psychok7 on 2011-09-21
hi for some reason netbeans 7 isn't deploying to tomcat 7, it used to work fine, i don't know what happened. i start tomcat manually and it seems to be running fine.
i am using ubuntu 10.04

i get this error message when i try to deploy from netbeans: 

```
In-place deployment at /home/psychok7/NetBeansProjects/WebApplication1/build/web
Deployment is in progress...
deploy?config=file%3A%2Ftmp%2Fcontext2553550515035430168.xml&path=/WebApplication1
http://localhost:8080/manager/text/deploy?config=file%3A%2Ftmp%2Fcontext2553550515035430168.xml&path=/WebApplication1
/home/psychok7/NetBeansProjects/WebApplication1/nbproject/build-impl.xml:721: 
The module has not been deployed.
	at org.netbeans.modules.j2ee.deployment.devmodules.api.Deployment.deploy(Deployment.java:210)
	at org.netbeans.modules.j2ee.ant.Deploy.execute(Deploy.java:106)
	at org.apache.tools.ant.UnknownElement.execute(UnknownElement.java:291)
	at sun.reflect.GeneratedMethodAccessor69.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.tools.ant.dispatch.DispatchUtils.execute(DispatchUtils.java:106)
	at org.apache.tools.ant.Task.perform(Task.java:348)
	at org.apache.tools.ant.Target.execute(Target.java:390)
	at org.apache.tools.ant.Target.performTasks(Target.java:411)
	at org.apache.tools.ant.Project.executeSortedTargets(Project.java:1399)
	at org.apache.tools.ant.Project.executeTarget(Project.java:1368)
	at org.apache.tools.ant.helper.DefaultExecutor.executeTargets(DefaultExecutor.java:41)
	at org.apache.tools.ant.Project.executeTargets(Project.java:1251)
	at org.apache.tools.ant.module.bridge.impl.BridgeImpl.run(BridgeImpl.java:284)
	at org.apache.tools.ant.module.run.TargetExecutor.run(TargetExecutor.java:539)
	at org.netbeans.core.execution.RunClassThread.run(RunClassThread.java:153)
```

please help me

---

### Post by koonunga on 2011-09-23
I'm seeing a similar thing after recently updating Netbeans.  Before the update, no problems at all. Hmmm.

---

### Post by psychok7 on 2011-09-23
> **koonunga said:**
> I'm seeing a similar thing after recently updating Netbeans.  Before the update, no problems at all. Hmmm.

the thing is, on my other computers it works.. thou i am using 11.04 there.. dont know if that is the problem

---

