---
title: "Java download issue"
date: 2012-08-07
forum: Programming Talk
---

### Post by Drenriza on 2012-08-07
[B]EDIT.
"Laughing to myself" thought about something........ the channel does not wait for the Java program to finish it just start it and then disconnect. So when it tries to download the mail.txt file the output has not yet been added to the file...[/B]


Hi guys & gails.

My issue is as follows. I have one method(**executeSSH_Command()**) to run a Java program on a remote site using JSch, which runs just fine. After this method, another method(**executeSSH_getOutput()**) also using JSch is runned to download the output of the first method, which is saved to a file.

But for some reason, what i download is a empty text file from the remote site even tho it's populated.

Here is the "strange" part. If i comment out the **executeSSH_getOutput()** method and just run the **executeSSH_Command()** method to run the Java program on the remote site, then comment out the **executeSSH_Command()** method and uncomment the **executeSSH_getOutput()** method, i download the text file WITH text.............

Hoping someone who can point out the obvious for me since i get the behavior from the methods that i'am getting,

Method run first.
```

public boolean executeSSH_Command() throws JSchException
    {
        System.out.print("Executing remote command method started \n");
        
        boolean done = false;
        
        byte count = 0;
        
        for(byte i = 0; i < ArrayListManagement_Class.xmlContent.size(); i++)
        {
            constructorXML Object = (constructorXML) ArrayListManagement_Class.xmlContent.get(i);
            
            String user = "username";
            String host = Object.returnIP();
            String password = Object.returnPassword();
            String command = "java -jar /home/username/program.jar"; 
            
            JSch jsch = new JSch();

            Session session = null;
            Channel channel = null;

            try
            {
                session = jsch.getSession(user,host,22);
                session.setPassword(password);
                
                java.util.Properties config = new java.util.Properties(); 
                config.put("StrictHostKeyChecking", "no");
                session.setConfig(config);
                
                session.connect();
                
                channel = session.openChannel("exec");
                ((ChannelExec) channel).setCommand(command);
                
                channel.connect(3000);
                
                channel.disconnect();
                
                session.disconnect();

            }
            catch(NullPointerException ex)
            {
                
            }
            finally
            {
                channel.disconnect();
                session.disconnect();
            }
            
            count++;
            
            if(count == ArrayListManagement_Class.xmlContent.size())
            {
                done = true;
            }
        }
        return done;
    }

```

Method run second.
```

public void executeSSH_getOutput() throws JSchException, IOException
    {
        System.out.println("Download method started \n");
        
        String user = "username";
        String host = "ip";
        String password = "password";
        String rfile = "/home/username/mail.txt";
        String command = "scp -f " + rfile;
        String lfile = "/home/username/mail.txt";
        
        JSch jsch = new JSch();

        Session session = null;
        Channel channel = null;
        
        FileOutputStream fos = null;
        
        String prefix = null;
        
        try
        {
            session = jsch.getSession(user,host,22);
            session.setPassword(password);
            
            java.util.Properties config = new java.util.Properties(); 
            config.put("StrictHostKeyChecking", "no");
            session.setConfig(config);
            
            session.connect();
            
            channel = session.openChannel("exec");
            ((ChannelExec)channel).setCommand(command);
            
            OutputStream out = channel.getOutputStream();
            InputStream in = channel.getInputStream();
            
            channel.connect();
            
            byte[] buf = new byte[1024];
            
            buf[0] = 0; out.write(buf, 0, 1); out.flush();
            
            while(true)
            {
                int c = checkAck(in);
                if(c != 'C')
                {
                    break;
                }
                
                in.read(buf, 0, 5);
                
                long filesize = 0L;
                while(true)
                {
                    if(in.read(buf, 0, 1)<0)
                    {
                        // error
                        System.out.println("error 1");
                        break; 
                    }
                    if(buf[0] == ' ')break;
                    filesize = filesize * 10L +(long)(buf[0]-'0');
                }
                
                String file = null;
                for(int i = 0;; i++)
                {
                    in.read(buf, i, 1);
                    if(buf[i] == (byte)0x0a)
                    {
                        file = new String(buf, 0, i);
                        break;
                    }
                }
                
                buf[0] = 0; out.write(buf, 0, 1); out.flush();
                
                fos = new FileOutputStream(prefix == null ? lfile : prefix + file);
                
                int foo;
                
                while(true)
                {
                    if(buf.length < filesize) foo = buf.length;
                    else foo = (int)filesize;
                    foo = in.read(buf, 0, foo);
                    if(foo < 0)
                    {
                        // error 
                        System.out.println("error 2");
                        break;
                    }
                    fos.write(buf, 0, foo);
                    filesize -= foo;
                    if(filesize == 0L) break;
                }
                fos.close();
                fos = null;
                
                if(checkAck(in) != 0)
                {
                    System.out.println("error 3");
                    System.exit(0);
                }
                
                buf[0]=0; out.write(buf, 0, 1); out.flush();
            }
            channel.disconnect();
            session.disconnect();
        }
        finally
        {
            channel.disconnect();
            session.disconnect();
        }
    }

```

Thanks on advance.

---

### Post by dwhitney67 on 2012-08-07
Please mark this thread as SOLVED if you have found a solution.  Thanks.

---

