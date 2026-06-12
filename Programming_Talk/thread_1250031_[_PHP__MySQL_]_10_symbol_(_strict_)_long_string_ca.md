---
title: "[ PHP / MySQL ] 10 symbol ( strict ) long string can't fit into varchar(10)."
date: 2009-08-26
forum: Programming Talk
---

### Post by credobyte on 2009-08-26
Problem solved! Didn't realized that rand(0, 10) should be rand(0, 9) :p

------------------------

As you see blow, I get "data too long" error quite often. Why it is so ? PHP generates 10 symbol long ID and there should be no problems at all .. am I wrong ?
What could be the reason for this problem ?


MySQL database field:
```
transaction_uid     varchar(10)

```Transaction ID / PHP:
[php]for ($i = 1; $i <= 10; $i++) {
    $n = rand(0, 10);
    $transaction_id .= $n;
}[/php]Form submissions ( done by myself ) and their result:
```
Transaction ID: 7190050395
Transaction ID: 4532942989
Transaction ID: 6227396954
Data too long for column 'transaction_uid' at row 1
Data too long for column 'transaction_uid' at row 1
Transaction ID: 9251940744

```

---

