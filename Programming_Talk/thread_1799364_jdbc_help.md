---
title: "jdbc help"
date: 2011-07-07
forum: Programming Talk
---

### Post by santhoshrayala on 2011-07-07
Can anyone help me with this..i am unable to connect to oracle xe 10 version..

package com.xpedite.training.sample.demo;
import java.sql.*;

public class MyJDBC {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String url = "jdbc:oracle:thin:@localhost:1521:XE";
		String user = "HR";
		String pwd = "hr";
		Connection con = null;
		Statement statement = null;
		ResultSet rs = null;
		try {
			Class.forName("oracle.jdbc.driver.OracleDriver");
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}	
		try {
			con=DriverManager.getConnection(url,user,pwd);
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}		
		try {
			statement=con.createStatement();
		} catch (SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}
		String query="SELECT * FROM COUNTRIES";
		try {
			rs=statement.executeQuery(query);
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		try {
			while(rs.next())
			{
				System.out.println(rs.getString("COUNTRY_ID"));
				System.out.println(rs.getString("COUNTRY_NAME"));
				System.out.println(rs.getLong("REGION_ID"));				
			}
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
	}

}


errors:

java.sql.SQLException: Io exception: The Network Adapter could not establish the connection
	at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:113)
	at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:147)
	at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:257)
	at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:389)
	at oracle.jdbc.driver.PhysicalConnection.<init>(PhysicalConnection.java:454)
	at oracle.jdbc.driver.T4CConnection.<init>(T4CConnection.java:165)
	at oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:35)
	at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:802)
	at java.sql.DriverManager.getConnection(DriverManager.java:620)
	at java.sql.DriverManager.getConnection(DriverManager.java:200)
	at com.xpedite.training.sample.demo.MyJDBC.main(MyJDBC.java:24)
Exception in thread "main" java.lang.NullPointerException
	at com.xpedite.training.sample.demo.MyJDBC.main(MyJDBC.java:30)


thanks

---

