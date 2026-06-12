---
title: "C++ - Returning an array from a function"
date: 2007-07-01
forum: Programming Talk
---

### Post by def_77 on 2007-07-01
I'm a relatively new C++ programmer, and I've been working on a function that can return roman numeral values given an integer. The function takes an int value, and I'd like it to be able to return a char array, since you dont seem to be able to return strings. So far my function only returns the first character. The framework of it is shown below -
```
char rconvert(int num){
	char converted = new char[MAX_SIZE];
 ... //Conversion taking place
 ... //here
	return *converted;
}

int main(){
    cout << rconvert(1111);
}
```

ive had a look to see how other people have overcome this problem but I havent found any useable solutions. Help appreciated.

---

### Post by Jessehk on 2007-07-01
One solution is to dynamically allocate memory inside the function using *new*, and return the pointer to the memory. At this point, you can either call *delete [] * on the pointer (which is prone to programmer error), or you can encapsulate the pointer into a class such as *std::auto_ptr<T>* or *boost::shared_ptr<T>* which will automatically call *delete []* on the pointer once it goes out of scope.

For the boost libraries (which influence the C++ standard and are well-written), see [http://www.boost.org](http://www.boost.org). I believe there's an Ubuntu package in the repositories.

Here's an example:
```

#include <memory>

int *arraycreate( int size, int elem ) {
    int *result = new int[size];
    
    for ( int i = 0; i < size; i++ )
        result[i] = elem;
    
    return result;
}

int main() {
    std::auto_ptr<int>( arraycreate( 3, 0 ) );
}

```

:)

---

### Post by Soybean on 2007-07-01
> **def_77 said:**
> since you dont seem to be able to return strings.
Wait... why can't you return strings?

```

#include <iostream>
#include <string>
using namespace std;

string rstring()
{
        string r("this is a string");
        return r;
}

int main(int argc, char *argv[])
{
        string x = rstring();
        cout << x << endl;
        return 0;
}

```

Another option is to take a reference to a string (or character array) as a parameter, and use that to return your result.

---

### Post by def_77 on 2007-07-01
> **Soybean said:**
> Wait... why can't you return strings?


whoops. I tried again and realised I had forget to declare the strings namespace. Thnx for that. I now have my return working :)
Mite as well post up what I made if anyone has any suggestions. I know its a messy long winded solution, and I'm not to sure on correct programming practises yet -

```

#include <string.h>
using std::string;

string rconvert(long int num){
	string str;
	//Add M's
	short int result; result = num / 1000;short int n = 0;
	if(result >= 1){
		for(int i = 0; i < result; i++){
			str.append("M");n++;
		}
	num = num - (1000 * result);
	}
	//Add D's
	result = num / 500;
	if(result >= 1){
		for(int i = 0; i < result; i++){
			str.append("D");n++;
		}
	num = num - 500;
	}
	//Add C's
	result = num / 100;
	if(result >= 1){
		for(int i = 0; i < result; i++){
			str.append("C");n++;
		}
	num = num - (100 * result);
	}
	//Add L's
	result = num / 50;
	if(result >= 1){
		for(int i = 0; i < result; i++){
			str.append("L");n++;
		}
	num = num - 50;
	}
	//Add X's
	result = num / 10;
	if(result >= 1){
		for(int i = 0; i < result; i++){
			str.append("X");n++;
		}
	num = num - (10 * result);
	}
	//Add V's and I's
	if(num == 4){ str.append("IV"); }else{
		result = (num + 5) / 5;
		if(result >= 1){
			str.append("V");n++;
			result = num - 5;
		}
		for(int i = 0; i < result; i++){;
			str.append("I");n++;
		}
	}
	return str;
}
```

---

### Post by hardyn on 2007-07-01
what about passing in a pointer, and not actully return an array?

---

### Post by brooksbp on 2007-07-01
def_77: When you dive deeping into C programming you'll learn that passing pointers to arrays instead of arrays themselves is much more efficient.

---

### Post by aks44 on 2007-07-01
> **Jessehk said:**
> At this point, you can either call *delete [] * on the pointer (which is prone to programmer error), or you can encapsulate the pointer into a class such as *std::auto_ptr<T>* or *boost::shared_ptr<T>* which will automatically call *delete []* on the pointer once it goes out of scope.

std::auto_ptr and boost::shared_ptr don't call delete[] on destruction, but **delete**. So they are **not** suitable to encapsulate an array pointer allocated by new[].

Unless you have *very* specific requirements, std::vector is the way to go when dealing with arrays.

---

### Post by halfhp on 2007-07-08
> **brooksbp said:**
> def_77: When you dive deeping into C programming you'll learn that passing pointers to arrays instead of arrays themselves is much more efficient.

Hmm...from the limited 'diving' Ive done, Ive always thought that you cant really pass an array by value unless you wrap it in a struct.  So if an array is always passed by reference, what exatly is the difference?  Most people will even tell you that the name of the array decays into a pointer, (which I think Ive read somewhere is also not absolutely true but still more or less equivalent)

Is this not true?

---

### Post by Jessehk on 2007-07-08
> **aks44 said:**
> std::auto_ptr and boost::shared_ptr don't call delete[] on destruction, but **delete**. So they are **not** suitable to encapsulate an array pointer allocated by new[].

Unless you have *very* specific requirements, std::vector is the way to go when dealing with arrays.

Ah, my apologies. I had forgotten about that little problem. :(

---

