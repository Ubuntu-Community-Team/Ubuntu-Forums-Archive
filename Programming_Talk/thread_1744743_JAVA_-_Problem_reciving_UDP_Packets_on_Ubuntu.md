---
title: "JAVA - Problem reciving UDP Packets on Ubuntu"
date: 2011-04-30
forum: Programming Talk
---

### Post by Frielspak on 2011-04-30
Hello i made a simple code to test a program that i was doing.

The code is here:

. . .
```

public static final byte precond[] = {(byte) 0xFF, (byte) 0xFF, (byte) 0xFF, (byte) 0xFF};
public static final byte aftercond[] = {(byte) 0x0a,(byte) 0x00};

String msg = new String(precond) + "challenge rcon" + new String(aftercond);
      String aux = "";

      //Enviar
      DatagramSocket sc2 = new DatagramSocket(27020);
      //sc2.setSoTimeout(5000);
      DatagramPacket pkt = new DatagramPacket(msg.getBytes(),msg.length(),InetAddress.getByName("82.102.15.70"),27050);
      sc2.send(pkt);
      System.out.println("SENT");

      //Receber
      DatagramPacket pkt2 = new DatagramPacket(new byte[1024],1024);
      sc2.receive(pkt2);
      String recived = new String(pkt2.getData(),0,pkt2.getLength());
      aux = recived.split(" ")[2].trim();
      sc2.close();
      System.out.println("RECIVED - " + aux);

```
. . .

Well this is a simple code the only think it does it's to send a udp packet to a server and server will respond.

The problem it's, this work's on Windows but it DON'T work on ubuntu(server/desktop edition, iam not saying in linux, because i haven't tried in another destro).

I already checked IPtables everything related with router but i can't solve this, the code run until 1st System.out then it block's waiting for the response, but the response on ubuntu never arrived :S

Can some one help please?

Already tried in another server (VPS) and it still the same problem.

---

