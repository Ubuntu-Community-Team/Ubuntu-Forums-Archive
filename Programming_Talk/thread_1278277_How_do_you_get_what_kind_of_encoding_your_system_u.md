---
title: "How do you get what kind of encoding your system uses in c/c++?"
date: 2009-09-29
forum: Programming Talk
---

### Post by Ubu-freak on 2009-09-29
In linux terminal one would type 
  ```
locale charmap
```  in order to see what kind of character-encoding your system uses, eg UTF-8. My question is how would you do this using c/c++.

---

### Post by dwhitney67 on 2009-09-29
Try something like:
```

#include <string>
#include <iostream>
#include <cstdlib>

int main()
{
   const char* lang = getenv("LANG");
   std::string encoding = "unknown";   // default this to whatever you please.

   if (lang)
   {
      // I'm not sure all of this is necessary;
      // but I did yield UTF-8 on my system.
      //
      size_t dot = std::string(lang).find_last_of('.');

      if (dot != std::string::npos)
      {
         encoding = std::string(lang).substr(dot + 1);
      }
   }

   std::cout << "Encoding = " << encoding << std::endl;
}

```

---

### Post by johnl on 2009-09-29
```

#include <locale>
#include <iostream>
#include <string>

using namespace std;


int main()
{
    cout << locale("").name() << endl;


    return 0;
}


```

You can also pass in a locale name to see if the system supports it:

```

#include <locale>
#include <iostream>
#include <string>

using namespace std;


int main()
{
    locale l;
    try {
        l = locale("en_US.UTF-8");   
        cout << l.name() << " is supported" << endl;
    } catch (runtime_error& err) {
        cout << "locale not supported" << endl; 
    }
    return 0;
}


```


Keep in mind that if you want to use a unicode locale, you will need to use wide character strings (wchar_t* , std::wstring, L"string constant") and associated functions.

---

