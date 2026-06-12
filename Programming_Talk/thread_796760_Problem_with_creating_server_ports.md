---
title: "Problem with creating server ports"
date: 2008-05-16
forum: Programming Talk
---

### Post by NormR2 on 2008-05-16
I have a test HTTP/FTP/SMTP server written in Java I've used on Windows that I'm trying to port to Ubuntu. I get the following errors:

> SMTPrun() ex: java.net.BindException: Permission denied
run(S) accept loop IOException: java.net.BindException: Permission denied
run() accept loop IOException: java.net.UnknownHostException: norm-desktop: norm-desktop
FTP IOE: java.net.BindException: Permission denied


The java code that's trying to create a socket:

      > acceptSocket = new ServerSocket(8080);
The FTP socket is 21 and the SMTP socket is 25.

Is there something in Ubuntu that's stopping the creation of the socket? How can I allow it?

Thanks,
Norm

---

### Post by public_void on 2008-05-16
Ports below 1024 are reserved, so you need root privileges.

---

### Post by NormR2 on 2008-05-16
What about port 8080?

Also what is:
> UnknownHostException: norm-desktop: norm-desktop

Is there a way to use ports below 1024? Can I unreserve them?
I'm not connected to the internet. There is no security issue.

---

### Post by dwhitney67 on 2008-05-16
Yes you can use ports below 1024, but as public_void pointed out, you need root-privileges.

To run a command (or in your case an application) with root-privileges:

$ sudo *someCommand*

---

### Post by NormR2 on 2008-05-17
I added "sudo' to the script and it changed how it works in one of 4 circumstances: from the commandline ONLY. It doesn't NOT work from the Applications menu, or from double clicking on the script from nautilus or from rightclicking and selecting Open in nautilus.

How do I get root privileges for a script launched from an Application menu or from a desktop Launcher?


I still get the following error:
> java.net.UnknownHostException: norm-desktop: norm-desktop
Where is 'norm-desktop' defined as an IP address or host?

---

### Post by geirha on 2008-05-17
Add gksudo to the start of the commandline of the menu-entry. gksudo acts like sudo except it brings up a graphical password prompt instead of a cli prompt.

---

### Post by dwhitney67 on 2008-05-17
> **NormR2 said:**
> 
I still get the following error:
```
java.net.UnknownHostException: norm-desktop: norm-desktop
```

Where is 'norm-desktop' defined as an IP address or host?

'norm-desktop' is (probably) defined in /etc/hostname.  If you wish for a different name for your server/desktop, then you can edit the file and change the name.  Of course, a reboot will be necessary for any change to be seen.

As for IP address and hostname association, this is specified in /etc/hosts.

Btw, are you handling the exception in your Java code?  Seems like your code needs at a minimum the try/catch(es) to handle the UnknownHostException.

P.S.  You should verify if you application 'works' by choosing a port number greater than 1024.  The port number you choose can be made to work if you have a router that can redirect port 80 traffic (or whatever port) to the port number you have chosen.

---

### Post by NormR2 on 2008-05-17
Thanks.
I was able to correct the Unknownhost problem and get the program to work from a commandline by changing the /etc/hosts file by adding a line:   127.0.0.1  norm-desktop

The java program is catching the IOException, displaying a message and skipping on.

The odd thing is I have another program that has very similiar code that is working fine. It opens a ServerSocket and communicates with Firefox just fine.

Both programs use ports in the 8000s - 8080 and 8091

I'll try gksudo in the script.

---

### Post by dwhitney67 on 2008-05-17
Unless you post the relevant sections of your code, it is kind of hard to provide worthy assistance with the problem you are encountering.

Does your server set up its socket similar to the following?
[PHP]class Server
{
  private ServerSocket serverSock = null;
  private Socket       clientSock = null;

  public Server( int port ) throws IOException
  {
    serverSock = new ServerSocket( port );
    clientSock = serverSock.accept();
    ...
  }
  ...
}[/PHP]

---

### Post by NormR2 on 2008-05-17
Thanks again.
The code has been working for years on Windows. I'm now trying to get it to work on Ubuntu. 
The last changes to /etc/hosts seems lets the program work when called from the commandline. 

However, it doesn't work from a launcher in the Applications menu. Or when DCed in nautilus.

The script is a modified version of a DOS batchfile. I've commented out DOS stuff and changed other for Ubuntu.

The output from a terminal session using gksudo follows:
> 
*************** First execute the script:

norm@norm-desktop:~/www$ ./StartHTTPServer 
>>>>>>> $PWD=/home/norm/www      args= <<<<<<<<<<<<<<<<<<<<<<<<<<<<
gksudo: invalid option -- c
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug 
...
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.

************ Now show the contents of the script****************
norm@norm-desktop:~/www$ cat StartHTTPServer
#!/bin/sh
#@REM Run HTTPServer without the ClassPath variable set
#@REM -jar with Class-Path: overrides all other Classpath= settings!
#@REM  Question: Will java use Class-Path: even if not -jar option? 
#@rem Seems to find SearchFiles from Servlets.jar mnf entry!
#set CLASSPATH=
#%DEV_DRIVE%
cd /home/norm/www
echo '>>>>>>> $PWD='$PWD '     args='$1 $2 $3 $4'<<<<<<<<<<<<<<<<<<<<<<<<<<<<'
# ??? following cmdline fails if ends with $1 $2 etc
# sudo doesnt' work from nautilus
#gksudo gives error -> invalid option -- c
gksudo java -DDEV_DRIVE=$DEV_DRIVE -DDEV_HOME=$DEV_HOME -DDOCS_HOME=$DOCS_HOME -cp /home/java/jsdk2.0/lib/jsdk.jar:HTTPServer.jar:Servlets.jar HTTPServer.HTTPServerMain $1 $2 $3 $4
norm@norm-desktop:~/www$ 


What does > gksudo: invalid option -- c mean?

---

### Post by dwhitney67 on 2008-05-17
> **NormR2 said:**
> 
What does
```
gksudo: invalid option -- c
```
mean?

It means that '-c' is an invalid option being passed to gksudo.  Perhaps you need to surround your lengthy java statement with single-quotes.

EDIT:  Should be double-quotes!!!

For example,

```
gksudo "someCmd"
```

If you are indeed attempting to open port 8080, then you should not need the gksudo.  This is only needed when opening ports below 1024!

Btw, when posting output or code, do not encapsulate with Quote tags.  Encapsulate with Code (#) tags.  The reason is that statements in Quote tags do not show up when someone attempts to quote your post with a reply.

---

### Post by NormR2 on 2008-05-17
Thanks.

Where did the -c option come from?  The -cp for the java command?
Does gksudo scan thru the full text of the command line looking for its options? Or just the first part?
Hence I should enclose the command I want executed in single-quotes.

Will the single-quotes be a problem with the $1 $2 $3 args being passed in to the script?  Will gksudo be looking at them and be confused? 

I am using several ports below 1024 for FTP and SMTP for example.

---

### Post by dwhitney67 on 2008-05-17
I just found out that double-quotes are needed, not the single-quotes.  Here's an example:

```
#!/bin/bash

FILE=/etc/hosts
CMD="gedit $FILE"

gksudo "$CMD"
```

---

### Post by NormR2 on 2008-05-17
Thanks again.
Yes, "s get me by having gksudo look at my commmandline. But they
seem to have a side effect of passing empty args to my program.
The program that scans what is in the "s doesn't seem to remove the $i variables if they are empty. Instead it leaves an empty string. So my program gets 4 empty args instead of no args. Easy programming fix, but weird and different from Windows.:(

---

### Post by geirha on 2008-05-18
The proper way is using --

```
gksudo -- java -cp ...
```
the -- says that everything behind -- belongs to the command that should be run as root, so -cp will then be parsed by java instead of gksudo.

---

