---
title: "How to send a mysql script from QT application?"
date: 2018-04-22
forum: Programming Talk
---

### Post by aemem on 2018-04-22
I want to execute the following SQL code using a QT application (entered from line edit).
```
DROP PROCEDURE IF EXISTS mprocedure;
DELIMITER $$
CREATE PROCEDURE mprocedure ()
BEGIN
   DECLARE EXIT HANDLER FOR SQLEXCEPTION
   BEGIN
      ROLLBACK;
      SELECT 'An exception occurred';
   END;

   START TRANSACTION;
   INSERT INTO `mschema`.`table1`
      (`maxbudget`, `blocked`, `d_percentage`, `max discount`)
      VALUES ('2250', '0', '.9', '.99');
   INSERT INTO `mschema`.`table2`
      (`name`,`image`,`date`,`fKey_id`)
     VALUES ('jhon','jfdd', '2018-01-01 00:00:00', LAST_INSERT_ID());
   COMMIT;
END;
$$
DELIMITER ;
```
**What I have tried:**

I tried the following code snippet:

```
if (query.exec(statement))    //statement..the user entered query 
         {    
            qDebug()<<"Executed correctly";
         }
     else
         {
           QMessageBox::warning((this),"Error","The statement cannot be executed");
           qDebug()<<query.lastError();
         }
```
the query is executed successfully i.e. ```
lastError()
``` does not return errors but unfortunately the query is not really 
executed (the database still as is). It is importatnt to say that this 
query was tested using MySQL workbench and made the required effects.

On the other hand if the user tries to execute 
```
call mprocedure(); 
```
in the QT application it affects the database.

So how to do the above SQL code using the QT application?

---

