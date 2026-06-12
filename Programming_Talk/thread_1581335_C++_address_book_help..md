---
title: "C++ address book help."
date: 2010-09-24
forum: Programming Talk
---

### Post by cgroza on 2010-09-24
Hello, I have this function in C++ that should write the users input in a line. It works (half of it). I am building this for my address book. When I run the program it writes the line to the file, but when i run it the second time it overwrites it. I think I open the file in append mode but I am missing something. Here is the code: 

```
void create()
{
     using namespace std;
     string name,telnr,address,email;
     cout << "Enter the name:" << endl;
     cin >> name;
     cout << "Enter the phone number:" << endl;
     cin >> telnr;
     cout << "Enter the address:" << endl;
     cin >> address;
     cout << "Enter the email:" << endl;
     cin >> email;
     cout << "Entry Modified. " << endl; 
     
     ofstream dafi;
     dafi.open(".contacts",ios::eek:ut | ios::ate);
     
     dafi << name <<", ";
     dafi <<address<<", ";
     dafi << email<<", ";
     dafi << telnr<<", "<<endl; 
     
     dafi.close();
              

     }
```Thanks.

---

### Post by endotherm on 2010-09-24
[http://www.cplusplus.com/reference/iostream/ofstream/open/](http://www.cplusplus.com/reference/iostream/ofstream/open/)

been many many years since I touched c++, but I don;t think you are supposed to use both out and ate. and are you doing a binary or on the values of each?

---

### Post by JakeFrederix on 2010-09-24
```
    using namespace std;
     string name,telnr,address,email;
     cout << "Enter the name:" << endl;
     cin >> name;
     cout << "Enter the phone number:" << endl;
     cin >> telnr;
     cout << "Enter the address:" << endl;
     cin >> address;
     cout << "Enter the email:" << endl;
     cin >> email;
     cout << "Entry Modified. " << endl;

     ofstream dafi;
     dafi.open(".contacts",**fstream::in | fstream::out | fstream::app**);

     dafi << name <<", ";
     dafi <<address<<", ";
     dafi << email<<", ";
     dafi << telnr<<", "<<endl;

     dafi.close();
```

---

### Post by CharlesA on 2010-09-24
*Moved to **Programming Talk**.*

---

### Post by piratebill on 2010-09-24
In the future, you might have better luck here:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by cgroza on 2010-09-24
Thanks.

---

### Post by dwhitney67 on 2010-09-25
Try:
```

std::ofstream dafi(".contacts", std::ios::app);

if (dafi)
{
   // file opened; can be written to now.
}
else
{
   // open failed
}

```
You should bookmark the following page as your C++ reference guide:
[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

Specifically for ofstream:
[http://www.cplusplus.com/reference/iostream/ofstream/](http://www.cplusplus.com/reference/iostream/ofstream/)


P.S.  If you need to read in multiple words (say for a name or street address), you will need to use [std::getline()]("http://www.cplusplus.com/reference/string/getline/"); merely using std::cin will not be sufficient, since it will only read up to the first white-space encountered.

---

### Post by cgroza on 2010-09-26
Ok, thanks a lot.

---

