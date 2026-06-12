---
title: "Hoping to get some help on multithreading"
date: 2012-11-16
forum: Programming Talk
---

### Post by crownedzero on 2012-11-16
I'm trying to delve into the world of multithreading and I'm having some difficulty... Typical producer-consumer results in an IllegalMonitorException.

```
public class Producer implements Runnable {
 
    protected final static List<Message> sharedQueue = new ArrayList<>();
    protected final int MAX_SIZE = 10;
 
    @Override
    public void run() {
        while (true) {
            synchronized (sharedQueue) {
                while (sharedQueue.size() == MAX_SIZE) {
                    try {
                        sharedQueue.wait();
                    } catch (InterruptedException e) {
                    }
                }
                sharedQueue.add(new Message(Utility.getRandomProduct(), new Date(), Utility.regionLookup(Utility.getState())));
                System.out.println(Thread.currentThread().getName() + " adding. Queue size: " + sharedQueue.size());
            }
        }
    }
 
    public static Message messageConsume(String region) {
        synchronized(sharedQueue) {
        while (sharedQueue.isEmpty()) {
            try {
                sharedQueue.wait();
            } catch (InterruptedException e) {
            }
        }
        if (sharedQueue.get(0).getRegion().equalsIgnoreCase(region)) {
            Message tempMessage = sharedQueue.get(0);
            sharedQueue.remove(0);
            return tempMessage;
        } else {
            return null;
        }
        }
    }
}
```

```
public class Consumer implements Runnable {
   
    private List<Message> consumerList = new ArrayList<>();
 
    @Override
    public void run() {
        while (true) {
            try {
                Message tempMessage = Producer.messageConsume(Thread.currentThread().getName());
                if (tempMessage.getRegion().equalsIgnoreCase(Thread.currentThread().getName())) {
                    consumerList.add(tempMessage);
                }  Thread.sleep(500);
            } catch (InterruptedException ex) {
                Logger.getLogger(Consumer.class.getName()).log(Level.SEVERE, null, ex);
            }
        }
    }
}
```

Other classes:
[http://pastebin.com/jhHB9kTY](http://pastebin.com/jhHB9kTY) - Main
[http://pastebin.com/BZSspf3x](http://pastebin.com/BZSspf3x) - Consumer
[http://pastebin.com/ndzAADJz](http://pastebin.com/ndzAADJz) - Producer
[http://pastebin.com/p7YdzH1D](http://pastebin.com/p7YdzH1D) - Product
[http://pastebin.com/rxs3WzDT](http://pastebin.com/rxs3WzDT) - Message
[http://pastebin.com/JR5ywgz1](http://pastebin.com/JR5ywgz1) - Utiliy

2 Producers, 4 Consumers

Essentially Producers push a message onto the queue, message consists of a prod obj, date obj, and region string.
This sharedQueue[0] is checked by each Consumer for their region in which case they store it in a local variable and append it to internal lists.

Any help on this and why is greatly appreciated. Thanks!

---

### Post by zobayer1 on 2012-11-17
What is the error you are getting exactly? When I try to run your program, I find a null pointer exception in your consumer class.
```

Exception in thread "Eastern" java.lang.NullPointerException
        at Consumer.run(Consumer.java:23)
        at java.lang.Thread.run(Thread.java:722)


```

Which is apparently on this section, the conditions in "if" is generating this, you may try to check if getRegion is actually getting anything, or whether consumerList is properly allocated or not.:
```

if(tempMessage.getRegion().equalsIgnoreCase(Thread.currentThread().getName())) {
    consumerList.add(tempMessage);
}  

```

Note: I have removed a few imports and package statements from your code to run it quickly, I haven't change anything other than in Mp3_2 the second name should be "Consumers". So, line number's may vary with your code, that's why I included the code segment as well.

---

