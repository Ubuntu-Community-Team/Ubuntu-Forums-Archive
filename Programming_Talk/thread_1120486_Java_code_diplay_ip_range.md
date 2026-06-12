---
title: "Java code diplay ip range"
date: 2009-04-09
forum: Programming Talk
---

### Post by Mia_tech on 2009-04-09
guys I'm working on an app in Java that display the number of ips for a given range of address like:
192.168.10.0 ---> 192.168.10.255

could someone give me a hand with this?


thanks

---

### Post by myrtle1908 on 2009-04-09
This is one way.  I have stolen parts of this code from various sources and added bits of my own here and there.

[PHP]
import java.util.*;
import java.net.*;

public class Test {
	public static void main(String[] args) {
		try {
			long start = host2long("192.168.1.164");
			long end = host2long("192.168.1.172");
			for (long i=start; i<=end; i++) {
				System.out.println(long2dotted(i));
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
	}


	public static long ip2long(InetAddress ip) {
		long l=0;
        byte[] addr = ip.getAddress();
		if (addr.length == 4) { //IPV4
			for (int i=0;i<4;++i) {
				l += (((long)addr[i] &0xFF) << 8*(3-i));
			}
		} else { //IPV6
			return 0;  // I dont know how to deal with these
		}
		return l;
	}


    public static long host2long(String host) {
		long ip=0;
		if (!Character.isDigit(host.charAt(0))) return -1;
		int[] addr = ip2intarray(host);
		if (addr == null) return -1;
		for (int i=0;i<addr.length;++i) {
			ip += ((long)(addr[i]>=0 ? addr[i] : 0)) << 8*(3-i);
		}
		return ip;
	}

	public static int[] ip2intarray(String host) {
		int[] address = {-1,-1,-1,-1};
		int i=0;
		StringTokenizer tokens = new StringTokenizer(host,".");
		if (tokens.countTokens() > 4) return null;
		while (tokens.hasMoreTokens()) {
			try {
				address[i++] = Integer.parseInt(tokens.nextToken()) & 0xFF;
			} catch(NumberFormatException nfe) {
				return null;
			}
		}
		return address;
	}

	public static String long2dotted(long address) {
		StringBuffer sb = new StringBuffer();
		for (int i = 0, shift = 24; i < 4; i++, shift -= 8) {
			long value = (address >> shift) & 0xff;
			sb.append(value);
			if (i != 3) {
				sb.append('.');
			}
		}
		return sb.toString();
	}

}
[/PHP]

Output ...

```

192.168.1.164
192.168.1.165
192.168.1.166
192.168.1.167
192.168.1.168
192.168.1.169
192.168.1.170
192.168.1.171
192.168.1.172

```

---

### Post by Mia_tech on 2009-04-09
cool!... seems to work fine, but do you mind explaining what this line do

[PHP]ip += ((long)(addr[i]>=0 ? addr[i] : 0)) << 8*(3-i);[/PHP]

also this method, I'm not very clear what is actually doing

[PHP]public static String long2dotted(long address) {
        StringBuffer sb = new StringBuffer();
        for (int i = 0, shift = 24; i < 4; i++, shift -= 8) {
            long value = (address >> shift) & 0xff;
            sb.append(value);
            if (i != 3) {
                sb.append('.');
            }
        }
        return sb.toString();
    }[/PHP]

---

### Post by sujoy on 2009-04-10
> **Mia_tech said:**
> cool!... seems to work fine, but do you mind explaining what this line do

[PHP]ip += ((long)(addr[i]>=0 ? addr[i] : 0)) << 8*(3-i);[/PHP]

also this method, I'm not very clear what is actually doing

[PHP]public static String long2dotted(long address) {
        StringBuffer sb = new StringBuffer();
        for (int i = 0, shift = 24; i < 4; i++, shift -= 8) {
            long value = (address >> shift) & 0xff;
            sb.append(value);
            if (i != 3) {
                sb.append('.');
            }
        }
        return sb.toString();
    }[/PHP]



[PHP]ip += ((long)(addr[i]>=0 ? addr[i] : 0)) << 8*(3-i);[/PHP]
this creates the network byte order from the ipaddress.
keep in mind that ip address in ipv4 is of 32bits with 4 octects of 8 bit each. so the max value in an octet is 2^8-1==255.

now addr[0] gives us the value of the first octet which is actually from bit 24 to 32. hence left shifting those 8 bits 24 places pushes it at its place filling up the right side with zeroes. similarly each octet is left shifted to its position, ie, addr[1] is left shifted 16 places to put it in 16 to 24 bit position and so on.

now while they are added keep in mind that it does not change the bits that are already set. after first iteration the last 24 bits are not set, after the second iteration the last 16bits are not set, similarly.. till at the last iteration where all the bits are set.


[PHP]public static String long2dotted(long address) {
        StringBuffer sb = new StringBuffer();
        for (int i = 0, shift = 24; i < 4; i++, shift -= 8) {
            long value = (address >> shift) & 0xff;
            sb.append(value);
            if (i != 3) {
                sb.append('.');
            }
        }
        return sb.toString();
    }[/PHP]

this just reverses the above process

by shifting the above byteorder 24 places to the right, you are placing the bits 24 to 32 at the position 0 to 8, where they are anded (logical &) with 0xff meaning all 8 bits set (that is 255), which returns the decimal equivalent of the first 8 bits discarding anything else.

similarly at the next iteration you shift the byteorder 16 places to the right thereby placing the bits 16 to 24 at the postion 0 to 8. which is again anded(logical &) with 0xff. see here only the decimal eqivalent value of the first 8 bits are returned since 0xff means only bits 0-8 are set rest are zero and we know 0 & anything = 0.

thus at each iterating we get the decimal equivalent for each octet starting from the 4th, which is just appended to a stringbuffer and a . attached to it to make it look like out regular ip address

see here for a bit more clarity, [http://stackoverflow.com/questions/491060/how-to-convert-standard-ip-address-format-string-to-hex-and-long](http://stackoverflow.com/questions/491060/how-to-convert-standard-ip-address-format-string-to-hex-and-long)

only instead of jumping across hex values we are directly shifting bits to get the byteorder.

---

### Post by Mia_tech on 2009-04-10
I came up with my own version... is much simpler, this display the class C network

[PHP]String strip = "10.200.50.0";//from ip
String strip2 = "10.200.50.50";//to ip
//spliting strings
String[] temp = strip.split("\\.");
String[] temp2 = strip2.split("\\.");
//array for storing the ip's
int[] ip = {0,0,0,0};
int[] ip2 = {0,0,0,0};
//parsing and adding ip to ip Array
for(int i = 0; i < temp.length; i++)
{
 ip[i] = Integer.parseInt(temp[i]);
 ip2[i] = Integer.parseInt(temp2[i]);
}
//displaying class C network
if((ip[3] != ip2[3]) && (ip[3] < ip2[3]))
{
for(int i = ip[3]; i <= ip2[3]; i++)
{
System.out.println(ip[0]+"."+ip[1]+"."+ip[2]+"."+i);
}
}[/PHP]

---

### Post by sujoy on 2009-04-11
yes thats simple indeed but works only for class C IPs, hence the complexity of the problem itself was reduced!

i went all the way through and made an over-engineered solution :P

```
package ipaddresses;

class IllegalIPAddressException extends Exception {

    private String exceptionData;

    public IllegalIPAddressException() {
        exceptionData = "Illegal IP Address";
    }

    public IllegalIPAddressException(String exData) {
        exceptionData = exData;
    }

    @Override
    public String toString() {
        return "IllegalIPAddressException [ " + exceptionData + " ]";
    }
}

// ipv6 to be implemented later
public class IPAddress {

    public enum IPType {

        ipv4, ipv6;
    }
    private IPType type;
    private String ipaddress;
    private long byteorder;

    public IPAddress() {
        type = IPType.ipv4;
        ipaddress = "0.0.0.0";
        byteorder = calcByteorder(type, ipaddress);

    }

    public IPAddress(IPType type, String ipaddress) throws IllegalIPAddressException {
        if (isValidIPAddress(type, ipaddress)) {
            this.type = type;
            this.ipaddress = ipaddress;
            this.byteorder = calcByteorder(this.type, this.ipaddress);
        } else {
            throw new IllegalIPAddressException();
        }
    }

    protected IPAddress(IPType type, String ipaddress, long byteorder) {
        this.type = type;
        this.ipaddress = ipaddress;
        this.byteorder = byteorder;
    }

    @Override
    public String toString() {
        return type + ": " + ipaddress;
    }

    final protected boolean isValidIPAddress(final IPType iptype, final String ip) {
        boolean returnValue = true;
        if (iptype == IPType.ipv4) {
            if (ip.matches("^[\\d]{1,3}\\.[\\d]{1,3}\\.[\\d]{1,3}\\.[\\d]{1,3}$")) {
                String[] segments = ip.split("\\.");
                for (String segment : segments) {
                    short octet = Short.valueOf(segment);
                    if (octet > 255 || octet < 0) {
                        returnValue = false;
                        break;
                    }
                }
            } else {
                returnValue = false;
            }
        }
        return returnValue;
    }

    final protected long calcByteorder(IPType iptype, String ip) {
        long bytecode = 0;
        if (iptype == IPType.ipv4) {
            String[] segments = ip.split("\\.");
            for (int i = 0; i < segments.length; i++) {
                bytecode += (Long.parseLong(segments[i])) << 8 * (3 - i);
            }
        }
        return bytecode;
    }

    final protected IPAddress nextIPAddress() throws IllegalIPAddressException {
        String ip = "";
        long bytecode = 0;
        if (type == IPType.ipv4) {
            bytecode = byteorder + 1;
            for (int i = 0, shift = 24; i < 4; shift -= 8, i++) {
                ip += ((bytecode >> shift) & 0xff) + (i < 3 ? "." : "");
            }

        } else {
            throw new IllegalIPAddressException("ipv6 not supported yet");
        }
        return new IPAddress(this.type, ip, bytecode);
    }

    final protected String nextIPAddress(IPType iptype, long bOrder) {
        String ip = "";
        if (iptype == IPType.ipv4) {
            long bytecode = bOrder + 1;
            for (int i = 0, shift = 24; i < 4; shift -= 8, i++) {
                ip += ((bytecode >> shift) & 0xff) + (i < 3 ? "." : "");
            }
        }
        return ip;
    }
}

```


```
package ipaddresses;

public class Main {

    public static void main(String[] args) throws IllegalIPAddressException {
        try {
            IPAddress startIP = new IPAddress(IPAddress.IPType.ipv4, "255.255.255.250");
            IPAddress ip = startIP;
            IPAddress endip = new IPAddress(IPAddress.IPType.ipv4, "0.0.0.10");

            while (!ip.toString().equals(endip.nextIPAddress().toString())) {
                System.out.println(ip);
                ip = ip.nextIPAddress();
            }
        } catch (IllegalIPAddressException ex) {
            ex.printStackTrace();
        }
    }
}
```

---

### Post by Mia_tech on 2009-04-12
> **sujoy said:**
> yes thats simple indeed but works only for class C IPs, hence the complexity of the problem itself was reduced!


well, I posted just the principle... doing it for class A and B.. just have to increment the number of nested for(loops) but instead of only incrementing the last octet or number, you would increment the 3 and 4 numbers for class B..... you get the idea

[PHP]else if((ip1[2] != ip2[2]) && (ip1[2] < ip2[2]))
{
  for(int i = ip1[2]; i <= ip2[2]; i++)
   {
    for(int j = 0; j <= 255; j++)
    {
      addr = ip1[0]+"."+ip1[1]+"."+i+"."+j;
      range.add(addr);
    }
  }
}[/PHP]

---

