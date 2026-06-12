---
title: "java socket client"
date: 2007-12-19
forum: Programming Talk
---

### Post by Geir102 on 2007-12-19
Hi, im writing a socket client in java. It is going to be GUI using swing. Its going to connect to a server and keep that connection true the hole run.  
And i want to be abel to recive new data while im working in the gui. 
How is it best to do this true treads or some kind of listener?
Exsampels wood be great:)

---

### Post by Geir102 on 2007-12-20
Humz no one knows, look like the best way is using treads.

---

### Post by andyrobo60 on 2007-12-20
Threads is the best way of doing it. Make one thread that reads data in from the socket and deals with the data, and another thread that handles the GUI. 


```


Thread reader = new Thread() {
	public void run() {
		while(true){
			try{
				int read = in.read();
				doSomething(read);
			}catch(IOException e){
				System.err.println("Error reading from input stream");
			}
		}
	}
};
reader.start();

```

Something like this in the class with the socket, with 'in' being the InputStream for the socket.

---

### Post by Geir102 on 2007-12-23
Tanks a lot:-) Any one know if there is some really basic chat client or someting out there. It gets a little easyer if you have some code to look at:-)

---

### Post by Geir102 on 2007-12-23
found this thing, but it dosent use threads
[http://www.cs.princeton.edu/introcs/84network/ChatClient.java.html](http://www.cs.princeton.edu/introcs/84network/ChatClient.java.html)

---

### Post by berserkr on 2007-12-24
This is what you're looking for:

[http://math.hws.edu/javanotes/c11/s5.html](http://math.hws.edu/javanotes/c11/s5.html)

That whole tutorial is very good.

My first post btw! 

printf("Hello, forum!\n");
std::cout << Hello, forum! << std::endl;
System.out.println("Hello, forum!");
(princ "Hello, forum!")

---

### Post by Ragazzo on 2007-12-24
> **Geir102 said:**
> found this thing, but it dosent use threads
[http://www.cs.princeton.edu/introcs/84network/ChatClient.java.html](http://www.cs.princeton.edu/introcs/84network/ChatClient.java.html)

Actually it does use different threads for input and output, though it's not that obvious. The input from the server is done in the main thread (the one that runs main-method) whereas the output to the server is done in the event dispatch thread (actionPerformed is always run in that thread). 

About the event dispatch thread:
[http://java.sun.com/docs/books/tutorial/uiswing/concurrency/dispatch.html](http://java.sun.com/docs/books/tutorial/uiswing/concurrency/dispatch.html)

---

### Post by Geir102 on 2007-12-28
thanks a lot, i'll try to make it work:popcorn:

---

### Post by Geir102 on 2008-01-04
At last my program is up and running:-) Tanks a lott every one:-) but i have a new problem. Using the GUIChat turorial, any one know how to get the Connectionhandeler class in a seperate file. I cant get it to work:-(

---

