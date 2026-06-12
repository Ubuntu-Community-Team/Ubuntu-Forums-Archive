---
title: "Changing IP adress with java?"
date: 2009-04-04
forum: Programming Talk
---

### Post by jspolen on 2009-04-04
Hi wondering if it's possible to send a string or whatever from a client class to a server class, but with a different ipnumber that I'm currently using. 

So when I retrieve the ip from the client on my server it says something like 111.222.333.444.

```


import java.io.BufferedReader;
import java.io.DataOutputStream;
import java.io.InputStreamReader;
import java.net.Socket;

public class SimpleClientMain
{
    public static void main(String[] args)
    {
        try
        {
            Socket socket = new Socket("127.0.0.1", 80);
            
           [color=#FF0000] //Change my ip number?????[/color]
            
            DataOutputStream writer = new DataOutputStream(socket.getOutputStream());
            BufferedReader reader = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            
            writer.writeBytes("Hello!\n");
            String fromServer = reader.readLine();
            
            System.out.println(fromServer); 
            
            socket.close();
        }
        catch(Exception e)
        {
            e.printStackTrace();
        }
        
    }
}

```

---

### Post by dwhitney67 on 2009-04-04
You would need to create a raw socket, in which you would setup the IP and the TCP (or UDP) header.

I have not tried this with TCP, but I have done so with UDP.  As for doing it in Java, I do not know if this is possible.

If it is possible, you (or I should say your application) will require root-privileges to create a raw socket.

---

### Post by jspolen on 2009-04-04
ok I will look into that
 thanks

---

### Post by myrtle1908 on 2009-04-04
I recall a library named RawSock or SockRaw or something ... can't quite remember.

Edit: Here it is ... RockSaw ... [http://www.savarese.org/software/rocksaw/index.html](http://www.savarese.org/software/rocksaw/index.html)

---

### Post by Arndt on 2009-04-05
> **dwhitney67 said:**
> You would need to create a raw socket, in which you would setup the IP and the TCP (or UDP) header.

I have not tried this with TCP, but I have done so with UDP.  As for doing it in Java, I do not know if this is possible.

If it is possible, you (or I should say your application) will require root-privileges to create a raw socket.

To create a new socket as such shouldn't require root privileges, but for low port numbers, such as port 80, it usually does. This is why you often see ports like 8000 or 8080.

---

### Post by dwhitney67 on 2009-04-05
> **Arndt said:**
> To create a new socket as such shouldn't require root privileges,...

oh, but it does... that is, for raw-sockets.  For regular sockets, root-privileges may not be required.

> **Arndt said:**
>  but for low port numbers, such as port 80, it usually does. This is why you often see ports like 8000 or 8080.
If a port number is above 1023, then root privileges are not required.  The max port number allowed is 65535 (2^16 -1).


P.S.  It does not matter if the language is Java, C, C++, or even python... for socket creation/usage, the high level language will ultimately interface with the underlying kernel and this is where the user's permission level and the parameters used to create the socket are examined.

---

### Post by Arndt on 2009-04-05
> **dwhitney67 said:**
> oh, but it does... that is, for raw-sockets.  For regular sockets, root-privileges may not be required.


I see; sorry for the misinformation.

---

