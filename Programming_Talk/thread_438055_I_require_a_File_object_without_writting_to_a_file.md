---
title: "I require a File object without writting to a file"
date: 2007-05-09
forum: Programming Talk
---

### Post by Bobtheknight on 2007-05-09
My Betters,

I have a java program that currently takes a BufferedImage and write it to a jpg file.  Then I upload the file to a server.  The method I use to upload things take a  File object.

But I wanna send the Buffered Image directly to the server without writing it into an actual file.  (Security concerns on the client side)  Anyone know where I can find out how?

Is it possible to write the File to the RAM somehow?

Thanks, 

Bob

---

### Post by b1g4L on 2007-05-09
Can you show some of your code dealing with the image?

---

### Post by Bobtheknight on 2007-05-10
Luckily for me I actually found a method that deals with streams instead of files.  After I read that file objects in java contain no more information then the path to the file, I gave up trying to store information into the file object.

This is my current code right now.  It works :D

ClientHttpRequest is a class someone else wrote that mimic HTML form input using java.  I have another question tho, since ClientHttpRequest is in sourcecode form, I just appended it after the class I'm writing, which made it long and ugly.  Is there a way I can compile it separately and "import" it somehow?

                 ByteArrayOutputStream outstream = new ByteArrayOutputStream();

   	    	ImageIO.write(image_out, "jpg", outstream);
			//System.out.println(output + Filename);
			//mimic form data

			ClientHttpRequest request = new ClientHttpRequest(output+Filename);
			request.setParameter("Filedata", "Screenshot.jpg", new ByteArrayInputStream(outstream.toByteArray()));
			request.post();

Thanks

---

