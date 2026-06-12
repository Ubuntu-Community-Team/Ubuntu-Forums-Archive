---
title: "Why are my else clauses ignored? (Java)"
date: 2009-09-12
forum: Programming Talk
---

### Post by s3a on 2009-09-12
First of all, is else CLAUSES the right terminology for the following?:
```

if(x == 0)
System.out.println("x = 0");
else
System.out.println("x &#8800; 0");
```

Secondly, the above is an example I just randomly created for the purpose of this post because I have a more complex program and my statements after the else clauses are being ignored! I don't have them wrapped in blocks but that's because it is a one line statement following each one. I have a lot of else clauses after if statements (One else clause per if statement) and after the else clauses I put a System.out.println("Something"); statement and they all get printed out _unconditionally_, why is this so?

Any input would be greatly appreciated!
Thanks in advance!

EDIT: MY MISTAKE WAS NOT WITH THE ELSE CLAUSES BUT I HAVEN'T DONE THE FOLLOWING:

"if(isLeapYear = true)" so it printed all the other stuff because the other statements already had if(month == whichever month) going on and since all the other 11 months were not equal to the chosen months, it printed all the other 11 messages.

I'd still like to know if the terminology is correct though please if anybody happens to pass by my post.

---

### Post by Arndt on 2009-09-13
> **s3a said:**
> First of all, is else CLAUSES the right terminology for the following?:
```

if(x == 0)
System.out.println("x = 0");
else
System.out.println("x &#8800; 0");
```

Secondly, the above is an example I just randomly created for the purpose of this post because I have a more complex program and my statements after the else clauses are being ignored! I don't have them wrapped in blocks but that's because it is a one line statement following each one. I have a lot of else clauses after if statements (One else clause per if statement) and after the else clauses I put a System.out.println("Something"); statement and they all get printed out _unconditionally_, why is this so?

Any input would be greatly appreciated!
Thanks in advance!

EDIT: MY MISTAKE WAS NOT WITH THE ELSE CLAUSES BUT I HAVEN'T DONE THE FOLLOWING:

"if(isLeapYear = true)" so it printed all the other stuff because the other statements already had if(month == whichever month) going on and since all the other 11 months were not equal to the chosen months, it printed all the other 11 messages.

I'd still like to know if the terminology is correct though please if anybody happens to pass by my post.

I would call what comes after 'else' an "else clause", yes.

---

