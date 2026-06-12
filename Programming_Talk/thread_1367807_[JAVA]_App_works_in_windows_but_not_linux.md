---
title: "[JAVA] App works in windows but not linux"
date: 2009-12-29
forum: Programming Talk
---

### Post by shadylookin on 2009-12-29
The jist of my story is this...
 I'm running a server in java, This server listens for a command to save pictures. In windows it works just fine however in linux a large portion of the picture data never gets saved to the file. 

I've used wireshark to confirm that in fact everything is being send to the server properly. Using a hexeditor I also know that the data that's save to file is actual picture data just missing a large chunk of the first part of the data. 

here's the code in question

[PHP]
String line;
			int imageCount = 0, imageByte;
			
			try {
				Scanner s = new Scanner(socket.getInputStream());
				
				line = s.nextLine();
				String[] items = line.split(" ");
				
				if(items.length == 2)
				{
					String directory = "pictures" + File.separator + items[0] + File.separator + items[1];
					
					new File(directory).mkdirs();
					
					do{
						try{
							line = s.nextLine();
						}catch(NoSuchElementException ex)
						{
							break;
						}
						
						if(line.equals("SAVEPICTURE")){
							
			                File imageFile = new File(directory + File.separator + imageCount + ".jpg");
			                imageCount++;
			                FileImageOutputStream fios;
			                byte[] success = {83, 85, 67, 67, 69, 83, 83, 13, 10};
							try {
								socket.getInputStream().skip(13);
								
								fios = new FileImageOutputStream(imageFile);
								System.out.println("Started getting picture");
				
								while((imageByte = socket.getInputStream().read()) != -1){
			                        //if it has reached the END\r\n
			                       System.out.print(imageByte+" ");
			                        if(imageByte == 69 ){//E
			                                if((imageByte = socket.getInputStream().read()) == 78){//N
			                                        if((imageByte=socket.getInputStream().read()) == 68){//D
			                                                if((imageByte=socket.getInputStream().read()) == 13){//carriage return
			                                                        if((imageByte=socket.getInputStream().read()) == 10){//new line
			                                                                break;
			                                                        } else{
			                                                                fios.write(69);
			                                                                fios.write(78);
			                                                                fios.write(68);
			                                                                fios.write(13);
			                                                                fios.write(imageByte);
			                                                        }
			                                                } else{
			                                                        fios.write(69);
			                                                        fios.write(78);
			                                                        fios.write(68);
			                                                        fios.write(imageByte);
			                                                }
			                                        } else{
			                                                fios.write(69);
			                                                fios.write(78);
			                                                fios.write(imageByte);
			                                        }
			                                }else{
			                                        fios.write(69);
			                                        fios.write(imageByte);
			                                }
			                        }
			                        else{
			                                fios.write(imageByte);
			                        }
			                       
								}
			               
			                fios.flush();
			                fios.close();
			                socket.getOutputStream().write(success);
			                socket.getOutputStream().flush();
			                System.out.println("finished recieving picture");
								
							} catch (FileNotFoundException e) {
								// TODO Auto-generated catch block
								e.printStackTrace();
							} catch (IOException e) {
								// TODO Auto-generated catch block
								e.printStackTrace();
							}
						}
					}while(!line.equals("QUIT"));
					
					s.close();
				}
[/PHP]

Anyone have any ideas what's going on or how to solve it?

---

### Post by jtuchscherer on 2009-12-30
My first thought would be that your server (or better the user who owns the server process) doesn't have rights to create the image folders. I would check that first

---

### Post by shadylookin on 2009-12-30
> **jtuchscherer said:**
> My first thought would be that your server (or better the user who owns the server process) doesn't have rights to create the image folders. I would check that first

good thought, but I'm running it as root. Also it creates the files they're just corrupt because a large chunk of the data is missing even though I can't think of a reason for it. 

I know java isn't completely cross platform, but I don't know what I've used that would change anything in this case.

---

### Post by Some Penguin on 2009-12-30
A few notes.

1.  You probably shouldn't both directly access the input stream *and* pass it to a Scanner object -- switching between them -- unless you've actually read the Scanner source code or sufficient documentation to understand what its assumptions are.

2.  You definitely shouldn't scan for END in that manner.  It's broken.  Try ENEND against the logic in your if() statements.  A state machine would be better -- each state having its own switch statement dictating transitions based on next observed character.

3.  Is this multithreaded?  If it is, you will have some problems because two threads may choose to write to the same file.

---

### Post by shadylookin on 2009-12-30
> **Some Penguin said:**
> A few notes.

1.  You probably shouldn't both directly access the input stream *and* pass it to a Scanner object -- switching between them -- unless you've actually read the Scanner source code or sufficient documentation to understand what its assumptions are.

2.  You definitely shouldn't scan for END in that manner.  It's broken.  Try ENEND against the logic in your if() statements.  A state machine would be better -- each state having its own switch statement dictating transitions based on next observed character.

3.  Is this multithreaded?  If it is, you will have some problems because two threads may choose to write to the same file.

Well the java api didn't mention there was a difference in how the Scanner was handled across platforms, but that's what it ended up being.

Apparently in windows Scanner doesn't read from the InputStream until requested and in Linux it must read ahead or something. 

Anyway thanks for the help and nice catch on the ENEND issue I didn't even notice it.

---

