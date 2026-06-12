---
title: "two keys in perl hash array"
date: 2009-04-16
forum: Programming Talk
---

### Post by monkeyking on 2009-04-16
Hi Im a beginner in perl, and my problem is maybe a design error comming from other programming languages.

Basicly I got a file with the the following columns.

```

id1   id2   val1    val2
1      1    asdf    fds
2      3     asdf   dfd
1      2     dfa    dad


```

I want to populate a hash array with the keys id1 and id2.
so that I afterwards can get the values val1 and val2.

But the problem is, that I want to extract the vals,
according to the ascending order of id2 with id1 fixed
like
1 1 asdf fds
1 2 dfa  dad

I hope it makes sense

thanks in advance

---

### Post by ghostdog74 on 2009-04-16
i would suggest reading perldoc perldsc for a start. get the basic idea of how hash of arrays are..
also, since you are a beginner, start reading up: perldoc perl

---

### Post by soltanis on 2009-04-17
Create two separate hashes with the corresponding key/value pairs (key1 -> value1, key2 -> value2). When you want to do what you described, nest the loops so that you iterate over one hash and then the other.

```


print "id1 id2 val1 val2\n";

for ($i = 0; $i < keys(hash1); $i++) {

 for ($j = 0; $j < keys(hash2); $j++) {

    print "$i $j $hash1{$i} $hash2{$j}\n";

 }

}

```

---

### Post by slavik on 2009-04-17
you can do something like:

```

$hash{$key1}{$key2} = [item1, item2];

```

---

### Post by monkeyking on 2009-04-18
Hi I have been playing around with perl before,
and I do know hash arrays.

But if slaviks code example works,
then this would seem to do the job.

thanks

---

