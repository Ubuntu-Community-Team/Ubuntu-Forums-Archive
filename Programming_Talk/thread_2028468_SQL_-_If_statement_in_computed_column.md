---
title: "SQL - If statement in computed column"
date: 2012-07-18
forum: Programming Talk
---

### Post by PaulM1985 on 2012-07-18
Hi

I am trying to output the following from my MySQL database:
player_id, number_of_wins, total_games

I am using:
```

SELECT player_id, SUM (money > opponents_money) as number_of_wins, COUNT(*) as total_games
FROM my_table
GROUP BY player_id

```

This works because it seems to promote (money > opponents_money) from TRUE/FALSE to 1/0, but I wanted to know if this is the right thing to do.  Is it possible to put something in to explicitly say that money > opponents_money should be treated as 1 if true and 0 if false?

Paul

---

### Post by SeijiSensei on 2012-07-18
That seems to be a MySQLism.  On my PostgreSQL server the syntax "SELECT SUM(a>b)" returns 

"ERROR:  function sum(boolean) does not exist
HINT:  No function matches the given name and argument types. You may need to add explicit type casts."

However the expression 

```
SELECT SUM(CAST(a>b) as integer) from ...
```

returns the appropriate sum.

---

