---
title: "C++ cin problems"
date: 2010-04-10
forum: Programming Talk
---

### Post by milawynsrealm on 2010-04-10
To help strengthen my C++ Programming skills, I am writing a simple Address Book program. Most of it works fine, but I seem to be stuck on one problem: when I enter in the information and it gets to the input for the phone number (I used a 'long' variable type for it) and I tell the program to output the contact information, the phone number comes out as a different number.

I am stuck and not sure what to do. I will post snippets of my code for simplicity reasons, but can post more of it if needed.

The Code used:
```
//variables to store the information
    string fName;
    string lName;
    string streetAddress;
    string city;
    string state;
    long phoneNumber = 0;

    //...

    cout << "Phone Number> ";
    cin >> phoneNumber;

    //...

    //Now it outputs the information for the user to see
    cout << "Personal Information:" << endl;
    cout << "---------------------" << endl;
    cout << lName << ", " << fName << endl; //the person's name
    cout << streetAddress << endl;
    cout << city << ", " << state << endl;
    cout << phoneNumber << endl;

```For FYI, for the Phone Number, I am using the American Phone Number system ((XXX)XXX-XXXX) for input minus the parenthesis and the dash when imputing in the variable.

---

### Post by geirha on 2010-04-10
A long is 4 bytes, which means it can hold the numbers -2147483648 to 2147483647 (those are 9 digits), so your 10-digit phone number is too large for that datatype. Either use a string, or long long (which is 8 bytes).

EDIT: Oops, 9-digits, silly me, they are 10-digits, but still not enough to hold all possible 10-digit phone numbers. If it starts with 3 you'll get a negative number.

---

### Post by Compyx on 2010-04-10
Are you compiling this on a 32-bit system by any chance? In that case you might have overflown your phone number variable: try entering a phone number equal to, or lower than 214-748-3647 and see if that does get printed correctly, then try a number higher than 214-748-3647.
The maximum value of a long on a 32-bit system is 214,748,3647, so any number higher than that causes overflow.

If you're running a 64-bit system, then something else might be clobbering your data, since a long on a 64-bit system has a maximum value of 9,223,372,036,854,775,807, quite enough to store a US phone number, I'd think.

Since you're using strings to store all the other data, why not store the phone number in a string as well, that way people can also enter phone numbers containing parentheses and dashes. And you'd avoid problems on 32-bit systems.

---

### Post by milawynsrealm on 2010-04-10
Thanks for the help!

I decided to use strings for my phone number. 

And just FYI for future reference, I am using both a 32-bit version of Vista and of Ubuntu.

---

### Post by lisati on 2010-04-10
> **milawynsrealm said:**
> I decided to use strings for my phone number. 

Random musing: one advantage of using strings is that it's sometimes easier with strings if you need to separate out the parts of the phone number (e.g. area code)

---

### Post by TehCodr on 2010-04-11
Just a comment... did you remember to use namespace std?

---

