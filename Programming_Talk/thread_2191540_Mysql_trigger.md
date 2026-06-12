---
title: "Mysql trigger"
date: 2013-12-03
forum: Programming Talk
---

### Post by siddharth007 on 2013-12-03
Hi everyone.I have written the following trigger

DELIMITER $$


CREATE TRIGGER copy_low_record
AFTER INSERT ON ossec.data
FOR EACH ROW BEGIN
DECLARE X varchar(10);
SET X=(select level from ossec.alert_levels where rule_id in(select rule_id from ossec.alert where id in (select max(id) from ossec.alert)));
IF (X='Low') THEN
Insert into ossec.data_critical (server_id,user,full_log,timestamp) values (NEW.server_id,NEW.user,NEW.full_log,NEW.timestamp);
END IF;
END$$

DELIMITER ;


I am required to initiate a trigger after a record is inserted into **data** table and it will insert the same record into the new table based on the output of another query(stored in variable X).The trigger doesn't throw up an error when executed.However,i am not able to get the desired functionality.Please help.

---

