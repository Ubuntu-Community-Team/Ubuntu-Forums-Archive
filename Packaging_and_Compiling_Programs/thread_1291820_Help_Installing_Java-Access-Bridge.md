---
title: "Help: Installing Java-Access-Bridge"
date: 2009-10-15
forum: Packaging and Compiling Programs
---

### Post by mari23 on 2009-10-15
Hello,
I need of Java accessibility features: I'm using ORCA screen reader, the latest JDK (java-6-sun) and I'm trying to install the Java Access Bridge for GNOME (java-access-bridge-1.24.2), but something does not work properly; After the installation, if I start a demo Java application, for example, java -jar $JDK_HOME/demo/jfc/Notepad/Notepad.jar, it shows the following message:
 
 
13-ott-2009 15.57.21 com.sun.corba.se.impl.interceptors.PIHandlerImpl peekClientRequestInfoImplStack
AVVERTENZA: "IOP00710817: (INTERNAL) Assertion failed: client request info stack is null"
org.omg.CORBA.INTERNAL: vmcid: SUN minor code: 817 completed: No
at com.sun.corba.se.impl.logging.InterceptorsSystemException.clientInfoStackNull(InterceptorsSystemException.java:701)
at com.sun.corba.se.impl.logging.InterceptorsSystemException.clientInfoStackNull(InterceptorsSystemException.java:723)
at com.sun.corba.se.impl.interceptors.PIHandlerImpl.peekClientRequestInfoImplStack(PIHandlerImpl.java:735)
at com.sun.corba.se.impl.interceptors.PIHandlerImpl.invokeClientPIEndingPoint(PIHandlerImpl.java:386)
at com.sun.corba.se.impl.encoding.BufferManagerWriteStream.overflow(BufferManagerWriteStream.java:56)
at com.sun.corba.se.impl.encoding.CDROutputStream_1_2.grow(CDROutputStream_1_2.java:211)
at com.sun.corba.se.impl.encoding.CDROutputStream_1_2.alignAndReserve(CDROutputStream_1_2.java:182)
at com.sun.corba.se.impl.encoding.CDROutputStream_1_0.internalWriteOctetArray(CDROutputStream_1_0.java:547)
at com.sun.corba.se.impl.encoding.CDROutputStream_1_0.write_octet_array(CDROutputStream_1_0.java:567)
at com.sun.corba.se.impl.encoding.CDROutputStream.write_octet_array(CDROutputStream.java:169)
at com.sun.corba.se.spi.servicecontext.UnknownServiceContext.write(UnknownServiceContext.java:43)
at com.sun.corba.se.spi.servicecontext.ServiceContexts.writeMapEntry(ServiceContexts.java:322)
at com.sun.corba.se.spi.servicecontext.ServiceContexts.writeServiceContextsInOrder(ServiceContexts.java:283)
at com.sun.corba.se.spi.servicecontext.ServiceContexts.write(ServiceContexts.java:247)
at com.sun.corba.se.impl.protocol.giopmsgheaders.ReplyMessage_1_2.write(ReplyMessage_1_2.java:175)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.createResponseHelper(CorbaMessageMediatorImpl.java:2201)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.createResponseHelper(CorbaMessageMediatorImpl.java:2164)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.createSystemExceptionResponse(CorbaMessageMediatorImpl.java:2089)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1873)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1882)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleThrowableDuringServerDispatch(CorbaMessageMediatorImpl.java:1823)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleRequest(CorbaMessageMediatorImpl.java:1548)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleInput(CorbaMessageMediatorImpl.java:922)
at com.sun.corba.se.impl.protocol.giopmsgheaders.RequestMessage_1_2.callback(RequestMessage_1_2.java:181)
at com.sun.corba.se.impl.protocol.CorbaMessageMediatorImpl.handleRequest(CorbaMessageMediatorImpl.java:694)
at com.sun.corba.se.impl.transport.SocketOrChannelConnectionImpl.dispatch(SocketOrChannelConnectionImpl.java:451)
at com.sun.corba.se.impl.transport.SocketOrChannelConnectionImpl.doWork(SocketOrChannelConnectionImpl.java:1213)
at com.sun.corba.se.impl.orbutil.threadpool.ThreadPoolImpl$WorkerThread.performWork(ThreadPoolImpl.java:471)
at com.sun.corba.se.impl.orbutil.threadpool.ThreadPoolImpl$WorkerThread.run(ThreadPoolImpl.java:500)
 
What can I do?
How can I obtain the correct installation of Java Access Bridge?
 
Thanks

---

### Post by dinxter on 2009-10-15
is this using the java access bridge for gnome from the repositories?, 
libaccess-bridge-java

or compiling from source,
[http://live.gnome.org/Java%20Access%20Bridge#head-333ffd762d5846f5b4226e2bc97089c8dcbabfec](http://live.gnome.org/Java%20Access%20Bridge#head-333ffd762d5846f5b4226e2bc97089c8dcbabfec)

---

### Post by mari23 on 2009-10-15
Hi,
I have selected the JABG version 1.24.2 from this link :
[http://download.gnome.org/sources/java-access-bridge/](http://download.gnome.org/sources/java-access-bridge/) 
 
and I have followed the instruction at this link:
[http://live.gnome.org/Java%20Access%20Bridge#head-333ffd762d5846f5b4226e2bc97089c8dcbabfec](http://live.gnome.org/Java%20Access%20Bridge#head-333ffd762d5846f5b4226e2bc97089c8dcbabfec)
 
Can you help me, please?
 
Thanks
Mari

---

### Post by anajuliaqm on 2009-10-27
Hi, I have almost the same problem. I'm using jdk 6 and java-access-bridge 1.24-2, I've installed all of them successfully according to [http://live.gnome.org/Java%20Access%20Bridge](http://live.gnome.org/Java%20Access%20Bridge), but when I try to run  java -jar $JDK_HOME/demo/jfc/Notepad/Notepad.jar e get this error message:
21/10/2009 10:22:49 com.sun.corba.se.impl.ior.IORImpl getProfile
WARNING: "IOP00511201: (INV_OBJREF) IOR must have at least one IIOP profile"
org.omg.CORBA.INV_OBJREF:   vmcid: SUN  minor code: 1201  completed: No
    at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:473)
    at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:495)
    at com.sun.corba.se.impl.ior.IORImpl.getProfile(IORImpl.java:334)
    at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:787)
    at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:761)
    at com.sun.corba.se.impl.encoding.CDRInputStream.read_Object(CDRInputStream.java:231)
    at com.sun.corba.se.impl.resolver.INSURLOperationImpl.getIORFromString(INSURLOperationImpl.java:120)
    at com.sun.corba.se.impl.resolver.INSURLOperationImpl.operate(INSURLOperationImpl.java:130)
    at com.sun.corba.se.impl.orb.ORBImpl.string_to_object(ORBImpl.java:836)
    at org.GNOME.Accessibility.AccessUtil.getRegistryObject(AccessUtil.java:143)
    at org.GNOME.Accessibility.JavaBridge.registerApplication(JavaBridge.java:1099)
    at org.GNOME.Accessibility.JavaBridge.<init>(JavaBridge.java:364)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    at java.lang.Class.newInstance0(Class.java:372)
    at java.lang.Class.newInstance(Class.java:325)
    at java.awt.Toolkit.loadAssistiveTechnologies(Toolkit.java:786)
    at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:875)
    at java.awt.Window.getToolkit(Window.java:1170)
    at java.awt.Window.init(Window.java:400)
    at java.awt.Window.<init>(Window.java:438)
    at java.awt.Frame.<init>(Frame.java:419)
    at java.awt.Frame.<init>(Frame.java:384)
    at javax.swing.JFrame.<init>(JFrame.java:180)
    at Notepad.main(Notepad.java:143)

if anyone could help me, I'd be very thankfull!

Thanks,
Ana Júlia.

---

### Post by mari23 on 2009-10-27
Hi Julia,
don't worry, your problem is different from mine and you can solve it easily!
In your /etc/ directory you have to create a orbitrc file (sudo gedit orbitrc), then edit the following two lines:
ORBIIOPIPv4=1
ORBLocalOnly=1
Then reboot and so your java applications are accessible, while my problem still persist! :-(

[http://ubuntuforums.org/showthread.php?t=1298880&highlight=java+access+bridge+problems](http://ubuntuforums.org/showthread.php?t=1298880&highlight=java+access+bridge+problems)

Give me good news on your problem

Bye
Mari

---

