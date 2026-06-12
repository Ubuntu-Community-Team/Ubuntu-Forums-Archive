---
title: "java: deadlock caused by threads"
date: 2008-03-31
forum: Programming Talk
---

### Post by galdren on 2008-03-31
Hi people,

i have a very irritating problem. I'm writing this code for a college project and my deadline is tomorrow and i've been looking for a solution for a couple of hours now... can anyone help me? Would be greatly appreciated..

this is the case...

i have a networkplayer who corresponds to a player over the network. The Game will ask him to make a move and he's supposed to come up with something and return it. When this networkplayer is queried for the move, he sends the command via a clienthandler to the corresponding client and waits. 

When the clienthandler receives a reply (it runs on a seperate thread which does nothing else than listening to the client), it will invoke the setChoice() command of the networkplayer which sets two variables according to what the client replied. The setchoice command finally calls notify() to wake up the original makeMove() command, which continues by processing the choice and returning it to the game:

```

public synchronized int[]makeMove(Invulling huidig, Bord bord, ArrayList<Invulling> stukken){
       try{

           client.sendMessage(Protocol.PLACE + Protocol.SEPERATOR + huidig.getIntValue());
           System.out.println("Hij gaat nu wachten");
           notify();
           this.wait();
           System.out.println("Hij komt voorbij de wait");
       }catch(InterruptedException ex){
           srv.broadcast("Internal error at client " + name+"! Server might crash!");
       }
       int[] result = new int[2];
       result[0] = pos;
       result[1] = stuk;
       return result;
   }

from ClientHandler, the method to process the reply of the client:
   void move(String param){
       StringTokenizer st = new StringTokenizer(param);
       speler.setChoice(new Integer(st.nextToken(""+Protocol.SEPERATOR)), new Integer(st.nextToken()));                  }

public synchronized void setChoice(int pos, int stuk){
       System.out.println("Het aanroepen van setChoice is gelukt");
       this.pos = pos;
       this.stuk = stuk;
       this.notifyAll();
} 
```

The problem:
Through debugging i found out that: the command is sent and received by the client. The client replies BUT..the clienthandler never receives this reply. So I'm guessing that the clienthandler was stopped somehow, though it runs on a different thread than this one (this is the only place where a wait() method is invoked)

An interesting detail is that this problem does not occur on the first turn, so the first player's turn is processed just like it is supposed to. But on the first turn of the second player (so the 2nd turn in total), the game hangs. Both players use the same NetworkPlayer and ClientHandler class so there is no different in the code between the two players.

Does anyone know what's wrong? I've already tried calling notify()  on the clienthandler just before the makeMove method goes to sleep, but this resulted in an exception...

any   suggestions are greatly appreciated!

---

### Post by leg on 2008-03-31
My first guess would be that your server is shutting down after the first player contacts it. Another possibility may be that when you loop back around so that your server can listen for your next player you have not properly disconnected and reconnected the socket it is listening on.

---

### Post by galdren on 2008-03-31
hey

just debugged it but it all works properly. I found out that whenever the game is started (the clients are not automatically playing when they join but can chat for a while untill they decide to play) the clienthandler of the second player automatically stops listening:

```

		game = new Game(handlers.get(0).getPlayer(),handlers.get(1).getPlayer());
		game.getBord().setServer(this);
		players.get(0).sendMessage(Protocol.START + Protocol.SEPERATOR + players.get(1).getClientName());
		players.get(1).sendMessage(Protocol.START + Protocol.SEPERATOR + players.get(0).getClientName());		

		game.run();

```

getPlayer() returns a networkplayer which is associated with the clienthandler.

So before this piece of code is run, everything works fine, both players receive and send messages as they wish.

But when the game starts, the clienthandler stored at handlers.get(1) stops listening...

---

### Post by imdano on 2008-03-31
You might be getting a deadlock caused by trying to run multiple synchronized methods at once.  As a rule you should never block in a synchronized method (which you are doing), because while it's blocking no other syncrhonized method can do anything.  I can't tell for sure from the code you posted if that's going on, but I'd check it over very carefully to make sure that it isn't.

---

### Post by galdren on 2008-03-31
nope i'm not afaik.

so for convenience:

makeMove() sends a message to the client asking him to decide his move and waits. When the client's reply arrives at the handler on the serverside, the handler will forward this response to the networkplayer with setChoice(). setChoice() sets the variables and calls notifyAll() so that the makeMove() can return the result.

It is never the intent to call a makeMove() twice

---

### Post by imdano on 2008-03-31
Are setChoice() and makeMove() running in the same thread?  Because that would cause a deadlock.  While makeMove is blocking setChoice can't run, but makeMove can't finish until it gets the notifyAll() from setChoice.

---

### Post by galdren on 2008-04-01
thanks for your response.

But they aren't running in the same thread: i have 1 Game thread, which handles the game and asks networkplayers to make moves, and I have a listener-thread for each clienthandler.

If it would help, I could upload the code for the serverside of this app

---

### Post by imdano on 2008-04-01
I sort of phrased that last post poorly.  A better question would be to ask if those two methods are part of the same object.  It doesn't matter if they're getting called from separate threads, you'd still see a deadlock if they're part of the same instance.

It would probably be helpful to see more of your code.

---

### Post by galdren on 2008-04-01
Hi,

i have finally found out what the problem is! What a relief after all those hours...

when the second player sends the command saying he wants to join the game. This command is processed by calling a method which marks him as playing. But after he has been marked, this method checks if there are two players, and if so, starts the game!

This way the second player's thread becomes the thread which upon the game is run and it never breaks out of the "processing" to start listening again.

Thanks for all the help, I really appreciate it.

---

