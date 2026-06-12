---
title: "need help to debug exception in Java"
date: 2006-02-24
forum: Programming Talk
---

### Post by kvorion on 2006-02-24
Hi guys,

I am new to java programming. Today I was trying to do a simple implementation of RMI. I tried to run my Server.class today, and it threw exceptions at me, which dont make any sense to me. Kindly help me find out what the problem is.

This is the exception:
```
Server exceptionjava.rmi.ServerError: Error occurred in server thread; nested exception is: 
	java.lang.UnsupportedClassVersionError: remoteInterface (Unsupported major.minor version 49.0)
```

the Server.java code is:

```


[B]import java.rmi.registry.Registry;
import java.rmi.registry.LocateRegistry;
import java.rmi.RemoteException;
import java.rmi.server.UnicastRemoteObject; 

public class Server implements remoteInterface
{
    // instance variables - replace the example below with your own
    private int x;

    /**
     * Constructor for objects of class Server
     */
    public Server()
    {
        // initialise instance variables
        x = 0;
    }

    /**
     * The implementation class Server implements the remote interface remoteInterface, providing an implementation for the remote method add. 
     *  
     * The main method of the server needs to create the remote object that provides the service. 
     * Additionally, the remote object must be exported to the Java RMI runtime so that it may receive incoming remote calls. 
     * The static method UnicastRemoteObject.exportObject exports the supplied remote object to receive incoming remote method invocations 
     * on an anonymous TCP port and returns the stub for the remote object to pass to clients.
     * 
     * @param  x   first double parameter
     * @param  y   second double parameter            
     * @return     the sum of x and y 
     */
    public double add(double x,double y) throws RemoteException
    {
            return x + y;
    }
    
    public static void main(String args[])
    {
        
    try
    {
     
        Server obj1 = new Server();
        //create a stub
        remoteInterface stub = (remoteInterface) UnicastRemoteObject.exportObject(obj1,0);
        
        //bind the remote object's stub in the registry to a name
        Registry registry = LocateRegistry.getRegistry();
        registry.bind("remoteobject",stub);
        System.err.println("server ready");
    }
    
    catch(Exception e)
    {
        System.out.println("Server exception" + e.toString());
        e.printStackTrace();
    }
    
        
    }
}[/B]
```

---

### Post by LordHunter317 on 2006-02-24
Roughly, it means the JVM on the otherside is of a different version and cannot run the code you sent.

---

### Post by kvorion on 2006-02-25
That is really funny, because I am trying out the program on my own pc....the client and server are both on my pc. So I dont understand how the JVM on the other side can complain.

---

### Post by JoshuaPDavis on 2006-02-25
It means you have code that was compiled for java 1.5 (either your own code or a jar file on your classpath) and you are trying to run it in a java 1.4 environment.

You should be able to find some help here: [http://forum.java.sun.com/thread.jspa?threadID=562771&tstart=0](http://forum.java.sun.com/thread.jspa?threadID=562771&tstart=0)

---

### Post by ZylGadis on 2006-02-25
This is actually the notorious "major.minor 49.0" error, and has absolutely nothing to do with the JVM on the other side in this case, as your error message clearly shows. There are several possible causes for the exception. Most probably you've compiled your code with a different version than the jvm you're using (1.5?). You may try to google for the exact cause related to your code.
Try reinstalling everything related to java, and then make sure that your javac and jvm know to compile/run code according to their versions.

---

### Post by kvorion on 2006-02-26
So does it mean that if I reinstall my JRE to the compatible version number as my JDK, then it wil be fine?

---

### Post by WelterPelter on 2006-02-26
It means you have to recompile your server file(s) to match your Java version.

---

### Post by kvorion on 2006-02-26
This is really funny. I tried checking up what versions of java I have installed on my comp. I installed both my JRE and JDK from automatix and they both appear to be compatible versions.

```
kv@kv:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

```

```
kv@kv:~$ javac -version
javac 1.5.0_05
javac: no source files

```

After this when I ran the same Server.class, I got a different exception.

```
java.rmi.AlreadyBoundException: remoteobject
	at sun.rmi.registry.RegistryImpl.bind(Unknown Source)
	at sun.rmi.registry.RegistryImpl_Skel.dispatch(Unknown Source)
	at sun.rmi.server.UnicastServerRef.oldDispatch(Unknown Source)
	at sun.rmi.server.UnicastServerRef.dispatch(Unknown Source)
	at sun.rmi.transport.Transport$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.rmi.transport.Transport.serviceCall(Unknown Source)
	at sun.rmi.transport.tcp.TCPTransport.handleMessages(Unknown Source)
	at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
	at sun.rmi.transport.StreamRemoteCall.exceptionReceivedFromServer(StreamRemoteCall.java:247)
	at sun.rmi.transport.StreamRemoteCall.executeCall(StreamRemoteCall.java:223)
	at sun.rmi.server.UnicastRef.invoke(UnicastRef.java:343)
	at sun.rmi.registry.RegistryImpl_Stub.bind(Unknown Source)
	at Server.main(Server.java:74)
	at __SHELL0.run(__SHELL0.java:6)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at bluej.runtime.ExecServer$3.run(ExecServer.java:858)
server ready
server ready

```

What does this exception mean? Oh and one more thing. The program worked inspite of the exception :) 
Now that is funny
Thanks for your comments guys

---

