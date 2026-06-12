---
title: "c++ multithreading design question"
date: 2012-07-12
forum: Programming Talk
---

### Post by akvino on 2012-07-12
Hello all!

Here is the layout of the problem... 

Let us asume I have 2 or 3 threads picking up the messages from the queue. Once they pickup the message they will follow it through to completion, and hand it over to consumer. 

I want to, by design to separate message processing from feature / functionality processing. In other words, once message is identified it will be delivered in certain format, but in case we want to add or remove the features to that message, i would rather do it in separate processing entity than message itself. That way message fields are not dependent on features, and vice versa. 

The question. If I have a feature that needs to be implemented over all messages, vs different feature that needs to be implemented over some of the messages, what is the best method to provide feature processing with minimal locking.

Should I just assume it is safe to place the feature processing into the function that can be called from each thread (thread hands over the data that needs to be processed), or is it better to enclose the feature processing into some sort of object that is handled through some version of inheritance. 

Some guidance would be helpful.

---

### Post by 11jmb on 2012-07-12
I'm not sure I follow entirely, so please confirm that I have this correct: you have a queue of messages, and you want your subroutines to process these message as they arrive. When you say you want to separate  your feature processing from message processing, do you mean that you want your "feature processing" to depend on some "type" of message (determined by another function) rather than the actual message contents? This is good design because your feature processing would be agnostic to packet structure.

Based on your description, I'm guessing that each thread will follow the general routine:
>parse message and determine its type
>"do stuff" based on the type of message
this is fine to break up into two different functions

As far as your question on how to minimize locking, the answer is simple and complex at the same time: do as few state-dependent operations as possible. Functional programs are built for concurrency because a "function" in its truest sense does not depend on any external state. If you are doing true functional programming with no side-effects, then concurrency is trivial. It gets very sticky very quickly when you start considering your environment and interprocess communication. The closer you can get to a functional style, the less you will have to deal with locking & communication

---

### Post by dwhitney67 on 2012-07-13
IMHO, the message should do the processing.  If you have message types A, B, and C, each should derive from a base Message class that has the common attributes, and an abstract method called 'execute' (or whatever you wish).  Keep your thread(s) as simple as possible.

For example:
```

class Message
{
public:
    virtual int execute() = 0;
protected:
    Message(int x, int y) : x(x), y(y) {}

    int x, y;
};

class AddMsg : public Message
{
public:
    AddMsg(int x, int y) : Message(x,y) {}

    int execute() { return x + y; }
};

class MultMsg : public Message
{
    MultMsg(int x, int y) : Message(x,y) {}

    int execute() { return x * y; }
};

class ScaleMsg : public Message
{
    ScaleMsg(int x, int y, int scale) : Message(x,y), scale(scale) {}

    int execute() { return x * y / scale; }

private:
    int scale;
};

```

Your thread could be something like:
```

void run()
{
    while (true)
    {
        Message* msg = queue.getMessage();

        int result = msg->execute();

        ...

        delete msg;
    }
}

```

P.S.  Not shown is that the queue is where the mutex/condition objects are used to govern concurrency.

---

### Post by 11jmb on 2012-07-13
> **dwhitney67 said:**
> IMHO, the message should do the processing.  If you have message types A, B, and C, each should derive from a base Message class that has the common attributes, and an abstract method called 'execute' (or whatever you wish).  Keep your thread(s) as simple as possible.

I was thinking that by "message" OP meant that there was some kind of raw data or text that needed to be parsed in order to ID which event to execute. your program exhibits great modular design, but for it to work, (if my understanding of OP's problem is correct) these messages would have to be parsed prior to being loaded onto the queue as event classes (which OP may want to do in parallel). Your overall design makes a lot of sense, but there might have to be an intermediate step between receiving a message and execution.

---

### Post by akvino on 2012-07-15
thanks for the reply...

in essence I am trying to separate messages that require little processing from those that require more processing, and the feature set on the slower messages is higher than on the faster message. Recently I got some help from a friend and he suggested that networking thread completes message type sorting and then places the message in a queue or a ring (lockless ring) allowing processing thread to run to completion. 

One thing did pop to mind after that conversation. If I do separate the trades into slower and faster processing, I am hoping to get the most out of the fast thread. Is there anything I have to do in order to assure that the faster thread will not be affected by the slower thread on the core itself. This is going on clients machine, so I will have to relay on the Kernel scheduler, I will not have much control over the clients server although I can make recommendations. Any thoughts on that, anything you would be concerned about in such situation?


Again, thanks for the reply..

---

