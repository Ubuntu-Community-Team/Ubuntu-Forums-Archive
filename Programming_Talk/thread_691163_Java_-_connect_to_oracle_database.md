---
title: "Java - connect to oracle database"
date: 2008-02-08
forum: Programming Talk
---

### Post by xlinuks on 2008-02-08
Hi,
I'm wondering whether there are experienced Java programmers who worked with Oracle. I got an Oracle DB on another computer, and can't really figure out how to connect to it.
Here's what I get after running the test:
```

driver loaded!!
java.sql.SQLException: ????? ???????? URL Oracle
        at oracle.jdbc.dbaccess.DBError.throwSqlException(DBError.java:187)
        at oracle.jdbc.dbaccess.DBError.throwSqlException(DBError.java:229)
        at oracle.jdbc.dbaccess.DBError.throwSqlException(DBError.java:292)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:214)
        at java.sql.DriverManager.getConnection(Unknown Source)
        at java.sql.DriverManager.getConnection(Unknown Source)
        at xlinuks.DB.test(DB.java:38)
        at xlinuks.Main.main(Main.java:32)

```
the source code:
```

	public static void test() {
		
		try {
              Class.forName ("oracle.jdbc.driver.OracleDriver");
        } catch (ClassNotFoundException e) {
              e.printStackTrace();
			  System.exit( 0 );
        }
		
		//every time it prints this line, thus the driver works
		Log.line( "driver loaded!!" );
		
		try {
			
			String sQuery = "SELECT kol FROM tbm04680.sklad WHERE n_skl = 4680 AND n_uch = 1 AND kod_tov = (SELECT kod FROM tovar WHERE art = '227354')";
			Properties props = new Properties();
			props.setProperty( "user", "(actual username)" );
			props.setProperty( "password", "(actual password)" );
			//the database name is tbm04680, the computer it's on is \\Tbm04680
			Connection conn = DriverManager.getConnection( "jdbc:oracle:oci7:\\\\Tbm04680\\\\tbm04680", props );
			
			//never gets to print this line
			Log.line( "CONNECTED!!!" );
			Statement stmt = conn.createStatement();
			ResultSet rset = stmt.executeQuery( sQuery );
			
			while( rset.next() ) {
				System.out.println (rset.getString(1));
			}
			
			stmt.close();
		} catch( Exception exc ) {
			exc.printStackTrace();
		}
	}

```

I guess I'm using the wrong URL format to connect to it, the username/password I'm sure are correct. The question signs in the exception string are Russian letters that the console can't recognize.
Any tip would be appreciated.

---

### Post by xlinuks on 2008-02-08
I've found out what's the matter!!!
Google saved my life!

```

	public static void test() {
		
		try {
              Class.forName ("oracle.jdbc.driver.OracleDriver");
        } catch (ClassNotFoundException e) {
              e.printStackTrace();
			  System.exit( 0 );
        }
		
		try {
			
			String sQuery = "SELECT N_SKL, KOD_TOV, KOL, REZ, N_UCH, OST, POST, OTP, INV, VOZV, PER, REZF, VOZO, WAY FROM TBM04680.SKLAD";
			String serverName = "Tbm04680";
			String portNumber = "1521";
	        String sid = "tbm04680";
			String url = "jdbc:oracle:thin:@" + serverName + ":" + portNumber + ":" + sid;
			String username = "hidden";
			String password = "hidden";
			Connection conn = DriverManager.getConnection( url, username, password );
			Log.line( "CONNECTED!!!" );
			Statement stmt = conn.createStatement();
			ResultSet rset = stmt.executeQuery( sQuery );
			
			while( rset.next() ) {
				System.out.println (rset.getString(1));
			}
			
			stmt.close();
		} catch( Exception exc ) {
			exc.printStackTrace();
		}
	}

```

---

