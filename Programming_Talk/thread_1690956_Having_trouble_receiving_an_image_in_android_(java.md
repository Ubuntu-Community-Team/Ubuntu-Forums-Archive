---
title: "Having trouble receiving an image in android (java) , sent from python"
date: 2011-02-19
forum: Programming Talk
---

### Post by Shpongle on 2011-02-19
Hi all basically I'm trying to send an image (which can vary in file size) from a python server to an android client . I'm not getting any errors and the file is being created client side however it always seems to fall short of the total file size. I have tried many different options in regards to input streams and buffer sizes but I have had no luck.

here is the server part where I do the sending 

```
 #open the watermarked image file and read it into an object
                imgfile = open (marked_image, 'rb')  
                obj = imgfile.read()
                
               #get the no of bytes in the image and convert it to a string
                bytes = str(len(obj))
                
                
                #send the number of bytes
                self.conn.send( bytes + '\n')
              
                
                
                
                if self.conn.sendall(obj) == None:
                    imgfile.flush()
                    imgfile.close()
                    print 'New Image Sent'
                else:
                    print 'Error'
```



Here is the client side where I am trying to receive the 

```
 //read the number of bytes in the image
        	   String noOfBytes =  in.readLine();
        	   
        	   // just to test and display the number of bytes
 expected          Toast.makeText(this, noOfBytes, 5).show();
        	 
        	   int bytes =  Integer.parseInt(noOfBytes);
        	   
        	   //create a file to store the retrieved image
        	   File photo = new File(Environment.getExternalStorageDirectory(),  "PostKey.jpg");
        	   
        	   DataInputStream dis = new DataInputStream(link.getInputStream());
        	   
        	   try{
        	   	
        		FileOutputStream fos =new FileOutputStream(photo);

        	        byte buf[]=new byte[1024];

        	        int len;

        	        while((len=dis.read(buf))>0)
        	        fos.write(buf,0,len);

        	        Toast.makeText(this, "File recieved", 5).show();

        	        fos.close();
        	        dis.close();
        	       }catch(IOException e){
        		   
        		   	Log.e("IO Error","Exception caught " + e.toString());
        		    e.printStackTrace();
        	   }
```

If anyone could help with this I would really appreciate it . I have been wracking my brain trying to solve this. I suspect the problem is client side.

---

### Post by The Cog on 2011-02-19
I don't know whtat the problem is, but some thoughts:

The python sender doesn't need to flush the file it just read, but it might help to flush the connection it just wrote to.

Here: "String noOfBytes =  in.readLine();" it's not clear what type of object in is. If it is a BufferefReader then it may well have read more bytes from the underlying InputStream than were in the first line. For example, the Reader might read 100 bytes from the InputStream, give you 8 bytes in the readline() call, and be sitting on the remaining 92 bytes. Then this line: "DataInputStream dis = new DataInputStream(link.getInputStream());" creates a DataInputStream round the input stream that has already had the first 92 bytes of the image removed. If this is what your problem is, then the destination file will be missing the first part of the file, and the missing bytes are in the BufferedReader's buffer.

It would be helpful to know if it's the beginning or the end of the file that's going missing.

---

### Post by Shpongle on 2011-02-19
First of all thanks for your time . You are correct, in is a buffered reader. Im not sure which end of the file is being disregarded. Is there any way I could find out ?

---

### Post by Shpongle on 2011-02-19
You were correct , It was that read line cutting it short. I would like to thank you for you help. I have been at this for days , up and down the internet on various forums etc . It's really appreciated

---

