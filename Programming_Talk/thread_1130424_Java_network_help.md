---
title: "Java network help"
date: 2009-04-19
forum: Programming Talk
---

### Post by Choad on 2009-04-19
this is the first time i've used threads and the first time i've used networking in java and i am hitting brick walls every time i try to create this. 

i attached my project so far (netbeans project)

right click -> run file on "hostGame" then "clientGame" to set things in motion 

quite why i made everything in the main network class static this time i don't know... feel free to change that. i just can't get the damn thing to work, all i want is to be able to send messages between the client and server.

please help!

---

### Post by Choad on 2009-04-20
bump! anyone!? me so tired of this :(

---

### Post by Zugzwang on 2009-04-20
Try to get rid of all static stuff first. 

Then, in your "createGame()" method, you are creating both the server and client sockets? That doesn't make much sense. Only create the sockets you actually need at one side of the connection.

Finally, you didn't gave the results of your tries to run it. Do it if you want answers. Did you got exceptions?

---

### Post by Choad on 2009-04-20
i was following this
[http://java.sun.com/docs/books/tutorial/networking/sockets/clientServer.html](http://java.sun.com/docs/books/tutorial/networking/sockets/clientServer.html)

which says to create a serversocket to accept connections, and then move the connection to a normal socket when it's accepted. i think it's a design that copes with lots of clients, but i'm only using it for one so it seems a bit redundant. 

the expected result would be for the host game and client game to print "hello from host" and visa versa. currently it just gives me a null pointer exception

i'll try and de-static everything see if it helps. thanks for the reply!!

---

### Post by Choad on 2009-04-20
ok 

non-static network class
```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package finalnetwork;

import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;
import java.net.UnknownHostException;

/**
 *
 * @author richard
 */
public class Network {
    private boolean host = true;
    private NetworkThread netThread;
    private int PORT = 4565;

    public void sendMessage( String message ) {
        netThread.pushOut( message );
    }

    public boolean messageWaiting() {
        return netThread.isOutQueueEmpty();
    }

    public String getMessage() {
        return netThread.popIn();
    }

    public boolean initConnection() {
        System.out.println( "Setting up Network..." );
        System.out.println( host ? "We are Host":"We are Client" );

        if ( isHost() ) {
            if ( createGame() ) {
                System.out.println( "Host Setup Complete" );
                return true;
            }
        }
        else if ( joinGame() ) {
            System.out.println( "Client Setup Complete" );
            return true;
        }
        System.out.println( "Initialisation Failed!!" );
        return false;
    }

    private boolean createGame() {
        ServerSocket serverSocket = null;
        try {
            System.out.println( "Creating server socket..." );
            serverSocket = new ServerSocket( PORT );
        } catch ( IOException e ) {
            System.out.println( "Could not create socket on port: " + PORT );
            return false;
        }
        System.out.println( "Server socket created!" );

        Socket clientSocket = null;
        try {
            System.out.println( "Trying to accept client..." );
            clientSocket = serverSocket.accept();
        } catch ( IOException e ) {
            System.out.println( "Accepting client failed." );
            return false;
        }
        System.out.println( "Connection to client estabilshed!" );

        netThread = new NetworkThread( clientSocket );
        if ( !netThread.initialise() ) {
            System.out.println( "Network Thread error" );
            return false;
        }

        return true;
    }

    private boolean joinGame() {
        Socket serverSocket;
        try {
            System.out.println( "Trying to connect to server socket..." );
            serverSocket = new Socket( "127.0.0.1", PORT );

        } catch ( UnknownHostException e ) {
            System.out.println( "Don't know about host :(" );
            return false;
        } catch ( IOException e ) {
            System.out.println( "i/o error while connecting to server :(" );
            return false;
        }
        System.out.println( "Connected to server!" );

        netThread = new NetworkThread( serverSocket );
        if ( !netThread.initialise() ) {
            System.out.println( "Network Thread error" );
            return false;
        }
        System.out.println( "I/o stream created!" );

        return true;
    }

    public boolean isHost() {
        return host;
    }

    public void setHost( boolean value ) {
        host = value;
    }
}

```

non static host game class
```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package finalnetwork;

/**
 *
 * @author richard
 */
public class hostGame {
    public static void main( String[] args ) {
        Network network = new Network();
        network.initConnection();
        network.sendMessage("hi from host");
        while(true) {
            if ( network.messageWaiting()) {
                System.out.println( network.getMessage() );
            }
        }
    }
}

```

non static client game class
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package finalnetwork;

/**
 *
 * @author richard
 */
public class clientGame {
    public static void main( String[] args ) {
        Network network = new Network();
        network.setHost( false );
        network.initConnection();
        network.sendMessage("hi from client");
        while(true) {
            if ( network.messageWaiting()) {
                System.out.println( network.getMessage() );
            }
        }
    }
}

```


exactly the same error

```

run:
Setting up Network...
We are Client
Trying to connect to server socket...
Connected to server!
**Exception in thread "Thread-0" java.lang.NullPointerException**
I/o stream created!
**        at finalnetwork.NetworkThread.run(NetworkThread.java:61)**
Client Setup Complete
**        at java.lang.Thread.run(Thread.java:619)**
BUILD STOPPED (total time: 19 seconds)


... and ....

run:
Setting up Network...
We are Host
Creating server socket...
Server socket created!
Trying to accept client...
Connection to client estabilshed!
**Exception in thread "Thread-0" java.lang.NullPointerException**
Host Setup Complete
        [B]at finalnetwork.NetworkThread.run(NetworkThread.java:61)
        at java.lang.Thread.run(Thread.java:619)[/B]
BUILD STOPPED (total time: 25 seconds)

```

notice how the error message is split up due to the threads interleaving... is this a clue as to what's going wrong?

---

### Post by Choad on 2009-04-20
moving

T = new Thread( this );
T.start();

from NetworkThread's constructor to the end of it's initialise method gets rid of the error. yay. that makes sense! unfortunately it still doesn't *work* so umm... lame :(

---

### Post by Choad on 2009-04-20
wow ok i fixed quite a few errors but it still doesn't work.

much less buggy version attached :)

---

### Post by PaulM1985 on 2009-04-20
I think I would break down what you are doing with Network and NetworkThread differently.  

I would have one class for the Host, HostConnection, which would have a ServerSocket defined in the constructor.  I would then have a method that would initialise the would set up the Socket using serverSocket.accept() and open streams for communication to the client.  You could then add futher methods to deal with the communication.  It could continually loop waiting for information from the client and then call methods to deal with the clients requests and send information back.

The other class would be for the client, ClientConnection.  Its constructor would have information to create the Socket and initialise communication streams.

By having Network as a class used by both Server and Client, it makes it more difficult to follow as it is trying to do two different jobs.

Hope this is of some help.

Paul

---

### Post by Choad on 2009-04-21
> **PaulM1985 said:**
> I think I would break down what you are doing with Network and NetworkThread differently.  

I would have one class for the Host, HostConnection, which would have a ServerSocket defined in the constructor.  I would then have a method that would initialise the would set up the Socket using serverSocket.accept() and open streams for communication to the client.  You could then add futher methods to deal with the communication.  It could continually loop waiting for information from the client and then call methods to deal with the clients requests and send information back.

The other class would be for the client, ClientConnection.  Its constructor would have information to create the Socket and initialise communication streams.

By having Network as a class used by both Server and Client, it makes it more difficult to follow as it is trying to do two different jobs.

Hope this is of some help.

Paul
thanks paul, i took your advice. one of my prototypes was written this way but it was an early one and was made of fail.

attached is an all new, all shiny version. have an abstract class NetworkThread which handles everything common to the server and client, then a Server class and a Client class which both extend NetworkThread, a Network class which is where the rest of my program will hook in to the network. also have a random hostGame and clientGame class just for testing purposes. 

the host is supposed to send "hello from host" "a" "b" "c" "d"

but only "hello from host" "a" was sent. odd. if anyone can have a look i would apprieciate it!!!

---

### Post by PaulM1985 on 2009-04-21
It looks like there is a problem with the threading somewhere.

It might be easier to use BufferedReaders and PrintWriters to pass messages between the host and client.

```

BufferedReader myReader = new BufferedReader(new InputStreamReader(mySocket.getInputStream()));

PrintWriter myWriter = new PrintWriter(mySocket.getOutputStream(), AUTO_FLUSH);

```

You can then use myWriter.println(String) and myReader.readLine() to send and receive messages.

Both the server and the client would read a line, complete actions, and then they can send something back.  This would make it so that you didn't need to use threading in the way you are now.

You could try this just to get it working with just one client and then introduce threading later to deal with multiple clients.

Paul

---

