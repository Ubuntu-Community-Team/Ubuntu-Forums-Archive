---
title: "C++, Odd &quot;cin&quot; behavior."
date: 2010-10-01
forum: Programming Talk
---

### Post by cgroza on 2010-10-01
Hello, I built my address book in C++ and it seems to work, but for example if I create a new entry and give input with a space in it , the characters after the space are assigned to the next cin command. Here is the code:


```
string name,telnr,address,email;
     cout << "Enter the name:" << endl;
     cin >> name;
     cout << "Enter the phone number:" << endl;
     cin >> telnr;
     cout << "Enter the address:" << endl;
     cin >> address;
     cout << "Enter the email:" << endl;
     cin >> email;

     ofstream dafi;
     dafi.open(homedir.c_str(),ios::app);

     dafi << name <<" | ";
     dafi << telnr<<" | ";
     dafi <<address<<" | ";
     dafi << email <<endl;

     dafi.close();
```


So when it asks my name if I put in there "Chuck Norris", Chuck will be in the name variable and Norris will be in the telnr variable.

---

### Post by TheBuzzSaw on 2010-10-01
[http://www.cplusplus.com/reference/string/getline/](http://www.cplusplus.com/reference/string/getline/)

---

### Post by schauerlich on 2010-10-01
When cin reads in a string, it reads to the next whitespace. To get a whole line, use [getline](http://www.cplusplus.com/reference/string/getline/).

---

### Post by cgroza on 2010-10-01
So I should use getline(cin,str); instead?

---

### Post by schauerlich on 2010-10-01
> **cgroza said:**
> So I should use getline(cin,str); instead?

yes.

---

### Post by cgroza on 2010-10-01
> **schauerlich said:**
> yes.

I did, and now  it asks me for my name but its skips instantly at the next ones.

---

### Post by TheBuzzSaw on 2010-10-01
> **cgroza said:**
> I did, and now  it asks me for my name but its skips instantly at the next ones.

Did you use getline on every single one? You should.

---

### Post by cgroza on 2010-10-01
Yes i did. The code looks like the other one except all lines with cin>>variable are replaced with getline(cin,variable).

---

### Post by TheBuzzSaw on 2010-10-01
You'll have to post more of your code. I just ran a test, and it worked just fine.

---

### Post by cgroza on 2010-10-01
It sounds weird but i added 2 of getline there and it works. Very weird.

---

### Post by dwhitney67 on 2010-10-01
> **cgroza said:**
> It sounds weird but i added 2 of getline there and it works. Very weird.

Was this topic not discussed last week?

If you have three strings to read, use a getline() to acquire each.

```

using namespace std;

string str1, str2, str3;

cout << "Enter string 1: ";
getline(cin, str1);

cout << "Enter string 2: ";
getline(cin, str2);

cout << "Enter string 3: ";
getline(cin, str3);

...

```

---

### Post by cgroza on 2010-10-01
> **dwhitney67 said:**
> Was this topic not discussed last week?

If you have three strings to read, use a getline() to acquire each.

```

using namespace std;

string str1, str2, str3;

cout << "Enter string 1: ";
getline(cin, str1);

cout << "Enter string 2: ";
getline(cin, str2);

cout << "Enter string 3: ";
getline(cin, str3);

...

```

Thats exactly what i did and i still got the problem, its fixed now, thanks.

---

