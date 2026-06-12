---
title: "Java: jsch scp maintaining one session and one channel"
date: 2013-11-11
forum: Programming Talk
---

### Post by erotavlas on 2013-11-11
Hi,

I'm new in java and jsch. In general I send and I receive a lot of files via scp command and hence I need to speed up the scp file transfer. I'm using the following code took from the examples here [http://www.jcraft.com/jsch/examples/](http://www.jcraft.com/jsch/examples/). I'm able to use a single session but I cannot use a single channel. Is it possible to use one single channel for each command?

```

      JSch jsch=new JSch();
      Session session=jsch.getSession(user, host, 22);
 
      // username and password will be given via UserInfo interface.
      UserInfo ui=new MyUserInfo();
      session.setUserInfo(ui);
      session.connect();
 
      // exec 'scp -f rfile' remotely
      String command="scp -f "+rfile;
      Channel channel=session.openChannel("exec");
      ((ChannelExec)channel).setCommand(command);
 
      // get I/O streams for remote scp
      OutputStream out=channel.getOutputStream();
      InputStream in=channel.getInputStream();
 
      channel.connect();
 
      byte[] buf=new byte[1024];
 
      // send '\0'
      buf[0]=0; out.write(buf, 0, 1); out.flush();
 
      while(true){
    int c=checkAck(in);
        if(c!='C'){
      break;
    }
 
        // read '0644 '
        in.read(buf, 0, 5);
 
        long filesize=0L;
        while(true){
          if(in.read(buf, 0, 1)<0){
            // error
            break; 
          }
          if(buf[0]==' ')break;
          filesize=filesize*10L+(long)(buf[0]-'0');
        }
 
        String file=null;
        for(int i=0;;i++){
          in.read(buf, i, 1);
          if(buf[i]==(byte)0x0a){
            file=new String(buf, 0, i);
            break;
        }
        }
 
    //System.out.println("filesize="+filesize+", file="+file);
 
        // send '\0'
        buf[0]=0; out.write(buf, 0, 1); out.flush();
 
        // read a content of lfile
        fos=new FileOutputStream(prefix==null ? lfile : prefix+file);
        int foo;
        while(true){
          if(buf.length<filesize) foo=buf.length;
      else foo=(int)filesize;
          foo=in.read(buf, 0, foo);
          if(foo<0){
            // error 
            break;
          }
          fos.write(buf, 0, foo);
          filesize-=foo;
          if(filesize==0L) break;
        }
        fos.close();
        fos=null;
 
    if(checkAck(in)!=0){
      System.exit(0);
    }
 
        // send '\0'
        buf[0]=0; out.write(buf, 0, 1); out.flush();
      }
 
      session.disconnect();
 
      System.exit(0);
    }
    catch(Exception e){
      System.out.println(e);
      try{if(fos!=null)fos.close();}catch(Exception ee){}
    }
  }


```

Thank you

---

