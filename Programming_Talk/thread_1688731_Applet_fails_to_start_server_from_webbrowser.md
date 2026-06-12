---
title: "Applet fails to start server from webbrowser"
date: 2011-02-15
forum: Programming Talk
---

### Post by bcz on 2011-02-15
Hi all

My applet connects to a local server. If not found, it loads the server and retries the connection.

"java class" runs fine, but running in a browser using html fails to load server.  html works fine if server is already running.

I  am using the Runtime class to start the server.  Dont know if there is a recommended way of doing this


My client code and html is attached

Snippet to start server

```
SocketAddress sa;
        while(starting){
try{            link= new Socket("localhost",PORT);
                ta.append("Server connect on port "+PORT+"\n");
                starting=false;
}catch (Exception e){
                ta.append("Server not found\n");
                ta.append("Error: "+e+"\n");
                cnt++; if(cnt==3)return;
try{            ta.append("Starting Server\n");
                Runtime rt=Runtime.getRuntime();
                Process proc=rt.exec("java Misam");
try{            Thread.sleep(1000);
}catch (InterruptedException ie){ta.append(ie.getMessage()+"\n");}
}catch (Throwable t){ ta.append("Server started\n");}
                }

```

---

### Post by bcz on 2011-02-15
Files which should have been attached

---

### Post by t1497f35 on 2011-02-15
> "java class" runs fine, but running in a browser using html fails to load server.  html works fine if server is already running.It might be an applet security limitation. To get around any applet security limitation you have to sign the applet, how to do that - google.
Remember, when you do stuff from a typical Java Swing app (inside JFrame) you have one type of security (basically none), when in applet another (no file access, and who knows what else).
Check the java console or make your applet/app display a dialog displaying the error so that you know what type of error happened in your applet so you can make progress.

---

