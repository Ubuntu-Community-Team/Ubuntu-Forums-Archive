---
title: "const gchar* to std::string?"
date: 2008-10-02
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-10-02
Lets say I have a function that returns 'const gchar*'. How do I convert it to std::string? I came up with:
[php]std::string my_string;
my_string = (std::string)my_function();
g_print(my_string.c_str());
[/php]

It works. But is it the correct way? Do I have a memory leak or something?

ps. I want to store the my_stringS in a vector for later use.

---

### Post by mike_g on 2008-10-02
The 'assign' method in the string class should convert a character array for you, and can do a few extra bits if you need them:
[http://www.cppreference.com/wiki/string/assign](http://www.cppreference.com/wiki/string/assign)

or you could create it from a character array in your constructor:
[http://www.cppreference.com/wiki/string/string_constructors](http://www.cppreference.com/wiki/string/string_constructors)

---

### Post by SledgeHammer_999 on 2008-10-02
thank you

---

### Post by dribeas on 2008-10-02
> **SledgeHammer_999 said:**
> It works. But is it the correct way? Do I have a memory leak or something?

ps. I want to store the my_stringS in a vector for later use.

gchar is just a typedef to char. Now, as you already pointed out, you might run into a memory leak. You should check the function's documentation as to determine whether the const gchar* should or not be deallocated by user code.

Also note that you don't need the cast, and I would completely remove it. std::string already has a constructor that takes const char* as argument.

---

### Post by SledgeHammer_999 on 2008-10-02
> **dribeas said:**
> gchar is just a typedef to char. Now, as you already pointed out, you might run into a memory leak. You should check the function's documentation as to determine whether the const gchar* should or not be deallocated by user code.

Also note that you don't need the cast, and I would completely remove it. std::string already has a constructor that takes const char* as argument.

Well the documentation of the function doesn't mention anything(it does for other functions), so I assume that I am ok.

---

### Post by rnodal on 2008-10-02
> **SledgeHammer_999 said:**
> Lets say I have a function that returns 'const gchar*'. How do I convert it to std::string? I came up with:
[php]std::string my_string;
my_string = (std::string)my_function();
g_print(my_string.c_str());
[/php]

It works. But is it the correct way? Do I have a memory leak or something?

ps. I want to store the my_stringS in a vector for later use.

May I ask why are you storing what "my_function" returns in a string? The function returns a constant pointer so you can also store this pointer in a vector that way you do not have the same information stored in two memory locations.  

-r

---

### Post by SledgeHammer_999 on 2008-10-03
You are right but it is easier for me to manipulate strings(I am noob).

---

### Post by rnodal on 2008-10-03
> **SledgeHammer_999 said:**
> You are right but it is easier for me to manipulate strings(I am noob).

NP, you should you go for whatever suits your needs first and once you get it working the worry about making it better. :)

-r

---

### Post by dribeas on 2008-10-03
> **rnodal said:**
> May I ask why are you storing what "my_function" returns in a string? The function returns a constant pointer so you can also store this pointer in a vector that way you do not have the same information stored in two memory locations.  

-r

There are reasons to prefer using std::string as storage instead of const char* (gchar or whichever variant). And I am not referring to the simplists 'it's more c++-like than c strings...'

If you are using that string with a number of other libraries/methods/functions that take a std::string const & you will have implicit conversions going on unless you do store it as std::string.

```

const char* generate();
void f( std::string const & );

int main()
{
   const char * str = generate();
   std::string str2 = generate();
   f( str ); // [1]
   f( str ); // [2]
   f( str2 ); // [3]
   f( str2 ); // [4]
}

```

The line marked as [1] is implicitly converted by the compiler into:
```

f( std::string(str) );

```

That creates an unamed temporary string using the const char* constructor, uses the temporary for the call and then disposes the temporary. That operation is repeated again in [2]. On the other hand, if a std::string is created initially, then a reference to the string is used from then on, so neither [3] nor [4] will create new objects.

Note that if the signature of the function takes a std::string & (non-const) then it is not even possible to make the call with a c-style string, as unnamed temporaries cannot be passed as non-const references.

On the opposite side, if you only call functions that take c-style strings then the cost of using std::string is just one construction an a small accessor overhead:

```

void f3( const char* );
int main()
{
   std::string str = generate(); // [1]
   f3( str.c_str() ); // [2]
   f3( str.c_str() ); // [3]
}

```

The call in [2] and [3] has just an accessor to the internal character array, and does not require creating/copying the data. In some C++ implementations (read as compiler/STL provider) including g++, the accessor is inlined so that the cost is negligible. The construction/copy cost takes place at [1], once for the lifetime of the string.

So at the end the question should be the opposite: what are the reasons to use old-style c-strings when using C++ strings are better in most cases and not worse in most others?

---

### Post by rnodal on 2008-10-03
> **dribeas said:**
> There are reasons to prefer using std::string as storage instead of const char* (gchar or whichever variant). And I am not referring to the simplists 'it's more c++-like than c strings...'

If you are using that string with a number of other libraries/methods/functions that take a std::string const & you will have implicit conversions going on unless you do store it as std::string.

```

const char* generate();
void f( std::string const & );

int main()
{
   const char * str = generate();
   std::string str2 = generate();
   f( str ); // [1]
   f( str ); // [2]
   f( str2 ); // [3]
   f( str2 ); // [4]
}

```

The line marked as [1] is implicitly converted by the compiler into:
```

f( std::string(str) );

```

That creates an unamed temporary string using the const char* constructor, uses the temporary for the call and then disposes the temporary. That operation is repeated again in [2]. On the other hand, if a std::string is created initially, then a reference to the string is used from then on, so neither [3] nor [4] will create new objects.

Note that if the signature of the function takes a std::string & (non-const) then it is not even possible to make the call with a c-style string, as unnamed temporaries cannot be passed as non-const references.

On the opposite side, if you only call functions that take c-style strings then the cost of using std::string is just one construction an a small accessor overhead:

```

void f3( const char* );
int main()
{
   std::string str = generate(); // [1]
   f3( str.c_str() ); // [2]
   f3( str.c_str() ); // [3]
}

```

The call in [2] and [3] has just an accessor to the internal character array, and does not require creating/copying the data. In some C++ implementations (read as compiler/STL provider) including g++, the accessor is inlined so that the cost is negligible. The construction/copy cost takes place at [1], once for the lifetime of the string.

So at the end the question should be the opposite: what are the reasons to use old-style c-strings when using C++ strings are better in most cases and not worse in most others?

I think you misunderstood why I was asking. If you look at OP code you will see that the OP is storing the string in a std::string and the passing the the c_str to another function that take a parameter which happens to be const g_char. To me that is redundant. If "myfunction" returns a g_char and later on the OP is using a function that takes a g_char storing in it in a std::string is pointless since it will store the same information in two different locations. Now, lets say that once the OP calls "myfunction" which returns a g_char then the OP stores the string in a std::string to later be used in a function that uses a std::string as parameter then it would make more sense. My reasoning was based on the OP posted code. I am not saying that it makes not sense to store c strings in a C++ string. I can not possible tell what the OP goals just by looking at that very small sample code. I do I agree with you that C++ strings are more convinient *most* of the time.  

-r

---

### Post by dribeas on 2008-10-03
> **rnodal said:**
> I think you misunderstood why I was asking. 
-r

:) I think there are more misunderstandings here. 

I just reasoned that even in this case, the extra cost is rather small, so that even in this case I would recommend what the OP did. It is one of those 'early optimization can end in later pessimization' kind of reasonings. I posted the rationale so that the OP understands what are the advantages and costs of each of the options.

Note that I did not try to hide the costs. But when designing you must be aware and beginners won't get to that line of reasoning on by themselves.

---

### Post by rnodal on 2008-10-03
I agree with you and after a little bit more of thinking about it I realized that the OP may want to do some work with the std::string and then send the results to that function that requires the c string. And as the OP expressed he/she feels more comfortable with C++ strings. 

-r

---

### Post by SledgeHammer_999 on 2008-10-03
Just to clarify things. I am a he. I used the g_print() function just to put a 'debug' feature i.e. to know if the code does what I expect it to do. The std::strings will be stored in a vector of std::strings. Most of the time I'll do comparisons between the strings. And when I find the suitable string I'll use the string.c_str() method to pass it to the function. (I am experimenting with gstreamer)

---

