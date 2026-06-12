---
title: "Communication  between applications"
date: 2012-09-16
forum: Programming Talk
---

### Post by KdotJ on 2012-09-16
Hey everyone, opinions welcome here...

I would like to know what is the recommended way to have two Java applications communicate with one another? I know that it depends on the specifics... so here's an example:

Let's say I have appA and appB. They may not be running on the same machine necessarily (say appA is on the client side and appB is a server side). 

- appA creates and object, and sends it to appB.
- appB does some stuff with the object, sends it back to appA 
- appA does whatever with it...

Now I know I have many options here... sockets, RMI... and if I wanted to get big on it I could use JMS.

Which would be the best idea here? 

Thanks

---

### Post by PaulM1985 on 2012-09-17
It is sort of up to you.  I have done similar stuff with RMI and with Sockets.

One of the projects I worked on recently involved distributing tasks across a multiple connected PCs.  I implemented this using RMI where each PC ran an "Executor" which was an RMI object.  They had an "execute" method which took a "Task" interface and returned the results of executing the task.

Another project I have been working on is wirelessly connecting to a camera on an Android phone.  I have had to use Sockets and Object[Input/Output]Stream to send images because Android doesn't support RMI according to online sources.

I prefer RMI because it allows me to treat the objects just like local objects, but you have to bear in mind they won't be as fast because of the data transfer.

Bear in mind that remote objects will not work in the same way as normal objects in some cases.  For example, if you have a remote object something like the following:
```

class Remote ....... (I forget the correct inheritance stuff)
{
   void doStuff(Integer i)
   {
      i = 2;
   }
}

```

If you called like this:
```

void myFunction()
{
   Remote local = new Remote();
   Remote remote = getRemoteFromOtherMachine();

   Integer localInt = 1;
   Integer remoteInt = 1;

   local.doStuff(localInt);
   remote.doStuff(remoteInt);

   // Here localInt will be 2, but remoteInt will be 1.
   // This is because remote changes the version on it's VM but
   // this is not passed back to the client.
}

```

Paul

---

### Post by Some Penguin on 2012-09-17
It depends on a lot of factors, like whether objects are meant to be processed and the results returned immediately and not persisted at all, whether they're being buffered for batch processing, whether they're small and frequent enough that request overhead matters...

---

