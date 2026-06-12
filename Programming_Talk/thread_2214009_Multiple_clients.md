---
title: "Multiple clients"
date: 2014-03-29
forum: Programming Talk
---

### Post by brick2 on 2014-03-29
I ve been at it for a couple of days now. I made a simple X O game and I need to create a server for it which would receive and send the status of the game, just sets of coordinates. 
Now I ve got the server working with multiple clients and they can all send info to the server and the server can respond, but what I need is for the server to respond to to all clients together not individually and in such a manner update the status of the game.
I found all sorts of sorts of things on the net but I do not require anything complex, all I need to do is pass a few ints couple of times and that is all. A set of coordinates.

Server:
```
import java.net.*;
import java.io.*;

public class Server extends SerResponse
{

    public static void main(String[] args)
    {
        int port = 1234;
        int i = 0;
        
        try
        {
            ServerSocket sock = new ServerSocket(port);
            System.out.println("SERVER WORKING......");
            
            while(true)
            {
                SerResponse ser = new SerResponse();
                soc[i] = connection;
                Socket connection = sock.accept();
                Runnable runnable = new Server(connection, ++ser.count);
                Thread t = new Thread(runnable);
                t.start();
                i++;
            }
        }
        catch(Exception e)
        {
            System.out.println("SERVER FAIL " + e);
        }
    }
    
    public Server(Socket s, int i) 
    {
        this.connection = s;
        this.ID = i;
    }
}
```

Server Response:
```
import java.awt.List;
import java.io.*;
import java.net.Socket;
import java.util.concurrent.CopyOnWriteArrayList;

public class SerResponse implements Runnable
{
    public static Socket connection;
    public int ID;
    public final static int size = 10;
    public static Socket[] soc = new Socket[size];
    public static Socket[] soc1 = soc1 = new Socket[size];
    public int count = 0;
    
    
    public void run()
    {
        
        
        try 
        {    
            
            int c = 1;
            
            
            DataInputStream in = new DataInputStream(connection.getInputStream());
            DataOutputStream out = new DataOutputStream(connection.getOutputStream());     
             
             while(c!=0)
             {
                 
                c = in.readInt();
                System.out.println(c);
                c += 1;
                out.writeInt(c);    
                
             }    
                
                 
              
             
        } 
        catch (Exception e) 
        {
            System.out.println("Runnable FAIL " + e);
        }
    }
}
```

Client:
```
import java.net.ServerSocket;
import java.net.Socket;
import java.io.DataOutputStream;
import java.io.DataInputStream;
import java.util.Scanner;


public class client 
{
    public static void main(String[] args)
    {
        int[][] arr = {{3,4},{6,2},{9,2}};
        int[][] arr1 = new int[3][2];
        int port = 1234;
        int test = 1;
        
        try
        {    
            System.out.println("Starting client");
            Socket sock = new Socket("localhost", port);
    
            DataOutputStream out = new DataOutputStream(sock.getOutputStream());
            DataInputStream in = new DataInputStream(sock.getInputStream());
            
            while(test!=0)
            {
                Scanner scan = new Scanner(System.in);
                test = scan.nextInt();
                out.writeInt(test);
                test = in.readInt();
                System.out.println(test);
            }
            
            sock.close();
        }
        catch(Exception e)
        {
            System.out.println("CLIENT FAIL " + e);
        }
    }
}
```

This is being done in Java, I know that it would be more efficient to do it in c or c++ I prefer them too, but my task is to do it in Java so here I am.
Could anyone help me out?

The code is messy to say the least as it is one of few versions so there are some leftofvers but I think it should be readable, it is pretty small.

Thank you all for your time.

---

