---
title: "Java ArrayList / Priority Queue Concurrency question"
date: 2010-08-02
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-08-02
I am developing an application that connects to a local server over a TCP/IP socket and transfers data.  I have the socket programming part worked out and the data is transferred using BufferedReader / BufferedWriter.  The data arrives slightly out of order, but it's easy to use a priority queue to sort it.  So what I planned on doing is whenever data is received from the server by BufferedReader, my app simply places the data in the priority queue.  To sort, I always leave 5 units in the queue and then start transferring units from the queue to an ArrayList once the queue is storing 5 of the data objects.  The reason that I want to put the data into an ArrayList is because I have several other objects / widgets in my application that need the data.  I plan to implement listeners to notify the widgets when new data arrives.  Each widget can keep track of what it has read out of the arrayList (the index) and when new data arrives, the widget gets notified and simply resumes pulling data out of the ArrayList starting from the index where it last left-off.  So that's one way to do it, but my goal is not to slow down the server.  I want my application's BufferedReader connection to the server to be as responsive as possible so that the server's BufferedWriter does not fill up causing the server to block / slow down.  To do this, I plan to have the BufferedWriter on the client running in a separate thread and feed the data into a BlockingPriorityQueue:

[http://download-llnw.oracle.com/javase/1.5.0/docs/api/java/util/concurrent/PriorityBlockingQueue.html](http://download-llnw.oracle.com/javase/1.5.0/docs/api/java/util/concurrent/PriorityBlockingQueue.html)

The reason for the blocking priority queue is that when new data arrives, it will eventually be transferred into an ArrayList in order to provide indexed-access for the widgets in the app.  All widgets will be accessing data from the same ArrayList.  Is there a better / more efficient way to do this?  I don't see any issues here as long as blocking only occurs during writes.  And even then, the load on the client would not be too much for it to handle...I just want to keep things as efficient as responsible as possible within reason.

---

### Post by Some Penguin on 2010-08-03
Do you have hard guarantees on how out-of-order things can actually be?

---

### Post by SNYP40A1 on 2010-08-03
> **Some Penguin said:**
> Do you have hard guarantees on how out-of-order things can actually be?

Yes, in practice I find that an event will not be out of order by more than 5 indexes.  And if it is, it happens so rarely that I don't care about those cases.

---

### Post by Some Penguin on 2010-08-03
Hm.  Depending upon how much data you need to buffer (for instance, whether clients need to be able to access historical data; or whether they'll fetch some, do some processing and fall behind, then need to catch up) you may want to use a list of fixed-length arrays.  

This might reduce the need for memory allocation and deallocation when you're moving data into or out of buffers, since you could change the list of array references while clients are reading individual arrays w/o worrying that data moves around.  Not relying on a monolithic array list might also scale better in the case that you need to provide lots of historical access (in extreme cases, you might be better off archiving old data in an on-disk B-tree or the like -- implementations abound).

---

### Post by PaulM1985 on 2010-08-03
Have you considered using RMI? You can create an object on the server computer and connect the client to it.  Then you can call a get method on the data and it will be transferred in the same data structure in the correct order.  You don't need to get bogged down in the low level data transfer stuff.

This link gives a basic description on how to setup RMI.

[http://www8.cs.umu.se/education/examina/Rapporter/471App.pdf](http://www8.cs.umu.se/education/examina/Rapporter/471App.pdf)

Bear in mind that you will have to use techniques for thread safety on the remote object on the server side. (synchronized, locks etc)

I think RMI would be an easier method for what you are trying to do.

Paul

---

### Post by SNYP40A1 on 2010-08-03
If you're new to this thread and want to save some reading, jump to [COLOR="Blue"]POINT A[/COLOR]:

Thanks, I appreciate the replies.  I actually went ahead and implemented the idea that I mentioned in the first post.  It seems to work, but it's 2 AM here and I have not sufficiently tested it out yet.  I thought about storing the data in a SQLLite or Berkley DB on the server computer.  However, that's a bit overkill for what I'm trying to do and I want to keep the workload on the server as minimal as possible (even with my current setup, I only see CPU usage peak to a whopping 5%...so I still have some headroom...just want to keep the load on the server as low as possible).  I don't really think blocking will be a big issue at this point so I simply used:

List list = Collections.synchronizedList(new ArrayList(...));

To handle concurrency issues related to my list.  Of course, I'm still interested in a multi-thread safe solution with less blocking if I can get it for cheap (not much work).

[COLOR="Blue"]POINT A:[/COLOR]
I gave my situation some more thought.  I don't really need an indexed array.  A linked list would actually work (as I only append to the end of the list) and each object only needs to hold a reference to it's place in the list.  The basic work flow looks like this:

1. Initialization stage -- "list" gets filled with data in sorted order.
2. Listener iterates through the list and does some processing on the data.  Saves references to last item in list.
3. More data gets appended to list.  Listener gets notified.
4. Listener picks up where it left off, continues until it reaches the end of list.
5. Repeat steps 3-4 many times.

I could do this by simply creating my own linked list and then simply checking whether the next element is null in order to determine if I am looking at end of list.  Question is, is there a data structure that supports this flavor or "concurrent iterator" so I don't have to make it from scratch?

---

### Post by Some Penguin on 2010-08-03
> **SNYP40A1 said:**
> I
List list = Collections.synchronizedList(new ArrayList(...));

To handle concurrency issues related to my list.  Of course, I'm still interested in a multi-thread safe solution with less blocking if I can get it for cheap (not much work).

Urg.  That's basically making every single call grab the list's lock -- mutually exclusive.  Even reads block each other.  This might make sense if you're write-heavy rather than read-heavy, but urg.

If you can bound the number of items that will ever be of sufficient interest to keep online, an ArrayBlockingQueue will give you an efficient bounded-buffer implementation.

> 
[COLOR="Blue"]POINT A:[/COLOR]
I gave my situation some more thought.  I don't really need an indexed array.  A linked list would actually work (as I only append to the end of the list) and each object only needs to hold a reference to it's place in the list.

But a linked list -- at least, the built-in ones -- don't expose the individual nodes, and if memory serves attempting to reference the Nth node in a linked list is rather likely to result in a sequential scan of length N.   Depending on how many items your buffering, this may be a problem.

> I could do this by simply creating my own linked list and then simply checking whether the next element is null in order to determine if I am looking at end of list.  Question is, is there a data structure that supports this flavor or "concurrent iterator" so I don't have to make it from scratch?

Hm, I'd worry more about how to have the clients catch store their references and 'catch up', per se.  Unless you transfer the whole list... how are you going to have them track where they are?  If you serialize the node they last processed, well, serializing an individual node without serializing the entire list it's in may be non-trivial.  If you transfer over an identifier, now you have to be able to translate that identifier into a node reference -- ideally, without sequential scan.

---

### Post by SNYP40A1 on 2010-08-03
> **Some Penguin said:**
> Urg.  That's basically making every single call grab the list's lock -- mutually exclusive.  Even reads block each other.  This might make sense if you're write-heavy rather than read-heavy, but urg.

If you can bound the number of items that will ever be of sufficient interest to keep online, an ArrayBlockingQueue will give you an efficient bounded-buffer implementation.



Yes, I checked and you're right.  That wrapper only allows one item to access the list object at a time.  Since my read to write ratio will be around 10:1, probably not a good idea.  However, the ArrayList gets rather big, maybe a million entries.  So I'd probably be better off implementing separate read write locks...which would actually be painful because each worker currently grabs a reference to the arrayList and reads data without synchronization.

> 
But a linked list -- at least, the built-in ones -- don't expose the individual nodes, and if memory serves attempting to reference the Nth node in a linked list is rather likely to result in a sequential scan of length N.   Depending on how many items your buffering, this may be a problem.


Hm, I'd worry more about how to have the clients catch store their references and 'catch up', per se.  Unless you transfer the whole list... how are you going to have them track where they are?  If you serialize the node they last processed, well, serializing an individual node without serializing the entire list it's in may be non-trivial.  If you transfer over an identifier, now you have to be able to translate that identifier into a node reference -- ideally, without sequential scan.

The idea I had was create a single linked list on the client that all listener processes reference.  The listeners only need to traverse the list once.  This is what I had in mind:

[PHP]
public class dataset {
	LinkedList<DataObject> list = new LinkedList<DataObject>();
	
	public void receiveObject(DataObject newdataobj)
	{
		list.append(newdataobj);
                notifyListeners();
	}
	
	/** other functions which handle receiving data objects from server **/
}

public class worker {
	private LinkedList<DataObject> list;
	private Iterator<DataObject> itr;
	
	public worker(LinkedList<DataObject> list)
	{
		this.list = list;
		itr = list.getIterator();
		notifyNewData();
	}

	public notifyNewData()
	{
		while(itr.hasNext())
		{
			process(itr.next()); //process is some function that does something with new data
		}
	}
}
[/PHP]

Basically, the Dataset class updates the linked list with data received from server and then notifies it's listeners (the worker objects).  On the client, there is only one copy of the linked list (hence all the questions related to handling concurrency).  Each worker simply gets an iterator which is initialized to the first element when it is constructed.  It iterates through the list until there are no more elements.  Then when new data comes in, it uses the same iterator it used before (hasNext() now returns true) and it iterates through the new data.  Is there a list object which has iterators which work like that?  Note, each worker only needs to traverse the list once, but each worker has it's own iterator.

UPDATE: What if I drop the concurrency requirement?  Just run everything one one thread which should be sufficient for now.  Is there then a way to do the above?  Obviously an array would work, but I'm trying to trade indexing capability and constant-time lookup for items in middle of the list for increased efficiency.  I don't really need the index, just the next available element.

---

### Post by kahumba on 2010-08-03
Have you tried java.util.Vector? It's same as the ArrayList except that the Vector is thread-safe and the ArrayList is not.

---

### Post by Some Penguin on 2010-08-03
The iterators for the Collection implementations outside the concurrency package won't work well for you, because they're typically rigged to throw a ConcurrentModificationException if they detect that the underlying structure has changed while you're still using the same iterator (regardless of whether it's the same thread or not).

---

### Post by SNYP40A1 on 2010-08-03
> **kahumba said:**
> Have you tried java.util.Vector? It's same as the ArrayList except that the Vector is thread-safe and the ArrayList is not.

I'll try vector if I must have concurrency...I think for now, I might be able to get away with out it.  It looks like the bottlenecks brought on with concurrency might not be worth the effort of implementing it.  I looked into using vectors before, but the general consensus on many internet forums (such as this one: [http://stackoverflow.com/questions/2358126/does-a-java-container-offer-a-fail-safe-iterator](http://stackoverflow.com/questions/2358126/does-a-java-container-offer-a-fail-safe-iterator)) was that it's an obsolete data structure that only remains because some core APIs still use it (which kinda contradicts the idea of it being an obsolete data type), but anyways.  It might work for me, here's some threads on vector vs. ArrayList for others interested:

[http://skeletoncoder.blogspot.com/2006/09/java-tutorials-arraylist-or-vector.html](http://skeletoncoder.blogspot.com/2006/09/java-tutorials-arraylist-or-vector.html)

[http://www.coderanch.com/t/203027/Performance/java/Vector-vs-ArrayList](http://www.coderanch.com/t/203027/Performance/java/Vector-vs-ArrayList)

But is there a list data structure in Java which offers iterators that do not "expire" or become corrupt / invalid when new data is added to the structure?  I would think this would be valuable in many applications.

---

### Post by Some Penguin on 2010-08-03
As far as I recall, the only list structures in the standard Java APIs that have iterators that don't mind concurrent modification are those in java.util.concurrent.*.

---

### Post by SNYP40A1 on 2010-08-03
> **Some Penguin said:**
> As far as I recall, the only list structures in the standard Java APIs that have iterators that don't mind concurrent modification are those in java.util.concurrent.*.

Does concurrent modification also include updating the structure while iterating over it or is that something else?

---

### Post by Some Penguin on 2010-08-03
> **SNYP40A1 said:**
> Does concurrent modification also include updating the structure while iterating over it or is that something else?

The former.

---

