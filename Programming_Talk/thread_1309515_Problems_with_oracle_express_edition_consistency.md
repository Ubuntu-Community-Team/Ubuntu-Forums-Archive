---
title: "Problems with oracle express edition consistency"
date: 2009-11-01
forum: Programming Talk
---

### Post by psychok7 on 2009-11-01
i there im having problems with oracle express edition 10g. Hi execute sql commands with sql developer and it works fine(selects and everything else).. but when i go to the web browser for oracle is doesnt show the changes i made in sql developer, and when i insert those commands (all at once) it gives me errors.
can anyone help?

OK i fixed the issue (it seem that sql developer does not have autocommit enabled by default.. nevertheless, why cant i execute lots of commands at the same time with the browser?

---

### Post by Waappu on 2009-11-02
Hi,

I do not know is it bug or something.

You can run multiple commands like this
```

Begin
INSERT INTO your_table (your_column) VALUES (1);
INSERT INTO your_table (your_column) VALUES (2);
INSERT INTO your_table (your_column) VALUES (3);
END;

```

Or use SQL Scripts

---

### Post by psychok7 on 2009-11-02
> **Waappu said:**
> Hi,

I do not know is it bug or something.

You can run multiple commands like this
```

Begin
INSERT INTO your_table (your_column) VALUES (1);
INSERT INTO your_table (your_column) VALUES (2);
INSERT INTO your_table (your_column) VALUES (3);
END;

```

Or use SQL Scripts

good idea,just like plsql.. ill give it a try thanks :)

---

### Post by Waappu on 2009-11-02
Hi,

Good =)

If you search you may find exact answer from Oracle Application forum
[http://forums.oracle.com/forums/forum.jspa?forumID=137](http://forums.oracle.com/forums/forum.jspa?forumID=137)

I'm sure this is asked many times there

---

