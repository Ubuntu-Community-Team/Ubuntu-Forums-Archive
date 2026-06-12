---
title: "MySQL"
date: 2009-04-15
forum: Programming Talk
---

### Post by detorresrc on 2009-04-15
Im creating a trigger and i need to make the table as current date. Can you correct my code. tnx

```

drop trigger if exists cdr_trigger;

SET @tablename:=concat('cdr_', CURDATE() + 0 );

delimiter |

CREATE TRIGGER cdr_trigger BEFORE INSERT ON asterisk_db.cdr
  FOR EACH ROW BEGIN
    INSERT INTO "@tablename" SET calldate = NEW.calldate,
	clid = NEW.clid,
	src = NEW.src,
	dst = NEW.dst,
	dcontext = NEW.dcontext,
	channel = NEW.channel,
	dstchannel = NEW.dstchannel,
	lastapp = NEW.lastapp,
	lastdata = NEW.lastdata,
	duration = NEW.duration,
	billsec = NEW.billsec,
	disposition = NEW.disposition,
	amaflags = NEW.amaflags,
	accountcode = NEW.accountcode,
	userfield = NEW.userfield,
	uniqueid = NEW.uniqueid;
  END;

```

---

### Post by khelben1979 on 2009-04-15
Check the code with yacker: MySQL validator. Check [this]("http://www.w3.org/2005/01/yacker/uploads/MySQL?lang=perl") webpage.

[Yacker User Guide]("http://www.w3.org/1999/02/26-modules/User/Yacker").

---

