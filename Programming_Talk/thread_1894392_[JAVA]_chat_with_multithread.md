---
title: "[JAVA] chat with multithread"
date: 2011-12-12
forum: Programming Talk
---

### Post by ubu87 on 2011-12-12
I've tried to modify a code which implements a simple chat with java. I've added the mapping between the nick of the user and the port from which the user sends the messages by means of HashMap. 

What I need is that the message of a client is sent to all the clients connected to the chat. I've tried to do the broadcast but it doesn't work! 

Can someone give a look to the code and help me please? It's very important!!!


```

import java.util.*;

public class ChatServer {
    private static int port = 8888; /* port to listen on */

    public static Vector users;
    Thread t;

    public static void main (String[] args) throws IOException { 
        new ChatServer();
    }

    public ChatServer() {

        ServerSocket server = null;
        try {
            server = new ServerSocket(port); /* start listening on the port */
        } catch (IOException e) {
            System.err.println("Could not listen on port: " + port);
            System.err.println(e);
            System.exit(1);
        }

        users = new Vector();        

        Socket client = null;
        while(true) {
            try {
                client = server.accept();

	        ClientConn c = new ClientConn(client);
                users.addElement(c);

            } catch (IOException e) {
                System.err.println("Accept failed.");
                System.err.println(e);
                System.exit(1);
            }

            /* start a new thread to handle this client */
            t = new Thread(new ClientConn(client));
            t.start();
        }
    }

 
    public void broadcast(String msg) {
       ClientConn you;
          for(int i=0;i<users.size();i++) {
             you = (ClientConn) users.elementAt(i);
             you.out.println(msg);
          }
    } 


}

class ChatServerProtocol {
    private String nick;
    private ClientConn conn;
    public ChatServer server;

/** a hash map from user nicks to the corresponding connections **/
    private static HashMap<String, ClientConn> nicks = new HashMap<String, ClientConn>();

    private static final String msg_OK = "OK";
    private static final String msg_NICK_IN_USE = "NICK IN USE";
    private static final String msg_SPECIFY_NICK = "SPECIFY NICK";
    private static final String msg_SEND_FAILED = "FAILED TO SEND";

/** Adds a nick to the hash map returns false if the nick is already in the table, true otherwise **/
    private static boolean add_nick(String nick, ClientConn c) {
        if (nicks.containsKey(nick)) {
            return false;
        } else {
            nicks.put(nick, c);
            return true;
        }
    }

    public ChatServerProtocol(ClientConn c) {
        nick = null;
        conn = c;
    }

    private void log(String msg) {
        System.err.println(msg);
    }

    public boolean isAuthenticated() {
        return ! (nick == null);
    }

    /** Implements the authentication protocol.
     * This consists of checking that the message starts with the NICK command
     * and that the nick following it is not already in use.
     * returns: 
     *  msg_OK if authenticated
     *  msg_NICK_IN_USE if the specified nick is already in use
     *  msg_SPECIFY_NICK if the message does not start with the NICK command 
     */
    private String authenticate(String msg) {
        if(msg.startsWith("NICK")) {
            String tryNick = msg.substring(5);
            if(add_nick(tryNick, this.conn)) {
                log("Nick " + tryNick + " joined.");
                this.nick = tryNick;
                return msg_OK;
            } else {
                return msg_NICK_IN_USE;
            }
        } else {
            return msg_SPECIFY_NICK;
        }
    }

    
    /** Send a message to another user. 
     * @recepient contains the recepient's nick
     * @msg contains the message to send
     * return true if the nick is registered in the hash, false otherwise
     */
// // //     private boolean sendMsg(String recipient, String msg) {
// // //         if (nicks.containsKey(recipient)) {
// // //             ClientConn c = nicks.get(recipient);
// // //             c.sendMsg(nick + ": " + msg);
// // //             return true;
// // //         } else {
// // //             return false;
// // //         }
// // //     }


    /** Process a message coming from the client sending it to all the connected clients */
    public String process(String msg) {
        if (!isAuthenticated()) 
            return authenticate(msg);

//         String[] msg_parts = msg.split(" ", 1);
// 
//             if(sendMsg(msg_parts[0]/*, msg_parts[1]*/)) return msg_OK;
//             else return msg_SEND_FAILED;

      server.broadcast(msg);
      return msg_OK;

   }
}



class ClientConn implements Runnable {
    private Socket client;
    private BufferedReader in = null;
    public PrintWriter out = null;

    ClientConn(Socket client) {
        this.client = client;
        try {
            /* obtain an input stream to this client ... */
            in = new BufferedReader(new InputStreamReader(client.getInputStream()));
            /* ... and an output stream to the same client */
            out = new PrintWriter(client.getOutputStream(), true);
        } catch (IOException e) {
            System.err.println(e);
            return;
        }
    }

    public void run() {
        String msg, response;
        ChatServerProtocol protocol = new ChatServerProtocol(this);
        try {
            /* loop reading lines from the client which are processed 
             * according to our protocol and the resulting response is 
             * sent back to the client */
            while ((msg = in.readLine()) != null) {
                response = protocol.process(msg);
                out.println("SERVER: " + response);
            }
        } catch (IOException e) {
            System.err.println(e);
        }
    }

    public void sendMsg(String msg) {
        out.println(msg);
    }
}

```

---

### Post by gateway67 on 2011-12-12
The first issue I saw was that you were unnecessarily creating two instances of Client Connection (ClientConn).  Simplify things using the following:
```

...
            try {
                client = server.accept();

                ClientConn c = new ClientConn(client);
                users.addElement(c);
[B]
                /* start a new thread to handle this client */
                t = new Thread(c);
                t.start();[/B]

            } catch (IOException e) {
                ...
            }
...

```
The other "major" problem you have with the code is when the ClientConn attempts to broadcast a message via the ChatServerProtocol; the latter requires a handle to the Server for broadcasting messages.  You might want to consider augmenting the ClientConn to accept a handle to the Server that created it; then in turn, the ClientConn can pass this information to the ChatServerProtocol.  This may not be the best design, but it will get you going in the right direction.

---

### Post by ubu87 on 2011-12-13
I changed something. Now the broadcast is done by the ChatServerProtocol class, but instead of printing the message on the terminal of each client, it prints the message as much as the number of connected clients!

```

/* ChatServer.java */
import java.net.ServerSocket;
import java.net.Socket;

import java.io.*;
import java.util.*;


public class ChatServerT {

    private static int port = 8888; 

    public static void main (String[] args) throws IOException {

        ServerSocket server = null;
        try {
            server = new ServerSocket(port); 
        } catch (IOException e) {
            System.err.println("Could not listen on port: " + port);
            System.err.println(e);
            System.exit(1);
        }

        Socket client = null;
        while(true) {
            try {
                client = server.accept();
            } catch (IOException e) {
                System.err.println("Accept failed.");
                System.err.println(e);
                System.exit(1);
            }

            Thread t = new Thread(new ClientConn(client));
            t.start();
        }
    }
}  // End class ChatServerT


class ChatServerProtocol {

    private String nick;
    private ClientConn conn;

    private static HashMap<String, ClientConn> nicks = new HashMap<String, ClientConn>();

    private static final String msg_OK = "OK";
    private static final String msg_NICK_IN_USE = "NICK IN USE";
    private static final String msg_SPECIFY_NICK = "SPECIFY NICK";
    private static final String msg_SEND_FAILED = "FAILED TO SEND";


    private static boolean add_nick(String nick, ClientConn c) {
        if (nicks.containsKey(nick)) {
            return false;
        } else {
            nicks.put(nick, c);
            return true;
        }
    }

    public ChatServerProtocol(ClientConn c) {
        nick = null;
        conn = c;;
    }

    private void log(String msg) {
        System.err.println(msg);
    }

    public boolean isAuthenticated() {
        return ! (nick == null);
    }


    private String authenticate(String msg) {
        if(msg.startsWith("NICK")) {
            String tryNick = msg.substring(5);
            if(add_nick(tryNick, this.conn)) {
                log("Nick " + tryNick + " joined.");
                this.nick = tryNick;
                return msg_OK;
            } else {
                return msg_NICK_IN_USE;
            }
        } else {
            return msg_SPECIFY_NICK;
        }
    }

    
    // Invia un messaggio in broadcast
    private boolean sendMsg(String recipient, String msg) {
        if (nicks.containsKey(recipient)) {
	int e = nicks.size();
	for(int i=0;i<e;i++){
            ClientConn c = nicks.get(recipient);
            c.sendMsg(nick + ": " + msg);
	}
            return true;
        } else {
            return false;
        }
    }

    // l'input del cliente viene processato
    public String process(String msg) {
        if (!isAuthenticated()) 
            return authenticate(msg);

        String[] msg_parts = msg.split(" ", 2);
            if(sendMsg(msg_parts[0], msg_parts[1])) return msg_OK;
            else return msg_SEND_FAILED;

    }
} // End class ChatServerProtocol


class ClientConn implements Runnable {

    private Socket client;
    private BufferedReader in = null;
    private PrintWriter out = null;

    ClientConn(Socket client) {
        this.client = client;
        try {
            in = new BufferedReader(new InputStreamReader(client.getInputStream()));
            out = new PrintWriter(client.getOutputStream(), true);
        } catch (IOException e) {
            System.err.println(e);
            return;
        }
    }

    public void run() {
        String msg, response;
        ChatServerProtocol protocol = new ChatServerProtocol(this);
        try {
            while ((msg = in.readLine()) != null) {
                response = protocol.process(msg);
                out.println("SERVER: " + response);
            }
        } catch (IOException e) {
            System.err.println(e);
        }
    }

    public void sendMsg(String msg) {
        out.println(msg);
    }
}  // End class ClientConn

```

---

### Post by dwhitney67 on 2011-12-13
You should consider implementing a method that complements add_nick() (i.e. remove_nick()) to be used in cases where the client disconnects and is no longer around.  Perhaps add a "finally" block within ClientConn's run() method where this method can be called.

---

