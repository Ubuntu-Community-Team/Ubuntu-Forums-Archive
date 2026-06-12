---
title: "Java: How to collect incoming data into properly terminated lines."
date: 2010-10-01
forum: Programming Talk
---

### Post by MountainX on 2010-10-01
I've been a member of these forums for a few years, but I never realized there were good quality programming discussions here until I did a google search yesterday and ubuntuforums.org came up with the best answer.

So here is my question:
My data arrives in fragments (it is serial data). I want to pass the data along to a method that will parse it. But I only want to pass along properly terminated lines. The lines will be terminated by '\r' (return char). Sometimes a fragment of data comes in that has multiple terminated lines. But sometimes a fragment of data comes in that doesn't yet have a terminator (it will arrive later).

My goal is to be able to send only properly terminated lines (complete lines) to dataProcessor.logSerialData. (The code works without this requirement, but I could write much cleaner code if I could meet this requirement. The logic would be easier to maintain.)

Here is my code that DOES work (but does not meet my new requirement):
```

case SerialPortEvent.DATA_AVAILABLE:
				if (statusReporter != null)
				{
					statusReporter.showStatus("Receiving data");
				}
                try
                {
                    int len = -1;
                    while ((len = in.read(readBuffer)) > 0)
                    {
                        if (len > 0)
                        {
                            String s = new String(readBuffer, 0, len);
                            if (dataProcessor != null)
                            {
                                dataProcessor.logSerialData(s);
                            }
                            else
                            {
                                Logger.log("ERROR: packetReceiver is null");
                            }
                        }
                    }
                }
                catch (IOException ex)
                {
                    Logger.log(ex);
                    return;
                }

```

Here is an example of one of the many things I tried that does NOT work. It somehow causes errors in the data stream.
```

private static final String REGEX = ".*\\r";
private Pattern p = Pattern.compile(REGEX);

    public void serialEvent(SerialPortEvent e)
    {
        byte[] readBuffer = new byte[11000];//tried many values for buffer size

        switch (e.getEventType())
        {
            case SerialPortEvent.DATA_AVAILABLE:
				if (statusReporter != null)
				{
					statusReporter.showStatus("Receiving data");
				}
				if (dataProcessor == null)
				{
					statusReporter.showStatus("error");
				}
                try
                {
                    int len = -1;
                    while ((len = in.read(readBuffer)) > 0)
                    {
                        if (len > 0)
                        {
							String input = new String(readBuffer, 0, len);
							Matcher m = p.matcher(input);
							int count = 0;
							while (m.find())
							{
								count++;
								String terminatedLine = m.group();
								if (!terminatedLine.isEmpty())
								{
									completedLines.add(terminatedLine);
								}
							}
                        }
                    }
                }
                catch (IOException ex)
                {
                    Logger.log(ex);
                    return;
                }
				for (String line : completedLines)
				{
					dataProcessor.logSerialData(line);
				}

```

---

### Post by PaulM1985 on 2010-10-01
I just want to understand the full scope of the problem...

You want to pass a string over a network which will be accepted as an argument of a function.  This string will have special formatting but not all of it may be passed because you are using data streams?

If this is the case, I would recommend using RMI.  You create a Java object on a server and the client connects to this client and can do method calls on it as if the server object is on the client machine, but the server object is actually running on the server machine.

[http://en.wikipedia.org/wiki/Java_remote_method_invocation](http://en.wikipedia.org/wiki/Java_remote_method_invocation)

Wikipedia will probably explain it better than me.  I have worked with it a bit and I really like it for client-server communication.

I think in your example, you would be having the dataProcessor as the object on the server.  The client connects to this and passes the string straight to the dataProcessor, so you don't have to worry about reading from the buffer, Java will do all that for you.

Hope this is of some help.

Paul

---

### Post by MountainX on 2010-10-01
> **PaulM1985 said:**
> I just want to understand the full scope of the problem...

You want to pass a string over a network which will be accepted as an argument of a function.  This string will have special formatting but not all of it may be passed because you are using data streams?

If this is the case, I would recommend using RMI. 

Paul

I guess I was not very clear. Please allow me to add more info.

My application receives ascii data from an instrument connected to the serial port. (I am not passing a string over a network.) I am just receiving incoming data and then parsing the data in my local application.

```

protected InputStream in;
in = serialPort.getInputStream();

```
it's pretty standard Rxtx serial code, I think.

---

### Post by Reiger on 2010-10-01
So if you want to turn character base IO into line based IO why not wrap the InputStream into a Reader into a BufferedReader and read lines from that?

---

### Post by MountainX on 2010-10-01
> **Reiger said:**
> So if you want to turn character base IO into line based IO why not wrap the InputStream into a Reader into a BufferedReader and read lines from that?

I think you are right! Thank you.
(I don't know Java very well yet.)

---

