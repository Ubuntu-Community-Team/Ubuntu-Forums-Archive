---
title: "Java MulticastSocket not working on Ubuntu"
date: 2007-08-03
forum: Programming Talk
---

### Post by jt68 on 2007-08-03
Hi,

Not sure if this belongs here or in a Java or a general Linux forum, but thought I'd try. I've run into a rather strange problem. I have a Java multicast server and a client that use MulticastSocket (simple examples attached at the bottom). The example server publishes a string periodically and the client listens to it. All works fine on a Windows XP box, but the client doesn't receive any messages when both are running on a Ubuntu 6.0.6 box. 

I searched the web and saw some folks suggesting turning IPv6 off by adding -Djava.net.preferIPv4Stack=true property to the command line. Tried that. Still doesn't work. Seems like I'm missing something obvious. Any suggestions would be much appreciated. Thanks in advance.

// ------ Start Client --------------
import java.io.*;
import java.net.*;
import java.util.*;

public class MulticastClient {
  public static void main(String[] args) throws IOException {
    int port = 4445;

    InetSocketAddress ina = new InetSocketAddress("localhost", port);
    MulticastSocket socket = new MulticastSocket(ina);
    System.out.println("Default TTL = " + socket.getTimeToLive());
    InetAddress address = InetAddress.getByName("230.0.0.1");
    socket.joinGroup(address);
        
    socket.setReceiveBufferSize(65536);
    System.out.println("Max size = " + socket.getReceiveBufferSize());

    DatagramPacket packet;
    boolean done = false;
    ByteArrayInputStream bais;
    ObjectInputStream ois;
    String received;
    while( ! done ) {
      try {
        byte[] buf = new byte[65536];
        packet = new DatagramPacket(buf, buf.length);
        socket.receive(packet);

        // String received = new String(packet.getData(), 0, packet.getLength());
        bais = new ByteArrayInputStream(buf);
        ois = new ObjectInputStream(bais);
        received = (String) ois.readObject();
        System.out.println("Received = " + received);
      } catch ( Exception ie ) {
        ie.printStackTrace();
        done = true;
      }
    }

    socket.leaveGroup(address);
    socket.close();
  }

}
// ------ End Client --------------



// ------ Start Server --------------
import java.io.*;
import java.net.*;
import java.util.*;

public class MulticastServer {
  protected MulticastSocket socket = null;
  private long FIVE_SECONDS = 5000;
  private InetAddress group;
  private int port = 4445;

  public MulticastServer() throws IOException {
    InetSocketAddress ina = new InetSocketAddress("localhost", port);
    socket = new MulticastSocket(ina);
    System.out.println("Default TTL = " + socket.getTimeToLive());
    group = InetAddress.getByName("230.0.0.1");

    socket.setSendBufferSize(65536);
    System.out.println("Max size = " + socket.getSendBufferSize());
  }

  public void run() {
    ByteArrayOutputStream baos = new ByteArrayOutputStream();
    int count = (int) (Math.random() * 10000);
		  
    while (true) {
      try {
        byte[] buf;
        String str = "hello world " + count;
        count++;
        System.out.println("Publishing : " + str);

        baos.reset();
        ObjectOutputStream oos = new ObjectOutputStream(baos);
        oos.reset();
        oos.writeObject(str);
        oos.flush();
        buf = baos.toByteArray();

        // send it
        DatagramPacket packet = new DatagramPacket(buf, buf.length, group, port);
        socket.send(packet);

        // sleep for a while
        try {
          Thread.sleep((long)(Math.random() * FIVE_SECONDS));
        } catch (InterruptedException e) { }
      } catch (IOException e) {
        e.printStackTrace();
      }
    }
  }

  public static void main(String[] args) {
    try {
      MulticastServer ms = new MulticastServer();
      ms.run();
    } catch( Exception e ) {
      e.printStackTrace();
    }
  }
}
// ------ End Server --------------

---

### Post by steve.horsley on 2007-08-05
Two corrections:

In your server, you must bind to a real local address, not the loopback address, or it won't transmit packets. On my PC, changing this line:
**InetSocketAddress ina = new InetSocketAddress("localhost", port);**
to 
**InetSocketAddress ina = new InetSocketAddress("192.168.8.101", port);**
enabled it to transmit packets. Your IP address is probably different of course.

On the receiver, you must not bind the listening socket to an address. On my PC, changing this line:
**MulticastSocket socket = new MulticastSocket(ina);**
to
**MulticastSocket socket = new MulticastSocket(port);**
enabled it to receive packets.

---

