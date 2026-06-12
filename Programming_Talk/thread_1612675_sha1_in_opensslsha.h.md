---
title: "sha1 in openssl/sha.h"
date: 2010-11-03
forum: Programming Talk
---

### Post by fantastic on 2010-11-03
I've been just trying to return a SHA1 hash in C++ - nothing fancy - so I thought.

I finally got it to compile with no errors but SHA1_Final returns "1", which means it works. I've look over the [docs on OpenSSL]("http://www.openssl.org/docs/crypto/sha.html"), but cannot figure out where to put a string to find it's hash nor how the result is returned. The documentation states it's placed in md, but do not understand how it works.

Here is what I have:

```

#include <iostream>
#include <stdio.h>
#include <string.h>
#include <openssl/sha.h>

int main()
{
    unsigned char *SHA1(const unsigned char *d, unsigned long n, unsigned char *md);
    int SHA1_Init(SHA_CTX *c);
    int SHA1_Update(SHA_CTX *c, const void *data, unsigned long len);
    int SHA1_Final(unsigned char *md, SHA_CTX *c);
    std::cout << SHA1_Final << std::endl;

    return 0;
}

```


If you have any suggestions I would appreciate it, or any or site with either a better explanation or a working example.

---

### Post by johnl on 2010-11-03
You just copied the function definitions.  You need to actually call the functions. (actually, in this case you probably just need SHA1())

```

#include <iostream>
#include <iomanip>
#include <string>
#include <openssl/sha.h>

using namespace std;

int main(int argc, char* argv[])
{
    string input;

    // a sha1 hash is 20 bytes
    unsigned char hash[20];

    cout << "enter your string: ";
    getline(cin, input);
  
    // compute the sha1 of the input, and store it our  hash array
    SHA1((unsigned char*)input.c_str(), input.size(), hash);
    // the above is the exact same thing as doing:
    //    SHA_CTX ctx;
    //    
    //    SHA1_Init(&ctx);
    //    SHA1_Update(&ctx, input.c_str(), input.size());
    //    SHA1_Final(hash, &ctx);

    // since the hash array just contains a bunch of bytes,
    // print them as hexadecimal values
    cout << "the hash was: ";
    for(int i = 0; i < 20; ++i) {
        cout << hex << setw(2) << setfill('0') << (int)hash[i];
    }
    cout << endl;
}

```

Example:

```

ledbettj@stone:~/Projects/test$ g++ -Wall test.cc -lssl -o test
ledbettj@stone:~/Projects/test$ ./test 
enter your string: hello world
the hash was: 2aae6c35c94fcfb415dbe95f408b9ce91ee846ed

```

---

### Post by fantastic on 2010-11-03
Thanks JohnL.

I saw a similar example before and NetBeans failed to compile it:

```
/home/user/NetBeansProjects/hash test/main.cpp:19: undefined reference to `SHA1'
```

Line 19 is:
```
SHA1((unsigned char*)input.c_str(), input.size(), hash);
```

I tried compiling it through the shell it worked:

```
g++ -Wall main.cpp -lssl -o test
```

I must have something configured wrong in NetBeans. I'll look into it. At least I understand how it's done.

Thank you again.


> **johnl said:**
> You just copied the function definitions.  You need to actually call the functions. (actually, in this case you probably just need SHA1())

```

#include <iostream>
#include <iomanip>
#include <string>
#include <openssl/sha.h>

using namespace std;

int main(int argc, char* argv[])
{
    string input;

    // a sha1 hash is 20 bytes
    unsigned char hash[20];

    cout << "enter your string: ";
    getline(cin, input);
  
    // compute the sha1 of the input, and store it our  hash array
    SHA1((unsigned char*)input.c_str(), input.size(), hash);
    // the above is the exact same thing as doing:
    //    SHA_CTX ctx;
    //    
    //    SHA1_Init(&ctx);
    //    SHA1_Update(&ctx, input.c_str(), input.size());
    //    SHA1_Final(hash, &ctx);

    // since the hash array just contains a bunch of bytes,
    // print them as hexadecimal values
    cout << "the hash was: ";
    for(int i = 0; i < 20; ++i) {
        cout << hex << setw(2) << setfill('0') << (int)hash[i];
    }
    cout << endl;
}

```

Example:

```

ledbettj@stone:~/Projects/test$ g++ -Wall test.cc -lssl -o test
ledbettj@stone:~/Projects/test$ ./test 
enter your string: hello world
the hash was: 2aae6c35c94fcfb415dbe95f408b9ce91ee846ed

```

---

