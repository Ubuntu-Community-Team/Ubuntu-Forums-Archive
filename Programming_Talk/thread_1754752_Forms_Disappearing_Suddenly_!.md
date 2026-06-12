---
title: "Forms Disappearing Suddenly !"
date: 2011-05-10
forum: Programming Talk
---

### Post by etdsbastar on 2011-05-10
Hello There,

I am using System.Windows.Forms in Monodevelop C# Programming. The code is given below:

```

using System;
using System.Windows.Forms;

class Test
{
Public static void Main() {
Form frm = new Form();
frm.Show();
}
}

```

The above code is showing the frm form but it is suddenly disappearing (exiting). Press F5 to run and the form appears and disappears, that's it.

How can this problem can be solved.

---

### Post by MadCow108 on 2011-05-10
you have no event loop so it will just go out of scope and get destroyed.

To get it to show do e.g.:
```
using System;
using System.Windows.Forms;

class Test
{
  public static void Main() {
    Application.Run(new Form());
  }
}

```

---

