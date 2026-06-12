---
title: "Launching concurrent background processes in shell"
date: 2013-11-15
forum: Programming Talk
---

### Post by Lars Noodén on 2013-11-15
The following line is incorrect.  I'm trying to get 3 background processes launched.

```

for i in 1 2 3;do {sleep 10 }&; done

```

It gives the error "*bash: syntax error near unexpected token `;'*"

What is the correct syntax?

---

### Post by Lars Noodén on 2013-11-15
It was a misplaced semicolon ;

```

for i in 1 2 3;do sleep 10 & done

```

---

