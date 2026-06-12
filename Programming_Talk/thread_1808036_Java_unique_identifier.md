---
title: "Java unique identifier"
date: 2011-07-19
forum: Programming Talk
---

### Post by tyzoid on 2011-07-19
Hi all, I was wondering if there was a way for java to get a unique identifying string from any computer. I was thinking about doing this:

String UUID = (new NetworkInterface).toString();

I was wondering how often this might change on a computer (Going to use it for software licenses) and if there is a better way to do this.

BTW, I am going to hash the UUID later in the program...

Edit1: Didn't test the code, might not compile (just a brainstorm)

---

### Post by jmartrican on 2011-07-19
A good unique identifier is the MAC address and it does not change often, but it can if someone really wanted to change it.

---

### Post by unknownPoster on 2011-07-20
Java has a UUID class. Maybe it will meet your needs.

[http://download.oracle.com/javase/6/docs/api/java/util/UUID.html](http://download.oracle.com/javase/6/docs/api/java/util/UUID.html)

---

### Post by doas777 on 2011-07-20
well, the first question is how do you define "Computer"?
the NIC UUID is probably based on OS install, and thus may not be completely globally unique, and it does change across rebuilds, and perhaps even kernel installs.

Intel toyed with making a universal CPU identifier that would allow a motherboard/cpu combo to be uniquely id'd but there was huge outcry and they backed off. [http://bigbrotherinside.org/](http://bigbrotherinside.org/)
 
here is how MS defines a computer for activation:
[http://technet.microsoft.com/en-us/library/bb457054.aspx](http://technet.microsoft.com/en-us/library/bb457054.aspx)

---

### Post by tyzoid on 2011-07-21
Ok, Thank you for your suggestions, but I am having trouble with this piece of code.
```

    String getUUID(){
    	String UUID = "No_Mac_Addresss";
    	try {
    		NetworkInterface inter = NetworkInterface.getByInetAddress(InetAddress.getLocalHost());
		UUID = new String(inter.getHardwareAddress()); //NPE here
	} catch (Exception e) {
		e.printStackTrace();
	}
		
    	return UUID;
    }

```

I am receiving a NullPointerException where the //NPE here is

Any thoughts as what that might be caused by?

If it matters, I am on ubuntu 11.04 using the Sun java.

---

### Post by doas777 on 2011-07-21
> **tyzoid said:**
> Ok, Thank you for your suggestions, but I am having trouble with this piece of code.
```

    String getUUID(){
        String UUID = "No_Mac_Addresss";
        try {
            NetworkInterface inter = NetworkInterface.getByInetAddress(InetAddress.getLocalHost());
        UUID = new String(inter.getHardwareAddress()); //NPE here
    } catch (Exception e) {
        e.printStackTrace();
    }
        
        return UUID;
    }

```I am receiving a NullPointerException where the //NPE here is

Any thoughts as what that might be caused by?

If it matters, I am on ubuntu 11.04 using the Sun java.


well, looks like either 'inter' or 'getHardwareAddress' is\returns null. 
add an ifstatement to check that both exist before attempting to do anything with them that would trigger a nullref ex.

---

### Post by tyzoid on 2011-07-22
inter is null.

Here is the current code:

```

    String getUUID(){
    	String UUID = "No_Mac_Addresss";
    	try {
    		InetAddress addr = InetAddress.getLocalHost();
    		System.out.println(addr.getHostAddress());
    		NetworkInterface inter = NetworkInterface.getByInetAddress(addr);
    		if(inter == null){System.out.println("null");} else {System.out.println("not null");}
    		if(inter.isUp()){System.out.println("true");} else {System.out.println("false");} //NPE here
    		byte[] test = inter.getHardwareAddress();
		UUID = new String(test);
	} catch (Exception e) {
		e.printStackTrace();
	}
		
    	return UUID;
    }

```

Here is the output:
```

127.0.1.1
null
java.lang.NullPointerException
	at ***.***.***.***.***.getUUID(***.java:**)

```

I am getting the NPE where it is labled //NPE here

Can anyone think of a solution?

---

### Post by doas777 on 2011-07-22
well, don't run this line if inter is null:
```

byte[] test = inter.getHardwareAddress();


```

if inter is null, the method will never ever return anyway, and any attempt to access it will cause an Nullrefex.
you can:

[LIST]
[*]attempt to get the info by other means, or
[*]supply a safe default value for cases where the info is inaccessible, or
[*]throw the exception to the caller and leave remediation up to them
[/LIST]

---

### Post by doas777 on 2011-07-22
ok, this works for me:
```

import java.net.InetAddress;
import java.net.NetworkInterface;
public class Main {
    
    public static void main(String[] args){
        byte[] mac = null;
        InetAddress address = null;
        try {
            address = InetAddress.getLocalHost();
            NetworkInterface ni = NetworkInterface.getByInetAddress(address);
            mac = ni.getHardwareAddress();
        } catch (Exception e) {
            e.printStackTrace();
        }
        System.out.println(mac.toString());
    }
}

```but the differance I am noticing is that my pc is not returning 127.0.0.1 from getLocalHost(). for me it returns my hostname\192.168.68.69.
try changing 'System.out.println(addr.getHostAddress());' to 'System.out.println(addr.tostring());' and see if it returns 127.0.0.1.

if the address returned is 127.0.0.1, then the network interface returned will not be a physical interface, but the logical loopback interface. 
when I get my network interface, it is the one on my lan, id'd as eth5. that means that if the app is run with no lan network interface, it will always break there.

Note, I am running this on windows so that may change matters.

---

### Post by tyzoid on 2011-07-23
```

    String getUUID(){
    	String UUID = "No_Mac_Addresss";
    	try {
    		//InetAddress addr = InetAddress.getLocalHost();
    		InetAddress addr = InetAddress.getByAddress(new byte[]{(byte) 192, (byte) 168, 1, 101});
    		//System.out.println(addr.getHostAddress());
    		System.out.println(addr.toString());
    		NetworkInterface inter = NetworkInterface.getByInetAddress(addr);
    		if(inter == null){System.out.println("null");} else {System.out.println("not null");}
    		if(inter.isUp()){System.out.println("true");} else {System.out.println("false");}
    		//byte[] test = inter.getHardwareAddress();
		//UUID = new String(test);
    		UUID = inter.toString();
	} catch (Exception e) {
		e.printStackTrace();
	}
    	
	System.out.println(UUID);
    	return UUID;
    }

```

outputs:
```

/192.168.1.101
true
not null
name:wlan0 (wlan0)

```
No mac address there. I also tried to output 
```

new String(inter.getHardwareAddress());

```

and it outputted some question marks and a box.

Any reason this is not returning a mac address?

---

### Post by doas777 on 2011-07-24
the GetHardwareAddress() method returns a Byte array. despite being in hex when encoded as a string, the byte representation of them at the io level is not encoded.

so you need to encode your data before trying to use it as a string. the question marks you are seeing are value in the byte array that are not part of your default encoding set. 

try somthing like this:

```

String getUUID(){
    	String UUID = "No_Mac_Addresss";
    	try {
    		InetAddress addr = InetAddress.getByAddress(new byte[]{(byte) 192, (byte) 168, 1, 101});
    		System.out.println(addr.toString());
    		NetworkInterface inter = NetworkInterface.getByInetAddress(addr);
    		if(inter != null){
                     if(inter.isUp()){
                          UUID = "";
                          byte[] mac = inter.getHardwareAddress();
                          for (int i = 0; i < mac.length; i++) {
		               UUID += String.format("%02X%s", mac[i], (i < mac.length - 1) ? "-" : "");
	        	}
                     }
                }
        } catch (Exception e) {
		e.printStackTrace();
	}
	System.out.println(UUID);
    	return UUID;
    }
```

---

