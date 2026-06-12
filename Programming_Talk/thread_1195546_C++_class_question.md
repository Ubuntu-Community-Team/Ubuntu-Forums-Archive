---
title: "C++ class question"
date: 2009-06-23
forum: Programming Talk
---

### Post by Mirge on 2009-06-23
```

 p, li { white-space: pre-wrap; }  #include <iostream>
 #include <string>
 
 using std::string;
 using std::cout;
 using std::endl;
 
 class MyClass
 {
 	public:
 	MyClass(const string& text);
 	
 	**const string& text() const;**
 	void setText(const string& text);
 	
 	int getLengthOfText() const;
 	
 	private:
 	string m_text;
 };
 
 int main()
 {
 	MyClass object("This is a test");
 	cout << object.text() << endl;
 }
 
 MyClass::MyClass(const string& text)
 {
 	this->m_text = text;
 }
 
 **const string& MyClass::text() const**
 **{**
 **	return this->m_text;**
 **}**
 

```

Can someone please explain the bold parts? Is it returning a constant string reference? How's that work? I can't modify the return value? or?

If I understand correctly, the const at the end means the method doesn't modify any class members.

---

### Post by Mirge on 2009-06-23
Just when I think I'm getting a grip on the many uses of "const" in C++, I am slapped in the face with another lol :P.

---

### Post by PandaGoat on 2009-06-24
What you said is correct.  

The first return type, const string&,  means it will return an alias to a string, but it cannot be used to modify the string.

The suffix of the method, const, means the member function is an "inspector" because it cannot modify any of its object's members.

Member functions that can change its object's members (the ones with no const suffix) are called "mutators" if you were curious.

---

### Post by Mirge on 2009-06-24
[http://www.gamedev.net/community/forums/topic.asp?topic_id=410498](http://www.gamedev.net/community/forums/topic.asp?topic_id=410498)

This helps quite a bit in understanding... but I still have a question (also mentioned there in the above URL).... is what's the point of having a const return value? In which context(s) would it prove useful?

The above code (see OP)... returns a reference to a string constant.. the value of which can be stored & modified freely. I'm lost.

---

### Post by fr4nko on 2009-06-24
> **Mirge said:**
> 
This helps quite a bit in understanding... but I still have a question (also mentioned there in the above URL).... is what's the point of having a const return value? In which context(s) would it prove useful?

The above code (see OP)... returns a reference to a string constant.. the value of which can be stored & modified freely. I'm lost.
I believe that the rational is:

[LIST]
[*]we return a string reference because we don't want to make a copy of the string. The reason is that make a copy is expensive so we return just a reference.
[*]The reason of the 'const' in the returning values is, ok you have a string reference but you're not authorised to modify the string. This is logical because it is a reference to a private member and the access should be done using only public methods.
[/LIST]
So, the logic when you call the text() method is that you get a value but for read only purpose. So you could do something like that:
```
MyClass mobj("some text here");
string mstr;

/* some code here */
mstr = mobj.text(); /* you get a copy of the string. This is ok.*/

/* example of C-like legitimate use. In this case no copy of the string is done. */
printf ("This is my text: %s\n", mobj.text().c_str());

```I hope that helps.

Francesco

---

### Post by Mirge on 2009-06-24
But I still just don't understand I guess... how it's returning a reference to a private variable. If I modify the return value, it doesn't modify the object's m_text variable (good)... but why not if it's a reference?

The const part I think I understand. You can assign a const to a non-const and change it... just can't change a const value once it's made a const.

---

### Post by Mirge on 2009-06-24
Ok, I modified the code a bit to try to understand. I took off "private" so that m_text was a public member... just temporarily to run this test.

I then did:

```

 int main()
 {
     MyClass object("This is a test");
    string retval = object.text();

    cout << &retval << endl; //         0x7fff09694920
    cout << &object.m_text << endl; //    0x7fff09694940
    
     cout << retval << endl;
    cout << object.text() << endl;
 }

```So, if I understand correctly, calling object.text() is returning a const string&.. but storing it in retval is making a copy of that variable. It can't be a reference to it, I don't think, because if I make m_string private again and do:

```

int main()
 {
     MyClass object("This is a test");
    string retval = object.text();

     cout << retval << endl;
    retval += " more text";
    cout << object.text() << endl;
 }

```The output is:
This is a test
This is a test

And object.m_string remains unmodified via retval.

Which still makes me wonder, what's the point of returning a const string& if it's just gonna make a copy anyway?

---

### Post by Habbit on 2009-06-24
> **Mirge said:**
> Which still makes me wonder, what's the point of returning a const string& if it's just gonna make a copy anyway?

Because you might not need that copy... You might just want to query the length of the string, or call c_str(), or find some character in it. Thus, by using a const reference you avoid an unneeded copy.

---

### Post by Mirge on 2009-06-24
> **Habbit said:**
> Because you might not need that copy... You might just want to query the length of the string, or call c_str(), or find some character in it. Thus, by using a const reference you avoid an unneeded copy.

Ohhh... so it does actually return a const string reference, but does not make the copy until I explicitly tell it to (via string retval = object.text())...... so I could have simply done a read-only operation on the reference, using the example you said, object.text().c_str()...

THANK YOU!!

---

### Post by johnl on 2009-06-24
Right:

```

string retval = object.text();

```
Is creating a copy of the string that was returned.  You are actually invoking the copy constructor here.

What you can do is this:

```

const string& retval = object.text();

```

In which case you will have a reference to the string.

---

### Post by Mirge on 2009-06-24
Understood, thanks a bunch folks!

---

