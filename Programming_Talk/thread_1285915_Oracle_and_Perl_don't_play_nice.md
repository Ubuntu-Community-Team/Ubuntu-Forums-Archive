---
title: "Oracle and Perl don't play nice"
date: 2009-10-08
forum: Programming Talk
---

### Post by slakkie on 2009-10-08
Code + error log here: [http://pb.opperschaap.net/63](http://pb.opperschaap.net/63)

The problem is (at least that is my assumption) that the function/procedure I'm calling is overloaded:

one is name_of_thing(int, int);
the other is name_of_thing(int,varchar2);

I think Oracle has problems deciding which one it should prepare and takes the wrong one. 

Does anyone has some insight in how to fix this problem?

---

### Post by slakkie on 2009-10-10
*bump*

---

### Post by slakkie on 2009-10-12
Fixed the issue.

```

# Causing the error
sth->bind_param(2, $queue, { TYPE => ORA_NUMBER });
# Fixing the error
$sth->bind_param(2, $queue, { ora_type => ORA_NUMBER });

```

---

