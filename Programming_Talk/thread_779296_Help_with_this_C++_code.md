---
title: "Help with this C++ code"
date: 2008-05-02
forum: Programming Talk
---

### Post by thursgun on 2008-05-02
Compiled and tested on windows xp with Dev-C++. No problems there.

Now in ubuntu (8.04) compiled fine with g++, but I get this runtime error:

terminate called after throwing an instance of 'std::ios_base::failure'
  what():  basic_ios::clear
HIHIHIHIHIHIHIHIHIHIHIHIHIHIHIAborted

As you can see, the program never find the EOF of "moving.in". Don't know why. (of course everything is in the same folder, and the names are correct).

```
vector<int> Leer () 

{

     vector<int> elementos; 

     int    dato_numero;

     char   dato_string[8];

     char  *dato_char;

  

     ifstream archivo;
     archivo.exceptions(ifstream::eofbit | ifstream::badbit | ifstream::failbit | ifstream::goodbit);
     archivo.open("moving.in");

     if (archivo) {

        while (!archivo.eof()) {

              archivo.getline(dato_string,8);

              dato_char = strtok (dato_string," ");

              while (dato_char != NULL) {

                    dato_numero = atoi(dato_char);

                    elementos.push_back(dato_numero);

                    dato_char = strtok (NULL, " ");

              }
		cout << "HI";

        }

        archivo.close();

        return elementos;

     }

     else 

     {

          cout << "No se puede abrir el archivo";

     }

}
```

---

### Post by dwhitney67 on 2008-05-02
Yep... You are definitely missing a try/catch in your code.  I was able to duplicate the same runtime error you got.  Make sure you have something like the following in the function that calls Leer():
[PHP]
try
{
  vector<int> resultados = Leer();
}
catch ( ifstream::failure &e )
{
  cout << "Excepcion: " << e.what() << endl;
}[/PHP]

-----------------------
Forget this.... I've never seen someone use the exceptions() method from an ifstream, so my first thoughts would be to comment that statement out unless you fully understand it.  (Do you have a try/catch in the main program??)

Forget this.... Second, I would remove the eof() test from your while-conditional, and place the getline() statement in its place.  This will prevent one less iteration of the loop.

This is still important... Lastly, make sure you return the (empty) vector 'elementos' even if you are unable to open the input file.  The function signature demands that you return something.

So something like:

[PHP]
vector<int> Leer()
{
   ...
   //archivo.exceptions(ifstream::eofbit | ifstream::badbit | ifstream::failbit | ifstream::goodbit);
   ...
   if (archivo) {
      while ( archivo.getline(dato_string,8) ) {
         //archivo.getline(dato_string,8);
         ...
      }
   }
   else
   {
      cout << "No se puede abrir el archivo" << endl;
   }

   return elementos;
}[/PHP]

---

### Post by thursgun on 2008-05-02
Thank you for your reply dwhitney67.

I did as you said, but now i get this:

```
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
```


P.S: No, I have no try{..}

EDIT: Didn't read your last edit...

---

### Post by thursgun on 2008-05-02
I'm still getting an endless loop... :(

This is the whole original program: (previous one + main)
[PHP]

#include <iostream>  
#include <fstream>      
#include <vector>      
#include <string>      

using namespace std;


/*============================================================================*/
vector<int> Leer () 

{

     vector<int> elementos; 

     int    dato_numero;

     char   dato_string[8];

     char  *dato_char;

  

     ifstream archivo("moving.in");

     if (archivo.is_open()) {

        while (!archivo.eof()) {

              archivo.getline(dato_string,8);

              dato_char = strtok (dato_string," ");

              while (dato_char != NULL) {

                    dato_numero = atoi(dato_char);

                    elementos.push_back(dato_numero);

                    dato_char = strtok (NULL, " ");

              }

        }

        archivo.close();

        return elementos;

     }

     else 

     {

          cout << "No se puede abrir el archivo";

     }

}
/*============================================================================*/

//Main

int main () {

    Leer();
    return 0;

}   
[/PHP]

This is the input: "moving.in"
```

15

2

3 4

5 70

3

34 56

21 89

32 90

2

34 45

32 56

5

56 78

12 34

45 74

123 345

13 400

4

9 12

3 5

4 78

45 46

2

3 4

5 70

3

34 56

21 89

32 90

2

34 45

32 56

5

56 78

12 34

45 74

123 345

13 400

4

9 12

3 5

4 78

45 46

2

3 4

5 70

3

34 56

21 89

32 90

2

34 45

32 56

5

56 78

12 34

45 74

123 345

13 400

4

9 12

3 5

4 78

45 99

```

---

### Post by dwhitney67 on 2008-05-02
I don't understand.  I copied your code (made some beautification changes) and copied your input file (moving.in).

I was able to compile the code and run it without any problems.  Here's the code after I beautified it to my liking:
[PHP]#include <iostream>  
#include <fstream>      
#include <vector>      

using namespace std;


vector<int> Leer () 
{
  vector<int> elementos; 

  ifstream archivo("moving.in");

  if (archivo.is_open())
  {
    char   dato_string[8];

    while ( archivo.getline( dato_string , sizeof dato_string ) )
    {
      char *dato_char = strtok( dato_string," " );

      while ( dato_char != NULL )
      {
        int dato_numero = atoi( dato_char );

        elementos.push_back( dato_numero );

        dato_char = strtok( NULL, " " );
      }
    }

    archivo.close();
  }
  else 
  {
    cout << "No se puede abrir el archivo";
  }

  return elementos;
}


int main ()
{
  vector<int> resultados = Leer();

  // output resultados
  for ( unsigned int i = 0; i < resultados.size(); ++i )
  {
    cout << resultados[i] << endl;
  }

  return 0;
}[/PHP]

---

### Post by thursgun on 2008-05-02
Thank you. It actually works. Maybe I had those errors because I was mixing it with other functions.

Thanks you again.

---

### Post by thursgun on 2008-05-02
I've just noticed that resultados.size() is 25. But the input has about 55 numbers.

What is wrong?

---

### Post by dwhitney67 on 2008-05-02
With the code I presented above, I get 112 values.  You might want to consider testing with a smaller test file.  Here's the "moving.in" input file I used which has your original data:
```
15
2
3 4
5 70
3
34 56
21 89
32 90
2
34 45
32 56
5
56 78
12 34
45 74
123 345
13 400
4
9 12
3 5
4 78
45 46
2
3 4
5 70
3
34 56
21 89
32 90
2
34 45
32 56
5
56 78
12 34
45 74
123 345
13 400
4
9 12
3 5
4 78
45 46
2
3 4
5 70
3
34 56
21 89
32 90
2
34 45
32 56
5
56 78
12 34
45 74
123 345
13 400
4
9 12
3 5
4 78
45 99
```

---

### Post by dwhitney67 on 2008-05-02
Btw, if you really want to focus exclusively on C++, you can opt to forgo using strtok() from the C-library, and use an istringstream container.

Here's how:
[PHP]#include <sstream>
...
    while ( archivo.getline( dato_string , sizeof dato_string ) )
    {
/*
 *    Remove this section of code
 *
      char *dato_char = strtok( dato_string," " );

      while ( dato_char != NULL )
      {
        int dato_numero = atoi( dato_char );

        elementos.push_back( dato_numero );

        dato_char = strtok( NULL, " " );
      }
*/

//    Add this section
//
      istringstream istr( dato_string );
      int value;

      while ( istr >> value )
      {
        elementos.push_back( value );
      }
    }
...[/PHP]

---

