---
title: "[SOLVED] XAMPP/WAMPP MySQL"
date: 2008-03-17
forum: Programming Talk
---

### Post by DouglasAWh on 2008-03-17
I believe this to not be a Window$ specific question, but I've been forced to do some Win dev work and I'm using XAMPP.  I'm also trying to check out phplabman, but I don't think that's necessarily important to the issue.  I think I ran a script in phplabman that set up the initial database...at least, MySQL gave no errors when I did.  The name of the database is "equipment" that the script sets up, but when I try to do 

```

use equipment;

```

I get an error saying it is an unknown database.

So, the question is, for this issue and for any other issue, is there a way to see what databases exist?

THANKS!

---

### Post by LaRoza on 2008-03-17
> **DouglasAWh said:**
> 
So, the question is, for this issue and for any other issue, is there a way to see what databases exist?

THANKS!

```

SHOW databases;

```

If you want a better Windows *AMP solution, VertigoServ was better IMO. [http://vertrigo.sourceforge.net/](http://vertrigo.sourceforge.net/)

---

### Post by DouglasAWh on 2008-03-17
"was" better?

I had tried 

```

show database;

```

but not show databaseS...

---

