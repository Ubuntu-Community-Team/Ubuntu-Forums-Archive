---
title: "Is it possible to both read and append to a file at the same time?"
date: 2010-07-07
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-07-07
Is it possible to both read and append to a file at the same time?  I believe it is, in both UNIX and Windows, I have opened a file while it was being written.  The text editor usually prompts the user for a refresh.  But in a programming language such as C++ or Java, can I open and read a file while it is being appended to by another process?  What happens when I reach the end of file, but then more data is written?  Is there a way to refresh the file end?

---

### Post by arubislander on 2010-07-07
I don't think it is possible to both read and write to a single file handle.. You could have two handles to the same file though, one to read and one to write.

You'd have to keep track of the time stamp since you last opened the file and refresh when necessary.

Keep in mind that the file will most likely be locked while being written to.

---

### Post by nvteighen on 2010-07-07
Of course you can.

```

FILE *somefile = fopen("path", "a+");

```

The "a+" mode will set the write cursor at the file's end (like the "a" mode) and also set the read cursor at the file's start. This is in C, but its appliable to Python too. I don't know how C++ does this, but I guess it involves some fstream trick.

---

### Post by SNYP40A1 on 2010-07-07
> **nvteighen said:**
> Of course you can.

```

FILE *somefile = fopen("path", "a+");

```

The "a+" mode will set the write cursor at the file's end (like the "a" mode) and also set the read cursor at the file's start. This is in C, but its appliable to Python too. I don't know how C++ does this, but I guess it involves some fstream trick.

Interesting, so it is possible to have a write process and a read process both active on the same file?  How does the read process determine when more data has been written to the file available for reading once it has already reached EOF?

---

### Post by ju2wheels on 2010-07-07
I *think* what would happen in such a case is that when reading EOF is not reached until the write handle is closed so if you were trying to read the file from beginning to end while its being written to you would get stopped on a file read at the end by an I/O wait until something is written or you get EOF when write handle closes. Or at least that is the behavior I would expect (just thinking in terms of pipes).

Also, depending on what you were trying to accomplish by doing read/writing at the same time, you have your fseek type functions to move around the file and read from different points. C++ also has seek functions for streams.

---

### Post by soltanis on 2010-07-08
The results of this seem to be undefined.

I've tried this concept out and while what you're saying makes sense in theory -- as you are writing to a file you should be able to read that data from it -- it seems that this is not the case. First of all, when I tested this by writing some data to a file at a certain rate in Python, and then tried to read the file with a different process (also in Python), I would get inconsistent results; i.e. sometimes calling read would give me a blank line, sometimes it would be the data in the file, but the data didn't seem to be changing. This is likely due to buffering, though.

From the **write**(2) manpage:

```

       POSIX  requires  that  a  **read**(2)  which can be proved to occur after a
       write() has returned returns the new data.  Note that not all file sys&#8208;
       tems are POSIX conforming.

```

My guess is that in a POSIX-conforming filesystem, so long as you ensure that your read operations occur after the corresponding write operations, you should be okay to read messages. This would require serious process synchronization mechanisms to keep the two processes in lockstep.

If you are trying to get two processes to communicate in real time using a file-like mechanism, you really should use UNIX pipes instead. The pipe mechanism is truly a godsend when it comes to programming.

Read the pages relevant to **pipe**(2) or **mknod**(2), or read about the **mkfifo**(1) utility for more on how to use pipes.

---

### Post by SNYP40A1 on 2010-07-08
I'm trying to send data from one computer to another.  The data is written to a file and I thought I could simply place the file in a shared folder and have the second computer read the data.  I know socket programming would be a better solution, but that would require the server computer to regurgitate everything it has stored in the file (probably no more than 50 MBs of data).   

Basically, I have previously recorded data as well as new data arriving at computer A.  After some time, computer B comes online and I want to update it with the recorded data and then keep it updated with new data.  What's the best approach to do that?

---

### Post by Some Penguin on 2010-07-08
Depending on update frequency, you might want to look into lightweight version control systems.

---

### Post by SNYP40A1 on 2010-07-08
Update frequency would be tens to hundreds, possibly over a thousand times per second during peak times.  At this point, I'm thinking socket programming might be best approach.

---

### Post by tbastian on 2010-07-08
> **SNYP40A1 said:**
> Interesting, so it is possible to have a write process and a read process both active on the same file?  How does the read process determine when more data has been written to the file available for reading once it has already reached EOF?

I've done something like this before. What I did was to enter an infinite loop, seek back a byte, read a byte then check the EOF flag.

edit:

I also had a sleep in there too.

---

### Post by ju2wheels on 2010-07-08
I definitely second the socket programming approach to this problem. I would also create a buffer to hold the data that needs to be transfered until computer B becomes available and reachable. That could be something as simple as an array in your app or if you want to get a bit more complex then maybe a sqlite db. Then you can have a thread attempt to reach computer B every minute or so and when it is reachable begin transferring everything from the buffer or sqlite db.

---

### Post by endotherm on 2010-07-08
I've never tried it, but most modern OS kernels implement what MS calls "multiple-read single-write file access semantics", meaning that many threads may read a file, but only one can write at any given time. most systems implement a lock mechanism to prevent multiple threads from writing to a file resource. basically the same principal as shared objects in multithreaded apps: read all you want, but synch-lock when you write.

---

### Post by nvteighen on 2010-07-08
Ok, now I am totally confused.

What is the idea, read and appending from different threads or in the same one? If it's just about having a file open for reading and appending, then fopen's "a+" mode is just what you need. Of course, if it's about different threads, then the others posts seem to be the answer.

---

### Post by endotherm on 2010-07-08
> **nvteighen said:**
> Ok, now I am totally confused.

What is the idea, read and appending from different threads or in the same one? If it's just about having a file open for reading and appending, then fopen's "a+" mode is just what you need. Of course, if it's about different threads, then the others posts seem to be the answer.
a thread can perform at most 1 action at any one time, so either the fopen is internally multithreaded or it is synchronously threaded and performs operations as they are buffered. my guess is that each stream runs on it;s own thread.

Edit:

per this ( [http://docs.hp.com/en/B2355-90694/fopen.3S.html](http://docs.hp.com/en/B2355-90694/fopen.3S.html) )
fopen(string , *char) is a blocking IO call, in that the write stream may never overwrite the contents of the file (append only) so if multiple threads access the file for append access, the data gets written in the order that each thread flushes the write stream, so there isn;t a multiaccess conflict. Interesting. I would not have guessed that. fopen for write however would block other threads from accessing the file until after the fflush and fclose. 
> When a file is opened for update, both input and output can be done on the resulting *stream*. However, output cannot be directly followed by input without an intervening call to fflush()  or to a file positioning function (fseek(), fsetpos(), or rewind()), and input cannot be directly followed by output without an intervening call to a file positioning function unless the input operation encounters end-of-file.
When a file is  opened for append (i.e., when *type*  is a, a+, ab+, or a+b), it is impossible to overwrite information already in the file. All output is written at the end of the file, regardless of intervening calls to fseek(). If two separate processes open the same file for append, each process can write freely to the file without fear of destroying output being written by the other. Output from the two processes will be intermixed in the file in the order in which it is written.


---

### Post by SNYP40A1 on 2010-07-08
Buffering the data was my first thought to solving this problem.  However, I am currently writing data into 18 files at the same time, generating around 2 GB of data per week (~600 MB when I convert the data logging format from text CSV to binary, even less if I compress that data using zlib or some other utility).  The issue is that I don't know what data computer B will request.  The user and application running on Computer B will determine that.  So that's what led me to consider a combination of reading the text files to get what data was logged, and then simply having computer B "subscribe" to a data stream from computer A.  Any new relevant data captured by computer A would be forwarded to computer B over a socket connection until computer B unsubscribes.  In Java, I think the socket buffering is already taken care of so probably would not be that hard. 

I thought about storing the data in a database, but I don't need a relational DB...seems like it would add a lot of overhead.  My ideal solution would be a very light-weight library that has basically manages a binary file.  It looks like the following:

[PHP]
import java.beans.XMLEncoder;
import java.io.BufferedInputStream;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStream;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.OutputStream;
import java.net.ServerSocket;
import java.net.Socket;
import java.util.ArrayList;
import java.util.Date;
import java.util.Iterator;

public class DataWriter {
	private BufferedWriter outputStream;
	private ServerAccepter serverAccepter;
	// List of object streams to which we send data
	private java.util.List<ObjectOutputStream> outputs =
	new ArrayList<ObjectOutputStream>();
	private String filename;
	

	//setup file
	public DataWriter(String filename)
	{
		this.filename = filename;
		try {
			outputStream = new BufferedWriter(new FileWriter(filename));
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		serverAccepter = new ServerAccepter(7454);
		serverAccepter.start();
	}
	
	//Would this function work if the file is open and being written to?
	public void forwardAllRecordedData(ObjectOutputStream output)
	{
		try {
			ObjectInputStream in = new ObjectInputStream(new FileInputStream(filename));
			while(in.available() > 0)
			{
				Message msg = (Message)in.readObject();
				output.writeObject(msg);
			}
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}
	
	public void forwardAllRecordedData(Date startrange, Date endrange, ObjectOutputStream output)
	{
		//how would this function be implemented?
	}

	//write new line of data to file.  
	public void appendNewData(Message message)
	{
		try {
			outputStream.write(message + "\n");
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		sendRemote(message);
	}

	// Sends a message to all of the outgoing streams.
	// Writing rarely blocks, so doing this on the swing thread is ok,
	// although could fork off a worker to do it.
	public synchronized void sendRemote(Message message) {
		// Convert the message object into an xml string.
		OutputStream memStream = new ByteArrayOutputStream();
		XMLEncoder encoder = new XMLEncoder(memStream);
		encoder.writeObject(message);
		encoder.close();
		String xmlString = memStream.toString();
		// Now write that xml string to all the clients.
		Iterator<ObjectOutputStream> it = outputs.iterator();
		while (it.hasNext()) {
			ObjectOutputStream out = it.next();
			try {
				out.writeObject(xmlString);
				out.flush();
			}
			catch (Exception ex) {
				ex.printStackTrace();
				it.remove();
				// Cute use of iterator and exceptions --
				// drop that socket from list if have probs with it
			}
		}
	}
	
	// Adds an object stream to the list of outputs
	// (this and sendToOutputs() are synchronzied to avoid conflicts)
	public synchronized void addOutput(ObjectOutputStream out) {
		outputs.add(out);
	}

	// Server thread accepts incoming client connections
	class ServerAccepter extends Thread {
		private int port;
		ServerAccepter(int port) {
			this.port = port;
		}
		public void run() {
			try {
				ServerSocket serverSocket = new ServerSocket(port);
				while (true) {
					Socket toClient = null;
					// this blocks, waiting for a Socket to the client
					toClient = serverSocket.accept();
					System.out.println("server: got client");
					// Get an output stream to the client, and add it to
					// the list of outputs
					// (our server only uses the output stream of the connection)
					ObjectOutputStream out = new ObjectOutputStream(toClient.getOutputStream());
					addOutput(out);
					forwardAllRecordedData(out);
				}
			} catch (IOException ex) {
				ex.printStackTrace();
			}
		}
	}

	public class Message {
		private Date date;
		private String data;

		public Message(Date date, String data)
		{
			this.date = date;
			this.data = data;
		}

		public Date getDate() {
			return date;
		}

		public String getData() {
			return data;
		}

		@Override
		public String toString()
		{
			return date.getTime() + "," + data;
		}
	}
}
[/PHP]

I copied most of this code from here:

[http://www.stanford.edu/class/cs108/handouts092/33Sockets.pdf](http://www.stanford.edu/class/cs108/handouts092/33Sockets.pdf)

Questions:

1. Would the function **void forwardAllRecordedData(ObjectOutputStream output)** work properly while the file is being appended to?

2. How would I implement the function **void forwardAllRecordedData(Date startrange, Date endrange, ObjectOutputStream output)**, I would like to forward all data in a specific Data range (assume binary file is sorted by Date timestamp from earliest at beginning of file to latest at end of file.  Since I am writing objects into the file and all objects have constant size, seems like I could do a binary search on the file similar to a binary search on an array or ArrayList.  Anyone know how to implement that function?

---

### Post by Some Penguin on 2010-07-08
You'd have to look into the synchronization methods specified by the filesystem drivers up through the application layer if you wanted to do that.

If you're mostly looking for range and point queries, and the updates are fairly small, you could look into e.g. Tokyo Tyrant w. the B+ tree or table methods with a timestamp-based key.

[http://1978th.net/tokyotyrant/]("http://1978th.net/tokyotyrant/")

---

### Post by SNYP40A1 on 2010-07-09
> **Some Penguin said:**
> You'd have to look into the synchronization methods specified by the filesystem drivers up through the application layer if you wanted to do that.

If you're mostly looking for range and point queries, and the updates are fairly small, you could look into e.g. Tokyo Tyrant w. the B+ tree or table methods with a timestamp-based key.

[http://1978th.net/tokyotyrant/]("http://1978th.net/tokyotyrant/")

But is it possible to do binary search on a binary file composed of constant-sized objects?  Seems like it would be although maybe not in Java.

---

### Post by dwhitney67 on 2010-07-09
I've only read the last few posts, so forgive me if I am way off-base here... but wouldn't it be easier to view the problem as one where you have one or more subscribers for the data.  Not only should you handle an external subscription from Computer B, but the application (or separate thread) on Computer A would also subscribe.  The subscriber on Computer A writes the data to a file.

In other words, before the data is ever written to a file, it should be disseminated to the one or more subscribers.

---

### Post by arubislander on 2010-07-09
This thread is an interesting read.. Gives me a reason to dive into the Linux Bible.

---

### Post by SNYP40A1 on 2010-07-09
> **dwhitney67 said:**
> I've only read the last few posts, so forgive me if I am way off-base here... but wouldn't it be easier to view the problem as one where you have one or more subscribers for the data.  Not only should you handle an external subscription from Computer B, but the application (or separate thread) on Computer A would also subscribe.  The subscriber on Computer A writes the data to a file.

In other words, before the data is ever written to a file, it should be disseminated to the one or more subscribers.

That's the way I would do it, but I also need to provide not only current updates for new subscribers, but also some history -- data collected at an earlier time when the connection is initiated.  After the connection is established, then I just stream current real-time data.  So my first thought on how to approach this was to use a database (SQLLite, MySQL, etc.), but I don't need the overhead of a relational database...it would work, but I think a simple binary file would be simpler...even better if I can do a binary search on it while it is being written.  I definitely need the ability to read it while it's being appended to.

---

### Post by Some Penguin on 2010-07-09
> **SNYP40A1 said:**
> But is it possible to do binary search on a binary file composed of constant-sized objects?  Seems like it would be although maybe not in Java.

From multiple machines on shared filesystem?  Like has been pointed out to you multiple times in this very thread, this is highly dependent upon what synchronization guarantees the filesystem drivers provide for you.

You can either continue down this "binary search on a binary file on a network file system" and either *guess* whether it works, you can study the documentation and probably the actual implementation of whatever network client and server you're using to see what guarantees exist, or you can do the more obvious and reliable thing which is to have a server sitting on a single machine that serves as the gateway to reads and writes, and therefore can rely on stronger consistency guarantees than are likely to exist on a shared filesystem.  This isn't a Java problem or a Python problem or what-have-you, it's "what consistency guarantees are provided by NFS or AFS or SMB or whatever protocol you choose to use" question combined with "what consistency guarantees are provided by the Linux kernel" stacked with similar questions for whatever code you write upon them.

But if you continue to insist on doing things the hard and unreliable way, well, that's your problem.

---

### Post by SNYP40A1 on 2010-07-10
> **Some Penguin said:**
> From multiple machines on shared filesystem?  Like has been pointed out to you multiple times in this very thread, this is highly dependent upon what synchronization guarantees the filesystem drivers provide for you.

You can either continue down this "binary search on a binary file on a network file system" and either *guess* whether it works, you can study the documentation and probably the actual implementation of whatever network client and server you're using to see what guarantees exist, or you can do the more obvious and reliable thing which is to have a server sitting on a single machine that serves as the gateway to reads and writes, and therefore can rely on stronger consistency guarantees than are likely to exist on a shared filesystem.  This isn't a Java problem or a Python problem or what-have-you, it's "what consistency guarantees are provided by NFS or AFS or SMB or whatever protocol you choose to use" question combined with "what consistency guarantees are provided by the Linux kernel" stacked with similar questions for whatever code you write upon them.

But if you continue to insist on doing things the hard and unreliable way, well, that's your problem.

I read up on Tokyo Cabinet and watched this informative video cast:

[http://www.youtube.com/watch?v=2k1J7Vn4EDg](http://www.youtube.com/watch?v=2k1J7Vn4EDg)

I think you're right.  I think this product is the way to go.  The B+ Tree structure should provide the store / access performance that I am looking for and I appreciated the user-defined sorting-order.  Only thing I wish it could do was store non-string data (integers and floating-point numbers).  I can get by with strings, but I'd still have to parse and translate floating-point numbers / ints to strings which is a bit of a drag.  Is there a DB very similar to Tokyo Cabinet which also supports integers and floating-point numbers?

Also, I'd like to define keys that are actually a combination of a few columns -- I'd like to keep them as separate columns for data organization reasons, but consider the key to be a combination of the values in the 3 columns.  Not sure if it can do that...still reading.

---

### Post by Some Penguin on 2010-07-10
> **SNYP40A1 said:**
> I read up on Tokyo Cabinet and watched this informative video cast:

[http://www.youtube.com/watch?v=2k1J7Vn4EDg](http://www.youtube.com/watch?v=2k1J7Vn4EDg)

I think you're right.  I think this product is the way to go.  The B+ Tree structure should provide the store / access performance that I am looking for and I appreciated the user-defined sorting-order.  Only thing I wish it could do was store non-string data (integers and floating-point numbers). I can get by with strings, but I'd still have to parse and translate floating-point numbers / ints to strings which is a bit of a drag.  Is there a DB very similar to Tokyo Cabinet which also supports integers and floating-point numbers?

If you examine the specifications, the data storage is actually char*.  Now, one thing that you can do which isn't necessarily wildly platform-independent is to store the integer or floating-point numbers in their native byte representations.  Thing is, the number and order of bytes in an integer can vary from architecture to architecture, so doing it this way would cause problems if the client machines aren't similar to the server.  This may or may not be a problem for you.

e.g. even in a pure Intel environment, having a mix of 32-bit and 64-bit systems would mean that you couldn't use int; you'd have to use some int32_t or the like.  Floats and doubles OTOH have actual IEEE formats.  If you needed to be able to access it from a SPARCstation for some reason, however... in that case, you'd probably be better off using a non-machine-specific format and doing some parsing.

They're not the only non-SQL system you may want to look at.  Cassandra, MongoDB tend to get mentioned.  Haven't looked at them much however.

> Also, I'd like to define keys that are actually a combination of a few columns -- I'd like to keep them as separate columns for data organization reasons, but consider the key to be a combination of the values in the 3 columns.  Not sure if it can do that...still reading.

Hrm.  For that, you may end up looking at a table of some kind anyway.

---

### Post by SNYP40A1 on 2010-07-10
> **Some Penguin said:**
> If you examine the specifications, the data storage is actually char*.  Now, one thing that you can do which isn't necessarily wildly platform-independent is to store the integer or floating-point numbers in their native byte representations.  Thing is, the number and order of bytes in an integer can vary from architecture to architecture, so doing it this way would cause problems if the client machines aren't similar to the server.  This may or may not be a problem for you.

e.g. even in a pure Intel environment, having a mix of 32-bit and 64-bit systems would mean that you couldn't use int; you'd have to use some int32_t or the like.  Floats and doubles OTOH have actual IEEE formats.  If you needed to be able to access it from a SPARCstation for some reason, however... in that case, you'd probably be better off using a non-machine-specific format and doing some parsing.

They're not the only non-SQL system you may want to look at.  Cassandra, MongoDB tend to get mentioned.  Haven't looked at them much however.



Hrm.  For that, you may end up looking at a table of some kind anyway.

Tokyo Cabinet does support tables too, it's just a little slower to manage the overhead.  Should be fine for my purposes.  The server is Ubuntu 9.10 (will upgrade to Ubuntu 10.04 soon) and the client is Ubuntu 10.04.  Both are 64-bit.  So casting should work for me and that's probably the most efficient way to handle it.  I started looking at MongoDB last night and I will checkout Cassandra too.  Thanks for the recommendations!

Update: At first glance, this looks to be a better fit: [http://1978th.net/kyotocabinet/](http://1978th.net/kyotocabinet/).  Have to play around with it to know for sure.

Update #2: [http://www.daniweb.com/forums/thread272775.html](http://www.daniweb.com/forums/thread272775.html)

---

