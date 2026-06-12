---
title: "Java to Netcat communication problem"
date: 2009-07-03
forum: Programming Talk
---

### Post by Joe88 on 2009-07-03
I have made a simple Java program which sets up a TCP socket connection to a netcat server running on my PC, but when my Java program writes Strings to the Sockets output stream; they do not appear in the Gnome terminal running the Netcat server.

No Exception error messages are printed to the terminal.

The arguments I've used to start the Netcat server are:

**nc -l -p 1334**

Heres the Java clients connection class:

```
import java.util.*;
import java.io.*;
import java.net.*;

/**
 * Write a description of class Chatter here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
public class Chatter
{
    private Socket connection;
    private PrintWriter connectionInputter;
    private URL theURL = null;
    
    public Chatter(String urlString,int port)
    {
        setUpConnection(urlString,port);
    }
    
    public void say(String statement)
    {
        connectionInputter.write(statement);
    }
    
    private void setUpConnection(String urlString,int port)
    {
        try
        {
            theURL = new URL(urlString);
            connection = new Socket(theURL.getHost(),port);    
            connectionInputter = new PrintWriter(new OutputStreamWriter(connection.getOutputStream()) ); 
        }
        
        catch(MalformedURLException e)
        {
            System.out.println(e);    
        }
        
        catch(UnknownHostException e)
        {
            System.out.println(e);    
        }
        
        catch(IOException e)
        {
            System.out.println(e);    
        }
    }
}
```

The command line interface class:

```
import java.util.*;
/**
 * Write a description of class CLI here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
public class CLI
{
    private static Chatter speaker = new Chatter("http://joesPC/blah",1334);

    public static void main(String args[])
    {
        Scanner reader = new Scanner(System.in);
        String statement = "";
        
        System.out.println("************** Chatter **************");
        System.out.println("");
        
        while(true)
        {
            System.out.println("Statement: ");
            System.out.print("> ");
            statement = reader.nextLine();
            speaker.say(statement);
            System.out.println("");
        }
    }
}
```

Please help if you can.

---

### Post by The Cog on 2009-07-03
It would work if you were persistent enough. Trouble is that the writer is buffering the output data. It would finally send when it had collected a buffer full. Modify Chatter by adding a flush after writing, like this:
```
    public void say(String statement)
    {
        connectionInputter.write(statement);
        connectionInputter.flush();
    }
```
You might also want to add a carriage return to the sent statements.

---

### Post by soltanis on 2009-07-03
Yep, its buffering.

---

### Post by Joe88 on 2009-07-03
Thanks for the help.

---

