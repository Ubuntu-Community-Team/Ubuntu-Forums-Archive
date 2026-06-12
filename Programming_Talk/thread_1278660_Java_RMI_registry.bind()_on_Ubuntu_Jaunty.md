---
title: "Java RMI registry.bind() on Ubuntu Jaunty"
date: 2009-09-29
forum: Programming Talk
---

### Post by Marcelo Ruiz on 2009-09-29
Hello All!

I am having a problem with RMI running on Linux (I use Ubuntu 9.04). Maybe some of you faced the same problem I do now and found a solution for this and can share it with me.

I get a RemoteException each time I try to bind a stub with the RMI Registry. According to the posts I read, most people have problems with client calls, but I cannot even get close to it.

I do rmic the code before executing it and as far as I know I don't need to be worried about setting up a policy file or a SecurityManager for this.

I read the item A.1 in the RMI FAQ, but I couldn't get it working. I also googled about this but all the information I read related to clients trying to connect to an existent working server (and I can not even get this working).

My static IP Address in my network is 192.168.0.101

## My /etc/hosts file content:

```

127.0.0.1 localhost
127.0.1.1 lobo-laptop

```

## My /etc/hosts.allow file content:
```

ALL: 192.168.0.111, 192.168.0.112, 192.168.0.100, 127.0.0.1, 127.0.1.1

```

## The (trimmed and simplyfied) relevant part of my code follows:

```

//DataServer Inteface extends Remote.  
DataServer instance = new DataServerImpl();  
DataServer stub;  
Registry rmiRegistry;  
   
//I read in the net that hostname should map the computer's host name,  
//but I tried this after trying without setting this property and  
//it didn't work (also tried my IP Addr with no luck).  
System.setProperty("java.rmi.server.hostname", "lobo-laptop");  
 
try {  
    stub = (DataServer) UnicastRemoteObject.exportObject(instance));  
    rmiRegistry = LocateRegistry.getRegistry();  
   
    //Here is where the exception is thrown.  
    rmiRegistry.rebind("DataServer", stub);  
} catch (RemoteException re) {  
    re.printStackTrace();  
    System.err.println();  
}

```

## stub information:
```

DataServerImpl_Stub[UnicastRef [liveRef: [endpoint:[lobo-laptop:47839](local),objID:[-31110a77:12407db5840:-7fff, -6460063892832792796]]]]

```

## registry information:
```

RegistryImpl_Stub[UnicastRef [liveRef: [endpoint:[127.0.1.1:1099](remote),objID:[0:0:0, 0]]]]

```

## Exception information:

```

1. ----REMOTE EXCEPTION----
2. java.rmi.ConnectException: Connection refused to host: 127.0.1.1; nested exception is:
3. java.net.ConnectException: Connection refused
4. at sun.rmi.transport.tcp.TCPEndpoint.newSocket(TCPEndpoint.java:601)
5. at sun.rmi.transport.tcp.TCPChannel.createConnection(TCPChannel.java:198)
6. at sun.rmi.transport.tcp.TCPChannel.newConnection(TCPChannel.java:184)
7. at sun.rmi.server.UnicastRef.newCall(UnicastRef.java:322)
8. at sun.rmi.registry.RegistryImpl_Stub.rebind(Unknown Source)
9. at suncertify.db.DataServerImpl.finishCompositeInitialization(DataServerImpl.java:327)
10. at suncertify.common.AbstractCompositeComponent.finishInitialization(AbstractCompositeComponent.java:206)
11. at suncertify.common.AbstractComponent.initialize(AbstractComponent.java:101)
12. at suncertify.db.DataServerImplTest.constructor(DataServerImplTest.java:175)
13. at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
14. at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
15. at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
16. at java.lang.reflect.Method.invoke(Method.java:597)
17. at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:44)
18. at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:15)
19. at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:41)
20. at org.junit.internal.runners.statements.InvokeMethod.evaluate(InvokeMethod.java:20)
21. at org.junit.internal.runners.statements.RunBefores.evaluate(RunBefores.java:28)
22. at org.junit.internal.runners.statements.RunAfters.evaluate(RunAfters.java:31)
23. at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:73)
24. at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:46)
25. at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:180)
26. at org.junit.runners.ParentRunner.access$000(ParentRunner.java:41)
27. at org.junit.runners.ParentRunner$1.evaluate(ParentRunner.java:173)
28. at org.junit.internal.runners.statements.RunBefores.evaluate(RunBefores.java:28)
29. at org.junit.internal.runners.statements.RunAfters.evaluate(RunAfters.java:31)
30. at org.junit.runners.ParentRunner.run(ParentRunner.java:220)
31. at junit.framework.JUnit4TestAdapter.run(JUnit4TestAdapter.java:39)
32. at org.apache.tools.ant.taskdefs.optional.junit.JUnitTestRunner.run(JUnitTestRunner.java:420)
33. at org.apache.tools.ant.taskdefs.optional.junit.JUnitTestRunner.launch(JUnitTestRunner.java:911)
34. at org.apache.tools.ant.taskdefs.optional.junit.JUnitTestRunner.main(JUnitTestRunner.java:768)
35. Caused by: java.net.ConnectException: Connection refused
36. at java.net.PlainSocketImpl.socketConnect(Native Method)
37. at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
38. at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
39. at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
40. at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
41. at java.net.Socket.connect(Socket.java:519)
42. at java.net.Socket.connect(Socket.java:469)
43. at java.net.Socket.<init>(Socket.java:366)
44. at java.net.Socket.<init>(Socket.java:180)
45. at sun.rmi.transport.proxy.RMIDirectSocketFactory.createSocket(RMIDirectSocketFactory.java:22)
46. at sun.rmi.transport.proxy.RMIMasterSocketFactory.createSocket(RMIMasterSocketFactory.java:128)
47. at sun.rmi.transport.tcp.TCPEndpoint.newSocket(TCPEndpoint.java:595)
48. ... 30 more

```


It looks weird to me that the Registry implementation was bound to 127.0.1.1, and also that its ObjID is [0:0:0, 0].
It also seems that hava is not able to create sockets, but Ubuntu's log mechanism has no information about

Any ideas on how to solve this?
Thanks!

---

### Post by annu2127 on 2010-09-16
There's a better option to do that,,....just take the eclipse plugin & make use of it.......i was having same Exception & then i installed it & was able to do things successfully....The plugins Page Link is: [http://www.genady.net/rmi/v20/downloads.html](http://www.genady.net/rmi/v20/downloads.html) enjoy!!!  ):P

---

### Post by annu2127 on 2010-09-17
The actual reason is the rmiregistry service on your machine is not running......u hav two ways to solve it......

1) start terminal, type "rmiregistry" (without quotes) & hit enter. it will look like something has hanged up....but the service has been started........run your code now & things will work (only till the terminal looks in hanging state). closing the terminal or stopping the rmiregistry by ctrl+c will stop it.

2) second way is to add following snippet in your code -
static
    {
        try
        {
            LocateRegistry.createRegistry(1099);
        }
        catch (RemoteException e)
        {
            e.printStackTrace();
        }
    }

this will start the service till your code is running (on the default port 1099).

):P

---

