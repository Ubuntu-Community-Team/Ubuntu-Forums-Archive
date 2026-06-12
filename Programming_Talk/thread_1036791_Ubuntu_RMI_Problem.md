---
title: "Ubuntu RMI Problem"
date: 2009-01-11
forum: Programming Talk
---

### Post by Black Mage on 2009-01-11
I have an RMI client/server set up that looks like this:

Server
```

public class Driver {
	
	public static void main(String[] args){
		
		System.getProperties().setProperty("java.security.policy", "no.policy");
		System.getProperties().setProperty("java.rmi.server.hostname", "65.x.x.x");
		if(System.getSecurityManager()==null){
    		RMISecurityManager security=new RMISecurityManager() ;
    		System.setSecurityManager(security);
		}
		
		new PRFromDBServer();
	}

}//end driver class

public class PRFromDBServer implements PRFromDatabaseInterface {
   private int      port;
    private String   ipAddress;
    private Registry registry;    
    
    public PRFromDBServer() {
    	// super();
    	 port=1099;
          
          try {
        	 //get the address of this host.
        	 ipAddress= (InetAddress.getLocalHost()).toString();
			 
        	 //PRFromDBServer engine=new PRFromDBServer();
	         PRFromDatabaseInterface stub=(PRFromDatabaseInterface)UnicastRemoteObject.exportObject(this, 1081);
	         
	         // create the registry and bind the name and object.
	         registry = LocateRegistry.createRegistry(port);
	         registry.rebind("prFromDBServer", stub);
	         
	         System.out.println("IP:"+ipAddress+" Port:"+port);
		} catch (UnknownHostException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (RemoteException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}   
    }
..............
}//end Server Class


```

And my Client

```

public class RmiClient {
    static public void main(String args[])
    {
    PRFromDatabaseInterface rmiServer;
       Registry registry;
       String serverAddress="www.myhostname.com";
       int serverPort=1099;
       String text="Sample Text";
       System.out.println("sending "+text+" to "+serverAddress+":"+serverPort);
       System.getProperties().setProperty("java.security.policy", "client.policy");
       //if (System.getSecurityManager() == null) {
         //  System.setSecurityManager(new SecurityManager());
       //}
     
       try{
           // get the “registry”
             registry=LocateRegistry.getRegistry(serverAddress, serverPort);
           // look up the remote object
          //LocateRegistry.g
           rmiServer= (PRFromDatabaseInterface)(registry.lookup("prFromDBServer"));
           // call the remote method
           System.out.println("Result: "+rmiServer.attemptLogin("bob@gmail.com", "passwoes"));
         
       }
       catch(RemoteException e){
           e.printStackTrace();
       }
       catch(NotBoundException e){
           e.printStackTrace();
       }
    }
}

```

So here is the problem I am having. The RMIclient works perfect with the server from behind the firewall on the same network....no problems. But when I take it to a different network or out from behind the firewall, there is problems.

The firewall does have port 1099 open and I can ping my server with no problem. All the other open ports work too. I think it is getting behind the firewall because I can error on the client side saying:
{code}
java.rmi.ConnectException: Connection refused to host: 65.x.x.x; nested exception is: java.net.ConnectException: Operation timed out
{code}

65.x.x.x is not at all defined in the rmiClient, so it has to be getting it from the server, because that is the server ip address.

So does anyone have any possible ideas to what is wrong?

---

