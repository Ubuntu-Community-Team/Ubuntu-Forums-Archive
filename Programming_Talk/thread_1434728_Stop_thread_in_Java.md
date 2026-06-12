---
title: "Stop thread in Java"
date: 2010-03-20
forum: Programming Talk
---

### Post by hyperAura on 2010-03-20
Hello people, I found this on the web which is a class creating an mp3 object which behaves as a thread..



import javax.media.*;
import java.io.*;
import java.net.URL;


class mp3 extends Thread
{

private URL url;
private MediaLocator mediaLocator;
private Player playMP3;

public mp3(String mp3)
{
try{
   this.url = new URL(mp3);
   }catch(java.net.MalformedURLException e)
      {System.out.println(e.getMessage());}
}//mp3 constructor

public void run()
{

try{
   mediaLocator = new MediaLocator(url);
   playMP3 = Manager.createPlayer(mediaLocator);
    }catch(java.io.IOException e)
      {System.out.println(e.getMessage());
    }catch(javax.media.NoPlayerException e)
      {System.out.println(e.getMessage());}

playMP3.addControllerListener(new ControllerListener()
  {
  public void controllerUpdate(ControllerEvent e)
     {
     if (e instanceof EndOfMediaEvent)
         {
         playMP3.stop();
         playMP3.close();
         }
     }
  }
 );
 playMP3.realize();
 playMP3.start();
 }//run
}//mp3 class



I can create a new object with this 
mp3 thread = new mp3("file location");

 and start playing music by doing
thread.start();

My problem is that I cannot stop the thread as Netbeans wont let me do it by thread.stop();

Is there another way that I can stop this tread? Thnx

---

### Post by chaanakya_chiraag on 2010-03-20
Try System.exit(0);

---

### Post by hyperAura on 2010-03-20
my problem is that i am using it on my GUI so i just want to hit a button call thread.start() and then by hitting another button call thread.stop();

if i do system.exit(0) the whole GUI will exit.. :(

---

### Post by LKjell on 2010-03-20
A thread stops when its run method is finish. If you want to stop before the run method is done you need to make logic for it.

---

### Post by CptPicard on 2010-03-20
More specifically, just simply flat out killing a thread has been deprecated in Java for a long time; read up on the Thread "interrupt" mechanism. You call interrupt() on the thread and then check the "interrupt flag" within the thread's run code. A cursory look over your code shows that it may be a bit difficult though, if you spend all the time inside the library call...

---

### Post by fingerprint211b on 2010-03-20
Introduce some kind of state to the class that does the job. For example, you can use a simple boolean and a loop :

```

void run()
{
while(running)
  {
  //Do work
  }

}

```

When you want to stop the thread, you simply set *running* to false.

---

### Post by Reiger on 2010-03-20
Hmm. While the basic idea is sound (and incidentally not unlike the interrupt mechanism) this particular proposal seems to leave no way to gracefully (or less gracefully) suspend or terminate the task.

I assume that the OP might want to `interrupt' the thread halfway through because, say, you want to play a different MP3. Or pause it -- and if you resume you do not necessarily resume at the `start' of the track.

If all the OP wants to do is simply play music (and no loop/seeking w/ever) then simply recoding his MP3 class to be a Runnable() subclass, and doing something like:
```

class PlaybackController {
     // Java util concurrent convenience class that handles thread management for us
     Executor playbackService=  Executors.newSingleThreadExecutor();

     // currently playing mp3; possibly null, possibly done according to isDone()
     Future playbackTask;

     public void play(MP3 mp3) {
         stop(); // stop previous track if applicable
         playbackTask=Executors.submit(mp3);
     }
     
     public void stop() {
         if(playbackTask!=null && !paybackTask.isDone()) {
             playbackTask.cancel(true); // cancel, possibly interrupting the thread
         }
     }
}

```

---

### Post by hyperAura on 2010-03-23
ok i tried to interrupt it but it does not work either..

after starting the thread with thread.start(); i tried tread.isAlive(); to check if the thread is alive.. this method returns true if alive but in my case it returns false even if the thread is already in running state.. :(

---

### Post by chaanakya_chiraag on 2010-03-23
I know this is not really helpful, but you could use VLC with the Command-line interface :D

---

