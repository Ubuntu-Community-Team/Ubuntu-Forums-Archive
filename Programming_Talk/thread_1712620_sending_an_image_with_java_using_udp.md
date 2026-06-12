---
title: "sending an image with java using udp"
date: 2011-03-22
forum: Programming Talk
---

### Post by beligor on 2011-03-22
Hi
I'm making a simple program that sends an image using udp and a receiver that will receive and save the image. My main problem right now is that when I run the receiver, while the sender is running the datagram socket is waiting to receive but doesn't seem to get any packets. The program just stops at that point and waits for a packet to arrive. Does anyone know any possible fixes or at least possible causes of the problem ?

---

### Post by Some Penguin on 2011-03-23
People here tend not to be psychic.  You're unlikely to get any meaningful help unless you show code excerpts.  I'd suggest that you use a debugger to verify where the programs are blocking.

---

### Post by beligor on 2011-03-23
Haha you've got a point. So, assuming that the sender works (since I get the message that is printed after sending out each packet, here is the Receiver. I have highlighted the line were it stops and waits, which I have identified by adding print statements before and after it:

import java.awt.Image;
import java.awt.image.*;
import java.io.*;
import java.net.*;

import javax.imageio.ImageIO;
import java.util.List;

public class Receiver {
  public static void main(String args) {
    try {
		 int DUMMY_PORT = 4524;
	     int PACKET_LENGTH = 1024;

      // Create a socket to listen on the port.
      DatagramSocket dsocket = new DatagramSocket(DUMMY_PORT);

      // Create a buffer to read datagrams into. If a
      // packet is larger than this buffer, the
      // excess will simply be discarded!
      byte[] buffer = new byte[PACKET_LENGTH+3];

      
      //System.out.println(buffer);
      
      // Create a packet to receive data into the buffer
     // DatagramPacket packet = new DatagramPacket(buffer, buffer.length);

      //System.out.println(buffer);
      int offset =buffer.length;

   
	 ByteArrayOutputStream inStream = new ByteArrayOutputStream();
	 System.out.println("avga");
	 inStream.write(buffer, 0,PACKET_LENGTH+3);

	 byte[] whole = new byte[195*PACKET_LENGTH];
	 
	 System.out.println(whole.length);
		 
     // Now loop forever, waiting to receive packets and adding them to the memory stream
     while (true) {
        // Wait to receive a datagram
        DatagramPacket packet = new DatagramPacket(buffer, PACKET_LENGTH+3);
        packet.setData(buffer,0, PACKET_LENGTH+3);

        inStream.write(buffer, 0, PACKET_LENGTH+3);

    	offset+=PACKET_LENGTH+3;

    	 try{
[B]        dsocket.receive(packet);
[/B]    	 }catch(IOException e){
    		 System.out.println( "Server IOException " + e );

    	 }
        System.out.print(packet);

        byte[] inPacket = new byte[PACKET_LENGTH+3];

        packet.setData(inPacket);
        
        //Add the contents of buffer to the Output Stream
        for (int i=3;i<buffer.length+3;i++){
   		 whole[i-3]=buffer[i];
   	 }
        System.out.println(packet.getLength());
        if (buffer[2]==1){
        	break;
        }
        
        
        // Reset the length of the packet before reusing it.
        packet.setLength(buffer.length);
        
        
        
      }
     File f=new File("pic.jpg");

     
     
       OutputStream outStream =new FileOutputStream(f);

     outStream.write(buffer);
     
     

      ImageIO.write((RenderedImage) inStream, "jpg", f);


      
    } catch (Exception e) {
      System.err.println(e);
    }
  
  }
}

---

### Post by Some Penguin on 2011-03-23
I wonder if the sender is properly sending them; with UDP it's trickier since it's best-effort only, not guaranteed delivery.  You've verified that it's properly set with your IP address and that if it's not within the same machine, you're not firewalling off the port?

You may want to eliminate this possibility by using something like 'echoping' ([http://linux.die.net/man/1/echoping]("http://linux.die.net/man/1/echoping")) to see whether that tool can send packets to your server.

Incidentally, it looks to me like the only time you're reading 'offset' is when you're adding to it.  My suspicion is that you probably intend to use it for indexing into 'whole'.

---

### Post by beligor on 2011-03-23
Hi again and thanks for the quick response. I doubt there's a problem with the ports since it did send a few packets at first. And everything is running on one pc. You're also right about offset I had temporarily stopped using it, although its not the cause of the problem.

---

### Post by dwhitney67 on 2011-03-23
Read the following information concerning receive():
[http://download.oracle.com/javase/6/docs/api/java/net/DatagramSocket.html#receive(java.net.DatagramPacket](http://download.oracle.com/javase/6/docs/api/java/net/DatagramSocket.html#receive(java.net.DatagramPacket))

Now that you have shown us the "receiving" side of your applications, can you please show us the "sending" side?

Also, please wrap any code that you post within CODE tags!  This helps preserve the formatting of the code.

---

### Post by beligor on 2011-03-23
This is my "Sender" class:

```

import java.awt.Image;
import java.awt.image.*;
import java.io.*;
import java.net.*;


import javax.imageio.*;
 
public class Sender1 {
	
	
	public static void main(String args[]) {        
	
		try {
			
		 if (args.length!= 4){
			 throw new IOException("Usage: java SenderX localhost <Port> <Filename");
		 }else{

		 InetAddress sock;
		 sock = InetAddress.getByName(args[1]);

		 int DUMMY_PORT = Integer.parseInt(args[2]);
	
		 InputStream is = new BufferedInputStream(new FileInputStream(args[3]));
		 BufferedImage pic = ImageIO.read(is);
		 ByteArrayOutputStream inStream = new ByteArrayOutputStream();
		 
	     //File sourceimage = new File("source.gif");
	     //BufferedImage pic = ImageIO.read(sourceimage);
	     ImageIO.write(pic, "JPG",inStream);
	     byte[] bytes = inStream.toByteArray();
	     int PACKET_LENGTH = 1024;
		 
		 DatagramSocket sendSocket = new DatagramSocket();
		 byte[] sendPacket = new byte[PACKET_LENGTH+3];
		 int offset = 0;

		 //the packet's sequence number
		 short id =0;

		 byte flag = 0;
		 sendPacket[0]=0;
		 sendPacket[1]=0;
		 sendPacket[2]=flag;
		 
		 for (int i=0;i<bytes.length%PACKET_LENGTH;i++)	{ 
			 
			 //fill the packet to be sent with the next series of bytes
			 for(int j=0;j<PACKET_LENGTH;j++){
				 sendPacket[j+3]=bytes[j+offset];
				 //System.out.println(sendPacket[i]);
			 }
			 
			 
			offset +=PACKET_LENGTH;
				
			//add header
			byte[] header = new byte[2];
			header[0] = (byte)(id & 0xff);
			header[1] = (byte)((id >> 8) & 0xff);
			bytes[0]=header[0];
			bytes[1]=header[1];
				
			id ++;

			//check if this is the last packet to be sent
			System.out.println(i);
			if (i==(bytes.length%PACKET_LENGTH-1)){
				flag =1;
			}
			bytes[2]=flag;
			 DatagramPacket dummyPacket = new DatagramPacket(bytes, PACKET_LENGTH+3,sock, DUMMY_PORT);
			 System.out.println(flag);
			 try {
			     sendSocket.send(dummyPacket);
			     System.out.println("send dummy packet succeeded so assume already connected");
			     
				 } catch (NoRouteToHostException nrthe) {
					 System.out.println("alreadyConnected: no route to host so assume not connected");
				 } catch (Exception e) {
					 }
		
		 
			if (flag==1){
				break;
			}
		 }
		 }
		 }catch (IOException es) {
	}	
}
	
}

```

---

### Post by dwhitney67 on 2011-03-23
> **beligor said:**
> Hi
I'm making a simple program that sends an image using udp and a receiver that will receive and save the image.
The app that is sending the data is not doing something "simple".

If you want to send the data of a file via a socket, you do the following (assuming all succeeds):

1.  Open the socket.
2.  Open the file.
3.  For every N-bytes in the file, generate a packet.
4.  Send the packet.
5.  Repeat Steps 3-5 until all the data has been sent.
6.  Close the file.
7.  Close the socket.

Some folks will debate why you chose to use a UDP socket versus a TCP socket, and frankly they will have valid reasons for questioning such.

Regardless, the fundamentals of what you require are stipulated in Steps 2-6 above.  So what in pray tell are you doing with your Sender code???

---

### Post by beligor on 2011-03-24
You, sir, did it. This is what i was looking for: a simple list of steps to follow, not a detailed overview of the UDP protocol as a whole, not a piece of barely commented code nobody understands. I rewrote everything following your steps and it seems to be working, although the packet loss is massive. Thanks

---

### Post by dwhitney67 on 2011-03-24
> **beligor said:**
> ... although the packet loss is massive. Thanks

There is probably an issue with your sender code, or conversely with the receiver code.  Of course, it could also be that you chose to use UDP (which does not guarantee delivery).

If I may ask, what protocol do you use between the sender and the receiver?  What I mean is, how does the sender know which file to send?  Does the receiver ask for it by name?

---

### Post by beligor on 2011-03-25
I rewrote the whole thing from scratch following your steps so this code is now obsolete. It is now smaller and i've added some features. The sender gets the filename as an input from the command line if that's what you're asking. And I used UDP cause I wanted to learn it, this program won't be used anywhere (which is probably a good thing).

---

### Post by Nora2 on 2011-04-04
hello, can u put the final code here, because i have to do something similar but i got problems always with the lost datas... thanks

---

