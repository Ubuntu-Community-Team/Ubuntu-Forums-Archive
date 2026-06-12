---
title: "cin.getline() Problem"
date: 2007-10-23
forum: Programming Talk
---

### Post by ankursethi on 2007-10-23
RANT
Normally I wouldn't touch C++ with a 10 foot pole, but since that's what they teach at school, I'm stuck with it. Moreover, they use the non standard syntax (.h after header files, no namespaces, no templates, no STL etc.) from Borland's Turbo C++ line of products. Now here I am, on Windows, trying to keep my head cool.
/RANT

When I do :
```
cin.getline(varname, size) ;
```
it works.
But if I do :
```
cin >> integername ;
cin.getline(varname, size) ;
```
then the program completely ignores the cin.getline() and moves on further. If I do another cin.getline() after the first one, it will still ignore the first one but the second one will work.

What's going on!?

PS : I'm using Visual C++ 6 in an effort to stay away from TC.

---

### Post by dwhitney67 on 2007-10-23
> **ankursethi said:**
> 
```
cin << integername ;

```


What operation is this??  Did you implement "<<", or is it a typo, and should be ">>" instead?

Anyhow, it seems your school is teaching what is formally known as Embedded-C++ (no templates, STL, namespaces, etc.).  Do a Google search on it so you can read more.

---

### Post by slavik on 2007-10-23
no, it's not embedded C++ ... they are using borland ... with .h after headers, this is just non-standard C++ ... whinea t the department head, if you have a computer club, complain to them too and get the students there to complain. it works, trust me.

---

### Post by ankursethi on 2007-10-23
@dwhitney67
Yup, that is a typo. I'm fixing it in the original post.

@slavik
No can do. This is what the Central Board of Secondary education reccommends and uses country wide. It's either this or Visual Basic 6. It's impossible to get a point across to these people. Most of these guys are greyheads who don't have the slightest idea what a computer is. And trust me, this scenario will not be changing soon. This is just one of those things which reminds me that my country is *still* a third world country, with rigid bodies like the CBSE.

Anyway, can somebody help me? I'm having the same problem with g++ (using corrected ISO standard code, of course). Is there a correct way to input a string or not?

---

### Post by dwhitney67 on 2007-10-23
Weird problem with the cin thingy.  To resolve it I used this and it worked:

```
int intValue;
char charArray[10];

cin >> intValue;
cin.ignore();
cin.getline( charArray, sizeof charArray );
```

---

### Post by ankursethi on 2007-10-23
All right, thanks. But can anybody find out exactly what is wrong? I'd really like to understand what's going on.

<Craves for C/Python>

---

### Post by dwhitney67 on 2007-10-23
I don't think anything is "wrong", but that the carriage return is still sitting in the cin input-stream.  Unless you ignore (discard) it, before you call getline(), it will immediately return upon finding the carriage return because that is a delimeter.  Any characters prior to the carriage return, which in your case are none, will be returned by the getline().

When you have successive statements such as the following, the input-stream knows to filter non-numeric characters to satisfy the request to obtain an integer, thus the reason why the carriage return does not come into play after the first *cin* should be understood.

```

int i;
int j;
char str[10];
cin >> i;
cin >> j;
cin.getline( str, sizeof str);

```

However, bear in mind that a carriage return is still sitting on the input-stream after the second cin statement.  With the following *getline()*, you still  observe the same anomaly as witnessed in your original code.

If you were to follow with a *cin >> str *then everything would work fine, however you risk that the *str* buffer would be overflowed if one enters more than 9 bytes of data.  Hence it would be preferable to declare *str* as a *std::string*, and not a character array.

Anyhow there's probably a better explanation for all this, but this is my take on what is occurring.  I'm merely using observational data to derive my theory.

---

### Post by hod139 on 2007-10-23
Your problem is explained in the [C++ faq]("http://www.parashift.com/c++-faq-lite/"), but the site seems to be down right now.

[This site]("http://www.new-brunswick.net/workshop/c++/faq/") seems to be an older copy of the faq, and [answers your question]("http://www.new-brunswick.net/workshop/c++/faq/input-output.html#faq-15.6").
I suggest you read the real site when it comes back online though.

---

