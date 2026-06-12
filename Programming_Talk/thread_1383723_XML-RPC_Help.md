---
title: "XML-RPC Help"
date: 2010-01-17
forum: Programming Talk
---

### Post by Black Mage on 2010-01-17
I am having a  problem with a Java program that calls a Perl/CGI Script using XML-RPC, creates a hash and returns it. A simple example looks like this:

Perl Script:

```


sub createHash{

%hashTable = ();

$hashTable{"first"} = 1; # inserts a new hash table entry with key="first" and value=1
$hashTable{"second"} = 2; # new entry with key="second" and value=2

return %hashTable;

}#end createHash


```

Java Program

```


public void getHash(){
		
		HashMap hashmap=new HashMap();
		Vector params = new Vector();
		
		//Create Variables
    	try {
			XmlRpcClient xmlrpc = new XmlRpcClient(SERVER_URL);
			
			//Set Strings
        	        String methodName = "MyProgram.createHash";
           
            
           
        	System.out.println(xmlrpc.execute( methodName, params));
                //The line below is commented out because it throws an error
                //hashmap=(HashMap) xmlrpc.execute( methodName, params);
		
    	
    	
    	} catch (MalformedURLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (XmlRpcException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
    	
    	
    	

	}//end class


```


The problems is this, when I perform a System.out.print the return hash created in Perl, is only prints out the last value. When I cast the return value to a Java Hash, it throws a string execption. So this means the return value is considered a string and not a hash map or a hash table.

So how do I return a hash table or return multiple values from a perl program?

---

### Post by Black Mage on 2010-01-18
Anyone have any ideas at all? Suggestions?

---

