---
title: "c++ help"
date: 2008-10-15
forum: Programming Talk
---

### Post by guest_user on 2008-10-15
```
cout << "\nPlease enter a number: ";
        cin >> number1;
        cin.clear();
        cin.ignore(200,'\n');
        cout << "\nPlease enter another number: ";
        cin >> number2;
```

Why does this piece of code work even when valid inputs are given for input1?

Isn't cin.ignore(200,'\n') suppose to ignore the next 200 characters or until the next newline character in the input stream so shouldn't number2 be ignored if a valid input is given in input1?

or is the newline character still left in the input stream after the reading of input1 from the pressing of enter which is why the ignore(200,'\n') is not "used" on number2?

---

### Post by guest_user on 2008-10-15
should be this "the newline character is still left in the input stream after the reading of input1 from the pressing of enter which is why the ignore(200,'\n') is not "used" on number2" right? it kinda slipped my mind for awhile, just asking for confirmation.

---

### Post by samjh on 2008-10-15
My apologies if English is not your native language.  Your post is very hard to understand.

cin.ignore only works on the data that's already in the stream.

If the user typed in 5555555 for cin >> number1, then cin.ignore will extract up to 200 characters from the input stream or until it hits a newline character and then extracts the newline character as well.  So number1 will be 5555555.

cin >> number2 works as normal.  The cin.ignore in the previous line has no effect on cin >> number2.

> **guest_user said:**
> should be this "the newline character is still left in the input stream after the reading of input1 from the pressing of enter which is why the ignore(200,'\n') is not "used" on number2" right? it kinda slipped my mind for awhile, just asking for confirmation.

The newline character is extracted and ignored by ignore(200, '\n').  But as I explained earlier, this ignore only works on cin >> number1.

If you want it to do something for cin >> number2, you'll need to use it again just after cin >> number2.




Aside from what I've just written, your code is very strange.  I'm not sure what your code is for, but you should know that cin >> *variable* will only read up to the first whitespace character.  So your ignore function is not necessary if you just don't want a newline after number1.

---

