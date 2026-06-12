---
title: "Eclipse problem when running java apps"
date: 2006-09-26
forum: Programming Talk
---

### Post by Ramses de Norre on 2006-09-26
Hi,

I always get this error in Eclipse when I try to run a java program, it's a very simple program (I'm just learning java) and I choose "Run as > Java Application".
Does anyone know how to get rid of this?
> Activation.main: warning: sun.rmi.activation.execPolicy system
property unspecified and no ExecPermissions/ExecOptionPermissions
granted; subsequent activation attempts may fail due to unsuccessful
ExecPermission/ExecOptionPermission permission checks.  For
documentation on how to configure rmid security, refer to:

[http://java.sun.com/j2se/1.4/docs/tooldocs/solaris/rmid.html](http://java.sun.com/j2se/1.4/docs/tooldocs/solaris/rmid.html)
[http://java.sun.com/j2se/1.4/docs/tooldocs/win32/rmid.html](http://java.sun.com/j2se/1.4/docs/tooldocs/win32/rmid.html)


The program works fine when I call it from terminal with the java command, this is the program in case you need to know that:
```
public class PrintSum {

	/**
	 * @auth
	 */
	public static void main(String[] args) {
		int i = 1;
		int sum = 0;
		while (i <= 10)
		{
			sum += i;
			i++;
			System.out.println("Value of sum is " + sum + ".");

		}
	}
}
```
All answers are appreciated!

---

### Post by sgtBiafra on 2006-09-26
Check to make sure that you created this as part of a vanilla "Java Project". Eclipse has a few template projects, so perhaps you selected the wrong one?

You shouldn't get a RMI error when attempting to run such a simple example locally.

---

### Post by Ramses de Norre on 2006-09-26
Hmm I started with file > new > project and chose "Java application".
I now get a larger error:
> Activation.main: warning: sun.rmi.activation.execPolicy system
property unspecified and no ExecPermissions/ExecOptionPermissions
granted; subsequent activation attempts may fail due to unsuccessful
ExecPermission/ExecOptionPermission permission checks.  For
documentation on how to configure rmid security, refer to:

[http://java.sun.com/j2se/1.4/docs/tooldocs/solaris/rmid.html](http://java.sun.com/j2se/1.4/docs/tooldocs/solaris/rmid.html)
[http://java.sun.com/j2se/1.4/docs/tooldocs/win32/rmid.html](http://java.sun.com/j2se/1.4/docs/tooldocs/win32/rmid.html)

Activation.main: an exception occurred: Port already in use: 1098; nested exception is: 
	java.net.BindException: Address already in use
java.rmi.server.ExportException: Port already in use: 1098; nested exception is: 
	java.net.BindException: Address already in use
	at sun.rmi.transport.tcp.TCPTransport.listen(TCPTransport.java:243)
	at sun.rmi.transport.tcp.TCPTransport.exportObject(TCPTransport.java:178)
	at sun.rmi.transport.tcp.TCPEndpoint.exportObject(TCPEndpoint.java:382)
	at sun.rmi.transport.LiveRef.exportObject(LiveRef.java:116)
	at sun.rmi.server.UnicastServerRef.exportObject(UnicastServerRef.java:180)
	at sun.rmi.registry.RegistryImpl.setup(RegistryImpl.java:92)
	at sun.rmi.registry.RegistryImpl.<init>(RegistryImpl.java:68)
	at java.rmi.registry.LocateRegistry.createRegistry(LocateRegistry.java:222)
	at sun.rmi.server.Activation.main(Activation.java:1892)
Caused by: java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:359)
	at java.net.ServerSocket.bind(ServerSocket.java:319)
	at java.net.ServerSocket.<init>(ServerSocket.java:185)
	at java.net.ServerSocket.<init>(ServerSocket.java:97)
	at sun.rmi.transport.proxy.RMIDirectSocketFactory.createServerSocket(RMIDirectSocketFactory.java:27)
	at sun.rmi.transport.proxy.RMIMasterSocketFactory.createServerSocket(RMIMasterSocketFactory.java:333)
	at sun.rmi.transport.tcp.TCPEndpoint.newServerSocket(TCPEndpoint.java:622)
	at sun.rmi.transport.tcp.TCPTransport.listen(TCPTransport.java:231)
	... 8 more
Both with the program I showed and a very simple HelloWorld program..
The helloworld used to work but it does the same now..

The error seems to complain about a network port being used? And in netstat the port is indeed listening to *:* but no process is mentioned..

I hope I can get this sorted out so I can use foss to learn programming.

---

### Post by Ramses de Norre on 2006-09-27
Anyone?

---

### Post by Blacktalon on 2006-09-27
it looks like your running java 1.4, so when you create a package makesure your setting your java to 1.4, and not 1.5 or 5.0.  This might be the problem.

Good luck
~BT

---

### Post by Ramses de Norre on 2006-09-28
I'm running sun java 5.0, and my compiler is set to that too I think.
In the preferences, compiler section I've set compiler compliance level to 5.0 (it was set to 1.4) and I get the same error.
I've also made a new JRE in "installed jre's" and picked "/usr/lib/jvm/java-1.5.0-sun-1.5.0.06" as jre home dir.
Is there anything else I need to change?

---

### Post by ruhar on 2006-09-28
What is your JAVA_HOME environment variable set to?  To see what Eclipse is using, go to Help->About Eclipse SDK->Configuration Details and look for the eclipse.vm property.  That will tell you what Eclipse is using as a jdk.  Do you have any other jdks installed on your box (e.g., gjc?)

---

### Post by hod139 on 2006-09-30
Not 100% sure what is wrong, but maybe something here: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378) will help

---

### Post by Ramses de Norre on 2006-10-01
Sorry for not replying, but I solved the issue.
I figured out that if I right clicked the class entry and choose "run as java app" it works, I only get the error when I do this on the project name.
I don't know whether this is normal but now I just click on the classes and it works.
Thanks for your suggestions ;)

---

