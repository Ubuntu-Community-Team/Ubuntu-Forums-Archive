---
title: "How to convert a string to double in C#?"
date: 2008-05-17
forum: Programming Talk
---

### Post by c@sp3r on 2008-05-17
I'm new to C# and I want to know how can I convert a string like "pizza slice $2.50" into a double so I can use the number to do mathematical operations with it?? Thanks in advance.

---

### Post by johnl on 2008-05-17
To convert a string to a double, you can use:

```

double value = double.Parse("1.03"); // this will throw an exception if it fails
// or
double.TryParse("1.03", out value); // this will return the result in 'value' and return true/false depending on success

```

In your case, however, you'll need to strip out the actual numbers from the containing string -- you can't just pass "price is $3.50".  You need to pass in "3.50".

If the price will always be right after the dollar sign, you can try something like:

```

string text = "pizza slice $3.50";
int dollarPos = text.IndexOf("$");

if (dollarPos == -1) { // no dollar sign in the string
   // do something.
}
else {
   // try to convert all the characters after the dollar sign to a double.
   double price = double.Parse(text.Substring(dollarPos + 1));
   // let's tax this sucker at 8%!
   price += price * .08;
}

```

---

### Post by c@sp3r on 2008-05-17
Thanks a lot, now I can work with it.

---

### Post by sakabato on 2008-05-18
for money issues try using **decimal** instead of **double**. It is more suitable

---

