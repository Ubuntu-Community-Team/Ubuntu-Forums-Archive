---
title: "InnoDB v MyISAM"
date: 2007-04-26
forum: Programming Talk
---

### Post by derby007 on 2007-04-26
I'm currently using the MyISAM engine for my DB tables, but i read that it doesnt do ForeignKeys, so i changed the tables to InnoDB, but now my prepared INSERT statements ( ps.setObject() etc ) doesnt show up in the DB when i do a Select !!!! whats goin on ? ie. everything is rosy for MyISAM....

---

### Post by phossal on 2007-04-26
Can you try to be more clear? Are there any error messages?

---

### Post by derby007 on 2007-04-27
No error messages, the prepared insert is run & it returns a value of 1, ie. int [] ins = ps.executeBatch();, but when i query the DB the values have not been written...

This code below works for MyISAM but not when i change the TAbles to InnoDB, I'm also not sure if I shud be doing setAutoCommit(true) or con.commit() in my commit function !

eg: 
[INDENT][/INDENT]public void doPersonPreparedStatement( Object [] objectIn, String insertIn ){
 [INDENT]       try{                
                [INDENT]conn.setAutoCommit( false );
                psPerson = conn.prepareStatement( insertIn ); 
                

                for( int i=0; i<objectIn.length; i++ ){
                    psPerson.setObject(i+1, objectIn[i]);                
                }
                psPerson.addBatch();                [/INDENT]
                

            }[INDENT]catch( SQLException e ){
                e.printStackTrace();[/INDENT]
            } 
    }[/INDENT]....

&&&&

public void commit(){
      [INDENT]  try{[/INDENT]            //conn.setAutoCommit( true );           
           [INDENT] int [] ins = psPerson.executeBatch();
            System.out.println("update : "+ins.length);[/INDENT]
.....

---

