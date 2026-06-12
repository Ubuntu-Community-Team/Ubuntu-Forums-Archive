---
title: "Java program download file from server"
date: 2012-07-05
forum: Programming Talk
---

### Post by Drenriza on 2012-07-05
Hey guys.

I'am currently working on a Java project where i need to download a file.
I have a remote Debian Lenny server where i have stored a file under the username "cristian".

Anyone that has some good coding examples on how to accomplish this under Linux?
I would prefer it not to be a solution with the use of FTP.

Thanks on advance.
Kind regards.

---

### Post by dwhitney67 on 2012-07-05
Why Java?  Just use SSH (err, scp).

---

### Post by codemaniac on 2012-07-05
From a java program you can call scp in order to transfer your files .
There are java classes avalable in order to handle ssh connections .
Have a look at the below link .

[http://stackoverflow.com/questions/199624/scp-via-java](http://stackoverflow.com/questions/199624/scp-via-java)

---

### Post by Drenriza on 2012-07-06
> **codemaniac said:**
> From a java program you can call scp in order to transfer your files .
There are java classes avalable in order to handle ssh connections .
Have a look at the below link .

[http://stackoverflow.com/questions/199624/scp-via-java](http://stackoverflow.com/questions/199624/scp-via-java)

Thanks for the link.

I looked at [https://github.com/shikhar/sshj/blob/master/src/main/java/examples/SCPDownload.java](https://github.com/shikhar/sshj/blob/master/src/main/java/examples/SCPDownload.java)

but i would still need to create a ssh RSA key. But cant quite see where to add it in this example, are you supposed to write it into the line somewhere.

```
ssh.authPublickey(System.getProperty("user.name"));
```

---

### Post by codemaniac on 2012-07-06
> **Drenriza said:**
> Thanks for the link.

I looked at [https://github.com/shikhar/sshj/blob/master/src/main/java/examples/SCPDownload.java](https://github.com/shikhar/sshj/blob/master/src/main/java/examples/SCPDownload.java)

but i would still need to create a ssh RSA key. But cant quite see where to add it in this example, are you supposed to write it into the line somewhere.

```
ssh.authPublickey(System.getProperty("user.name"));
```


In your example , passwordless login is required , i.e.  [B]key -based ssh login is required .You need to set it up .

I can try to write up a code for you that would create a ssh tunnel with username and password .However from security perspective it is not suggested as it will expose your password in clear text .

[/B]

---

### Post by Drenriza on 2012-07-06
> **codemaniac said:**
> In your example , passwordless login is required , i.e.  [B]key -based ssh login is required .You need to set it up .

I can try to write up a code for you that would create a ssh tunnel with username and password .However from security perspective it is not suggested as it will expose your password in clear text .

[/B]

But how secure is key based ssh? If someone finds the key (the physical file) can they use it to access the system that the key gives access to?

---

### Post by codemaniac on 2012-07-06
There is Jsch class which allows you to connect to an sshd server and use port               forwarding, X11 forwarding, file transfer, etc.

you have to download the jsch jar from jcraft website .

[http://www.jcraft.com/jsch/](http://www.jcraft.com/jsch/)

You can have an idea how to start with , please refer the below code .

```
import com.jcraft.jsch.*;
import com.jcraft.jsch.Channel;
import com.jcraft.jsch.Session;
import com.jcraft.jsch.UserInfo;
import java.io.*;

public class MainSSH
{
    public static void main(String args[])
    {
        String user="your_use_name";
        String host="localhost";//place the hostname to which you want to connect 
        String cmd="cd $HOME"; //here you can fore your scp command to tranfer file 
        JSch jsch = new JSch();
    try
    {
    Session session=jsch.getSession(user,host,22);
    session.setPassword("your_password"); 
    UserInfo usrInfo=new MyUserInfo();
    session.setUserInfo(usrInfo);
    session.connect();
    Channel channel=session.openChannel("exec");
    ((ChannelExec) channel).setCommand(cmd);
    channel.setXForwarding(true);
    InputStream in = channel.getInputStream();
    channel.connect();
    channel.setInputStream(System.in);
    byte[] tmp = new byte[1024];
    while (true)
    {
        while (in.available() > 0)
        {
        int i = in.read(tmp, 0, 1024);
            if (i < 0)
            break;
        System.out.print(new String(tmp, 0, i));
        }
    if (channel.isClosed())
    {
    in.close();
    break;
    }
    try
    {Thread.sleep(1000);}
    catch (Exception ee)
    {}
    }
    channel.disconnect();
    session.disconnect();
    }
catch(Exception e)
{
e.printStackTrace();
System.out.println("Exception"+e);
}
}
public static class MyUserInfo implements UserInfo 
{
public String getPassword()
{ return "password"; }
public String getPassphrase()
{return ""; }
public boolean promptPassword(String arg0)
{ return true; }
public boolean promptPassphrase(String arg0)
{ return true; }
public boolean promptYesNo(String arg0)
{ return true; }
public void showMessage(String arg0)
{ }
}
}
```

---

### Post by dwhitney67 on 2012-07-06
> **Drenriza said:**
> But how secure is key based ssh? If someone finds the key (the physical file) can they use it to access the system that the key gives access to?

How would this 'someone' get access to the system in which the public key is stored?  If they were able to get access using user-id/password, do you think they really care about the public key anymore?  (well, there might be reasons.)

As for storing a password in plain-text within an application or even a properties file, you are still at the mercy of a hacker (or even another user who is authorized to use your computer).

So, in conclusion, you have to have a certain level of faith that your system is secure and that it will not be breached.  Consider changing your password every 60 days, and ensure that it is 12+ characters long and it contains mixed-case letters, numbers, and special symbols.

---

### Post by Drenriza on 2012-07-06
> **dwhitney67 said:**
> How would this 'someone' get access to the system in which the public key is stored?  If they were able to get access using user-id/password, do you think they really care about the public key anymore?  (well, there might be reasons.)

As for storing a password in plain-text within an application or even a properties file, you are still at the mercy of a hacker (or even another user who is authorized to use your computer).

So, in conclusion, you have to have a certain level of faith that your system is secure and that it will not be breached.  Consider changing your password every 60 days, and ensure that it is 12+ characters long and it contains mixed-case letters, numbers, and special symbols.

Im not afraid of crackers getting into the system. But some (stupid is a hard word) less capable system administrators have access to the same system. And was wondering IF! they found the key file, would they be able to use it to get access to the system to which it gives access, besides the purpose of downloading files (as for what i'am using it), but like ssh to the machine.

---

### Post by Drenriza on 2012-07-16
Codemaniac.

Is it in this section
**String cmd="cd $HOME";**
where i would say what file / folder to download?

Kind regards.

---

### Post by codemaniac on 2012-07-16
> **Drenriza said:**
> Codemaniac.

Is it in this section
**String cmd="cd $HOME";**
where i would say what file / folder to download?

Kind regards.

In the sample code you can execute whatever command you wish in the cmd string at remote host .

You should try doing a scp of wget in the mentioned **cmd **string .

---

### Post by Drenriza on 2012-07-17
Hey codemanic

I dont get this part.

> public static class MyUserInfo implements UserInfo 
{
public String getPassword()
{ return "password"; }
public String getPassphrase()
{return ""; }
public boolean promptPassword(String arg0)
{ return true; }
public boolean promptPassphrase(String arg0)
{ return true; }
public boolean promptYesNo(String arg0)
{ return true; }
public void showMessage(String arg0)
{ }
}

up in the user, host and cmd string i enter information about the remote host i want to connect to. So what is the UserInfo used for?

Thanks on advance.
Kind regards.

---

### Post by codemaniac on 2012-07-17
> **Drenriza said:**
> Hey codemanic

I dont get this part.



up in the user, host and cmd string i enter information about the remote host i want to connect to. So what is the UserInfo used for?

Thanks on advance.
Kind regards.

UserInfo interface allows user interaction. The application can provide an implementation of this interface to the Session to allow for feedback to the user and retrieving information (e.g. passwords, passphrases or a confirmation) from the user.

---

### Post by Drenriza on 2012-07-17
So in theory i could comment out these two lines? If i understand correctly.

//UserInfo usrInfo = new MyUserInfo();
//session.setUserInfo(usrInfo);

Also i get this error when trying to run my program

```
java -jar -cp dist/program.jar dist/lib/jsch-0.1.48.jar 
Failed to load Main-Class manifest attribute from
dist/lib/jsch-0.1.48.jar
```

But i don't quite understand this error.
Kind regards.

---

### Post by codemaniac on 2012-07-18
> **Drenriza said:**
> So in theory i could comment out these two lines? If i understand correctly.

//UserInfo usrInfo = new MyUserInfo();
//session.setUserInfo(usrInfo);

Also i get this error when trying to run my program

```
java -jar -cp dist/program.jar dist/lib/jsch-0.1.48.jar 
Failed to load Main-Class manifest attribute from
dist/lib/jsch-0.1.48.jar
```

But i don't quite understand this error.
Kind regards.

Ypu can use 
```
javac -cp /path/to/jar/file Myprogram.java
```

If you have an IDE like eclipse things would be more easier to include a external jar file in the current java program .

---

### Post by Drenriza on 2012-08-06
@Codemanian

I have "created" a method as follows

```

public void executeSSH_Command() throws JSchException
    {
        for(byte i = 0; i < ArrayListManagement_Class.xmlContent.size(); i++)
        {
            constructorXML Object = (constructorXML) ArrayListManagement_Class.xmlContent.get(i);
            
            String user = "nice";
            String host = Object.returnIP();
            String password = Object.returnPassword();
            String command = "command to run on remote system"; 
            
            JSch jsch = new JSch();

            Session session = null;
            Channel channel = null;

            try
            {
                session = jsch.getSession(user,host,22);
                session.setPassword(password);
                
                java.util.Properties config = new java.util.Properties(); 
                config.put("StrictHostKeyChecking", "no");
                session.setConfig(config);
                
                session.connect();
                
                channel = session.openChannel("exec");
                ((ChannelExec) channel).setCommand(command);
                
                channel.connect(3000);
                
                channel.disconnect();
                
                session.disconnect();

            }
            catch(NullPointerException ex)
            {
                
            }
            finally
            {
                channel.disconnect();
                session.disconnect();
            }
        }
    }

```

And the method start and run the command on the remote system, no big issues here.

My "issue" is. The command i run creates a file on the remote system that i would like to download down to my local system....... what is a cleaver way to do this?

From what i can see, here i ssh to the system and then run the "remote command" local on that system. So if i made a scp request in the command String i would just be asked for a password for my local machine from the remote machine to loop back around O.o thus my question here.

What is a cleaver way to do this? :)

Thanks on advance.

---

