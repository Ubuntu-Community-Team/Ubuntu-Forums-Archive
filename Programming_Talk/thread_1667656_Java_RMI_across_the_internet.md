---
title: "Java RMI across the internet"
date: 2011-01-15
forum: Programming Talk
---

### Post by PaulM1985 on 2011-01-15
Hi

I have set up a server using RMI.  I have been doing testing using my LAN, just using my local IP address.  My server has one simple function called connect().  Here are my server interface and server implementation:

Host interface:
```

package host;

import java.rmi.Remote;
import java.rmi.RemoteException;

/**
 *
 * @author paul
 */
public interface RMIHost extends Remote {

    public void connect() throws RemoteException;
}

```

HostImpl:
```

package host;

import java.rmi.RemoteException;
import java.rmi.server.UnicastRemoteObject;

/**
 *
 * @author paul
 */
public class HostImpl extends UnicastRemoteObject implements RMIHost {

    public HostImpl()
    {
        System.out.println("Create host");
    }

    public void connect() throws RemoteException
    {
        System.out.println("Connected");
    }
}

```

main:
```

package host;

import java.rmi.registry.LocateRegistry;
import java.rmi.registry.Registry;

/**
 *
 * @author paul
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here

        RMIHost host;
        Registry registry;

        try            // try to create registry
        {
            System.setProperty("java.rmi.server.hostname", [My_QUESTION]);
            registry = LocateRegistry.createRegistry(Registry.REGISTRY_PORT);
            System.out.println("Registry created.");
        }
        catch(Exception e)
        {
            System.out.println("Registry not created: " + e.getMessage( ));
            return;
        }

        try            // try to create remote object
        {
            host = new HostImpl( );
            System.out.println("Host created.");
        }
        catch(Exception e)
        {
            System.out.println("Host not created: " + e.getMessage( ));
            return;
        }
        
        try            // try to bind name in registry
        {
            registry.bind("my_host", host);
            System.out.println("Host registered.");
        }
        catch(Exception e)
        {
            System.out.println("Host not registered: " + e.getMessage( ));
            return;
        }
    }
}

```

My connection from the client program:
```

private void tempGetHost()
    {
        Registry registry;
        try                // try to locate registry
        {
            registry = LocateRegistry.getRegistry(IP_ADDRESS, Registry.REGISTRY_PORT);
            System.out.println("Registry stub created.");
        }
        catch(Exception e)
        {
            System.out.println("Registry stub not created: " + e.getMessage( ));
            return;
        }

        try                // try to look up the remote object
        {
            mHost = (RMIHost) registry.lookup("my_host");
            System.out.println("Host found.");
        }
        catch(Exception e)
        {
            System.out.println("Engine not found: " + e.getMessage( ));
            return;
        }

        try
        {
            mHost.connect();
        }
        catch (RemoteException re)
        {
            System.out.println("Could not connect");
        }
    }

```

In the client code I am using my external IP address to get the registry.  

I now want to be able to get RMI working across the internet, but I don't know what I need to set as "java.rmi.server.hostname".  When I set the host name to be the IP address on my local network, a connection from a computer on my local network works fine, but a connection from a computer across the internet at the call of connect():
```

        try
        {
            mHost.connect();
        }
        catch (RemoteException re)
        {
            System.out.println("Could not connect");
        }

```

However, when I set the hostname to be my external IP address, a computer on my local network fails to even get the Host from the registry:
```

        try                // try to look up the remote object
        {
            mHost = (Host) registry.lookup("my_host");
            System.out.println("Host found.");
        }
        catch(Exception e)
        {
            System.out.println("Engine not found: " + e.getMessage( ));
            return;
        }

```

whereas the computer across the internet can lookup the host, but again fails to call the connect method.

Does anyone know where I may be going wrong and how I should fix this?  I am assuming it is something to do with the setting of the host name, but I don't know what it should be.

Any help would be massively appreciated.

Paul

EDIT:  I have set up port forwarding on my router.  I guess this is proved by the fact the the computer across the internet could get the RMIHost from the registry.

---

### Post by PaulM1985 on 2011-01-15
Hi

After some extensive googling I have managed to solve it.  I have set my hostname to be my external IP address.  The thing I needed to do was in the constructor of my remote object.  I needed to call the constructor on the parent class passing in the port I wanted the remote object to be created for, so:
```

package host;

import java.rmi.RemoteException;
import java.rmi.server.UnicastRemoteObject;

public class HostImpl extends UnicastRemoteObject implements RMIHost {

    public HostImpl()
    {
        System.out.println("Create host");
    }

    public void connect() throws RemoteException
    {
        System.out.println("Connected");
    }
}

```

becomes:
```

package host;

import java.rmi.RemoteException;
import java.rmi.server.UnicastRemoteObject;

public class HostImpl extends UnicastRemoteObject implements RMIHost {

    public HostImpl()
    {
        **super(Registry.REGISTRY_PORT);**
        System.out.println("Create host");
    }

    public void connect() throws RemoteException
    {
        System.out.println("Connected");
    }
}

```

I hope this helps other people out in the future.

Paul

---

### Post by samarth3692 on 2011-04-28
Server code 
here server.config_address is set to my external ip
SERVER:
[PHP]public class Server extends Thread
{
 public static void Start() throws IOException
  {
   running = false;             

try{
   System.setProperty("java.rmi.server.hostname",Config.server_address);
   if (Config.ssl_enabled && Config.multihomed_enabled)
  serverImpl = new ServerImpl(new MultihomeRMIClientSocketFactory(new SslRMIClientSocketFactory(),
                     InetAdrUtility.getLocalIPAdresses()),new SslRMIServerSocketFactory(null, null, true));                         

  //An SslRMIClientSocketFactory instance is used by the RMI runtime in order to obtain client sockets for RMI calls via SSL.
 else if (Config.ssl_enabled && !Config.multihomed_enabled)
   serverImpl = new ServerImpl(new SslRMIClientSocketFactory(),new SslRMIServerSocketFactory(null, null, true));                    

 else if (!Config.ssl_enabled && Config.multihomed_enabled)
   serverImpl = new ServerImpl(new MultihomeRMIClientSocketFactory(null,InetAdrUtility.getLocalIPAdresses()), null);                       

 else if (!Config.ssl_enabled && !Config.multihomed_enabled)
   serverImpl = new ServerImpl();                        

 if (Config.ssl_enabled)
   registry = LocateRegistry.createRegistry(Config.server_port,new SslRMIClientSocketFactory(),
                       new SslRMIServerSocketFactory(null, null, true));
// Creates and exports a Registry instance on the local host that uses custom socket factories for communication with that instance.
  else
   registry = LocateRegistry.createRegistry(Config.server_port); 

    registry.rebind("ServerImpl", serverImpl);
   } catch (Exception e)
        {
            e.getStackTrace();
            Stop();          
          JOptionPane.showMessageDialog(null, e.getMessage(), "Error !!",JOptionPane.ERROR_MESSAGE); 
            return;
        }   
        System.out.println(getStatus());
        running = true;
        clipbrdUtility = new ClipbrdUtility();
        String currentDirectory = null;
        currentDirectory = new File(".").getCanonicalPath() + File.separatorChar;
        uploadingFolder = currentDirectory;
       }    [/PHP]

interface Implementation:
using custom socket factort
As u mentioned in ur post..i have called the constructor 
[PHP]
public class ServerImpl extends UnicastRemoteObject implements ServerInterface
{        
    public ServerImpl () throws RemoteException  {
     super(Config.server_port);

    }
    public ServerImpl (RMIClientSocketFactory csf,RMIServerSocketFactory ssf) throws RemoteException
    {

      super(0, csf, ssf);
    }   
    [/PHP]

by doing so it is not allowing rmi over internet or lan

---

