---
title: "Java DeSerialization"
date: 2007-02-28
forum: Programming Talk
---

### Post by phossal on 2007-02-28
I've created a Java HashMap like this:
```
[SIZE="1"]
public HashMap<String, HashMap<String, String>> new_data = new HashMap<String, HashMap<String, String>>();[/SIZE]
```

I've serialized it into a blob column of a MySQL table with a direct insert statement like so: (The simple table has an auto_increment id column, a blob column, and a date column)
```
sm.execute("insert into verify values (null, '"+new_data+"', now())");
```
It works. No errors. It's written fairly plainly in the DB. How do I get it back out?

---

### Post by ZylGadis on 2007-02-28
Check java.io.ObjectInputStream.

---

### Post by phossal on 2007-02-28
I can usually tell I'm asking the wrong question when I can't get an answer. I'm very familiar with the flavors of the OIS's. How do I pull my object out of the database though. Can you provide an example?

---

### Post by ZylGadis on 2007-02-28
The java.sql.ResultSet.getBinaryStream(..) methods return a binary stream. Wrap an OIS around it and you're done. There are also getBlob(..) methods, but you end up with the same thing in the end, so just get the IS right away.

---

### Post by phossal on 2007-02-28
Yeah. I need to see how to do what I outlined in my first post. Can you provide a working example?

---

### Post by lloyd mcclendon on 2007-03-01
i would not recommend storing it as a blob.  you really want to map the properties of the object to a table, this can be tedious, but it is the correct way.  hibernate handles maps pretty well - you could probably get your hands on a database diagram that correctly stores nested maps (i have done this), create the schema yourself and map it the correct way.  

or you could have some fun and learn hibernate.  but if this is the last time you'll be dealing with persisting object graphs to a relational db don't bother.  this example is very trivial, imagine something 10x as big and 5 times more complicated, hope you like unworkable sql and / or blobs.



i've never used serialization, but if i was going to i would start by doing,

```
public class SomeEntity implements Serializable  {
    public static final Long serialVersionUID = 1L; // increment this every single time you touch this file

    private Map<String, Map<String, String>> newData;

    public SomeEntity()  {
        newData = new HashMap<String, Map<String, String>>();
        // maybe something like 
        for (String key : someKnownKeySet)  {
             newData.put(key, new HashMap<String, String>());
        }
    }
}
```

then i would read this, it shoudl get you rolling, let me know what you end up doing i've been curious about serialization for other stuff

 [http://mindprod.com/jgloss/serialization.html](http://mindprod.com/jgloss/serialization.html)

---

### Post by phossal on 2007-03-01
I appreciate the responses, even if they didn't provide me with easy answers. As I mentioned in a previous post, I have experience with streams and serialization, but I had never taken the time (or needed) to funnel a byte[] into MySQL. 

My impression is that the solution I'm going to use is only necessary because I'm too lazy to design this part of my application correctly. It's analogous to those beginning web designers who think storing *images* in MySQL somehow solves this or that problem. It's almost never true. There is always a better, faster, cleaner way. In this case, though, I made a decision about how I want to deploy my application, and I still enjoy the benefits of it, and storing an object or two this way *does* work. 

Anyway, here is a working example. I'll include it in my threads at [phossal.com]("http://phossal.com/thread?view=702219643") eventually. MySQLJavaConnection is just a class I use to manage connecting to my database. I consider that a separate task, and there are at least two easy-to-find, *high-quality* tutorials available on the topic. I did go ahead and use the *blob* type, rather than invest any time doing other mapping. It just isn't necessary in this case.

```
import java.util.HashMap;

import java.io.*;
import java.sql.*;
import javax.swing.*;

import database.*;


public class PersistenceTesting  {
	
	public static void main(String args[]) {
		
		//GETTING AND STORING THE DATA OBJECTS
		MySQLJavaConnection my = new MySQLJavaConnection();
		
		
		try {
				
			/* Table Information:
			 * ---------------------------
			 * create table verify
			 * (
			 * row int not null auto_increment,
			 * primary key (row),
			 * name varchar(250),
			 * object mediumblob
			 * )
			 */
			
			
			//CREATE A SIMPLE OBJECT
			HashMap<String, HashMap<String, String>> x = new HashMap<String, HashMap<String, String>>();
			x.put("Key", new HashMap<String,String>());
			x.get("Key").put("Hex", "Reader");
			
	        // Serialize to a byte array
	        ByteArrayOutputStream bos = new ByteArrayOutputStream() ;
	        ObjectOutput out = new ObjectOutputStream(bos) ;
	        out.writeObject(x);
	        out.close();
	        byte[] buf = bos.toByteArray();
			
			
			//Delete everything from persist table so that testing is simple
	        my.sm.execute("delete from verify");
	        
			
		    //INSERT
			PreparedStatement p = my.con.prepareStatement("insert into verify values (null, null, ?, now())");
		    p.setObject(1, buf);
		    p.executeUpdate();

		    
		    
			
			//EXTRACT
			try {
				my.rs = my.sm.executeQuery("select object from verify");
				
				if (my.rs.next()) {
					buf = my.rs.getBytes(1);	
				}
				
				//Read In Object
				ObjectInput in = new ObjectInputStream(new ByteArrayInputStream(buf));
		        x = (HashMap<String, HashMap<String, String>>) in.readObject();
		        in.close();
		        
		        //Test Object, Launch Button
				JOptionPane.showMessageDialog(null, x.get("Key").get("Hex"));
				
			} catch (Exception E) {
				System.out.println("Exception: "+E);
			}
	       

			
		} catch (Exception E) {
			System.out.println("Outer Exception: "+E);
		}
	}
}
```

---

