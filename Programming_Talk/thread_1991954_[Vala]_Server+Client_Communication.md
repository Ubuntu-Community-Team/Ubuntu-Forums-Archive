---
title: "[Vala] Server+Client Communication"
date: 2012-05-31
forum: Programming Talk
---

### Post by sacridex on 2012-05-31
Hello,

I am trying to write a simple server and client application. The Client connects to the server, sends a message and the server shall respond.
But there is a problem: The Server receives the message from the client(and writes it into the stdout), but the responding message is not sent at all, the client is waiting forever. When I quit the client(ctrl+c), the message is sent(obv to late).

Here is my code - Server:
```
void process_request (InputStream input, OutputStream output) throws Error
{
    var data_in = new DataInputStream (input);
    string line;
   
    while ((line = data_in.read_line (null)) != null)
    {
        stdout.printf ("%s\n", line);
    }
    data_in.close ();
    
    string content = "Hello!";
    stdout.printf ("sent?: %lu\n", output.write (content.data));
    output.flush ();
}

int main ()
{
    try
    {
        var service = new SocketService ();
        service.add_inet_port (1337, null);
        service.start ();
        while (true)
        {
            var conn = service.accept (null);
            process_request (conn.input_stream, conn.output_stream);
        }
    }
    catch (Error e)
    {
        stderr.printf ("%s\n", e.message);
    }
    return 0;
}
```Client:
```
class Client : Object
{
    public Client ()
    {
        var add = new InetAddress.from_string ("127.0.0.1");
        
        try
        {
            var sock = new SocketClient ();
            var conn = sock.connect (new InetSocketAddress (add, 1337));
            var output = conn.output_stream;
            output.write ("test\n".data);
            output.flush ();

            var response = new DataInputStream (conn.input_stream);
            var line = response.read_line (null);
            stdout.printf ("received message: %s\n", line);
        }
        catch (Error e)
        {
            stdout.printf ("error: " + e.message + "\n");
        }
    }
    
    public static int main ()
    {
        new Client ();
        
        return 0;
    }
}
```

---

### Post by sacridex on 2012-06-01
Some updates:
Now I can actually connect to the server, send a message and get a respond from the server. But thats it. I have to close the connection, otherwise the message sent by the server would not arrive at the client...
The message is sent by the server, but the client freezes at [FONT=monospace]"[/FONT]response.read_line (null);" until the connection is closed at serverside.
Is there a way to communicate any further? I do not want to open a new connection after every message...

thx


Server:
```
void process_request (InputStream input, OutputStream output) throws Error
{
    var data_in = new DataInputStream (input);
    var line = data_in.read_line (null);
    stdout.printf ("received message: %s\n", line);
    
    string content = "Hello!";
    stdout.printf ("number of characters sent: %lu\n", output.write (content.data));
    output.flush ();
}

int main ()
{
    try
    {
        var service = new SocketService ();
        service.add_inet_port (1337, null);
        service.start ();
        while (true)
        {
            var conn = service.accept (null);
            process_request (conn.input_stream, conn.output_stream);
            /*
             *    Only if I close the connection, the message sent above arrives at the client(or if i quit the server, which closes the connection)
             */
            conn.close ();
        }
    }
    catch (Error e)
    {
        stderr.printf ("%s\n", e.message);
    }
    return 0;
}
```Client:
```
class Client : Object
{
    public Client ()
    {
        var add = new InetAddress.from_string ("127.0.0.1");
        
        try
        {
            var sock = new SocketClient ();
            var conn = sock.connect (new InetSocketAddress (add, 1337));
            conn.output_stream.write ("test\n".data);

            var response = new DataInputStream (conn.input_stream);
            var line = response.read_line (null);
            stdout.printf ("received message: %s\n", line);
        }
        catch (Error e)
        {
            stdout.printf ("error: " + e.message + "\n");
        }
        
        
    }
    
    public static int main ()
    {
        new Client ();
        
        return 0;
    }
}
```

---

