---
title: "Java network help, narrowed down the problem!"
date: 2009-04-22
forum: Programming Talk
---

### Post by Choad on 2009-04-22
still struggling with this networking stuff, but i've figured out it's to do with the way i receive messages. when it gets to that part of the logic it won't proceed until it receives a message.

uncomment the println in run() to make it super obvious what is happening (project attached, first run hostGame then clientGame)
```
public void run() {
        while ( true ) {
//            System.out.println("Thread: send()");
            send();
//            System.out.println("Thread: receive()");
            receive();
        }
    }

    private void send() {
        if ( !outQueueEmpty ) {
            String message = popOut();
            System.out.println( "Thread Sent: " + message );
            out.println( message );
        }
    }

    private void receive() {
        String message;
        try {
            if (( message = in.readLine()) != null ) {
                System.out.println( "Thread Received: " + message );
                pushIn( message );
            }
        } catch ( IOException e ) {
            return;
        }
    }
```

so what's up here? this is the same code used on sun's tutorial page. how can i modify this so that if there is no message to be received it doesn't hold up the whole thing? do i need 2 threads for the network? one for in one for out?

---

### Post by Zugzwang on 2009-04-22
> **Choad said:**
> 
so what's up here? this is the same code used on sun's tutorial page. how can i modify this so that if there is no message to be received it doesn't hold up the whole thing? do i need 2 threads for the network? one for in one for out?

This is a typical approach. Most network protocols, however, define clearly whose turn it is to send some data, so the problem does not occur there. Alternatively, you can extend your approach to require both client and server to send "Blank" messages every 0.1 seconds or so, so every blocking is of limited duration. Other people use non-blocking read/writes (not sure how this would work in Java) and call "Thread.yield()" and/or "Thread.sleep(0.1)" or so whenever there's nothing to do.

---

### Post by Choad on 2009-04-22
> **Zugzwang said:**
> This is a typical approach. Most network protocols, however, define clearly whose turn it is to send some data, so the problem does not occur there. Alternatively, you can extend your approach to require both client and server to send "Blank" messages every 0.1 seconds or so, so every blocking is of limited duration. Other people use non-blocking read/writes (not sure how this would work in Java) and call "Thread.yield()" and/or "Thread.sleep(0.1)" or so whenever there's nothing to do.

i just made a new thread to handle inbound stuff and it all works beautifully so i'm leaving it there. i had a look at java.nio (non blocking stuff) and it seemed good, but very different from the standard network stuff so i thought save me learning a whole new module i'll just thread it

---

