---
title: "Java - Segmentation Fault"
date: 2008-12-30
forum: Programming Talk
---

### Post by sdhoigt on 2008-12-30
Hi,

I'm running 8.04 with all updates.  

I don't know what happened, but somehow my Java development environment became hosed.

I have some simple Java database code that *previously* worked.  Now it seg faults when I try to run it (still compiles though).

I've verified that the db is running and I can log in with the credentials used in the code.

```

import Java.sql.*;

public class SQLPlay {
	public static void main(String args[]) {
		try {
			Class.forName("com.mysql.jdbc.Driver");
			Connection con = DriverManager.getConnection
					   ( "jdbc:mysql://localhost:3306/JunkDB", "user","password");
						
			Statement stmt = con.createStatement();
			ResultSet rs = stmt.executeQuery("SELECT test_id, test_val FROM MyTable");
			while (rs.next()) {
				int i = rs.getInt("test_id");
				String s = rs.getString("test_val");
				System.out.println(i + " : " + s);
			}
		} catch( Exception e ) {
			e.printStackTrace();
		}
	}
}

```

If I comment out everything in the try block from the "Connection" line and down, it compiles, runs and does not seg fault (doesn't do much of course).

Also, if I try to deploy a simple hello world app (no db code) to Tomcat via Ant, it seg faults as well.

```

$ ant && ant deploy
BUILD SUCCESSFUL
Total time: 3 seconds
Buildfile: build.xml

prepare:

compile:

deploy:
Segmentation fault

```

Any ideas?  Thanks for reading!
sd

---

### Post by Reiger on 2008-12-31
I'd try tracing my/the environments 'steps': did I do any configuring lately? Did the environment get 'updated' ? What happens if you purge the environment from your system then install it from scratch again?

---

### Post by escapee on 2008-12-31
Edit:
Wasn't sure if this was environment or code problem, posting code help anyway.

Check each one of your variables like 'con', 'stmt', and 'rs' before accessing their methods to see if any of them are NULL.  Accessing memory that you do not have would result in a seg fault.

---

