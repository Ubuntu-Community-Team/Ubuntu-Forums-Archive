---
title: "Sockets Java ._. please help..."
date: 2010-09-26
forum: Programming Talk
---

### Post by Atzu on 2010-09-26
Hello everyone! 

I need help... I'm trying to make a Server that is able to accept more than 4 clients... for now i tried to make it work for 2 clients... and it doesn't work very well...
My problem is when i try to send data from client to server when the first client is connected i can send data without problems...

But when the second client connects... the first one can only send 1 string and won't receive the "Hello There" from Server but the server will print what i send from the client... after that then the server won't print on screen any message from the first client... and on the client side the "Hello There" Message won't print on screen... (The second client works without problems) Any help is really appreciated.

Thanks!!

This is what i have... 

On the server:

```
public static void InitServer(int Port) throws IOException{
		
		ServerSocket s = new ServerSocket(Port); 
		
		try{ 
		      while(true){ 
		    	  
		        Socket socket = s.accept(); 
		        try {
		        	new SocketClientes(socket); 
		        }
		        catch(IOException e) {
			          socket.close();
			    }
		      }
		    }
		finally{
		}
	}
```

And SocketClientes is:
```
class SocketClientes extends Thread {
	
  public Socket socket;
  public static BufferedReader in;
  public static PrintWriter out;
  
  
  public SocketClientes(Socket s) throws IOException {
	  
    socket = s; //El nuevo socket
    in = new BufferedReader(new InputStreamReader(socket.getInputStream())); 
    out = new PrintWriter(new BufferedWriter
    		(new OutputStreamWriter(socket.getOutputStream())), true); 
    
    System.out.println("Client Accepted: " + s);
    
    start();
   }
  
  public void run() {
	    try {
	      while (true) {  
	        String data = in.readLine(); 
	        if (datos.equals("End"))
	        	break;
	        System.out.println("Echoing: " + data); 
	        out.println("hello there");
	      }
	      System.out.println("closing...");
	    } 
	    catch (IOException e) {
	    } 
  }
}

```

On the client this is what i have:
```
public class Main {
	
	private static Socket socket;
	private static BufferedReader in;
	private static PrintWriter out;
	
	public static void Cliente(String Comp, int Port) throws IOException{
		try{
			socket = new Socket(Comp, Port);
			out = new PrintWriter(socket.getOutputStream(), true);
			in = new BufferedReader(new InputStreamReader(socket.getInputStream()));	
		}
		finally{
			System.out.println("Conenected.");
		}
	}
	
	public static void main(String[] args) throws IOException {
		String w = "";
		Scanner in1 = new Scanner(System.in);
		Cliente("Andres-PC", 4445);
		while(w != "exit"){
			w = in1.nextLine();
			out.println(w);
			System.out.println(in.readLine());
		}
	}
}
```

Most of the code is from here: 
[http://www.codeguru.com/java/tij/tij0165.shtml](http://www.codeguru.com/java/tij/tij0165.shtml)

---

### Post by Atzu on 2010-09-27
Solved it... i think...

I modified the run()... now it looks like this:

```
public void run(){
	    try{
	      while (true){
	    	in = new BufferedReader(new InputStreamReader(socket.getInputStream())); //Entrada de datos
	        String str = in.readLine();
	        if (str.equals("END"))
	        	break;
	        System.out.println("Echoing: " + str);
	        out = new PrintWriter(new BufferedWriter(new OutputStreamWriter(socket.getOutputStream())), true); //Salida de datos
	        out.println("Hello There");	
	      }
	      System.out.println("closing...");
	    }
	    catch (IOException e){
	    } 
	    finally{
	      try{
	        socket.close();
	      }
	      catch(IOException e){
	      }
	    }
  }
```

If anyone knows why this work please tell me because it was more like... trying and failing and not actually thinking :X

---

### Post by Some Penguin on 2010-09-27
Please avoid using static mutables.  Having multiple clients attempt to share the same input/output streams does not seem a good idea.

(not that static mutables are never the answer, but they are not to be used lightly)

---

