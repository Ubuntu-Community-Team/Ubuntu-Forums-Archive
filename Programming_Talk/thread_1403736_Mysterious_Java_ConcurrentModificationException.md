---
title: "Mysterious Java ConcurrentModificationException"
date: 2010-02-10
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-02-10
Ey guys, I have data I have inserted into a container object that holds the variables I need. I then insert that object into a linked list. Now I am trying to print the list with one element in it(for now), but I want to loop through the list and check one of the values in the object to see if it is the one I want to select. So I am starting off by just printing out the linked list's contents. However, I can't figure out why I am getting this modification error as I don't believe I am modifying anything... Here is my code:

```

protected static LinkedList<uSIPStackContainer> SIPStack = new LinkedList<uSIPStackContainer>();

//....

//while(true) {
	    		socket.receive(packet);
	    		data = new String(packet.getData(), 0, packet.getLength());
	    		parsed = data.split("\n");;
	    		
	    		System.out.println("Packet data:" + data);
	    		for(int i = 0; i < parsed.length; i++)
	    			System.out.println("Parsed data:" + parsed[i]);
	    		
	    		cmd = parsed[0];
	    		branch = Integer.parseInt(parsed[1]);
	    		callerID = Long.parseLong(parsed[2]);
	    		payloadIP = InetAddress.getByName(parsed[3]);
	    		payloadPort = Integer.parseInt(parsed[4]);
	    		
	    		System.out.println("Separate values:" + " " + cmd + " " + String.valueOf(branch) + " " + 
	    				String.valueOf(callerID) + " " + payloadIP.toString() + " " + String.valueOf(payloadPort));
	    		
	    		tempContainer = new uSIPStackContainer(callerID,cmd,branch,payloadIP,payloadPort);
	    		SIPStack.add(tempContainer);
	    		while(litr.hasNext())
	    			litr.next().print();
	    		
	    	//}

```

And my container class:

```

import java.net.InetAddress;

public class uSIPStackContainer {
	private static long callerID;
	private static String cmd;
	private static int branch;
	private static InetAddress payloadIP;
	private static int payloadPort;
	
	public uSIPStackContainer(long cID, String c, int b, InetAddress pIP, int pP) {
		callerID = cID;
		cmd = c;
		branch = b;
		payloadIP = pIP;
		payloadPort = pP;
	}
	
	public long getCallerID(){
		return callerID;
	}
	
	public String getCMD(){
		return cmd;
	}
	
	public int getBranch(){
		return branch;
	}
	
	public InetAddress getPayloadIP(){
		return payloadIP;
	}
	
	public int getPayloadPort(){
		return payloadPort;
	}
	
	public void print(){
		System.out.println("Separate values:" + " " + cmd + " " + String.valueOf(branch) + " " + 
				String.valueOf(callerID) + " " + payloadIP.toString() + " " + String.valueOf(payloadPort));
	}
	
}//class uSIPStackContainer


```

And this is the error I get:

```

$ java Test 
Packet data:INVITE
0
2581277130996773306
192.168.1.99
4445

Parsed data:INVITE
Parsed data:0
Parsed data:2581277130996773306
Parsed data:192.168.1.99
Parsed data:4445
Separate values: INVITE 0 2581277130996773306 192.168.1.99 4445
Exception in thread "uSIPServerThread" java.util.ConcurrentModificationException
	at java.util.LinkedList$ListItr.checkForComodification(LinkedList.java:761)
	at java.util.LinkedList$ListItr.next(LinkedList.java:696)
	at uSIPServerThread.run(uSIPServerThread.java:67)
$

```

Thanks for any help! :)

---

### Post by dwhitney67 on 2010-02-10
What is 'litr'??
```

while(litr.hasNext())
        ...

```
If it is a list iterator that you declared earlier, then it is no longer valid if you add (and you have) an element to the list.

---

### Post by doas777 on 2010-02-10
you can't change a list as you are iterating over it. get a new instance of the iterator before you go through the loop

---

### Post by StunnerAlpha on 2010-02-10
Ah ok... so I can only create the iterator when I am about to iterate through it... I don't think I was changing anything in the while loop. I guess when it hit the .add method it threw that exception, right? Thanks guys!

---

### Post by dwhitney67 on 2010-02-10
> **StunnerAlpha said:**
> Ah ok... so I can only create the iterator when I am about to iterate through it... I don't think I was changing anything in the while loop. I guess when it hit the .add method it threw that exception, right? Thanks guys!

You have two while loops; the inner one, where you access the iterator is what threw the exception.  Feel free to add to the container all day... just make sure you obtain a fresh iterator before attempting to access the modified container.

---

