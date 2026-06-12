---
title: "c++ stringstream issue"
date: 2006-01-15
forum: Programming Talk
---

### Post by oldmanstan on 2006-01-15
ok, this is an edit, the below problem is solved, figured it out right after posting, i needed to include <string> and <sstream>, oops. however, what is the difference between ostringstream and stringstream?

Ok, here's what i'm trying to do, convert an int to a std::string. i'm trying to use the stringstream type, i'm basically copying an example i found using google, but mine won't compile, here's the code basically...

```

std::stringstream ResultStream;
ResultStream << i;
return ResultStream.str();

```

however, when i compile it using g++ i get the following error:

```
bigints.cpp:212: error: aggregate &#8216;std::stringstream ResultStream&#8217; has incomplete type and cannot be defined
```

any ideas? thanks a bunch!

---

### Post by Viro on 2006-01-15
std::stringstream is the superclass that contains some abstract methods. That's why you can't instantiate it directly. Instead, you should work with istringstream and ostringstream. You use istringstream when you want to convert a string to some primitive type like a float or an int. If you want to convert a float/int or something else to a string, use ostringstream.

If you're familiar to C, you should view istringstream as a kind of scanf and ostringstream as a kind of printf.

---

### Post by thumper on 2006-01-15
[QUOTE=Viro]std::stringstream is the superclass that contains some abstract methods. That's why you can't instantiate it directly. Instead, you should work with istringstream and ostringstream. You use istringstream when you want to convert a string to some primitive type like a float or an int. If you want to convert a float/int or something else to a string, use ostringstream.[/QUOTE]
Unfortunately not correct.

You can instantiate std::stringstream quite fine thank you very much ;)

In fact that is exactly what [boost::lexical_cast ](http://www.boost.org/libs/conversion/lexical_cast.htm) uses.

std::stringstream inherits from both std:: ostringstream and std::istringstream.

**oldmanstan** sorry, can't say why you are getting that error without seeing the code and your compilation command.

```

#include <boost/lexcal_cast.hpp>
//...
int val = 42;
std::string vals = boost::lexical_cast<std::string>(val);

```

---

### Post by emsee on 2007-12-26
here is why:
 you forgot this #include <sstream>
just fuxed same thing in my code

---

### Post by tiamatschosen on 2013-02-19
slightly different issue. 

here is the code:
```

void *U_Tunnel(void *city)
{
    string *destination;
    destination = (string *)city;
    int num = traincount;
    stringstream out;
    
    out << *destination << " Train " << num << " wants to enter the tunnel.\n";
    cout << out;
    out.str("");
    
    do
    {
        if (pthread_mutex_trylock(&Tunnel) == 0)
        {
            if (pthread_mutex_trylock(&Tunnel) == 0)
                pthread_mutex_lock(&Tunnel);
            out << *destination << " Train " << num << " is in the tunnel.\n";
            cout << out;
            out.str("");
            pthread_yield();
            if (pthread_mutex_trylock(&Tunnel) != 0)
                pthread_mutex_unlock(&Tunnel);
            out << *destination << " Train " << num
                << " is exiting the tunnel.\n";
            cout << out;
            out.str("");
            pthread_exit(NULL);
        }
        else
            pthread_yield();
    }while(1);
    
}

```here is the output:

```
0x7f54edf56d880x7f54ed755d880x7f54eef58d880x7f54ef759d880x7f54eff5ad880x7f54ef759d880x7f54ef759d880x7f54eef58d880x7f54eef58d880x7f54edf56d880x7f54edf56d880x7f54ecf54d880x7f54eff5ad880x7f54eff5ad880x7f54ee757d880x7f54ecf54d880x7f54e77fdd880x7f54ecf54d880x7f54ed755d880x7f54ed755d880x7f54e7ffed880x7f54ee757d880x7f54ee757d880x7f54e7ffed880x7f54e7ffed880x7f54e77fdd880x7f54e77fdd880x7f54e6ffcd880x7f54e6ffcd880x7f54e6ffcd88
```

i know its probably something kind of simple but im blined to it.

---

### Post by QIII on 2013-02-19
Thank you for sharing.  Everyone&#8217;s questions and answers are valuable.

But if a thread has had no activity for about a year or more, it is best to start a new thread of your own because you will be more likely to get a response.    This thread is very, very old.

Please feel free to add a link to this thread in the new one you start.

*Thread **closed***.

---

