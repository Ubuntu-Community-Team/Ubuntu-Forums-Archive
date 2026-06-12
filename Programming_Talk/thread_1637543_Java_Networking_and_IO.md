---
title: "Java Networking and IO"
date: 2010-12-04
forum: Programming Talk
---

### Post by vandorjw on 2010-12-04
Hey everyone,

I am trying to build a server client program using Java.
At the moment I am stuck.

I have multiple objects coming at the server through the socket, but one at a time.

Is there a way for the server to check what the object or type is?
For example:

```

...
ois = new ObjectInputStream(client.getInputStream());
input = ois.readObject();

if( input is of type Object1 ) {//do something }
else( input is of type Object2 ) {//do somethingelse}


```

If anyone understood what I want to do, I would appreciate your help.

Also, its not always objects being passed...Some times it might also be a string.

Thanks a lot in advance.

--Cc7

---

### Post by Some Penguin on 2010-12-04
If you care about whether an object implements a particular interface or extends a given class, without worrying about the *exact* type (which might even be an anonymous class), use 'instanceof' ("obj instanceof Integer", for instance).

If you care about the exact class, use the instance method getClass().

---

### Post by vandorjw on 2010-12-05
I don't understand what you are trying to tell me :(
Can you give me an example?

The client has an object UserEntity which implements serializable.
It also has an object has the PaymentInfo which also implements serializable.

When I send those objects through the sockets, how can the server tell which one I am sending at it?

Because if it receives a UserEntity, it'll need to act different from the event that it receives a PaymentInfo object.

I have a feeling this is what you are trying to tell me...but I think I am doing it wrong..
```

//some code before this
...
public void run()
    {
        UserEnt dummyUser;
        PayEnt dummyPay;
        String emptyString;

    try
    {
        if(ois.readObject().getClass() == dummyUser.getClass())
        {
            dummyUser = (UserEnt) ois.readObject();
            //do stuff
        }

        else if (ois.readObject().getClass() == dummyPay.getClass())
        {
            //do stuff
        }

        else
        {
             System.exit(1); 
             //Something went wrong.
         }
     }
     catch(Exception e)
     {
           System.out.println(e.getMessage());
     }
}

```

this does not work. When I tied it, the server did this
> 
Created a new Controller.
Listening at 127.0.0.1 on port: 7777
Listening...
Connected to: /72.38.27.117
Created input and outputStreams
Started a new connection. <--here
Make a connection with the client
Listening...
Exception: Software caused connection abort: recv failed
Java Result: 1

and the client said this
> 
run:
task1
task2
Entered Save Date for Task Ent
Inside Try Block
We Have a File OutPutStream
We have a objectOutStream
Tried to write the object
Tried to flush the stream
Tried to Close the Stream
Done ?
Conneting to 72.38.27.117on port 7777
Connected
Exception:null
Java Result: -1


I can upload the Actual code if someone is interested :)


Thanks
CC7

---

### Post by myrtle1908 on 2010-12-05
```
if (ois.readObject() instanceof UserEntity) {
  // do stuff
}
```

[http://en.wikibooks.org/wiki/Java_Programming/Keywords/instanceof](http://en.wikibooks.org/wiki/Java_Programming/Keywords/instanceof)

---

### Post by PaulM1985 on 2010-12-06
Why not have the server take a string message and then the object?

So your client can say "Sending PurchaseInfo", then you server would know what the next object sent will be by parsing the "Sending PurchaseInfo" message.

So your server will alternately handle:
String,
DefinedObject

Just an idea.

Paul

---

### Post by dwhitney67 on 2010-12-06
Whenever you serialize data, eventually you must un-serialize (deserialize) it.

You should have some way to identify the object being sent via the socket so that you know which type of object you are dealing with.  Perhaps the first collection of bytes (say an int or enumerated value) of the data can be used to identify the object.  You server could implement the use of an object-factory that fabricates the appropriate object based on this value, and then uses the object to deserialize the rest of the data.

Btw, it would be more helpful to see the client-side of your application.

---

### Post by VernonA on 2010-12-06
You have a bug in your code which is stopping much of this advice from working. Specifically you say:
```
if(ois.readObject().getClass() == dummyUser.getClass())
{
    ...
}
else if (ois.readObject().getClass() == dummyPay.getClass())
{

```when you really mean:
```
Object obj = ois.readObject();
if(obj.getClass() == dummyUser.getClass())
{
    ...
}
else if (obj.getClass() == dummyPay.getClass())
{

```You can only read the object once, a second read will return null. Once you make this change try using the instanceof again, as I'm pretty sure the Serializable interface includes a routine that allows the type of the received object to be known. Ie you can (and should) use:
```
Object obj = ois.readObject();

if (obj instanceof UserEnt)
    dummyUser = (UserEnt) obj;
else if (obj instanceof PayEnt)
    dummyPay = (PayEnt) obj;
etc.
```

---

### Post by vandorjw on 2010-12-06
Thank you very much for all your replies and steady work towards a solution to my problem. 

I'll implement ```

Object obj = ois.readObject();

if (obj instanceof UserEnt)
    dummyUser = (UserEnt) obj;
else if (obj instanceof PayEnt)
    dummyPay = (PayEnt) obj;
etc.

``` and let you all know how it goes.
Once again, thank you VERY MUCH!

Cheers - CC7

---

### Post by vandorjw on 2010-12-07
Hey everyone, thanks for the help so far.
Right now, I am stuck at not being able to actually send anything across anymore, let alone decipher what it was.

I'll include the code for the server, since it cannot receive anything...the client sends but the server never gets it. :(

It is very simular to what I found here.
[http://java.sun.com/developer/technicalArticles/ALT/sockets/](http://java.sun.com/developer/technicalArticles/ALT/sockets/)

The server makes a connection, 
but always fails here...scr/Network/connect.. run() method

"Object obj = ois.readObject();
I have a feeling that at this point, it does not know what or where ois is...


Hopefully someone knows whats going on.

Thanks once again,
-- CC7

PS: The last post I used dummy Names, but included the actual source this time.

---

### Post by dwhitney67 on 2010-12-07
Avoid starting a thread until the thread object is fully constructed.

For example:
```

   public static void main(String argv[]) throws Exception {
     Controller c = new Controller();
     **c.start();**
   }

```

```

...
System.out.println("Waiting for connections.");
Socket client = arrayServer.accept();
System.out.println("Accepted a connection from: "+ client.getInetAddress());
Connect c = new Connect(client);
**c.start();**
...

```

```

public Connect(Socket clientSocket)
{
  try
  {
    ...
  }
  catch (...)
  {
    ...
  }

  **//this.start();**
}

```


P.S.  A little advice... choose a consistent manner of using curly braces {}, and also a consistent number of white-space for indenting code.  Personally, I prefer using curly braces to form "blocks", similar to the Connect constructor shown above.

---

### Post by VernonA on 2010-12-07
Try two approaches:
1) Put more printfs in your code so you (and we) can see what is going on. You can comment them out later once it's all working. A common approach to adding debug is to define yourself a small class which provides println calls conditionally, such that by changing a flag they get turned off. The compiler is smart enough to know that code which cannot be called can be removed, and it will take them out for you. For example, use:
```
public class DBG
{
    static final   boolean  DEBUG_ON = true;  // Edit for release

    // Low-level debug. Calls are removed from release code by
    // changing the value of the DEBUG_ON flag. They are used 
    // to check code behaviour at the lowest level.

    public static void  lo( String msg )
    {
        if (DEBUG_ON) System.err.println("DBG: "+ msg);
    }
}

```
I use a similar class (it provides more options and controls so I can do hex dumps, add asserts, add debug that only appears on certain conditions, etc) so I can write things like:
```
    DBG.lo("Creating socket..");
    sock = createSocket();
    if (sock==null) DBG.lo("** Doh! Couldn't create socket!")
    int ret = sock.write(data);
    DBG.lo("Sent data. Ret=" + ret);

```By using this sort of technique you can quickly find out where code is not working as expected. (Learn to use asserts too.)

2) The second thing I would do is test the comms link using "Hello World"s instead of serialized objects until you are sure you have a good connection. In other words make sure your code is able to reliably send/receive a trivial buffer of bytes before you start squirting complex, variable length, unintelligible blobs down the pipe.

---

