---
title: "Creating CLI for java daemon"
date: 2012-02-10
forum: Programming Talk
---

### Post by pcman312 on 2012-02-10
I have a java daemon that is running constantly. It periodically gets data from other sources and process them autonomously. I would like to create a command line interface for the application that I can start up at any time while the daemon is running. I'd prefer to accomplish this without spawning a new JVM if possible.

I do have some ideas in mind, but I wanted to get some other opinions too.

---

### Post by r-senior on 2012-02-10
My first thought would be to use a java.net.ServerSocket to listen for connections on some port. When connection is made, interpret simple commands delivered by the admin tool and deliver status information in response.

So you'd have an admin tool with an interface like this:

```
$ java mypackage.AdminTool
> status
Active
> shutdown
Shutting down ...
OK
> quit
$
```

It wouldn't be that much of an extension to get such a listener interpreting simple HTTP requests and return HTML pages as responses. You wouldn't have to write the command line tool then - it would have a web interface accessible from a browser. You'd be able to bookmark the daemon, print response pages, etc.

For example, if you typed [http://localhost:12345/status](http://localhost:12345/status) into a web browser and had the daemon listening on port 12345, it would get an HTTP string like this:

```
GET /status HTTP/1.1
```

Take the parts you need and respond accordingly. You could even use a template engine like Velocity to format the responses if you went that route.

---

### Post by pcman312 on 2012-02-10
> **r-senior said:**
> My first thought would be to use a java.net.ServerSocket to listen for connections on some port. When connection is made, interpret simple commands delivered by the admin tool and deliver status information in response.

So you'd have an admin tool with an interface like this:

```
$ java mypackage.AdminTool
> status
Active
> shutdown
Shutting down ...
OK
> quit
$
```

It wouldn't be that much of an extension to get such a listener interpreting simple HTTP requests and return HTML pages as responses. You wouldn't have to write the command line tool then - it would have a web interface accessible from a browser. You'd be able to bookmark the daemon, print response pages, etc.

For example, if you typed [http://localhost:12345/status](http://localhost:12345/status) into a web browser and had the daemon listening on port 12345, it would get an HTTP string like this:

```
GET /status HTTP/1.1
```

Take the parts you need and respond accordingly. You could even use a template engine like Velocity to format the responses if you went that route.
I love this idea. My long term goal is to be able to have a website that would be able to manage parts of the daemon while it runs.
Before I start asking questions I should mention that I have a bunch of experience with RMI, though not much with socket programming. I can look up some tutorials on the basics and get my bearings pretty quickly that way.

How do I get the daemon to respond to the HTTP requests? I want the ability to say something like:
```
http://localhost:12345/updateConfig
```
it would go and update the configuration, and then another call:
```
http://localhost:12345/doSomething
``` with some POST or GET variable(s) would have the daemon perform some other action based on the input variables. I have done a little bit of ajax, so I'm assuming it's going to be something similar to that.

---

### Post by r-senior on 2012-02-11
OK, here's a little proof of concept ...

*DataCollector.java*
```
package com.mypackage;

import java.util.Properties;

/** 
 * The public interface to the data collector daemon
 */
public interface DataCollector {
	public Properties getProperties();
}

```

*Daemon.java*
```
package com.mypackage;

import java.util.Properties;

public class Daemon implements DataCollector, Runnable {

	private Properties properties; 
	
	public static void main(String[] args) {
		Runnable daemon = new Daemon();
		daemon.run();
	}

	public void run() {
		// Spawn the admin listener thread to listen for admin requests
		Thread adminListener = new AdminListener(this);
		adminListener.start();
		
		// Start doing the main work in the main thread. This properties
		// object represents the collected data. Obviously this would be
		// in a loop, doing its thing. I've ignored synchronization but
		// that would be essential.
		System.out.println("Starting data collection ...");
		properties = System.getProperties();
	}
	
	public Properties getProperties() {
		return properties;
	}
	
}

```

*AdminLIstener.java*
```
package com.mypackage;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.net.InetAddress;
import java.net.ServerSocket;
import java.net.Socket;

public class AdminListener extends Thread {

	// You'd need to check that nothing else is listening on this
	// arbitrary port number, e.g. netstat -ln | grep 12345
	private static final int PORT = 12345;
	
	// The data collector is running as the main thread. This
	// reference allows us to access its properties.
	private DataCollector dataCollector;
	
	public AdminListener(DataCollector dataCollector) {
		this.dataCollector = dataCollector;
	}
	
	public void run() {
		System.out.println("Admin Listener starting ...");
		
		// The new try-with-resources block in Java 1.7 automatically
		// closes the resource that it opened :)
		try (ServerSocket serverSocket = new ServerSocket(PORT)) {
			while (true) {
				acceptConnections(serverSocket);
			}
		}
		catch (IOException e) {
			System.err.println("Failed to start listener");
		}
	}

	private void acceptConnections(ServerSocket serverSocket) throws IOException {
		try (Socket socket = serverSocket.accept()) {
			
			// If I wanted a multi-threaded server I would have to spawn
			// another thread to deal with the request and go straight back
			// to accepting connections. But this is single-threaded, i.e.
			// it only allows one connection to the admin listener.
			
			InetAddress client = socket.getInetAddress();
			System.out.println("Accepted connection from " + client.getHostAddress());
	
			try (BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()))) {
				try (PrintWriter out = new PrintWriter(new OutputStreamWriter(socket.getOutputStream()))) {
					doResponse(in, out);
				}
			}
		} // Sockets and streams close automatically here
	}

	private void doResponse(BufferedReader in, PrintWriter out) throws IOException {
		String request = in.readLine();
		if (request != null) {
			
			// Send out the HTTP response line and headers to make the browser happy
			out.println("HTTP/1.1 200 OK");
			out.println("Content-Type: text/html");
			out.println(); // Blank line to separate header and content
			
			out.println("<html><head><title>Admin</title></head><body>");
			out.printf("<h1>%s</h1>", request);
			
			// This represents getting data from the collector.
			out.println("<p><b>System information:</b></p>");
			out.println("<span style=\"color: #800000\"><ul>");
			out.printf("<li>%s</li>", dataCollector.getProperties().get("java.version"));
			out.printf("<li>%s</li>", dataCollector.getProperties().get("java.vendor"));
			out.println("</ul></span>");
			
			out.println("</body>");
		}
	}
	
}

```

It's all relatively simple stuff. Create a project with those classes in a package com.mypackage, run the Daemon class and connect with a web browser to [http://localhost:12356/](http://localhost:12356/). Try other URLs under this base, e.g. [http://localhost:12345/command](http://localhost:12345/command). (See attachment).

I've used the new try-with-resources blocks in Java 1.7, so you'll need JDK1.7. I've done nothing with synchronization, which would be essential.

Apart from generating an HTML response, this is all exactly the same code as you'd use for creating the command-line interface. But in that case, you'd have to write the command line tool yourself.

The doResponse() method will get messy really quickly so organising that needs some thought when you start dealing with multiple commands. But ...

... I am conscious that I've started writing the bare bones of a web application server here. There will be a point where, if this gets too complex, you'd be better off making the whole thing a web service and running it on Apache Tomcat or similar.

Interesting project though. Kept me amused this morning. :)

---

### Post by pcman312 on 2012-02-11
Thanks a lot r-senior! This is exactly what I was hoping for. I should be able to piece together the rest of it from this.

Again, thanks!

---

### Post by pcman312 on 2012-02-11
For anyone who is looking at this thread and using Java 1.6 (I am, and I tried using 1.7 in eclipse, but it didn't like it and I didn't want to go down that rabbit hole right now), here is a version of the AdminListener that works in 1.6.

There are some extra print statements, and I added a null request line in the doResponse() method as well.

I should note that when I ran it without doing the close() method on the socket, it never returned back to the browser, so it just sat there spinning. Java 1.7 might fix this problem.

```

package com.mypackage;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.net.InetAddress;
import java.net.ServerSocket;
import java.net.Socket;

public class AdminListener extends Thread
{
	
	// You'd need to check that nothing else is listening on this
	// arbitrary port number, e.g. netstat -ln | grep 12345
	private static final int	PORT	= 12345;
	
	// The data collector is running as the main thread. This
	// reference allows us to access its properties.
	private DataCollector		dataCollector;
	
	public AdminListener(DataCollector dataCollector)
	{
		this.dataCollector = dataCollector;
	}
	
	public void run()
	{
		System.out.println("Admin Listener starting ...");
		
		// The new try-with-resources block in Java 1.7 automatically
		// closes the resource that it opened :)
		try
		{
			ServerSocket serverSocket = new ServerSocket(PORT);
			while (true)
			{
				acceptConnections(serverSocket);
			}
		}
		catch (IOException e)
		{
			System.err.println("Failed to start listener");
		}
	}
	
	private void acceptConnections(ServerSocket serverSocket) throws IOException
	{
		System.out.println("acceptConnections()");
		Socket socket = null;
		try
		{
			System.out.println("Socket accept");
			socket = serverSocket.accept();
			System.out.println("Socket accepting");
			
			// If I wanted a multi-threaded server I would have to spawn
			// another thread to deal with the request and go straight back
			// to accepting connections. But this is single-threaded, i.e.
			// it only allows one connection to the admin listener.
			
			InetAddress client = socket.getInetAddress();
			System.out.println("Accepted connection from " + client.getHostAddress());
			
			BufferedReader in = null;
			PrintWriter out = null;
			try
			{
				in = new BufferedReader(new InputStreamReader(socket.getInputStream()));
				try
				{
					out = new PrintWriter(new OutputStreamWriter(socket.getOutputStream()));
					System.out.println("doResponse()");
					doResponse(in, out);
					System.out.println("Done with doResponse()");
				}
				catch (Exception e)
				{
					e.printStackTrace();
				}
			}
			catch (Exception e)
			{
				e.printStackTrace();
			}
			finally
			{
				in.close();
				in = null;
				
				out.close();
				out = null;
			}
		}
		catch (Exception e)
		{
			e.printStackTrace();
		}
		finally
		{
			socket.close();
			socket = null;
		}
		
		System.out.println("Finished with acceptConnections()");
	}
	
	private void doResponse(BufferedReader in, PrintWriter out) throws IOException
	{
		System.out.println("doResponse() starting");
		String request = in.readLine();
		if (request != null)
		{
			System.out.println("Request is not null");
			
			// Send out the HTTP response line and headers to make the browser happy
			out.println("HTTP/1.1 200 OK");
			out.println("Content-Type: text/html");
			out.println(); // Blank line to separate header and content
			
			out.println("<html><head><title>Admin</title></head><body>");
			out.printf("<h1>%s</h1>", request);
			
			// This represents getting data from the collector.
			out.println("<p><b>System information:</b></p>");
			out.println("<span style=\"color: #800000\"><ul>");
			out.printf("<li>%s</li>", dataCollector.getProperties().get("java.version"));
			out.printf("<li>%s</li>", dataCollector.getProperties().get("java.vendor"));
			out.println("</ul></span>");
			
			out.println("</body>");
			out.flush();
		}
		else
		{
			System.out.println("Request is null");
			
			out.println("HTTP/1.1 200 OK");
			out.println("Content-Type: text/html");
			out.println(); // Blank line to separate header and content
			
			out.println("<html><head><title>Admin</title></head><body>");
			out.printf("<h1>%s</h1>", request);
			
			// This represents getting data from the collector.
			out.println("<p><b>System information:</b></p>");
			out.println("<span style=\"color: #800000\"><ul>");
			out.println("No arguments");
			out.println("</ul></span>");
			
			out.println("</body>");
			out.flush();
		}
		
		System.out.println("doResponse() done");
	}
}
```

---

### Post by r-senior on 2012-02-11
I'm basically using Eclipse. Actually it's SpringSource Tool Suite, which is Eclipse Indigo with Spring plugins.

Anyway, no matter. Yes, with Java 1.6 you need to close the streams and sockets to flush the output to the browser. That's what it expects. The Java 1.7 construct automatically closes the streams and socket however the block ends.

Apart from playing with Java 1.7 this morning, I also had a quick play with Apache Velocity again and I think it would be useful. Writing out HTML using println statements gets messy after a while.

[http://www.javaworld.com/javaworld/jw-12-2001/jw-1228-velocity.html](http://www.javaworld.com/javaworld/jw-12-2001/jw-1228-velocity.html)
[http://velocity.apache.org/engine/devel/index.html](http://velocity.apache.org/engine/devel/index.html)

---

### Post by pcman312 on 2012-02-11
> **r-senior said:**
> I'm basically using Eclipse. Actually it's SpringSource Tool Suite, which is Eclipse Indigo with Spring plugins.

Anyway, no matter. Yes, with Java 1.6 you need to close the streams and sockets to flush the output to the browser. That's what it expects. The Java 1.7 construct automatically closes the streams and socket however the block ends.

Apart from playing with Java 1.7 this morning, I also had a quick play with Apache Velocity again and I think it would be useful. Writing out HTML using println statements gets messy after a while.

[http://www.javaworld.com/javaworld/jw-12-2001/jw-1228-velocity.html](http://www.javaworld.com/javaworld/jw-12-2001/jw-1228-velocity.html)
[http://velocity.apache.org/engine/devel/index.html](http://velocity.apache.org/engine/devel/index.html)
Luckily for this particular application, very little needs to be returned from the daemon back to the web layer. Just some acknowledgement that it received the command and that it processed correctly, so sending back complicated HTML is not an issue here.

I am having an issue when I try to connect using jquery though.

Here's my code:

AdminListener.java (very little changed here from the previous post)
```

package com.mypackage;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.net.InetAddress;
import java.net.ServerSocket;
import java.net.Socket;

public class AdminListener extends Thread
{
	
	// You'd need to check that nothing else is listening on this
	// arbitrary port number, e.g. netstat -ln | grep 12345
	private static final int	PORT	= 12345;
	
	// The data collector is running as the main thread. This
	// reference allows us to access its properties.
	private DataCollector		dataCollector;
	
	public AdminListener(DataCollector dataCollector)
	{
		this.dataCollector = dataCollector;
	}
	
	public void run()
	{
		// The new try-with-resources block in Java 1.7 automatically
		// closes the resource that it opened :)
		try
		{
			ServerSocket serverSocket = new ServerSocket(PORT);
			while (true)
			{
				acceptConnections(serverSocket);
			}
		}
		catch (IOException e)
		{
			System.err.println("Failed to start listener");
		}
	}
	
	private void acceptConnections(ServerSocket serverSocket) throws IOException
	{
		Socket socket = null;
		try
		{
			socket = serverSocket.accept();
			
			// If I wanted a multi-threaded server I would have to spawn
			// another thread to deal with the request and go straight back
			// to accepting connections. But this is single-threaded, i.e.
			// it only allows one connection to the admin listener.
			
			InetAddress client = socket.getInetAddress();
			
			System.out.println("Received request from " + client.getHostAddress());
			
			BufferedReader in = null;
			PrintWriter out = null;
			try
			{
				in = new BufferedReader(new InputStreamReader(socket.getInputStream()));
				try
				{
					out = new PrintWriter(new OutputStreamWriter(socket.getOutputStream()));
					doResponse(in, out);
				}
				catch (Exception e)
				{
					e.printStackTrace();
				}
			}
			catch (Exception e)
			{
				e.printStackTrace();
			}
			finally
			{
				in.close();
				in = null;
				
				out.close();
				out = null;
			}
		}
		catch (Exception e)
		{
			e.printStackTrace();
		}
		finally
		{
			socket.close();
			socket = null;
		}
	}
	
	private void doResponse(BufferedReader in, PrintWriter out) throws IOException
	{
		System.out.println("Accepted request");
		String request = in.readLine();
		if (request != null)
		{
			// Send out the HTTP response line and headers to make the browser happy
			out.println("HTTP/1.1 200 OK");
			out.println("Content-Type: text/html");
			out.println(); // Blank line to separate header and content
			
			out.println("<html><head><title>Admin</title></head><body>");
			out.printf("<h1>%s</h1>", request);
			
			// This represents getting data from the collector.
			out.println("<p><b>System information:</b></p>");
			out.println("<span style=\"color: #800000\"><ul>");
			out.printf("<li>%s</li>", dataCollector.getProperties().get("java.version"));
			out.printf("<li>%s</li>", dataCollector.getProperties().get("java.vendor"));
			out.println("</ul></span>");
			
			out.println("</body>");
			out.flush();
		}
		else
		{
			out.println("HTTP/1.1 200 OK");
			out.println("Content-Type: text/html");
			out.println(); // Blank line to separate header and content
			
			out.println("<html><head><title>Admin</title></head><body>");
			out.printf("<h1>%s</h1>", request);
			
			// This represents getting data from the collector.
			out.println("<p><b>System information:</b></p>");
			out.println("<span style=\"color: #800000\"><ul>");
			out.println("No arguments");
			out.println("</ul></span>");
			
			out.println("</body>");
			out.flush();
		}
		System.out.println("Finished request");
	}
}
```

index.html
```
<html>
<head>
    <title>Test Interface</title>
</head>
<body>
    Data: <input type="text" name="data_name" id="data_id" /><br />
    <input type="submit" id="submit" value="Submit" /><br />
    <div id="processing">Processing!</div><br><br>
    <div id="results" style="border: 1px solid black; min-height: 100px"></div>
    
    <script type="text/javascript" src="jquery-1.7.1.js"></script>
    <script type="text/javascript" src="ajaxSubmit.js"></script>
</body>
</html>
```

ajaxSubmit.js
```
$(document).ready(function(){
    $('#processing').hide(0);
    
    $('#submit').click(function() {
        $('#processing').fadeTo(500, 1.0);

        $.ajax({
            type: "POST",
            url: "http://localhost:12345/someCommand"
        }).done(function( msg ) {
            alert("Returned");
        });

        return false;
    });
});
```


When I click the submit button, the Processing div fades in as expected, the ajax call fires off, the server receives it (I see it in the console output from the daemon), but the done() function is never called. When I run it through firebug on FFX, it sees that the POST call was made, says 200 OK, and the line is in red. When I open it up for more details, the headers look correct, but there isn't anything under the HTML tab.

There are a couple of notes I'd like to make since I'm sure someone will wonder:
No, this is not for a class.
No, I'm not doing fully fleshed out Java right now (like closing the streams in a safe way), I'm just trying to get a proof of concept working.

---

### Post by r-senior on 2012-02-12
I don't know jQuery but my best suggestion is that the response only returns a Content-Type header. Browsers seem happy with that but maybe jQuery expects a Content-Length header? You'd probably have to assemble the response HTML into a string using a StringBuilder and get the length of its .toString() before printing it to the response writer?

I wonder if you should also make the server multi-threaded so it behaves more like a "normal" web server:

```

    while(true) {
        socket = serverSocket.accept();
        Thread t = new RequestProcessor(socket);
        t.start();
    }    

```

You'll need to rearrange things a bit. I'm not sure that will help, but it won't do any harm.

---

### Post by pcman312 on 2012-02-12
I posted the problem on the jquery forums and the suggestion I've seen is because it's doing a cross-domain call (even though it's on the same server). I'm doing some googling now to see if I can find a way around this.

As for the multithreading, I intend to add that in to the final product (seeing as it's already multithreaded), but for now it's unnecessary since I'm just trying to get the simple case to work properly.

---

### Post by pcman312 on 2012-02-12
Just wanted to give an update:

I adjusted my ajax call to this:
```
$.ajax({
    type : 'GET',
    url : '[http://www.mywebsite.com/path/to/ajax.php]',
    dataType: 'jsonp',
    jsonp: 'jsonp_callback',
    success : function(data, textStatus, jqXHR){
        alert("success!");
    },
    error : function(XMLHttpRequest, textStatus, errorThrown) {
        alert("error: " + ";;;;;text: " + textStatus + ";;;;;thrown: " + errorThrown);
    }
});
```

And I set up my website (unrelated to the java daemon) with a simple php script:
```
echo $_GET['jsonp_callback'] . "( {\"woo\":\"woo value\"} );";
```

Which resulted in a success. I'm adjusting my java daemon to return similarly.

With the daemon, I receive this request:
```
GET /somecommand?jsonp_callback=jQuery17108303754010703415_1329089911272&_=1329090470168 HTTP/1.1
```

So I need to return:
```
jQuery17108303754010703415_1329089911272( {"woo":"woo value"} );
```

Are there any simple libraries out there to parse the request into its various components? Particularly, I'm interested in separating it thusly:
```
GET
/somecommand
jsonp_callback=jQuery17108303754010703415_1329089911272
_=1329090470168
```
That way I can extract the specific URL that is being accessed (somecommand) and the arguments with it (jsonp_callback=... etc.)

I can manually split it out on my own, but why reinvent the wheel?

---

### Post by pcman312 on 2012-02-13
Update: I'm going to look into using Jersey/JAX-RS embedded within my daemon to handle the requests. I figure it's a safer approach then writing the web server myself which would be prone to failure. Why reinvent the wheel when you can use someone else's?

---

### Post by pcman312 on 2012-02-13
I set up a simple Jersey server and created a resource to run a command through to a simple daemon thread that I created. Unfortunately, because I can't seem to pass java objects to the constructor of the resource, I can't access the daemon thread(s) unless I make static calls to them. Is there a way that I can get around this necessity? Ideally, I'd like to be able to pass various Runnable classes (that are doing the work in the daemon) into the DaemonControlInterface and have that class call the various commands on the various other threads running in the daemon, with the various resource classes calling methods on the DaemonControlInterface class. If anyone knows of a better way to implement this, I'd probably prefer it over this.

Here's the code that I have:
Main.java:
```
package main;
import java.io.IOException;
import java.net.URI;

import javax.ws.rs.core.UriBuilder;

import org.glassfish.grizzly.http.server.HttpServer;

import daemon.Configuration;
import daemon.Daemon;
import com.sun.jersey.api.container.grizzly2.GrizzlyServerFactory;
import com.sun.jersey.api.core.PackagesResourceConfig;
import com.sun.jersey.api.core.ResourceConfig;

public class Main {

  private static URI getBaseURI() {
    return UriBuilder.fromUri("http://localhost/").port(9998).build();
  }

  public static final URI BASE_URI = getBaseURI();

  protected static HttpServer startServer() throws IOException {
    System.out.println("Starting grizzly...");
    ResourceConfig rc = new PackagesResourceConfig("resources");
    return GrizzlyServerFactory.createHttpServer(BASE_URI, rc);
  }

  public static void main(String[] args) throws IOException {
    Configuration conf = Configuration.getInstance();
    Daemon daemon = new Daemon(conf);
    Thread daemonThread = new Thread(daemon);
    daemonThread.start();
    
    HttpServer httpServer = startServer();
    System.out.println(String.format("Jersey app started with WADL available at "
        + "%sapplication.wadl\nTry out %shelloworld\nHit enter to stop it...", BASE_URI, BASE_URI));
    
    System.in.read();
    System.out.println("Stopping HTTP server...");
    httpServer.stop();
    System.out.println("Stopping daemon...");
    daemonThread.interrupt();
    try {
      daemonThread.join();
    } catch (InterruptedException e) {
      e.printStackTrace();
    }
    
    System.out.println("Goodbye");
  }
}
```

Daemon.java
```
package daemon;

public class Daemon implements Runnable {
  
  private Configuration conf;
  
  public Daemon(Configuration conf) {
    this.conf = conf;
  }
  
  @Override
  public void run() {
    System.out.println("Daemon thread starting");
    while (true) {
      try {
        String rawRefresh = conf.getProperty("refreshTime", "5000");
        int refresh = Integer.parseInt(rawRefresh);
        System.out.println("Sleeping for " + (refresh / 1000d) + " seconds");
        Thread.sleep(refresh);
      } catch (InterruptedException e) {
        System.out.println("Daemon interrupted!");
        break;
      }
    }
    System.out.println("Daemon thread finished");
  }
  
  public void refreshConfig() {
    Configuration.refreshConfig();
  }
}
```

RefreshConfigResource.java
```
package resources;

import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.Produces;

import daemon.DaemonControlInterface;

@Path("refreshConfig")
public class RefreshConfigResource {
  
  @GET
  @Produces("text/plain")
  public String refreshConfig() {
    DaemonControlInterface.refreshConfig();
    return "Configuration refreshed";
  }
}
```

DaemonControlInterface.java
```
package daemon;

public class DaemonControlInterface {
  public static void refreshConfig() {
    System.out.println("Control Interface: Refreshing Configuration...");
    Configuration.refreshConfig();
    System.out.println("Control Interface: Configuration Refreshed");
  }
  
  // Other commands to the daemon would go here
}
```

---

### Post by r-senior on 2012-02-14
This project has moved on a bit! ;)

Some ideas as alternatives ...

I wonder if, rather than writing your own server, albeit using the help of Grizzly, you'd be better off turning the project upside down and running your daemon inside a web application server, e.g. Tomcat, that delivers a web service/web application for monitoring?

You could use a ServletContextListener to control your daemon thread. This has to be registered in web.xml for the web application but it's just a one-liner: 

[php]public class DaemonControl implements ServletContextListener {

    private Thread daemonThread;

    /*
     * Runs when the web application starts up, e.g. when the 
     * application is deployed or when the server subsequently
     * starts up.
     */
    public void contextInitialized(ServletContextEvent event) {
        // Construct the daemon with a reference to the servlet
        // context, which can be used for communication between
        // your web service/application and the daemon. Access to
        // the servlet context would need to be synchronized 
        // because it is not inherently thread-safe.
        daemonThread = new DaemonThread(event.getServletContext());
        daemonThread.start();
    }

    /* 
     * Runs when the application is shutdown or undeployed, including
     * when the server is shut down
     */
    public void contextDestroyed(ServletContextEvent event) {
        event.getServletContext().setAttribute("STOP_DAEMON", true);
        // The daemon thread responds to interrupts and will check
        // the attribute in the servlet context, in this case detecting
        // that it needs to shut down gracefully.
        daemonThread.interrupt();
    }

}[/php]

The difference with this architecture is that the daemon is no longer autonomous. It is under the control of the web service/application. The daemon only runs while the application is deployed and active on the server and the server is running. But, assuming Tomcat is set up as a service, it does shutdown and restart gracefully on reboot.

Your web service/application has easy access to the servlet context, e.g. in servlets/JSP or frameworks that build on the Servlet API. The daemon has access as injected in the example above. (If you are not familiar with it, the servlet context is basically an application-global Map object).

You can still make use of the Jersey APIs if you want to create a web service accessible from elsewhere. Or you could just write the control and monitoring as a straight web application. Or both.

Alternatively you could use some other mechanism for communication, e.g. a database (embedded or external), with the web service/application picking up data and sending control instructions via database tables and interrupts.

Thinking slightly differently, perhaps your daemon doesn't have to be a daemon? Perhaps it could be a series of discrete scheduled jobs, controlled by something like Quartz (think cron for Java). I don't know enough about your daemon to know whether scheduled invocation suits.

What are your thoughts?

---

### Post by pcman312 on 2012-02-14
For the purposes of this daemon, it doesn't make sense to put it inside a webserver. I can't give you a lot of detail, but I'll give you a basic outline.

The daemon receives data from various other processes (which generate files that are consumed by the daemon). The daemon then parses the file, inserts the contents into the DB, and then runs some queries on the DB based on the information that was just entered. If the queries return the right data, various other actions will be performed based on that data. Emails then get sent out informing various people of the actions that were taken.

The daemon needs to be running as a daemon and not on a cron-like job because response time is paramount.

I'm thinking that setting up Jetty as a separate thread within the daemon will work just fine for this project. As you can see from the code I showed on my last post, I have it working such that I can access the /refreshConfig page, which will go and actually execute a command on the daemon. The problem right now is that the response classes are created and destroyed every time there is a call to that page, which means that I can't have a response class with a reference to a non-static class that I would pass in via a constructor or setter. It ends up meaning that I'm going to have to make some static references to concrete classes in the daemon, which I don't think will be too big of an issue given the way the daemon has been structured so far.

---

### Post by pcman312 on 2012-02-14
I'm running into an issue when I start up the thread containing the Jersey server:
```
Exception in thread "HTTP Server" java.lang.IllegalArgumentException: No container provider supports the type class org.glassfish.grizzly.http.server.HttpHandler
	at com.sun.jersey.api.container.ContainerFactory.createContainer(ContainerFactory.java:196)
	at com.sun.jersey.api.container.ContainerFactory.createContainer(ContainerFactory.java:134)
	at com.sun.jersey.api.container.grizzly2.GrizzlyServerFactory.createHttpServer(GrizzlyServerFactory.java:242)
	at web.WebControlServer.startServer(WebControlServer.java:52)
	at web.WebControlServer.run(WebControlServer.java:63)
	at java.lang.Thread.run(Thread.java:662)
```

---

### Post by pcman312 on 2012-02-14
Update: This appears to be some sort of environment issue between when I run the WebControlServer (where I have the code for the creation of the Jersey server) directly through eclipse vs packaging it through ant which the existing application is doing. I can run a copy of the code in eclipse without issue, but when I put it in with the existing application, I get the error from my previous post.

---

### Post by pcman312 on 2012-02-14
Update:

This post fixed the problem:
[http://stackoverflow.com/questions/1190646/ant-jar-files-and-class-path-oh-my](http://stackoverflow.com/questions/1190646/ant-jar-files-and-class-path-oh-my)

I added a classpath variable to the manifest in the jar that I am creating in the build.xml:

```
<manifestclasspath property="lib.list" jarfile="${dist}/lib/myprog.jar">   <---- this entire tag
    <classpath refid="build-classpath"/>
</manifestclasspath>

<jar jarfile="${dist}/lib/myprog.jar"
     basedir="${build}"
     includes="com/my/prog/**" >
    <manifest>
        <attribute name="Main-Class" value="com.my.prog.MyProg"/>
        <attribute name="Class-Path" value="${lib.list}"/>      <------- and this line referencing the manifestclasspath tag
    </manifest>
</jar>
```

---

### Post by pcman312 on 2012-02-14
Final(ish) update:
It works!  I set up the jetty server within the daemon and have it running on one machine, and am able to access the webserver from another machine on the same network. Baring any networking issues, this should work perfectly. Thanks for all of your help r-senior!

---

