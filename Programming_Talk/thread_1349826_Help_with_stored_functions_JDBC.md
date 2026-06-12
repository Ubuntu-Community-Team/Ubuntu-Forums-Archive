---
title: "Help with stored functions JDBC"
date: 2009-12-08
forum: Programming Talk
---

### Post by psychok7 on 2009-12-08
hi there.. im having problems with my stored functions(java oracle),where i create the functions but then im i call them, it doesn't return any value(nothing happens after i call my function). Can someone help me? 

here's how i create the stored function:

/******************************************************************/
create or replace FUNCTION insert_client_func(a_client_name IN CLIENTS.client_name%TYPE) 

RETURN VARCHAR2

	IS


	BEGIN

	  INSERT INTO CLIENTS (client_name)

	  VALUES (a_client_name);
    

    return a_client_name;

END;
/*******************************************************************/

Heres how i call it: 

/*******************************************************************/
        name="'"+name+"'";

        String command="{ call insert_client_func("+name+") }";

   try{
       String url="jdbc:oracle:thin:@localhost:1521:xe";
       this.dbConnection=DriverManager.getConnection(url,"bd2009","bd2009");
        System.out.println(command);
        this.callstmt=this.dbConnection.prepareCall(command);
        this.callstmt.registerOutParameter(1,Types.VARCHAR);
        this.callstmt.executeUpdate();
        String simpleArray = this.callstmt.getString(1);
        System.out.println(simpleArray);
        
        this.dbConnection.commit();
        this.callstmt.close();
        this.dbConnection.close();
   }
/*******************************************************************/

---

### Post by psychok7 on 2009-12-10
Your call syntax is incorrect. For functions it should be

"{ ? = call insert_client_func(?) }"

or you could use the PL/SQL syntax

"BEGIN ? := insert_client_func(a_client_name=>?); END;"

Then set up your parameters

this.callstmt.registerOutParameter(1, Types.VARCHAR);
this.callstmt.setObject(2, <value>);

What is the data type of IN_CLIENTS.client_name?

Call the function and retrieve the return value

this.callstmt.execute();
String value = this.callstmt.getString(1);

---

